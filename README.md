# FT\_HideAndSeek

This mechanic is a change to the player around with some AI functionality. I have built a script that allows an AI to follow the player or move to random locations.

Use P to show the navmesh in the Engine.

An interesting view on this is the [OpenAI Agent-based approach, and the glitches they learn](https://www.youtube.com/watch?v=kopoLzvh5jY)

## Overview
Controls:
Click, and the player will move to the click position if possible

# Where to find the relevant scripts
In the C++ Classes->Public->StalkerAIController
I have made a separate Blueprint for the AI in Top Down->Blueprints->BP_TopDownAI

# Task
- Play about the bool on the AI 
- Try to add feedback to the player on what the AI is doing

# Changes from base project
You will notice that both AI and Player are actually driven by the same script! This is because the character script handles movement, and the input comes from the IMC or an AI controller. So only minor changes were made to have an AI take control. This is overall good coding practice; you see it in how [easy modders can take control of enemies in games.](https://www.youtube.com/watch?v=8yCiUW1v58Q)

# Challenges
Tes your might

## Easy
* Play around with some of the different AI logic I have put into the **StalkerAIController (header file)**, by changing the bIsStalkingPlayer bool
* Notice the AI gets stuck on the platform a lot. Maybe add some more jump points to allow smoother traversal
* Using the getpawn() (Shown in the **StalkerAIController->Tick**), you can adjust the character parameters, try to make the stalker **2/3rd** of the player max speed. You can change the player speed with

```
Cast<ACharacter>(GetPawn())->GetCharacterMovement()->MaxWalkSpeed = ;
```

## Medium
* Look at the **FT\_HUD** focus topic, and the Naïve State machine, try to implement that with 3 key states, IDLE (Player is more than 1000 away), HUNT (Player is less than 1000 away), KILLED (Player is less than 100 away, stop player movement). See how I do the distance in **StalkerAIController->Tick**
```
if (FVector::Dist(GetPawn()->GetActorLocation(), Target) < 200.0f) 
```
* Add feedback to the player, so they know when they are safe, hunted and dead. This could be audio, a sign in a Widget, or a screen overlay effect 
* Add an Objective, such as a collectables for the player (**FT_ReloadingAndAmmo**), that affects the AI, e.g., every time the player collects, the AI's speed is slightly increased, and the detection radius increases

## Hard
* Add subtle feedback like a screen effect to show when the player is in danger, such as in [**Slenderman and the Eight Pages**](https://dylanhoctor.itch.io/slender-the-eight-pages-reupload)
* See how you can implement a patrol route for the AI, like in the lab sheets
* Add feedback to the AI, which is either an icon showing [line of sight (Unreal has C++ built-in function)](https://dev.epicgames.com/documentation/en-us/unreal-engine/BlueprintAPI/Controller/LineOfSightTo), or a ghost image of where the player was last seen, forcing it to go to that point first

## Very Hard
* Work on your assignment
* You only have 3 weeks of support left on it
* Easter is not as long as you think


# Reference
Content is made by Connah Kendrick (Connah.Kendrick@mmu.ac.uk) using the Unreal Engine 3rd Person Template for the MMU 1st year Game Mechanics Module taught to both Game Development and Game Design Students. 


