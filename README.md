			Implementation of FP-Growth algorithm
FP-Growth: allows frequent itemset discovery without candidate itemset generation. Two step approach:
–	Step 1: Build a compact data structure called the FP-tree
–	Step 2: Extracts frequent itemsets directly from the FP-tree
	Step:1:- FP Tree Construction
–	Sub step 1:
•	Scan data and find support for each item.
•	Discard infrequent items.
•	Sort frequent items in decreasing order based on their support.
Use this order when building the FP-Tree, so common prefixes can be shared.
–	Sub step 2:
•	Nodes correspond to items and have a counter.
•	FP-Growth reads 1 transaction at a time and maps it to a path.
•	Fixed order is used, so paths can overlap when transactions share items(when they have the same prefix). In this case, counters are incremented.
•	Pointers are maintained between nodes containing the same item, creating singly linked lists (dotted lines denote these linked lists in the figure)
•	The more paths that overlap, the higher the compression. FP-tree may fit in memory.
•	Frequent itemsets extracted from the FP-Tree.

	Step 2:- Frequent Itemset Generation
–	FP-Growth extracts frequent itemsets from the FP-tree.
–	Bottom-up algorithm - from the leaves towards the root
–	Divide and conquer: first look for frequent itemsets ending in e, then de, etc. . . then d, then cd, etc. . .
–	First, extract prefix path sub-trees ending in an item(set). 
–	Each prefix path sub-tree is processed recursively to extract the frequent itemsets. Solutions are then merged.
–	E.g. the prefix path sub-tree for e will be used to extract frequent itemsets ending in e, then in de, ce, be and ae, then in cde, bde, cde, etc.
–	Divide and conquer approach.
  

	Conditional FP-Tree:-
–	The FP-Tree that would be built if we only consider transactions containing a particular itemset (and then removing that itemset from all transactions).

  
•	In the code, I have printed the frequent item sets along with their frequencies. Images of the output are attached in the folder (1.png and 2.png).
	Advantages of FP-Growth
–	only 2 passes over data-set
–	“compresses” data-set
–	no candidate generation
–	much faster than Apriori
	Disadvantages of FP-Growth
–	FP-Tree may not fit in memory!!
–	FP-Tree is expensive to build

