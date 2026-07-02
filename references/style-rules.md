# Local IEEE BibTeX Style Rules

Use these rules as a checklist, not as a universal bibliography law. Infer the user's local target style first. If no project-specific style file is supplied, use `template.bib` in the repository root as the canonical wireless IEEE template.

## Template First

- Inspect `template.bib` before flagging unknown IEEE journal or conference macros.
- Prefer the template's `@string` macros for IEEE journals and proceedings when they are available.
- Preserve existing citation keys unless the user asks for key normalization or deduplication.
- Do not invent missing metadata. Report missing `volume`, `number`, `pages`, `month`, `doi`, or `address` instead of filling them from memory.

## Preferred Entry Shapes

### Journal article

```bibtex
@ARTICLE{key,
  author={Last, F. and Last, F. M.},
  journal=ieee_j_wcom,
  title={Title With Protected {Acronyms}},
  year={2024},
  volume={23},
  number={9},
  pages={11904--11919},
  month={Sep.},
  doi={10.xxxx/xxxxx}
}
```

Literal journal names are acceptable when already abbreviated:

```bibtex
journal={IEEE Trans. Wireless Commun.}
```

Flag full names such as `IEEE Transactions on Wireless Communications`.

### Conference paper

```bibtex
@INPROCEEDINGS{key,
  author={Last, F. and Last, F.},
  booktitle={Proc. IEEE Int. Conf. Commun. (ICC)},
  title={Title With Protected {CSI}},
  year={2024},
  month={Jun.},
  pages={1--6},
  address={Denver, CO, USA},
  doi={10.xxxx/xxxxx}
}
```

Local string macros are acceptable when they expand to a `Proc.` venue, e.g. `booktitle=priicassp`.

### arXiv preprint

```bibtex
@misc{key,
  author={Last, F. and Last, F.},
  title={Title With Protected {Acronyms}},
  year={2025},
  eprint={2501.01234},
  archivePrefix={arXiv},
  primaryClass={cs.LG},
  journal={arXiv preprint arXiv:2501.01234},
  note={[Online]. Available: https://arxiv.org/abs/2501.01234}
}
```

Flag arXiv entries written as `@article` when they lack `eprint/archivePrefix`, unless the local file intentionally treats arXiv as articles.

### Book

```bibtex
@BOOK{key,
  author={Last, F. and Last, F.},
  title={Book Title},
  publisher={Publisher},
  year={2006},
  address={New York, NY, USA},
  edition={2nd}
}
```

Book author names should still follow initialized local style unless preserving publisher-provided names is intentional.

## Common Issues To Report

- Full natural-order author names: `Wei Xu and Jie Wu and Shi Jin`.
- Full comma author names: `Bertsimas, Dimitris and Tsitsiklis, John N.`.
- Full IEEE journal names: `IEEE Transactions on Information Theory`.
- Missing journal month in otherwise complete IEEE entries.
- Month format drift: `June`, `March`, `sep`, or `Feb` instead of `Jun.`, `Mar.`, `Sep.`, `Feb.`.
- Conference booktitle without `Proc.`.
- Conference booktitle with long form such as `International Conference on Machine Learning` when the local style abbreviates venues.
- Conference entries missing `address` or `month`.
- Empty fields such as `pages={}`.
- `location` used instead of `address` when the local style uses `address`.
- Duplicate keys or duplicate titles.

## Reporting Guidance

Do not over-report local string macros as missing `Proc.`. Inspect the `@string` definitions first.
Distinguish strong findings from possible style choices:

- Strong: duplicate key, full IEEE journal name in a file that defines `ieee_j_it`, missing conference address/month, empty pages.
- Possible: `@article` vs `@misc` for arXiv, whether NeurIPS/ICLR should include month/address, whether to abbreviate non-IEEE journals.
