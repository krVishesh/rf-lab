# Spectrum Field Manual

A self-contained SDR + GNU Radio field manual for cyber security operators. It is a static, single-page site: no build step, no dependencies, and no server-side code.

## What is inside

- 15 modules with Study / Build / Solo checkpoints
- 10 interactive charts and six calculator-style tools
- Simulated GNU Radio labs that work without a radio, plus receive-only hardware paths
- RF security, capture, evidence handling, and defensive monitoring material
- Field reference, formula sheet, debug playbook, coverage map, and accuracy limits

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
npx wrangler pages deploy public --project-name spectrum-field-manual
```

The project name is already set in `wrangler.toml`.

## Structure

```text
spectrum-field-manual/
├── public/
│   ├── index.html      # the complete site
│   ├── _headers        # security headers for Cloudflare Pages
│   └── robots.txt
├── README.md
├── wrangler.toml
└── .gitignore
```

## Notes

- All CSS, JavaScript, and charts are embedded in `index.html`.
- No external JavaScript libraries, fonts, or build tooling are required.
- External links in the field library open in a new tab.
- The RF material is receive-first and educational. It is not a substitute for local radio regulations, licensing, calibration, or RF safety advice.
