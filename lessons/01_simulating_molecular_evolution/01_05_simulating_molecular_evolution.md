# Module 1, Lesson 5: Simulation of molecular evolution

## Convert phylogenetic tree to python dictionary

The following tree has 4 tips (a,b,c,d) and four nodes (n0,n2,n3,n4). The time scale indicates how many years (in millions of years) divergences occured before present time.

Construct a dictionary with

```python
phylogeny = {
  "n1":{
    "children":{
      "a":{
        "children":None,
        "time":6
      },
      "n2":{
        "children":{
          "b":{
            "children":None,
            "time":4
          },
          "n3":{
            "children":{
              "c":{
                "children":None,
                "time":2
              },
              "d":{
                "children":None,
                "time":2
              },
            },
            "time":2
          },
        },
        "time":2
      }
    },
    "time":0
  }
}

```

Iterate over the phylogeny to see how it works

```python
# Perhaps could do this recursively, where the function prints the children iteratively or something like that
for branch in phylogeny:
  print(branch)
```

### Evolving sequences along the tree

Evolve a sequence along a branch of length t
calculate transition probability matrix P(t) = pij(t)
Simulate nucleotide substitutions at every site independently

### On your own

Use the above phylogeny to simulate evolution along the branch lengths starting at node1 for time t in millions of generations.

For example, start at $n_1$ then evolve two sequences corresponding to its two children $a$ (t = 6M) and $n2$ (t = 2M). Then take the new evolved sequence from $n2$ and evolve it two sequences corresponding to it's two children. Repeat this until all seuqences have been simulated.

## End of Module homework

Use the ape phylogeny to first convert it to a python dictionary like before. Then simulate a sequence along the phylogeny.
