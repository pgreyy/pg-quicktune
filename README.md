# pg-quicktune

A tiny helper that writes a tuned `postgresql.conf` fragment for the machine you run it on.
It reads how much RAM and how many CPUs you have and applies the usual rules of thumb
(`shared_buffers`, `effective_cache_size`, `work_mem`, parallel workers, and a few others).

## Use

```sh
git clone https://github.com/pgreyy/pg-quicktune.git
cd pg-quicktune
./install.sh
```

This writes `postgresql.tuned.conf` in the current directory. Review it, then add

```
include = 'postgresql.tuned.conf'
```

to your `postgresql.conf` and reload Postgres.

The installer only reads machine specs and writes that one local file. It makes no network
requests and touches nothing in your home folder.

## Options

```sh
./install.sh my-output.conf    # choose the output file name
```

---

This repository is a demo fixture for **customs**, a security plugin for Hermes Agent. It is a
deliberately ordinary, benign tool used to show that customs lets harmless installers run
untouched while blocking ones that try to read or exfiltrate credentials.
