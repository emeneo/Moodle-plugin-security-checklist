https://docs.moodle.org/dev/Plugin_contribution_checklist#Security
Never trust the user input.
Do not access superglobals like $_REQUEST directly, use wrappers like required_param() with correct type declared to sanitize input.
Always use placeholders in custom SQL queries (? or :named).
Always check for the sesskey before taking an action on submitted data.
Check for require_login().
Always check that the user has appropriate capabilities before displaying the widgets and before taking the actual action.
Avoid using malicious functions like call_user_func(), eval(), unserialize() and so on, especially when they would be called with user-supplied data


From https://moodle.org/mod/forum/discuss.php?d=263614#p1142448 :
Database access and MySQLisms

It seems that quite a lot of authors of contributed plugins use MySQL database only when they are developing and testing their plugin. Moodle provides solid data manipulation API to deal with tiny differences in the syntax of SQL queries for all supported database engines (MySQL, PostgreSQL, MS SQL and Oracle). To make the plugin cross-db compatible, it is necessary to avoid DB engine specific syntax.

    Always use the $DB to access the database, avoid functions like mysql_query() to execute your query.
    Aim to use the most specific $DB method to do the job. That is, use $DB->get_records() if you can instead of $DB->get_records_sql() if you don't really need to.
    Do not use MySQL specific backtick quotes in the queries. It makes the query fail badly on other databases.
    Keep in mind that when using aggregations via GROUP BY, the SELECT part of the statement must explicitly contain all the fields your are grouping by. MySQL allows you to avoid them, which I personally really hate as it goes against some fundamental aspects of RDBMS - such as being deterministic.
    Do not use LIMIT in your queries. The $DB methods have explicit parameters for them.
    Neither use $CFG->prefix in your queries nor use hard-coded prefix like mdl_user. Use the {tablename} syntax and let the $DB driver to replace it with the actual table name.
    In order to prevent SQL injection, always use data placeholders in your queries (? or :named) to pass data from users into the queries.
    Always use the XMLDB editor to perform the schema changes via db/upgrade.php.

Our experience says that having the code tested against MySQL and PostgreSQL is usually enough to make sure it's cross-db compatible.
Prevent the cross-site request forgery

I was quite surprised how often this happens. Using the sesskey() feature to prevent CSRF attacks is a basic security protection you should include in your code whenever you are performing an action. When using the forms API, session key is checked implicitly. In all other cases it's your duty to perform the check. See this page for more details.
Check capabilities

It is important to highlight that permission checks must be done at both places. Not only there where your code is deciding whether or not a certain action link should be displayed (has_capability() is typically used there). It is essential to also check it just before you actually perform the action (that's where you want to call require_capability()). Remember, your code is open source. If require_capability() is missing, users can easily bypass your "protection" by submitting the data directly.
Sanitize user's input

You should never need to access superglobals $_GET, $_POST and $_COOKIE directly. Moodle provides wrappers for getting HTTP parameters - such as optional_param() and required_param(). Make sure you pick the most specific PARAM type for each of the parameters.




