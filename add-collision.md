```
extends Spatial

var children : Array
var bits = [1, 5, 6] # For the Collision bit layers

func _ready():
	children = get_children()
	for node in children:
		if node is MeshInstance:
			if(node.get_child_count() == 0):
				node.create_trimesh_collision()
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
			if(child != null):
				for i in range(0, bits.size()):
					child.set_collision_layer_bit(bits[i], true)
					child.set_collision_mask_bit(bits[i], true)
```
