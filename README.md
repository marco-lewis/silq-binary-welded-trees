# Quantum Walk on a Binary Welded Tree

This repository contains an implementation of the quantum walk on a binary welded tree in Silq.

## The Problem
<img src="https://user-images.githubusercontent.com/33728296/132327104-ae12b6e7-672f-4ff4-81de-05e81ae75f3c.png" align="right" alt="drawing" width="350"  >

You are given two binary trees whose leaves are joined together by a weld. A weld is a cyclic subgraph that visits all leaves once. You start from the root of one tree and the goal is to reach the root of the other tree. When at a node, you only have knowledge of the paths you can take from the node you are currently in (this is commonly depicted by coloring edges). An example of a labelled binary welded tree with colored edges is given to the right (note that while labels here are given in order, they can be random).

Classically, you would walk along paths randomly, noting what nodes you have visited, and you would eventually reach the root of the other tree.

Quantumly, you can travel down each path at the same time and walk straight to the root of the tree (and measure you are there with high probability).


## Creating a Binary Welded Tree
You can easily create a binary welded tree by importing the BWTGeneralGraph and creating a weld. An example of a 3-depth tree can be made by:
```
import BWTGeneralGraph;

d = 3;

def Oracle[n:!N](color:!N, node:uint[n]){
	return BWT[n,d]((4,12,6,14,5,11,7,13):!uint[n]^(2^d), color, node);
}
```
Note that the weld is a list that requires:
1. Numbers in the ranges (2^depth-1^, 2^depth^ - 1) and (2^depth^ + 2^depth-1^, 2^depth+1^ - 1), where depth is the welded trees' depth
2. Each number to only appear once in the weld
3. Numbers must alternate between each range (but the first number can be from either)

## Resources
This implementation is partly based off the Quipper implementation, with details given [here](https://www.mathstat.dal.ca/~selinger/quipper/doc/Quipper-Algorithms-BWT-Main.html).

See the Silq homepage ([https://silq.ethz.ch/](https://silq.ethz.ch/)) or [Github](https://github.com/eth-sri/silq) for information on Silq.

For details of the algorithm, see:
```
A. M. Childs, R. Cleve, E. Deotto, E. Farhi, S. Gutmann, and D. A. Spielman. 
"Exponential algorithmic speedup by a quantum walk."
Proceedings of the 35th Annual ACM Symposium on Theory of Computing, 
pp. 59–68, 2003.
```
The paper is also available on the [arXiv](http://arxiv.org/abs/quant-ph/0209131).

## Possible extensions
- Randomising the values that label nodes (e.g. start at 7, goal is to reach 15)
- Implementing different types of graph oracles (number of colors, similar graph structures)
