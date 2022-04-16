Snowflake RBAC Viewer
=====================

Simple Python script that generates DOT and HTML files with the role hierarchy, and the user-role hierarchy from a Snowflake account. You can visualize directly the HTML files in your browser. The DOT files are just an alternative, to be used with either a **Graphviz Preview** VSC extension - alongside the **Graphviz (dot) language support ...** extension - or with a free online visualizer like [viz-js.com](http://viz-js.com/).

# Database Profile File

Create a **profiles_db.conf** copy of the **profiles_db_template.conf** file, and customize it with your own Snowflake connection parameters. Your top [default] profile is the active profile, considered by our tool. Below you may define other personal profiles, that you may override under [default] each time you want to change your active connection.

We connect to Snowflake with the Snowflake Connector for Python. We have code for (a) password-based connection, (b) connecting with a Key Pair, and (c) connecting with SSO. For password-based connection, save your password in a SNOWFLAKE_PASSWORD local environment variable. Never add the password or any other sensitive information to your code or to profile files. All names must be case sensitive, with no quotes.

We always collect RBAC-related data from the whole Snowflake account, so do not specify a database or a schema in the profile file. Also, while all collected data is metadata, there is no need for a virtual warehouse.

# CLI Executable File

You can invoke the tool directly from a Terminal window in Visual Source Code, as it follows:

**<code>python rbac-viewer.py</code>**  

To compile into a CLI executable:

**<code>pip install pyinstaller</code>**  
**<code>pyinstaller --onefile rbac-viewer.py</code>**  
**<code>dist/rbac-viewer</code>**  

# The Role Hierarchy

A graph with the role hierarchy - including the system roles - is saved in the output/account-roles DOT and HTML files:

![Roles Hierarchy](/images/account-roles.png)

# The User-Role Hierarchy

A graph with the user-role hierarchy - including the system roles - is saved in the output/account-users DOT and HTML files:

![Users Hierarchy](/images/account-users.png)
