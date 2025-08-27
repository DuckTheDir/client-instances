# client-instances
Add client Instances with this module easily and with chunk based culling for them.

--- !!! CULLING IS ONLY WORKING ON CLIENT INSTANCES THAT WAS ADDED IN THE STORAGE !!!
--- !!! CULLING IS ONLY WORKING FOR MODELS AND PARTS !!!
--- !!! TO MAKE PREMADE CLIENT INSTANCES THAT WILL AUTOMATICALLY BE ADDED TO THE STORAGE,
--- MAKE A MODULESCRIPT ADD TAG TO IT NAMED "Instance", AND SOURCE OF THE MODULE SCRIPT SHOULD BE ARGUMENT AS I
--- I SHOWN IN THE .Create() METHODS , ALSO PREMADE INSTANCES HAVE Classes "whitelist" FIND IT IN THE MODULE
--- AND ADD MORE IF YOU WANT!!!

--- !!! TO CHANGE CULLING CENTER RANGE , CHANGE THE chunkSize IN THE MODULE!!!

-- checking for available Instances and adds them to the storage
instCreator.check()

-- adds instance to the storage
instCreator.addInstance(Instance)
-- removes instance from the storage (doesn't destroy it)
instCreator.removeInstance(Instance)
-- gets array of instances from the storage
instCreator.getInstances()
-- removes Instances from the storage , and destroys them
instCreator.clearStorage()

-- set before you start culling | use character's root for culling or not
instCreator.useCharacterRoot = false 

-- starts culling of client Instances that was added to the storage | sets parent of instances to nil
-- if they're not in range of culling center, and adds them back to their parents if they're in range.
instCreator.startCulling() 

-- assigns center of culling , similliar to the Player:AddReplicationFocus() , but it's only for client instances in the storage
instCreator.assignCenterOfCulling(Instance)
-- removes center of culling (doesn't destroy it)
instCreator.removeCenterOfCulling(Instance)
-- clears all center of culling | if useCharacterRoot is set to true , it will add player's character root back
-- doesn't destroy the centers of culling
instCreator.clearCentersOfCulling()

-- stops culling of the Instances and adds them back to their parents if they're in nil.
instCreator.stopCulling()





-- [CREATE METHODS ]

-- One Instance method , creates Instance and adds it to the storage
instCreator.Create({
	type = "Part",
	InstanceProperties = {
		Anchored = true,
		BrickColor = BrickColor.random(),
		Name = "Test",
	}
})

-- Multiple Instances method , creates Instances and adds them to the storage
instCreator.Create({
	{
		type = "Part",
		InstanceProperties = {
			Anchored = true,
			BrickColor = BrickColor.random(),
			Name = "Test",
			Parent = workspace,
		},
	},
	{
		type = "Part",
		InstanceProperties = {
			Anchored = true,
			BrickColor = BrickColor.random(),
			Name = "Test",
		},
	},
	{
		type = "Part",
		InstanceProperties = {
			Anchored = true,
			BrickColor = BrickColor.random(),
			Name = "Test",
		},
	},
})
