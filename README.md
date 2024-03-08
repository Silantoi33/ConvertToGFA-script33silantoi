# ConvertToGFA-script33silantoi
```
#!/usr/bin/env python

import sys

def convert_to_gfa(fasta_file, gfa_file):
    with open(fasta_file, 'r') as f:
        with open(gfa_file, 'w') as g:
            node_id = 1
            for line in f:
                if line.startswith('>'):
                    header = line.strip()[1:]
                    g.write("S\t{}\t{}\n".format(node_id, header))
                else:
                    sequence = line.strip()
                    g.write("L\t{}\t+\t{}\t+\t0M\n".format(node_id - 1, node_id))
                    node_id += 1

if __name__ == "__main__":
    if len(sys.argv) != 3:
        print("Usage: {} <input_fasta> <output_gfa>".format(sys.argv[0]))
        sys.exit(1)
    
    input_fasta = sys.argv[1]
    output_gfa = sys.argv[2]
    convert_to_gfa(input_fasta, output_gfa)
```
