The goal is to create a simple mechanic where a turret auto-fires at the player and deals damage to it. 

1. Open Unreal Engine and create a new Third-Person Template project
1. Open ThirdPerson > Blueprints > BP_ThirdPersonCharacter and add two float variables, MaxHealth and Health (or CurrentHealth). Compile the blueprint and default both to 100
1. Add an Event AnyDamage and decrement the Health value by the damage amount, print the new health to the screen.
1. Add a PainCausingVolume to the level and use it to test the damage event
1. Then delete the PainCausingVolume from the lebel
1. Open the Content Drawer and make a Blueprints folder under Content. Create a new Pawn blueprint called BP_Turret in this folder.
1. In the viewport, add a cylinder static mesh for the base and a capsule for the barrel 
1. Add a PawnSensingVolume and adjust the radius and sight angle. Add the OnSeePawn event and print something to test.
1. Add a float Damage variable to the BP_Turret, default it to 1 or 2.
1. Cast the pawn from the OnSeePawn to a BP_ThirdPersonCharacter and ApplyDamage on successful cast
1. Test the turret
1. At this point, can go back to ThirdPersonCharacter and add clamp to 0 if we want and a "you died!" string print
1. In BP_Turret, add a function "Shoot"
1. We don't have anything to shoot yet, create a new BP_Projectile blueprint (Actor)
1. Add a sphere, sphere collision, and ProjectileMovement components to BP_Projectile. Give the ProjecileMovement an initial speed of 1000-5000. Make the sphere scale .3 all around.
1. Add Damage to BP_Projectile and make it Instance Editable and Expose on Spawn
1. OnComponentBeginOverlap on the sphere collision, cast to BP_ThirdPersonCharacter like we did in the turret and apply the damage variable
1. Remove ApplyDamage from the turret. Add a new function called Shoot. Call it when sensing pawn.
1. Add an Arrow to serve as a fire point transform for the turret.
1. In Shoot, SpawnActorFromClass a BP_Projectile with the Arrow as Spawn Transform and pass in the variable Damage.
1. DestroyActor when projectile hits Player
1. The turret is not turning to face the Player yet, add this with WorldRotation
