### Tree traverses:
- <em>pre-order</em>
- <em>in-order</em>
- <em>post-order</em>

<pre>
function Node(value) {
  this.value = value;
  this.left = null;
  this.right = null;
}

function Tree(){
  this.root = new Node("Root");
}

Tree.prototype.traverseInOrder = function(callback) {
  (function traverse(node) {
	  if(node){
  	  if(node.left){
    	  traverse(node.left)
        }

        callback(node)

        if(node.right){
          traverse(node.right)
        }
      }
  })(this.root)
 }

Tree.prototype.traversePreOrder = function(callback) {
	(function traverse(node) {
	  if(node){
	    callback(node);

  	if(node.left){
    	traverse(node.left)
      }

      if(node.right){
        traverse(node.right)
      }
    }
  })(this.root)
}

Tree.prototype.traversePostOrder = function(callback) {
	(function traverse(node) {
    if(node){
      if(node.left){
        traverse(node.left)
      }

      if(node.right){
        traverse(node.right)
      }

      callback(node);
     }
  })(this.root)
}

// CREATING A NEW TREE
var tree = new Tree();
tree.root.left = (new Node("1"));
tree.root.right = (new Node("2"));

tree.root.left.left = (new Node("3"));
tree.root.left.right = (new Node("4"));

tree.root.right.left = (new Node("5"));
tree.root.right.right = (new Node("6"));

// TESTING TRAVERSES
tree.traverseInOrder(function(node){
	console.log(node.value)
})

tree.traversePreOrder(function(node){
	console.log(node.value)
})

tree.traversePostOrder(function(node){
	console.log(node.value)
})
</pre>
