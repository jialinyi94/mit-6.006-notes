==================
Depth-First Search
==================

.. contents:: Table of Contents

Depth-First Search with Back-Tracking
=====================================

.. code-block:: python
    
    def dfs(start, destination, adj, visited=None, path=None):
        if start == destination:
            return path
        visited.append(start)
        for child in adj[start]:
            if child not in visited:
                res = dfs(child, destination, adj, visited, path + [child])
                if res: return res

    dfs(start, destination, adj, [], [start])
    

    
