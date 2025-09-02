# Automatic-garbage-collector-using-AI
#define TREE_NODE_PTR_COUNT 2
  typedef struct TreeNode {
  struct TreeNode _gc   *left,  *right;   //pointers at top
  int value;
} TreeNode;

TreeNode *top, *node0, *node1, *node2;


int main()
{
  node0 = (TreeNode*)CollectMalloc(sizeof(TreeNode),  TREE_NODE_PTR_COUNT);
  node1 = (TreeNode*)CollectMalloc(sizeof(TreeNode),  TREE_NODE_PTR_COUNT);
  node2 = (TreeNode*)CollectMalloc(sizeof(TreeNode),  TREE_NODE_PTR_COUNT);

  CollectRoot(&top);   //define a fixedroot node
  top = node0;
  node0->left = node2;

  CollectGarbage();   //frees unreferenced node1
  top = NULL;
  CollectGarbage();   //frees node0 and node2
  return 0;
}
