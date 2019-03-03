The interval tree structure stores a set of intervals and returns for any query
key all the intervals that contain this query value.

Suppose the underlying set
of intervals is the set {[a1, b1],[a2, b2],...,[an, bn]}. Let T be any balanced search tree for the set of interval endpoints {a1, a2,...,an, b1,...,bn}.

Each interval [ai, bi]
of our set is now stored in a node that satisfies
1. the key of the node is contained in [ai, bi], and
2. the interval [ai, bi] is contained in the interval associated with the node.

This node might not be unique; if during this descent the key of
the current node occurs as endpoint of the interval, then some node below the
current node will also satisfy both properties. For the interval tree structure, it
makes no difference which node we choose.

![interval tree]()

To
implement it, we need two different types of nodes: the search-tree nodes
augmented by the left and right list pointers, and the list nodes. 
```C++
// list node
typedef struct ls_n_t { 
    key_t key;
    struct ls_n_t *next;
    object_t *object;
} list_node_t;

// tree node
typedef struct tr_n_t { key_t key;
    struct tr_n_t *left;
    struct tr_n_t *right;
    list_node_t *left_list;
    list_node_t *right_list;
    /* balancing information */
} tree_node_t;
```

Theorem. The interval tree structure is a static data structure that can be built
in time O(n log n) and needs space O(n). It lists all intervals containing a given
query key in output-sensitive time O(log n + k) if there are k such intervals.

Why not a dynamic structure?
1. Insertion of an interval at a node involves insertion into two ordered lists of endpoints. For each list (when established using a BST with a doubly linked list of leaves), O(k) time to list the first k elements and O(log n) time for insertion and deletion.

2. Restructuring of the tree to make it balanced requires correction of associated lists at each affected node. Requires joining and separation of ordered lists:  No known way to achieve this in sublinear time!

So, Building a tree for a superset of all expected interval endpoints, if known, can be an option, and it still requires search trees for the left and right lists in each node!

