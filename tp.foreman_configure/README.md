Configuring Foreman with the foreman-ansible-modules
====================================================

At the time of writing this (sometime 2019 with foreman v1.3.0),
there are 54 interdependent modules to configure foreman.
Unfortunately, some things can be defined in more than one place:

* `architecture` can take a list of operatingsystems the architecture supports.
* `operatingsystem` can take a list of architectures it can be installed on.

This complicates things.  In this ansible role I will deduplicate such
occurences as much as I can, e.g. I will ignore lists of operatingsystems
in 'architecture'.

In order to determine the order in which the modules should be run,
I created a dependency-graph with [graphviz](https://graphviz.org) and
[sorted it topologically](https://en.wikipedia.org/wiki/Topological_sorting)
from "doesn't depend on anything" to "depends on everything".

Find the dependency-graph in /docs/foreman-ansible-dependencies.dot, fetch
[tsort.g](https://gist.github.com/carld/e7f48dc15b870a850dd701900d279848)
and run

    gvpr -f tsort.g foreman-ansible-dependencies.dot | tac | sed 's/^/- /'

You'll find the generated list in "{{ tp_foreman_configure_modules_in_topological_order }}"
and I'm looping over it in tasks/main.yml.

To generate a pdf-graph, do
    dot -Tpdf foreman-ansible-dependencies.dot -o foreman-ansible-dependency-graph.pdf
