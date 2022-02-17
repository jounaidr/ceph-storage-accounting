# ceph-storage-accounting

Script to generate [StAR](https://www.ogf.org/Public_Comment_Docs/Documents/2012-02/EMI-StAR-OGF-info-doc-v2.pdf) format storage accounting records on Ceph systems, to be ingested by [APEL](https://github.com/apel/apel). Tested with Python 3.7, but versions 3.x should also work.

---

Dependencies:

`python_dateutil==2.8.2`

Script usage:
```shell
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
Example storage record (see [docs]((https://www.ogf.org/Public_Comment_Docs/Documents/2012-02/EMI-StAR-OGF-info-doc-v2.pdf)) for info on properties):

```xml
<?xml version="1.0" ?>
<sr:StorageUsageRecords xmlns:sr="http://eu-emi.eu/namespaces/2011/02/storagerecord">
  <sr:StorageUsageRecord>
    <sr:RecordIdentity sr:createTime="2022-02-17T13:07:50Z" sr:recordId="ceph.host.org/sr/14423"/>
    <sr:StorageSystem>ceph.host.org</sr:StorageSystem>
    <sr:StorageShare>pool-6</sr:StorageShare>
    <sr:FileCount>3</sr:FileCount>
    <sr:SubjectIdentity>
      <sr:LocalUser>bob</sr:LocalUser>
    </sr:SubjectIdentity>
    <sr:MeasureTime>2022-01-22T12:53:02Z</sr:MeasureTime>
    <sr:ValidDuration>PT3600S</sr:ValidDuration>
    <sr:ResourceCapacityUsed>97698</sr:ResourceCapacityUsed>
    <sr:LogicalCapacityUsed>102400</sr:LogicalCapacityUsed>
    <sr:ResourceCapacityAllocated>-1</sr:ResourceCapacityAllocated>
  </sr:StorageUsageRecord>
</sr:StorageUsageRecords>
```