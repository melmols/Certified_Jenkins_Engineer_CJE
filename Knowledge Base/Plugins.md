#Plugins

- A plugin is in .hpi format
- This is a JAR format with some special conventions (e.g. no web.xml)
- Apache Maven knows how to handle the hpi format
- Some plugins may be found using jpi
- Plugins are versioned artifacts
- You can upgrade and downgrade
- They may have dependencies (mandatory or optional)
- Plugins are located in ${JENKINS_HOME}/plugins
- Both hpi files and un-archived versions

##Available plugins

- Plugins are grouped logically, which is sometimes helpful
- Use the Filter box if you are looking for something in particular
- Right click on the title of a plugin to display documentation about that plugin in a new tab
- Always read the documentation before installing a plugin
- Note that plugins with _known _security or other issues are identified
- Installed Plugins
- You can disable, downgrade, or uninstall plugins:




