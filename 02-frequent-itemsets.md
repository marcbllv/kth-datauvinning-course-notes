# Frequent Itemsets

*Goal*: Identify items that frequently occur in the same sets of items
(baskets). It can be viewed as the association rule discovery: we wan to find
itemsets that match rules like X -> Y.

Example: {diaper, milk} -> {beer}

## Association rules

X,Y are two sets of items. An association rule X -> Y is the rule "if all
elements of X in the basket, then it's likely to contain all elements of Y".
Y can contain only one element.

*Confidence*: the confidence of the rule X -> j (j is a single element) is
$conf(X -> j) = \frac{support(I \union j)}{support(I)}$

## Mining association rules

1st step: find itemsets I with at least a given support.

2nd step: for every *subset* A of I generate the rule: A -> I\A.
Then output rules where confidence is over a certain threshold (like 50% for
instance).

## Finding frequent pairs

Hard problem: they are quite common (while frequent triples are much rarer).

Count all pairs, and store triples [i,j,c], where i and j are two items, and c
is the count. If we store only triples for c > 0, it's much smaller in the
memory.

## A-priori algorithm 

When too much pairs and they don't fit in the main memory:
- Count frequent items (~1% of overall items)
- Build pairs only from those frequent items

Can be extended to find frequent triples and k-tuples:
- Filter each (k-1)-tuples to only get thoses who are really frequents
- Build all the k-tuples from the previous set and the frequent items
- Keep only the frequent k-tuples that have support \> s.

But to be in the candidates k-tuples, a k-tuple must have all its subsets in
the frequent itemsets.

