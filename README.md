# RF Lab

**Version:** 1.1

The Spectrum Field Manual: a self-contained SDR + GNU Radio field manual for cyber security operators, expanded with physical-layer and hardware material from *Practical SDR* (Clark & Clark, 2025). It is a static, single-page site: no build step, no dependencies, and no server-side code.

## What is inside

- 19 modules with Study / Build / Solo checkpoints
- 13 interactive charts, six calculator-style tools, and a 65-block GRC guide
- Simulated GNU Radio labs that work without a radio, plus receive-only hardware paths
- RF security, capture, evidence handling, and defensive monitoring material
- Per-chapter GRC block sidebar with what / why / parameters / gotchas
- Searchable 65-block guide plus a downloadable 564-block GRC catalogue generated from the installed GNU Radio block definitions
- Field reference, formula sheet, debug playbook, coverage map, and accuracy limits

The physical-layer track is informed by [*Practical SDR*](https://nostarch.com/practical-sdr) by David Clark and Paul Clark (No Starch Press, 2025). No text or figures from the book are reproduced here. The downloadable GRC catalogue is generated locally from the block definition files installed with GNU Radio 3.10.9.2.

Progress is stored in the visitor’s browser under the localStorage key `spectrum-field-manual:v1`. It is not sent to a server.

## Local preview

```bash
python3 -m http.server 8099 -d public
```

Then open <http://localhost:8099/>.

## Cloudflare Pages

### Git integration

1. Push this repository to GitHub/GitLab.
2. In Cloudflare Pages, create a project and connect the repository.
3. Use these settings:
   - **Framework preset:** None
   - **Build command:** leave blank
   - **Build output directory:** `public`
4. Deploy.

The `wrangler.toml` file also declares the Pages output directory for Wrangler-based deploys.

### Direct upload with Wrangler

```bash
npx wrangler pages deploy public --project-name rf-lab
```

The project name `rf-lab` is already set in `wrangler.toml`.

### If the build log says `npx wrangler deploy`

This is a **Pages** site, not a Worker. `npx wrangler deploy` is the Workers deploy command and will fail with:

```text
Missing entry-point to Worker script or to assets directory
```

Fix it in one of two ways:

1. **If the project is Pages:** open **Settings → Builds & deployments** and set:
   - **Framework preset:** None
   - **Build command:** blank
   - **Build output directory:** `public`
   - **Deploy command**, if shown: `npx wrangler pages deploy public --project-name rf-lab`
2. **If you created a Worker instead:** delete it and create a new project via **Workers & Pages → Create application → Pages → Connect to Git**.

Do not add `main` or `[assets]` to `wrangler.toml` just to satisfy `wrangler deploy`; that deploys a Worker rather than this Pages project.

## Structure

```text
rf-lab/
├── public/
│   ├── index.html      # the complete site
│   ├── _headers        # security headers for Cloudflare Pages
│   ├── robots.txt
│   └── grc-block-catalog.csv
├── README.md
├── wrangler.toml
└── .gitignore
```

## Notes

- All CSS, JavaScript, and charts are embedded in `index.html`.
- No external JavaScript libraries, fonts, or build tooling are required.
- External links in the field library open in a new tab.
- The RF material is receive-first and educational. It is not a substitute for local radio regulations, licensing, calibration, or RF safety advice.
