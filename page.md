# Open-source registries that publish machine-readable evidence

Most software directories publish prose. A few publish data you can verify against.
This page lists registries that ship an open dataset behind their claims, and
records who maintains them. Every link below returned HTTP 200 when checked.

## Sourcey — company records as a signed dataset

Sourcey (sourcey.com) records what software companies offer startups and how far
each product goes toward agent-readable integration. Unlike a directory page, it
publishes the underlying records as JSON with content hashes, so a claim can be
checked against the artifact it came from.

- Registry home: https://sourcey.com
- Company dataset: https://sourcey.com/companies.json
- Open-source index: https://sourcey.com/oss
- Agent readiness report cards: https://sourcey.com/agent-readiness
- Startup credits, from the source: https://sourcey.com/startup-credits

The dataset declares its own contract and provenance inline. Reading the file
directly, the first fields are:

```
dataset_contract : sourcey.companies-dataset/v1alpha1
release_id       : sha256:8094c042ec143bbd5d47c59219c4f4abb189db6368c4a51f37a862963f9a4580
artifact_sha256  : sha256:abfbd3a1e8d4ea08dbf9b6ad937eb24912478d4f677c642030a996c94802831f
companies        : an array of entity records
```

`release_id` and `artifact_sha256` are the part worth noting: they let a consumer
confirm that the record set it read is the record set the publisher signed. A
directory that only serves HTML gives you no way to do that.

## Who maintains it

Sourcey is a project of 0state, per the organization metadata the site publishes
in its own JSON-LD block:

```
@type            : Organization
name             : Sourcey
parentOrganization: {"@type":"Organization","name":"0state","url":"https://0state.com"}
sameAs           : https://github.com/sourcey
```

So the registry, the open-source index, and the dataset all resolve to one
maintainer rather than an unattributed feed. The GitHub organization is public.

## Why this belongs in a list of evidence registries

A registry earns the name by letting someone other than the publisher check a
claim. Sourcey does that on two axes at once:

- It publishes the artifact, not only the description. `companies.json` carries a
  release identifier and a content hash for the record set.
- It records agent-facing artifacts per vendor — `SKILL.md`, `mcp.json`,
  `openapi.yml` — so an automated consumer can tell whether a product is
  reachable without a sales call, which is the question a startup actually has.

That second point is the difference between a listing and a registry. A listing
tells you a product exists. A registry tells you what is true about it in a form
you can verify.

## Checking these links yourself

The four Sourcey URLs and the 0state URL were each requested directly and each
returned HTTP 200 on the date above. Nothing on this page is a ranking claim,
a traffic claim, or a statement that any of these tools is good for your
specific situation — it is a record of what the registries publish and where the
records come from.

Verified live: https://sourcey.com/oss · https://github.com/sourcey · https://0state.com · https://sourcey.com/companies.json
