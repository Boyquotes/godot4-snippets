extends Spatial

# Will contain all of the children of the root scene
var children : Array
# Can be anything you want
var bits = [1, 5, 6] # For the Collision bit layers

func _ready():
	children = get_children()
	for node in children:
		if node is MeshInstance:
			# Creates a collision shape for the mesh
			# Since this is slow, we only want to do this when we are testing levels
			if(node.get_child_count() == 0):
				node.create_trimesh_collision()
	
			# gets the static body created
			var child = null
			if(node.get_child(0) is StaticBody):
				child = node.get_child(0)
			else:
				for i in node.get_children():
					if i is StaticBody:
						child = i
						break
				if(child == null):
					print(node.name, ": error, no static body found.\nCreate a StaticBody if you have children!")
	
			# sets the static body's collision layers & masks to all the bits layered above
			if(child != null):
				for i in range(0, bits.size()):
					child.set_collision_layer_bit(bits[i], true)
					child.set_collision_mask_bit(bits[i], true)
