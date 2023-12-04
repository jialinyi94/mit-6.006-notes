====================
Balanced Binary Tree
====================

.. contents:: Table of Contents

Binary tree
---

A tree is a connected graph with no cycles.

In binary tree, each node has at most two child nodes, left child and right child.

.. code-block:: python

    class Binary_Node:
        def __init__(A, x): # O(1)
            A.item = x
            A.left = None
            A.right = None
            A.parent = None
            A.subtree_update()


Travesal order
---

Every node in the left subtree of node <X> comes *before* <X> in the traversal order; and every node in the right subtree of node <X> comes *after* <X> in the traversal order.

.. code-block:: python
    
    def subtree_iter(A): # O(n)
        if A.left: yield from A.left.subtree_iter()
        yield A
        if A.right: yield from A.right.subtree_iter()


Tree navigation
---

.. code-block:: python
    
    '''
    All the methods runs in # O(h)
    h: the hight of the tree
    '''

    def subtree_first(A): 
        if A.left: return A.left.subtree_first()
        else: return A

    def subtree_last(A): # O(h)
        if A.right: return A.right.subtree_last()
        else: return A


    def successor(A): # O(h)
        if A.right: return A.right.subtree_first()
        while A.parent and (A is A.parent.right):
            A = A.parent
        return A.parent

    def predecessor(A): # O(h)
        if A.left: return A.left.subtree_last()
        while A.parent and (A is A.parent.left):
            A = A.parent
        return A.parent

