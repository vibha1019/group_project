# blog

I added two features that are relevant in the game. 
I created a file called PlatformFilter.js which extends GameObject. I added a change Appearance function that applies filters to platforms.

<code>
constructor(canvas, image, data, xPercentage, yPercentage) {
        super(canvas, image, data);
        this.platformX = xPercentage * GameEnv.innerWidth;
        this.platformY = yPercentage;
        this.direction = -1; // Move up
        this.speed = 0.5; // Reduced speed
        this.maxTop = 300;


movePlatform() {
        let currentPosition = parseInt(this.canvas.style.top) || 0;

        // Only move up
        if (currentPosition <= this.maxTop) { // Changed condition to check if it's below maxTop
            this.direction = 1; // Change direction to move down
        } else if (currentPosition >= (GameEnv.bottom - this.canvas.height)) { // Ensure it stays within the bottom of the game environment
            this.direction = -1;
        }

        this.canvas.style.top = currentPosition + this.direction * this.speed + 'px';
        this.draw();
    }
}
<code>

In the platform code above, it defines the action of the game object. The constructors provide the variables needed to construct the object, such as the image, direction and x and y percentages. For the moving platform, we wanted it to carry out a specific function that is set off by the player. We created a movePlatform function describes the objects function. 

<code>
 changeAppearance() {
       
        const element = document.getElementById('yourElementId');
    
    // Apply CSS filter
    //this.canvas.style.filter = 'blur(5px)';
    this.canvas.style.filter = 'hue-rotate(90deg)';
    //this.canvas.style.filter = 'sepia(0.9)';
    //this.canvas.style.filter = 'drop-shadow(5px 5px 5px rgba(0, 0, 0, 0.5))';

    }
<code>




The next feature I added is the moving platform function. I created the move Platform function by first initializing the platform position before adding code to check the position of the platform to move it upwards and downwards. This.draw() gives a visual representation so that the image moves with the hitbox. I also had to define more variables in the constructor, such as the direction, speed, and a maximum top position which was not previously needed. 

<code>
constructor(canvas, image, data, xPercentage, yPercentage) {
        super(canvas, image, data);
        this.platformX = xPercentage * GameEnv.innerWidth;
        this.platformY = yPercentage;
        this.direction = -1; // Move up
        this.speed = 0.5; // Reduced speed
        this.maxTop = 300;


movePlatform() {
        let currentPosition = parseInt(this.canvas.style.top) || 0;

        // Only move up
        if (currentPosition <= this.maxTop) { // Changed condition to check if it's below maxTop
            this.direction = 1; // Change direction to move down
        } else if (currentPosition >= (GameEnv.bottom - this.canvas.height)) { // Ensure it stays within the bottom of the game environment
            this.direction = -1;
        }

        this.canvas.style.top = currentPosition + this.direction * this.speed + 'px';
        this.draw();
    }
}
<code>

The next feature I added is the moving platform function. I created the move Platform function by first initializing the platform position before adding code to check the position of the platform to move it upwards and downwards. This.draw() gives a visual representation so that the image moves with the hitbox. I also had to define more variables in the constructor, such as the direction, speed, and a maximum top position which was not previously needed. 

<code>
constructor(canvas, image, data, xPercentage, yPercentage) {
        super(canvas, image, data);
        this.platformX = xPercentage * GameEnv.innerWidth;
        this.platformY = yPercentage;
        this.direction = -1; // Move up
        this.speed = 0.5; // Reduced speed
        this.maxTop = 300;


movePlatform() {
        let currentPosition = parseInt(this.canvas.style.top) || 0;

        // Only move up
        if (currentPosition <= this.maxTop) { // Changed condition to check if it's below maxTop
            this.direction = 1; // Change direction to move down
        } else if (currentPosition >= (GameEnv.bottom - this.canvas.height)) { // Ensure it stays within the bottom of the game environment
            this.direction = -1;
        }

        this.canvas.style.top = currentPosition + this.direction * this.speed + 'px';
        this.draw();
    }
}
<code>
