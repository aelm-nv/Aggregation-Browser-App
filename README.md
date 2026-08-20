# Dimer Browser

A browser-based workbench for systematically constructing and inspecting molecular dimer geometries.

The app loads two XYZ monomers, lets you define molecular orientation from atom indices, samples translations and rotations, rejects geometries with van der Waals clashes, previews structures in 3D, and exports individual structures or a ZIP archive. It runs entirely in the browser; molecular files are not uploaded to a server.

## Scientific philosophy

Dimer Browser inherits the **systematic-search philosophy** of Elmanova, Jahn, and Presselt, [“Catching the π-Stacks: Prediction of Aggregate Structures of Porphyrin”](https://doi.org/10.1021/acs.jpca.4c05969), *The Journal of Physical Chemistry A* **128** (2024), 9917–9926.

In particular, the app is motivated by the idea that aggregate structures should be explored reproducibly across explicit translational and rotational grids rather than selected only by intuition. The paper combines systematic dimer sampling with quantum-chemical energy evaluation, minimum detection, structural clustering, and optimization. This repository currently implements the **geometry-generation and inspection layer only**; it does not perform DFT calculations, rank structures by energy, identify minima, cluster structures, or reproduce the complete published workflow.

The reference above is an acknowledgment of methodological inspiration. It does not imply affiliation with or endorsement by the paper’s authors, their institutions, or the American Chemical Society.

## Features

- Load monomer A and B from `.xyz` files
- Use the same monomer on both sides for homodimers
- Center and orient monomers from selected atom indices
- Sample Cartesian translations and Euler-angle rotations
- Filter close contacts using scaled van der Waals radii
- Preview monomers and generated dimers with 3Dmol.js
- Export a selected dimer, all dimers, or a ZIP archive
- Preserve generation parameters in XYZ comment lines

## Run locally

No build step is required. Open `index.html` in a modern browser with internet access. The first visualization loads 3Dmol.js from a CDN, and ZIP export uses JSZip from a CDN.

For more consistent browser behavior, serve the directory locally:

```bash
python -m http.server 8000
```

Then open `http://localhost:8000`.

## GitHub Pages

In the repository settings, choose **Pages → Deploy from a branch**, select the default branch and `/ (root)`. The app is already arranged for root-level static hosting.

## Input and output

Input files use standard XYZ format:

```text
3
water
O  0.000000  0.000000  0.000000
H  0.758602  0.000000  0.504284
H -0.758602  0.000000  0.504284
```

Generated structures are exported as XYZ files. Their comment line contains JSON metadata describing the sampled translation and rotation.

## Scientific-use note

Generated geometries are candidates, not predicted stable structures. Use an appropriate electronic-structure or molecular-mechanics workflow to evaluate energies and refine geometries before drawing scientific conclusions.

## Citation

If this app contributes to scientific work, cite the repository release you used and acknowledge the methodological paper:

> A. Elmanova, B. O. Jahn, M. Presselt, “Catching the π-Stacks: Prediction of Aggregate Structures of Porphyrin,” *J. Phys. Chem. A* **2024**, *128*, 9917–9926. https://doi.org/10.1021/acs.jpca.4c05969

## License

Released under the [MIT License](LICENSE).
