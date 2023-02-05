The problems you will have when creating a plugins system for your shiny UI project
===================================================================================

The goal of this presentation is to share not to say how to solve.

There are many systems using plugins written in Javascript like VSCode or Mattermost.
Headlamp also uses plugins to mainly change the UI but not only.

The plugin code is bundled in a Javascript file which includes any dependencies.
It also comes with a ``package.json`` file containing some information.

How to load plugins?
--------------------

To load plugins, there are two ways:

1. Either you have an *activate* method which tells the plugin developer exactly when the main plugin code is executed.
2. Without it, loading the code is itself the activation.

You could also have a *deactivate* method, which should allow the plugin to stop any ongoing work.
Nonetheless, deactivating does not mean unloading!

Plugins themselves
------------------

You have the choice between object-oriented code or functional one, which is a taste of matter.
If you plugin is an actual React component, you can use hooks in your plugin code.

You have two approches:

1. Declarative: plugins would be simpler to learn but they require more maintenance.
2. Imperative: it offers more flexibility but less control by the system.

You should also have an API for plugin functionnalities, *e.g.* having some functions to permit plugins to add menu to the topbar.
Those functions should take ID to help identifying to which plugin you are refeering.


Developer experience
--------------------

There should be a bootstrap process to create plugins, at least a directory of examples.
Developers should configure as little as possible, particularly the infrastructure.
By doing so, it avoids breakage.

Run plugins
-----------

You should ensure the compatibility before loading a plugin.
