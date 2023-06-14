func findByClass(node: Node, className : String, result : Array) -> void:   
  if node.is_class(className) :   
    result.push_back(node)    
  for child in node.get_children():   
    findByClass(child, className, result)     


func test() -> void:    
  var res = []    
  findByClass(self, "Control", res)   
  print(res)     
