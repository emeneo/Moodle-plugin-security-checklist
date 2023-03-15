https://docs.moodle.org/dev/Plugin_contribution_checklist#Security
Never trust the user input.
Do not access superglobals like $_REQUEST directly, use wrappers like required_param() with correct type declared to sanitize input.
Always use placeholders in custom SQL queries (? or :named).
Always check for the sesskey before taking an action on submitted data.
Check for require_login().
Always check that the user has appropriate capabilities before displaying the widgets and before taking the actual action.
Avoid using malicious functions like call_user_func(), eval(), unserialize() and so on, especially when they would be called with user-supplied data
