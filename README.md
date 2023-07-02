Moodle plugin security checklist
================================
```
⬜ Not checked yet     ✅ checked
```


| No. | Description                                                       | Reference                 | Status |
| --- | ------------------------------------------------------------------| ------------------------- | ------ |
| 001 | Use latest security checklist                                     | [Latest Moodle plugin security checklist](https://github.com/emeneo/Moodle-Plugin-Security-Checklist)|⬜|
| 002 | Do not access superglobals like $_REQUEST, $_GET, $_POST and $_COOKIE directly. Use wrappers like required_param() and optional_param() with correct type declared to sanitize input. Make sure you pick the most specific PARAM type for each of the parameters.|[Plugin Contribution Checklist 3.10 Security](https://docs.moodle.org/dev/Plugin_contribution_checklist#Security), [Moodle Traffic forum](https://moodle.org/mod/forum/discuss.php?d=263614#p1142448) |⬜|   
| 003 | Always use data placeholders in custom SQL queries (? or :named) to pass data from users into the queries      | [Plugin Contribution Checklist 3.10 Security](https://docs.moodle.org/dev/Plugin_contribution_checklist#Security)    [Forum Post](https://moodle.org/mod/forum/discuss.php?d=263614#p1142448)                 |⬜|
| 004 |Check for require_login().       |  [Plugin Contribution Checklist 3.10 Security](https://docs.moodle.org/dev/Plugin_contribution_checklist#Security)                         |⬜|
| 005 | Always check that the user has appropriate capabilities before displaying widgets/ action links (has_capability() is typically used there)    |  [Plugin Contribution Checklist 3.10 Security](https://docs.moodle.org/dev/Plugin_contribution_checklist#Security) ,  [Moodle Traffic forum](https://moodle.org/mod/forum/discuss.php?d=263614#p1142448)  |⬜|
| 006 | Always check users capabilities just before you actually perform the action (call require_capability())    |   [Plugin Contribution Checklist 3.10 Security](https://docs.moodle.org/dev/Plugin_contribution_checklist#Security) ,  [Moodle Traffic forum](https://moodle.org/mod/forum/discuss.php?d=263614#p1142448)  
| 007 | Always check for the sesskey before taking an action on submitted data.  |[Plugin Contribution Checklist 3.10 Security](https://docs.moodle.org/dev/Plugin_contribution_checklist#Security)               |⬜|
| 008 | Avoid using malicious functions like call_user_func(), eval(), unserialize() and so on, especially when they would be called with user-supplied data      |  [Plugin Contribution Checklist 3.10 Security](https://docs.moodle.org/dev/Plugin_contribution_checklist#Security)                         |⬜|
| 009 | Use the Form API whenever possible for handling HTML forms | [Security guidelines](https://docs.moodle.org/dev/Security:Cross-site_request_forgery#What_you_need_to_do_in_your_code)     |⬜|
| 010 | GET requests should be used for getting information. So, for example, viewing a user's profile should be a GET request.POST requests should be used for changing things in the application. For example deleting a user should be a POST request.        |  [Security guidelines](https://docs.moodle.org/dev/Security:Cross-site_request_forgery#Use_HTTP_correctly)|⬜|
| 011 | Never display the Sesskey in the browser url bar or similar| [Secuirty guidelines](https://docs.moodle.org/dev/Security:Cross-site_request_forgery#Use_HTTP_correctly) |⬜|
| 012| Do not require outdated / insecure moodle plugins |  |⬜|
| 013| Do not include third party library code in your plugin package which ist already provided by moodle core (e.g jQuery) |[Moodle thrid party libraries](https://moodledev.io/general/community/credits/thirdpartylibs)  |⬜|
| 014| Keep included third party libraries up to date|  |⬜|
| 015| Never put any passwords etc. into the code/ comments|  |⬜|



