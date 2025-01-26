<h1 align=center> Roblox Studio: The workshop </h1>

|Workshop's Difficulty|
|:-:|
|▰▰▱▱ Medium 😐|

## `0` | Setting Up
> ${\textsf{\color{#f00}╸}}$━━━━━━━━━━━━━━━━━━━ `0xp` `mandatory`

See this little bar ? This is how much you'vee learned about
the basics of roblox studio !

But first, you will have to set the things up:
1. Have a Windows Boot
2. Install Roblox & Roblox Studio

If you're using Linux and don't have windows, please follow
[this tutorial](https://devforum.roblox.com/t/the-ultimate-guide-on-how-to-play-roblox-on-linux/3171920)
to install roblox studio.

Now, you should be able to create a game after launching Roblox
Studio, so please create once.

Now that you created your game, it should look like the image here at the bottom left.

<img align=right width=45% src="https://github.com/user-attachments/assets/3662084e-c172-42ac-8f88-ffeb797cc7ed">

As you can see, you have serveral windows that shows up, here are the ones
on this screenshot:
- the **explorer** at the left, that allows you to manage your instances
- the **properties** on the top right, that allows you to change some
properties of an instance (size, color, name...)
- the **output** on the bottom right, that shows the results of `print` &
`warn` functions, as long as the errors if you encounter any.
- at the center, you have your **workspace**, which is basically what your
game is going to look like.


## `1` | I'm not like the other parts
> ${\textsf{\color{#c00}╸}}$━━━━━━━━━━━━━━━━━━━ `5xp` `mandatory`

Your part will not be like others. It will be special.

1. First, let's setup our part
   Here’s what you need to do:
   - Your first step will be to create a Part
   - Then, lets make this part a bit more splendid, here is what you will have to change:
     - **Color**: Change it to **Really Red**
     - **Size**: Set the size to **(10, 3, 20)**.
     - **Position**: Set the position to **(0, 50, 0)**.
     - **Anchored**: Don’t forget to set it as **Anchored**

> [!NOTE]
> What does anchored means ?

2. Now, let's make our part do something
   In roblox studio, we can do actions to everything using scripting.

   Make a script that changes the color of the Part after 3 seconds
   ```lua
   wait(3) -- Wait for 3 seconds
   script.Parent.BrickColor = BrickColor.new("Bright blue") -- Change the color to blue
   ```

   Once the script is inserted, the part should change color after 3 seconds of the game running.

4. **Make the Part Non-Collidable**:  
   Now let’s go one step further! After 3 seconds, make the part **Non-Collidable** (so players can walk through it). Update your script with this line of code:
   ```lua
   script.Parent.CanCollide = false -- Make the part non-collidable
   ```

5. **Create Another Part Named 'Foo'**:  
   We’ll add another part for some fun interaction. Create a new part named **Foo**, set it to position **(0, 5, 10)** and anchor it.

6. **Part Touch Event**:  
   Now for the fun part! We want the part to respond when something touches it. Add a new **Script** to the **Foo** part, and make it print a message when it’s touched. Here’s the basic structure for that:
   ```lua
   script.Parent.Touched:Connect(function(hit)
       print("Something touched Foo!")
       -- You can also print the name of the object that touched it!
       print(hit.Name)
   end)
   ```

7. **Make the Part Fall**:  
   When **Foo** is touched, we’ll make it fall. Update your script to un-anchor the part, so it will start falling:
   ```lua
   script.Parent.Anchored = false -- Un-anchor the part to make it fall
   ```

8. **Create a Little Hobby**:  
   As a final challenge for this exercise, let’s add a cool little effect. After 3 seconds of being touched, the part should start falling again. Modify your script to do this by using `wait(3)` before un-anchoring it again.

---

## `2` | Second Exercise: Parenting and Children 🤖
> ${\textsf{\color{#090}╸}}$━━━━━━━━━━━━━━━━━━━ `10xp`

Now that we’ve got some basic scripting down, let’s dive into **parenting** and **children**! This is super important for handling parts and objects in Roblox.

### Exercise: Getting Parents and Children

1. **Getting the Parent**:  
   Every object in Roblox has a **parent** — that’s the object that contains it. Let’s start by printing the parent of a part:
   ```lua
   print(script.Parent.Parent) -- This will print the parent of the part.
   ```

2. **Getting Children**:  
   You can also get a part’s **children**, which are the objects inside it. Here’s how to print all of the children of a part:
   ```lua
   for _, child in ipairs(script.Parent:GetChildren()) do
       print(child.Name) -- Prints the name of each child
   end
   ```

3. **Waiting for Children**:  
   Sometimes, you might need to wait for a child to appear. Here’s a simple example of how to wait for a new child:
   ```lua
   script.Parent.ChildAdded:Wait() -- Waits for a child to be added
   print("A new child has been added!")
   ```

4. **Finding the First Child**:  
   If you want to find the first child of a certain class (e.g., a **Part**), you can do it like this:
   ```lua
   local firstPart = script.Parent:FindFirstChildOfClass("Part")
   print(firstPart.Name) -- Prints the name of the first Part found
   ```

   This is helpful when you want to make sure a certain type of object exists before doing something with it.

---

## `3` | Third Exercise: Humanoids 🧍‍♂️
> ${\textsf{\color{#08f}╸}}$━━━━━━━━━━━━━━━━━━━ `15xp`

Let’s step things up with **Humanoids**! Humanoids are what make player characters in Roblox work, so it’s super important to understand them. Every player’s character is made of a **model** with a **Humanoid** inside.

### The Theory:

- The **Humanoid** is a special object that controls things like health, movement speed, and animations for a player’s character.  
- If you want to kill a player or adjust their properties (like health), you’ll interact with the **Humanoid** inside their character model.

### Exercise: Kill Brick (Make It Dangerous!)

1. **Create a Kill Brick**:  
   We’ll start by creating a red **Neon Part** that will act as a "kill brick." This part will reduce the health of any player that touches it.

   - Create a **Part** and set its **Material** to **Neon** and its **Color** to **Bright red**.

2. **Print What Touched the Part**:  
   Insert a **Script** into the kill brick, and make it print out the name of whatever touches it:
   ```lua
   script.Parent.Touched:Connect(function(hit)
       print(hit.Name) -- Prints the name of what touches the part
   end)
   ```

3. **Display the Parent**:  
   Next, let’s check what the parent of the object is:
   ```lua
   script.Parent.Touched:Connect(function(hit)
       print(hit.Parent) -- Prints the parent of the object that touched the part
   end)
   ```

4. **Check for Humanoids**:  
   Now we need to check if the object that touched the brick has a **Humanoid** inside it. If it does, we’ll set the **Humanoid Health** to 0, effectively "killing" the player.
   ```lua
   script.Parent.Touched:Connect(function(hit)
       local humanoid = hit.Parent:FindFirstChildOfClass("Humanoid")
       if humanoid then
           humanoid.Health = 0 -- Set the health to 0 (kill the player)
       end
   end)
   ```

