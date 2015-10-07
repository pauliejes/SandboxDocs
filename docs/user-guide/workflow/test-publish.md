# Test Publishing

## Publishing 

Publishing a simulation world typically involves changing the World Settings on the simulated world's landing page.  Settings such as whether the Editor Tools should be shown or what camera users should be in upon login are commonly set to "publish" a world.  See the [World Settings](world-settings.md) section for other options that can be set when the owner of a world is ready to make it ready for other users.

## Testing

Typically, testing is done in the simulated world using the play, pause, and stop controls.  However, it can sometimes be difficult to iteratively change the settings of a world for publish, determining that something needs to be changed, and then changing the settings again to edit, and returning to edit.  

To mitigate this difficulty, a Test Publish mode is available.  While in Edit mode, you should see an option under the File menu called World Settings.  In "World Settings", you have the same options as are available on the Publish page. Fill these out as you would when publishing the world. You can use the "Test Publish" mode to get a real time view of exactly how the published world will behave. This feature will create a clone of your world on the server, set the publish settings, and launch it in a child window. The main window will be disabled. When the child window closes, the temporary world is delete off the server, and the main window is re-enabled.

Again, usually the play/pause feature of the editor should be enough to test, but you can use the above workflow to test aspects of your scene that play/pause cannot simulate - for instance, you might want to test code that responds to a users log in.