Ansible Role: Blast Database Download
=====================================

An Ansible role that installs [blastdl][].

Table of Contents
-----------------

<!-- toc -->

- [Requirements](#requirements)
- [Role Variables](#role-variables)
- [Dependencies](#dependencies)
- [Example Playbook](#example-playbook)
  * [Top-Level Playbook](#top-level-playbook)
  * [Role Dependency](#role-dependency)
- [License](#license)
- [Author Information](#author-information)

<!-- tocstop -->

Requirements
------------

- Ansible 2+
- **cron** on the target host

Role Variables
--------------

These are the used variables and their defaults.

```yml
blastdl_user: 'blastdl'

blastdl_group: 'blastdl'

blastdl_home: '/var/lib/{{ blastdl_user }}'

blastdl_repo_dir: '{{ blastdl_home }}/src/blastdl'

blastdl_db_dir: '/data/db/blast'

blastdl_databases:
  - nr
  - nt
  - refseq_genomic
  - refseq_protein
```

Dependencies
------------

None.

Example Playbook
----------------

Add to `requirements.yml`:

```yml
---

- src: idiv-biodiversity.blastdl

...
```

Download:

```console
$ ansible-galaxy install -r requirements.yml
```

### Top-Level Playbook

Write a top-level playbook:

```yml
---

- name: blast database download
  hosts: head
  roles:
    - role: idiv-biodiversity.blastdl
      tags:
        - blast
        - blastdl

...
```

### Role Dependency

Define the role dependency in `meta/main.yml`:

```yml
---

dependencies:

  - role: idiv-biodiversity.blastdl
    tags:
      - blast
      - blastdl

...
```

License
-------

MIT

Author Information
------------------

This role was created in 2017 by [Christian Krause][author] aka [wookietreiber at GitHub][wookietreiber], HPC cluster systems administrator at the [German Centre for Integrative Biodiversity Research (iDiv)][idiv].


[author]: https://www.idiv.de/groups_and_people/employees/details/eshow/krause-christian.html
[idiv]: https://www.idiv.de/
[wookietreiber]: https://github.com/wookietreiber
[blastdl]: https://github.com/idiv-biodiversity/blastdl
