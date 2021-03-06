# Problem

[return to homepage](../../readme.md) | [return to PDDL2.1 main page](./main.md)

The problem syntax in PDDL 2.1 has to be extended in order to complement the syntax of the domain file. One interesting extension to the syntax in PDDL 2.1 is the addition of a metric. A metric, which behaves like an optimisation function, defines a cost value for a plan. We then express whether we want this metric to be maximised (like in football) or minimised (like in golf).

```LISP
(define
    (problem rover1)
    (:domain rover-domain)
    (:objects
        r1 r2 - rover
        wp1 wp2 - waypoint
    )
    (:init
        (= (battery-amount r1) 100)
        (= (recharge-rate r1) 2.5)
        ...
    )
    (:goal (and
            ...
        )
    )
    (:metric maximize (+
            (battery-amount r1)
            (battery-amount r2)
        )
    )
)
```

## Contents

- [Numeric Fluents](#numeric-fluents)
- [Metric](#metric)
- [Length (Deprecated)](#length)

## Numeric Fluents

[back to contents](#contents)

Support: <span style="color:yellow">High</span>
Usage: <span style="color:green">High</span>

`(= (<fluent_name> <argument>) <value>)`

An equals prefix notation is used to assign a value to a numeric fluent. Some planners will require all possible numeric values for numeric fluents should be declared before it will attempt to plan.

`(= (battery-amount r1) 10)`

## Metric

[back to contents](#contents) | [Report a problem with this guide](https://github.com/nergmada/pddl-reference/issues/new/choose)

Support: <span style="color:orange">Medium</span>
Usage: <span style="color:green">High</span>

`(:metric minimize (<numeric_operation>))`

`(:metric maximize (<numeric_operation>))`

A metric can be defined using some numeric operation on fluents, including using just a single fluent. The most common method for declaring a metric, is to declare a numeric fluent with no arguments and increase it within the effect of each action by the cost of that action.

We can choose to either minimize or maximize the value of the metric function. Note, a metric function is NOT a replacement for a goal.

## Length

[back to contents](#contents)

Support: <span style="color:pink">Deprecated</span>
Usage: <span style="color:red">Rare</span>

The length argument is deprecated. Few planners will support it (if any).

## References

- [PDDL - The Planning Domain Definition Language](http://www.cs.cmu.edu/~mmv/planning/readings/98aips-PDDL.pdf), [Ghallab, M. Howe, A. Knoblock, C. McDermott, D. Ram, A. Veloso, M. Weld, D. Wilkins, D.]
- [PDDL2.1: An Extension to PDDL for Expressing Temporal Planning Domains](https://jair.org/index.php/jair/article/view/10352/24759), [Fox, M. Long, D.]
- [PDDL Examples](https://github.com/yarox/pddl-examples)
- [OPTIC - Optimising Preferences and Time Dependent Costs](https://nms.kcl.ac.uk/planning/software/optic.html)