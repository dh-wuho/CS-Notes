## Measure Tree

### Measure
each node n contains the measure n->measure of the union of all
node intervals of nodes in the subtree below n

For any node n, this information
can easily be reconstructed from its lower neighbors:
{ if n->interval list = NULL,
then n->measure is the length of the node interval of n;
{ if n is a leaf and n->interval list = NULL, then n->measure
is 0;
{ if n is an interior node and n->interval list = NULL, then
n->measure = n->left->measure + n->right->measure.

### Dynamic Measure Tree
A fully dynamic structure to maintain the measure of a union of intervals is
the measure tree defined by Gonnet, Munro, and Wood (1983).

The construction of the measure tree begins with any balanced search tree
on the endpoints of all intervals in the current set and −∞. The associated
intervals of a node are all those intervals in the current set that have at least
one endpoint in the node interval; like the node interval, we do not store the
associated intervals in the node, but just need them as concept.

Each node n of the search tree contains three additional fields:
{ n->measure is the measure of the intersection of the node interval of n
with the union of all its associated intervals.
{ n->rightmax is the maximum right endpoint of all intervals associated
with n.
{ n->leftmin is the minimum left endpoint of all intervals associated
with n.

For any interior node n, this information can be reconstructed from its lower
neighbors. Two of the fields are easy:
{ n->rightmax =
max(n->left->rightmax, n->right->rightmax), and
{ n->leftmin = min(n->left->leftmin, n->right->leftmin).

if $l$ and $r$ are the left and right endpoints of the node interval of n, we have
1. if n->right->leftmin < l and n->left->rightmax ≥ r,
n->measure = r − l;
2. if n->right->leftmin ≥ l and n->left->rightmax ≥ r,
n->measure = (r − n->key) + n->left->measure;
3. if n->right->leftmin < l and n->left->rightmax < r,
n->measure = n->right->measure + (n->key − l); and
4. if n->right->leftmin ≥ l and n->left->rightmax < r,
n->measure = n->right->measure + n->left->measure.

Theorem. The measure tree structure is a dynamic data structure that keeps
track of a set of n intervals, supporting insertion and deletion of intervals in
time O(log n), and that answers queries for the measure of the union of the
intervals in O(1) time. The structure has size O(n).