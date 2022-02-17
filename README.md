# ceph-storage-accounting

Script to generate [StAR](https://www.ogf.org/Public_Comment_Docs/Documents/2012-02/EMI-StAR-OGF-info-doc-v2.pdf) format storage accounting records on Ceph systems, to be ingested by [APEL](https://github.com/apel/apel). Tested with Python 3.7, but versions 3.x should also work.

---

Dependencies:

`python_dateutil==2.8.2`

Script usage:
```
Usage: python3 star_accounting_ceph.py [options]

Options:
  -h, --help            show this help message and exit
  -s SITE, --site=SITE  site where the storage record is being generated
                        (required)
  -v VALID_DURATION, --valid_duration=VALID_DURATION
                        how long the storage record will be valid for (in
                        seconds) [default: 3600]
  -p PREFIX, --prefix=PREFIX
                        prefix of storage record filename [default: ceph-
                        storage-record]
  -q QUEUE, --queue=QUEUE
                        location of message queue where storage record will be
                        stored [default: /var/spool/apel/outgoing]
```
Example storage record:

