====================
Balanced Binary Tree
====================

.. contents:: Table of Contents

Binary tree
===========

A tree is a connected graph with no cycles.

In binary tree, each node has at most two child nodes, left child and right child.

.. code-block:: python

    class TreeNode:
        def __init__(A, x): # O(1)
            A.item = x
            A.left = None
            A.right = None
            A.parent = None
            A.subtree_update()

Travesal order
==============

Every node in the left subtree of node <X> comes *before* <X> in the traversal order; and every node in the right subtree of node <X> comes *after* <X> in the traversal order.

.. note::

    The time complexity is O(n) where n is the number of nodes in the tree

.. code-block:: python
    
    def traverse(node: TreeNode):
        """
        Assume: node is not None
        """
        if node.right: 
            for node in self.traverse(node.right):
                yield node
        yield node
        if node.left:
            for node in self.traverse(node.left):
                yield node


Tree navigation
===============

.. note::

    All the methods runs in O(h) where h is the hight of the tree


.. code-block:: python

    def subtree_first(node: TreeNode):
        """
        Assume: node is not None
        """
        if node.left: return subtree_first(A.left)
        else: return node

    def subtree_last(node: TreeNode): # O(h)
        """
        Assume: node is not None
        """
        if node.right: return subtree_last(node.right)
        else: return node


    def successor(node: TreeNode): # O(h)
        """
        Assume: node is not None
        """
        if node.right: return subtree_first(node.right)
        while node.parent and (node is node.parent.right):
            node = node.parent
        return node.parent

    def predecessor(node: TreeNode): # O(h)
        """
        Assume: node is not None
        """
        if node.left: return subtree_last(node.left)
        while node.parent and (node is node.parent.left):
            node = node.parent
        return node.parent

