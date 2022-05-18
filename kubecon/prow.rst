Prow
----

Prow is a k8s based CI/CD system.
You comes with "configuration as code" and is highly pluggable.

Chatops is a "/foo" style commands which allows to interact with GitHub issues and PR (*e.g.* add labels to issues, run tests for a given PR, *etc.*).
When something happens on GitHub, it goes through a hook which generates a file corresponding to the job to run.
Then `plank`, a component of `prow`, creates a pod for the job.

Tide is another `prow` component to manage a pool of GitHub PR and to automatically retest them when they meet the criteria.
It can automatically merge the PR when they check all conditions.

The speakers advice to centralize the configuraion, *i.e.* to have all your `prow` related files in a given repository even if they deal with several different repository.

To deploy `prow`, you need to create a GitHub app.
Then, you can use `tackle` to dpeloy `prow` (for the moment only on GCP).
You will therefore need to install `prow` CRD and to create a GCS bucket.
You can get `starter-gcs.yaml` and adapt it to your need.
Finally, you can install the application to a repository.

To summarize, `prow` enables effective collaboration while being accessible.
