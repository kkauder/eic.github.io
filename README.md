
# EIC Software

This is the home of the EIC software website. It is currently under development.

Deployment: https://eic.github.io/

# Useful links

* The EIC Software Group page on the EIC User Group Website: http://www.eicug.org/web/content/eic-software
* The EIC User Group Wiki: https://wiki.bnl.gov/eicug/

# Navigation Logic Updates
* Menu logic updated for easier edits and maintenance
  * Items ordering and other characteristics of its appearance in the menu is no longer defined in Front Matter but instead in one centralized file, "menus.yml"
  * Both "menu" and "submenu" entries can now have an optional "exclude" attribute which if set results in this element being excluded from the layout while still being coded and documented, to simplify development
* Introduced sections to dropdown menus (with labels also defined in "menus.yml")

# Recent changes
* Removed the "EIC" menu category (still in the menu definition file, disabled until further notice)
* New labels for entries in the "About" dropdown menu
* Renamed the "teams" dropdown to "people" and added the "Software Group" page to it (added the "software-core" members to the "people" YAML file)

# In the works

Nested/paginated menu structure
