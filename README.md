A Director class/module to be used with the Impact javascript game engine (http://impactjs.com/).

This module essentially stores an array of levels which can be traveresed using different functions.


How to use:

  - Create a new plugins folder if one does not exist: `lib/plugins`
  - Create a new folder called director: `lib/plugins/director`
  - Place the `director.js` file within that folder.
  - Within the `main.js` file, require: `'plugins.director.director'`
  - Within game init, create a new director:

        MyGame = ig.Game.extend({
          
          font: new ig.Font( 'media/04b03.font.png' ),
          
          init: function() {
            ig.input.bind( ig.KEY.LEFT_ARROW, 'left' );
            ...
            this.myDirector = new ig.Director(this, [LevelMain,  LevelForest, LevelMountains]);
            ...
        }

From here you can use `this.myDirector` (or whichever name you choose) to navigate through levels.

Examples:

Create a new director:

      this.myDirector = new ig.Director(this, [LevelMain,  LevelForest, LevelMountains]);
      
      //Initializes the Director. The first parameter is the actual game object.
      //The next parameter is an array of levels to include. This may also be 
      //initialized with a single level that is not within an array as in:
      //new ig.Director(this, LevelMain);.

Append additional levels:

      this.myDirector.append([LevelDesert, LevelVolcano]);
      //Adds additionals levels to the end of the array of levels. This will
      //also accept a single level not contained in an array.

Go to the next level:

      this.myDirector.nextLevel();
      //Note: this will return false if already at the end of the array of levels.

Go to the previous level:

      this.myDirector.previousLevel();
      //Note: this will return false if already at the begining of the array of levels.

Go directly to a level:

      this.myDirector.jumpTo(LevelMountains);
     //Note: this will return false if the level cannot be found.

Go to the first level:

      this.myDirector.firstLevel();

Go to the last level:

      this.myDirector.lastLevel();

Reload the current level:

      this.myDirector.reloadLevel();



***Note: for those using the latest dev version of impactjs, .loadLevelDeferred(data) can be used instead by making the appropriate change within the Director's .loadLevel(levelNumber) function.
