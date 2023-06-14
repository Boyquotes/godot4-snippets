func get_all_children(in_node,arr:=[]):
arr.push_back(in_node)
for child in in_node.get_children():
    arr = get_all_children(child,arr)
return arr
and call it like..

var all_children = get_all_children(the_node)
