========================
Floyd Warshall Algorithm
========================

- All-Pairs Shortest Paths.
- Enumerate the nodes so that :math:`V = \{1, 2,\dots, N\}`.
- Can achieve :math:`O(N^3)` running-time with a simple dynamic programming.

.. note::

    This algorithm only works when edge weights are non-negative.

SRTBOT
======

- Subproblem


Implementation
==============

.. code-block:: python
    def floyd_warshall_directed(n: int, edges: list):
        """
        Assumes that edges are directed, i.e. (a, b) != (b, a)
        """
        dp = [[0 if i ==j else float("inf") for j in range(n)] for i in range(n)]
        for e in edges:
            dp[e[0]][e[1]] = e[2]
        # print(dp)
        for k in range(n):
            for i in range(n):
                for j in range(n):
                    dp[i][j] = min(dp[i][j], dp[i][k] + dp[k][j])
        return dp  

