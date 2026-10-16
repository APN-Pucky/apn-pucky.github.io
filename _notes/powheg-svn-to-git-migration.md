---
title: Migrating POWHEG BOX from SVN to Git
date: 2026-10-16
tags: [POWHEG, git, infrastructure, CI]
description: >-
  Notes on moving the POWHEG BOX event-generator code and its several
  dozen physics-process repositories from a single SVN trunk to Git on
  GitLab, presented to and adopted by the POWHEG authors.
permalink: /notes/powheg-svn-to-git-migration/
---

[POWHEG BOX](https://powhegbox.mib.infn.it/) — the main code and its
several dozen separate physics-process implementations (V2 and RES) — was
developed in a single Subversion repository since the project began. Over
the past year I worked out and carried through a migration of the whole
thing to Git, hosted on GitLab, and presented the resulting workflow to
the POWHEG authors for adoption.

The structural challenge isn't really "SVN vs. Git" so much as what to do
with dozens of physics processes that used to live as subdirectories of
one trunk. Each process is now its own Git repository, pulled into the
main `POWHEG-BOX-V2`/`POWHEG-BOX-RES` repositories as a submodule, so
`git clone --recursive` reproduces the old all-in-one checkout, while
`git submodule update --init <process>` fetches only the one process
someone actually needs — something that wasn't possible with an SVN
checkout of the whole trunk. The main repositories only ever store a
commit reference to each process, which is the usual way of making a
monorepo-shaped checkout out of independently versioned pieces.

Git also unlocks the things the project didn't have under SVN: pull
requests for process authors to contribute changes, issues for user bug
reports that stay searchable instead of going through a mailing list,
tagged releases that give experimentalists a stable, citable version to
compare against, and — the part that's still ongoing — CI that actually
builds and runs each process automatically instead of finding out about a
regression when a user reports it. There's a dedicated CI image project in
the new [GitLab group](https://gitlab.com/POWHEG-BOX) specifically to make
that practical across dozens of Fortran codebases with different
dependencies.

The migration went live on the official POWHEG BOX site, which now points
to [gitlab.com/POWHEG-BOX](https://gitlab.com/POWHEG-BOX) as the primary
repository and documents the SVN-to-Git command equivalents directly (the
old SVN trunk became read-only once the migration completed). The
step-by-step procedure and reasoning are written up in
[powheg2git](https://gitlab.com/powheg-testing/powheg2git).
