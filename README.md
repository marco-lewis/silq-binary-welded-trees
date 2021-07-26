
# Quantum Walk on a Binary Welded Tree

This repository contains an implementation of the quantum walk on a binary welded tree in Silq.

## Creating a Binary Welded Tree
You can easily create a binary welded tree by importing the BWTGeneralGraph and creating a weld. An example of a 3-depth tree can be made by:
```
import BWTGeneralGraph;

d = 3;

def Oracle[n:!N](color:!N, node:uint[n]){
	return BWT[n,d]([4,12,6,14,5,11,7,13] coerce !uint[n]:(2^d), color, node);
}
```
Note that the weld is a list that requires:
1. Numbers in the ranges (2^depth-1^, 2^depth^ - 1) and (2^depth^ + 2^depth-1^, 2^depth+1^ - 1), where depth is the welded trees' depth
2. Each number to only appear once in the weld
3. Numbers must alternate between each range (but the first number can be from either)

## Resources
This implementation is partly based off the Quipper implementation available [here](https://www.mathstat.dal.ca/~selinger/quipper/doc/Quipper-Algorithms-BWT-Main.html).

See the Silq homepage ([https://silq.ethz.ch/](https://silq.ethz.ch/)) or [Github](https://github.com/eth-sri/silq) for information on Silq.

For details of the algorithm, see:
```
A. M. Childs, R. Cleve, E. Deotto, E. Farhi, S. Gutmann, and D. A. Spielman. 
"Exponential algorithmic speedup by a quantum walk."
Proceedings of the 35th Annual ACM Symposium on Theory of Computing, 
pp. 59–68, 2003.
```
The paper is also available on the [arXiv](http://arxiv.org/abs/quant-ph/0209131).