![Alt text](https://g.gravizo.com/source/lattice1?https%3A%2F%2Fgithub.com%2Faltoxml%2Fboard%2Fnew%2Fgh-pages%2Fmisc%2Flattice.md) 
<summary></summary>
<details>
lattice1
  digraph G {
    size ="4,4";
    main [shape=box];
    main -> parse [weight=8];
    parse -> execute;
    main -> init [style=dotted];
    main -> cleanup;
    execute -> { make_string; printf};
    init -> make_string;
    edge [color=red];
    main -> printf [style=bold,label="100 times"];
    make_string [label="make a string"];
    node [shape=box,style=filled,color=".7 .3 1.0"];
    execute -> compare;
  }
lattice1
</details>
