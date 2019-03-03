The primary task performed by a segment tree is the same as that done by an
interval tree: keeping track of a set of n intervals, here assumed to be halfopen,
and listing for a given query key all the intervals that contain that key in
output-sensitive time O(log n + k) if the output consisted of k intervals.

Assume a setX = {x1, . . . , xn} of key values and a search tree T for {−∞} ∪
X. Any interval [xi, xj [ can be
expressed in many ways as union of node intervals,4 so it can be represented
by subsets of the tree nodes.

Theorem. The canonical interval decomposition is a representation of the
interval as union of disjoint node intervals. Any search path for a value in the interval will go through exactly one node that belongs to the canonical interval
decomposition.

The canonical interval decomposition is easy to construct. We start with the
interval [xi, xj [ at the root:
1. Each time the node interval of the current node is entirely contained in
[xi, xj [, we take that node into our representation and stop following that
path down because all nodes below are redundant;
2. Each time the node interval of the current node partially overlaps [xi, xj [,
we follow both paths down;
3. Each time the node interval of the current node is disjoint from [xi, xj [, we
stop following that path down.

Theorem. Let X = {x1, . . . , xn} be a set of key values and T a search tree for
{−∞} ∪ X. Then for any interval bounded by values from X, the canonical
decomposition has size at most 2 height(T ) and can be constructed in time
O (height(T )). If T is of height O(log n), the canonical interval decomposition
has size O(log n) and can be found in time O(log n).

Theorem. The segment tree structure is a static data structure that can be built
in time O(n log n) and needs space O(n log n). It lists all intervals containing
a given query key in output-sensitive time O(log n + k) if there are k such
intervals.

To implement the segment tree structure, we again need two types of nodes –
the tree nodes and the interval lists attached to each tree node.
```c++
typedef struct ls_n_t {
    /* interval [a,b[ */ 
    key_t key_a, key_b;
    struct ls_n_t *next;
    object_t *object;
} list_node_t;

typedef struct tr_n_t { 
    key_t key;
    struct tr_n_t *left;
    struct tr_n_t *right;
    list_node_t *interval_list;
    /* balancing information */
} tree_node_t;
```

Interval containment queries:
Nither the root nor any node on the left or right boundary path of the tree, can have any intervals of the canonical interval decomposition. Node intervals are unbounded, and we are representing only finite intervals.
Nodes near the leaf level will have nonempty lists.
Interval trees tended to store intervals in higher-up nodes.
Segment tree is static structure.

### Problems in Making it Dynamic
1. Allow insertion and deletion in each node.
- There are O(log n) fragments of the canonical decomposition for single insert or delete.
- efficient O(log n) - use a search tree only for the first fragment, and doubly linked list for the remaining fragments.
- allowing O(1) insertion and deletion of intervals.

2. Rebalancing of the underlying tree by rotations causes changes in the lists attached to the tree nodes
- no efficient solution,
- better than for interval trees, since the sequence of the intervals attached to a tree node does not matter.
- allows a representation of the sets of intervals attached to the nodes, which makes segment trees truly dynamic.
