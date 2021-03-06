[toc]
### 可用参数
- EXPLAIN [EXTENDED|DEPENDENCY|AUTHORIZATION|LOCKS|VECTORIZATION] query


## 常见的阶段
### Fetch
### Map Reduce 

## 常见的算子(operator)

## 例一
### sql 代码
```
set mapred.job.queue.name=root.zm_yarn_pool.development;
create table tmp.tmp_bi_pintuan_call_tmp_detail as
select
     call_stu_user_id as stu_user_id,
     to_date(call_start_time) as call_date,
     min(call_start_time) first_start_time,
     max(call_start_time) last_start_time,
     max(call_bridge_duration) call_bridge_duration
from
    dw.dwd_seller_call_df
where
    pt= '${day}'
group by
    to_date(call_start_time),call_stu_user_id
;
```
### 运行日志
```
INFO  : Compiling command(queryId=hive_20191107105448_dfce24f3-835d-4e9e-834e-466778ddd7c9): 
create table tmp.tmp_bi_pintuan_call_tmp_detail as
select
     call_stu_user_id as stu_user_id,
     to_date(call_start_time) as call_date,
     min(call_start_time) first_start_time,
     max(call_start_time) last_start_time,
     max(call_bridge_duration) call_bridge_duration
from
    dw.dwd_seller_call_df
where
    pt= '2019-11-06'
group by
    to_date(call_start_time),call_stu_user_id
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:stu_user_id, type:bigint, comment:null), FieldSchema(name:call_date, type:date, comment:null), FieldSchema(name:first_start_time, type:string, comment:null), FieldSchema(name:last_start_time, type:string, comment:null), FieldSchema(name:call_bridge_duration, type:string, comment:null)], properties:null)
INFO  : Completed compiling command(queryId=hive_20191107105448_dfce24f3-835d-4e9e-834e-466778ddd7c9); Time taken: 0.505 seconds
INFO  : Concurrency mode is disabled, not creating a lock manager
INFO  : Executing command(queryId=hive_20191107105448_dfce24f3-835d-4e9e-834e-466778ddd7c9): 
create table tmp.tmp_bi_pintuan_call_tmp_detail as
select
     call_stu_user_id as stu_user_id,
     to_date(call_start_time) as call_date,
     min(call_start_time) first_start_time,
     max(call_start_time) last_start_time,
     max(call_bridge_duration) call_bridge_duration
from
    dw.dwd_seller_call_df
where
    pt= '2019-11-06'
group by
    to_date(call_start_time),call_stu_user_id
WARN  : 
INFO  : Query ID = hive_20191107105448_dfce24f3-835d-4e9e-834e-466778ddd7c9
INFO  : Total jobs = 3
INFO  : Launching Job 1 out of 3
INFO  : Starting task [Stage-1:MAPRED] in serial mode
INFO  : Number of reduce tasks not specified. Estimated from input data size: 248
INFO  : In order to change the average load for a reducer (in bytes):
INFO  :   set hive.exec.reducers.bytes.per.reducer=<number>
INFO  : In order to limit the maximum number of reducers:
INFO  :   set hive.exec.reducers.max=<number>
INFO  : In order to set a constant number of reducers:
INFO  :   set mapreduce.job.reduces=<number>
INFO  : number of splits:62
INFO  : Submitting tokens for job: job_1572267407778_199747
INFO  : Executing with tokens: [Kind: HDFS_DELEGATION_TOKEN, Service: ha-hdfs:nameservice1, Ident: (token for hive: HDFS_DELEGATION_TOKEN owner=hive/zmbd-pm-server01@FAYSON.COM, renewer=yarn, realUser=, issueDate=1573095289271, maxDate=1573700089271, sequenceNumber=1562688, masterKeyId=230)]
INFO  : The url to track the job: http://zmbd-vm02:8088/proxy/application_1572267407778_199747/
INFO  : Starting Job = job_1572267407778_199747, Tracking URL = http://zmbd-vm02:8088/proxy/application_1572267407778_199747/
INFO  : Kill Command = /opt/cloudera/parcels/CDH-6.2.0-1.cdh6.2.0.p0.967373/lib/hadoop/bin/hadoop job  -kill job_1572267407778_199747
INFO  : Hadoop job information for Stage-1: number of mappers: 62; number of reducers: 248
INFO  : 2019-11-07 10:54:58,984 Stage-1 map = 0%,  reduce = 0%
INFO  : 2019-11-07 10:55:18,514 Stage-1 map = 4%,  reduce = 0%, Cumulative CPU 116.27 sec
INFO  : 2019-11-07 10:55:19,547 Stage-1 map = 23%,  reduce = 0%, Cumulative CPU 762.95 sec
INFO  : 2019-11-07 10:55:20,577 Stage-1 map = 28%,  reduce = 0%, Cumulative CPU 1001.09 sec
INFO  : 2019-11-07 10:55:21,603 Stage-1 map = 31%,  reduce = 0%, Cumulative CPU 1206.67 sec
INFO  : 2019-11-07 10:55:24,690 Stage-1 map = 37%,  reduce = 0%, Cumulative CPU 1295.15 sec
INFO  : 2019-11-07 10:55:25,719 Stage-1 map = 54%,  reduce = 0%, Cumulative CPU 1537.74 sec
INFO  : 2019-11-07 10:55:26,747 Stage-1 map = 56%,  reduce = 0%, Cumulative CPU 1568.37 sec
INFO  : 2019-11-07 10:55:27,774 Stage-1 map = 62%,  reduce = 0%, Cumulative CPU 1641.83 sec
INFO  : 2019-11-07 10:55:31,888 Stage-1 map = 65%,  reduce = 0%, Cumulative CPU 1968.42 sec
INFO  : 2019-11-07 10:55:32,915 Stage-1 map = 68%,  reduce = 0%, Cumulative CPU 1980.88 sec
INFO  : 2019-11-07 10:55:33,942 Stage-1 map = 73%,  reduce = 0%, Cumulative CPU 2061.4 sec
INFO  : 2019-11-07 10:55:34,972 Stage-1 map = 77%,  reduce = 0%, Cumulative CPU 2102.36 sec
INFO  : 2019-11-07 10:55:35,998 Stage-1 map = 81%,  reduce = 0%, Cumulative CPU 2135.09 sec
INFO  : 2019-11-07 10:55:37,025 Stage-1 map = 85%,  reduce = 0%, Cumulative CPU 2191.71 sec
INFO  : 2019-11-07 10:55:38,051 Stage-1 map = 88%,  reduce = 0%, Cumulative CPU 2299.92 sec
INFO  : 2019-11-07 10:55:39,078 Stage-1 map = 91%,  reduce = 0%, Cumulative CPU 2306.42 sec
INFO  : 2019-11-07 10:55:40,106 Stage-1 map = 92%,  reduce = 0%, Cumulative CPU 2382.45 sec
INFO  : 2019-11-07 10:55:41,134 Stage-1 map = 94%,  reduce = 0%, Cumulative CPU 2390.13 sec
INFO  : 2019-11-07 10:55:42,160 Stage-1 map = 98%,  reduce = 0%, Cumulative CPU 2409.15 sec
INFO  : 2019-11-07 10:55:43,187 Stage-1 map = 99%,  reduce = 0%, Cumulative CPU 2421.33 sec
INFO  : 2019-11-07 10:55:44,217 Stage-1 map = 100%,  reduce = 0%, Cumulative CPU 2426.06 sec
INFO  : 2019-11-07 10:55:57,592 Stage-1 map = 100%,  reduce = 2%, Cumulative CPU 2513.43 sec
INFO  : 2019-11-07 10:55:58,629 Stage-1 map = 100%,  reduce = 7%, Cumulative CPU 2756.79 sec
INFO  : 2019-11-07 10:55:59,664 Stage-1 map = 100%,  reduce = 19%, Cumulative CPU 3315.5 sec
INFO  : 2019-11-07 10:56:00,694 Stage-1 map = 100%,  reduce = 27%, Cumulative CPU 3710.27 sec
INFO  : 2019-11-07 10:56:01,724 Stage-1 map = 100%,  reduce = 35%, Cumulative CPU 4069.9 sec
INFO  : 2019-11-07 10:56:02,754 Stage-1 map = 100%,  reduce = 59%, Cumulative CPU 5189.11 sec
INFO  : 2019-11-07 10:56:03,785 Stage-1 map = 100%,  reduce = 70%, Cumulative CPU 5750.83 sec
INFO  : 2019-11-07 10:56:04,817 Stage-1 map = 100%,  reduce = 79%, Cumulative CPU 6137.35 sec
INFO  : 2019-11-07 10:56:05,847 Stage-1 map = 100%,  reduce = 81%, Cumulative CPU 6252.57 sec
INFO  : 2019-11-07 10:56:06,879 Stage-1 map = 100%,  reduce = 84%, Cumulative CPU 6447.26 sec
INFO  : 2019-11-07 10:56:07,908 Stage-1 map = 100%,  reduce = 87%, Cumulative CPU 6626.01 sec
INFO  : 2019-11-07 10:56:08,935 Stage-1 map = 100%,  reduce = 93%, Cumulative CPU 6897.42 sec
INFO  : 2019-11-07 10:56:09,963 Stage-1 map = 100%,  reduce = 94%, Cumulative CPU 6942.22 sec
INFO  : 2019-11-07 10:56:10,990 Stage-1 map = 100%,  reduce = 99%, Cumulative CPU 7255.61 sec
INFO  : 2019-11-07 10:56:12,020 Stage-1 map = 100%,  reduce = 100%, Cumulative CPU 7261.78 sec
INFO  : MapReduce Total cumulative CPU time: 0 days 2 hours 1 minutes 1 seconds 780 msec
INFO  : Ended Job = job_1572267407778_199747
INFO  : Starting task [Stage-7:CONDITIONAL] in serial mode
INFO  : Stage-4 is filtered out by condition resolver.
INFO  : Stage-3 is selected by condition resolver.
INFO  : Stage-5 is filtered out by condition resolver.
INFO  : Launching Job 3 out of 3
INFO  : Starting task [Stage-3:MAPRED] in serial mode
INFO  : Number of reduce tasks is set to 0 since there's no reduce operator
INFO  : number of splits:9
INFO  : Submitting tokens for job: job_1572267407778_199756
INFO  : Executing with tokens: [Kind: HDFS_DELEGATION_TOKEN, Service: ha-hdfs:nameservice1, Ident: (token for hive: HDFS_DELEGATION_TOKEN owner=hive/zmbd-pm-server01@FAYSON.COM, renewer=yarn, realUser=, issueDate=1573095374322, maxDate=1573700174322, sequenceNumber=1562703, masterKeyId=230)]
INFO  : The url to track the job: http://zmbd-vm02:8088/proxy/application_1572267407778_199756/
INFO  : Starting Job = job_1572267407778_199756, Tracking URL = http://zmbd-vm02:8088/proxy/application_1572267407778_199756/
INFO  : Kill Command = /opt/cloudera/parcels/CDH-6.2.0-1.cdh6.2.0.p0.967373/lib/hadoop/bin/hadoop job  -kill job_1572267407778_199756
INFO  : Hadoop job information for Stage-3: number of mappers: 9; number of reducers: 0
INFO  : 2019-11-07 10:56:24,927 Stage-3 map = 0%,  reduce = 0%
INFO  : 2019-11-07 10:56:44,457 Stage-3 map = 4%,  reduce = 0%, Cumulative CPU 153.42 sec
INFO  : 2019-11-07 10:56:50,624 Stage-3 map = 8%,  reduce = 0%, Cumulative CPU 211.07 sec
INFO  : 2019-11-07 10:56:56,788 Stage-3 map = 15%,  reduce = 0%, Cumulative CPU 267.3 sec
INFO  : 2019-11-07 10:57:02,964 Stage-3 map = 19%,  reduce = 0%, Cumulative CPU 324.38 sec
INFO  : 2019-11-07 10:57:09,152 Stage-3 map = 23%,  reduce = 0%, Cumulative CPU 380.42 sec
INFO  : 2019-11-07 10:57:15,336 Stage-3 map = 26%,  reduce = 0%, Cumulative CPU 437.01 sec
INFO  : 2019-11-07 10:57:21,501 Stage-3 map = 31%,  reduce = 0%, Cumulative CPU 495.21 sec
INFO  : 2019-11-07 10:57:27,669 Stage-3 map = 35%,  reduce = 0%, Cumulative CPU 551.8 sec
INFO  : 2019-11-07 10:57:32,803 Stage-3 map = 37%,  reduce = 0%, Cumulative CPU 564.45 sec
INFO  : 2019-11-07 10:57:33,833 Stage-3 map = 41%,  reduce = 0%, Cumulative CPU 609.31 sec
INFO  : 2019-11-07 10:57:38,966 Stage-3 map = 46%,  reduce = 0%, Cumulative CPU 669.53 sec
INFO  : 2019-11-07 10:57:45,129 Stage-3 map = 50%,  reduce = 0%, Cumulative CPU 726.42 sec
INFO  : 2019-11-07 10:57:51,290 Stage-3 map = 55%,  reduce = 0%, Cumulative CPU 782.73 sec
INFO  : 2019-11-07 10:57:56,424 Stage-3 map = 56%,  reduce = 0%, Cumulative CPU 787.66 sec
INFO  : 2019-11-07 10:57:57,451 Stage-3 map = 61%,  reduce = 0%, Cumulative CPU 837.56 sec
INFO  : 2019-11-07 10:58:03,611 Stage-3 map = 64%,  reduce = 0%, Cumulative CPU 887.64 sec
INFO  : 2019-11-07 10:58:09,783 Stage-3 map = 68%,  reduce = 0%, Cumulative CPU 937.6 sec
INFO  : 2019-11-07 10:58:15,947 Stage-3 map = 72%,  reduce = 0%, Cumulative CPU 987.31 sec
INFO  : 2019-11-07 10:58:21,080 Stage-3 map = 73%,  reduce = 0%, Cumulative CPU 999.85 sec
INFO  : 2019-11-07 10:58:22,109 Stage-3 map = 77%,  reduce = 0%, Cumulative CPU 1037.2 sec
INFO  : 2019-11-07 10:58:27,243 Stage-3 map = 80%,  reduce = 0%, Cumulative CPU 1080.41 sec
INFO  : 2019-11-07 10:58:33,408 Stage-3 map = 84%,  reduce = 0%, Cumulative CPU 1132.66 sec
INFO  : 2019-11-07 10:58:39,588 Stage-3 map = 87%,  reduce = 0%, Cumulative CPU 1182.26 sec
INFO  : 2019-11-07 10:58:45,750 Stage-3 map = 90%,  reduce = 0%, Cumulative CPU 1231.84 sec
INFO  : 2019-11-07 10:58:50,886 Stage-3 map = 91%,  reduce = 0%, Cumulative CPU 1239.13 sec
INFO  : 2019-11-07 10:58:51,912 Stage-3 map = 95%,  reduce = 0%, Cumulative CPU 1275.61 sec
INFO  : 2019-11-07 10:58:58,094 Stage-3 map = 96%,  reduce = 0%, Cumulative CPU 1308.76 sec
INFO  : 2019-11-07 10:59:04,260 Stage-3 map = 98%,  reduce = 0%, Cumulative CPU 1335.01 sec
INFO  : 2019-11-07 10:59:06,314 Stage-3 map = 99%,  reduce = 0%, Cumulative CPU 1338.99 sec
INFO  : 2019-11-07 10:59:10,422 Stage-3 map = 100%,  reduce = 0%, Cumulative CPU 1350.95 sec
INFO  : MapReduce Total cumulative CPU time: 22 minutes 30 seconds 950 msec
INFO  : Ended Job = job_1572267407778_199756
INFO  : Starting task [Stage-0:MOVE] in serial mode
INFO  : Moving data to directory hdfs://nameservice1/user/hive/warehouse/tmp.db/tmp_bi_pintuan_call_tmp_detail from hdfs://nameservice1/user/hive/warehouse/tmp.db/.hive-staging_hive_2019-11-07_10-54-48_581_4998208461212321770-974/-ext-10001
INFO  : Starting task [Stage-8:DDL] in serial mode
INFO  : Starting task [Stage-2:STATS] in serial mode
INFO  : MapReduce Jobs Launched: 
INFO  : Stage-Stage-1: Map: 62  Reduce: 248   Cumulative CPU: 7261.78 sec   HDFS Read: 3284441895 HDFS Write: 2361824630 HDFS EC Read: 0 SUCCESS
INFO  : Stage-Stage-3: Map: 9   Cumulative CPU: 1350.95 sec   HDFS Read: 2361857748 HDFS Write: 2361814820 HDFS EC Read: 0 SUCCESS
INFO  : Total MapReduce CPU Time Spent: 0 days 2 hours 23 minutes 32 seconds 730 msec
INFO  : Completed executing command(queryId=hive_20191107105448_dfce24f3-835d-4e9e-834e-466778ddd7c9); Time taken: 464.296 seconds
INFO  : OK
```

## 例二
### SQL 代码
```
set mapred.job.queue.name=root.zm_yarn_pool.production;
select
   a.*,b.bu
from
(
   select
       *
   from
       ods.ods_gp_group_df
   where
       pt='${day}'
       and status=2
) a
inner join (
   select
       *
   from
       ods.ods_gp_activity_info_df
   where
       pt='${day}'
       and act_tag!=1
 ) b
on
   a.act_id=b.id
;
```
### 运行日志
```
INFO  : Compiling command(queryId=hive_20191107193833_6aecc322-ab4c-47b3-8303-a31f57c87af9): 
select
   a.*,b.bu
from
(
   select
       *
   from
       ods.ods_gp_group_df
   where
       pt='2019-11-06'
       and status=2
) a
inner join (
   select
       *
   from
       ods.ods_gp_activity_info_df
   where
       pt='2019-11-06'
       and act_tag!=1
 ) b
on
   a.act_id=b.id
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:a.id, type:int, comment:null), FieldSchema(name:a.group_no, type:string, comment:null), FieldSchema(name:a.open_time, type:string, comment:null), FieldSchema(name:a.close_time, type:string, comment:null), FieldSchema(name:a.act_name, type:string, comment:null), FieldSchema(name:a.captain, type:string, comment:null), FieldSchema(name:a.captain_id, type:bigint, comment:null), FieldSchema(name:a.member_num, type:int, comment:null), FieldSchema(name:a.act_id, type:int, comment:null), FieldSchema(name:a.status, type:tinyint, comment:null), FieldSchema(name:a.create_time, type:string, comment:null), FieldSchema(name:a.update_time, type:string, comment:null), FieldSchema(name:a.pt, type:string, comment:null), FieldSchema(name:b.bu, type:tinyint, comment:null)], properties:null)
INFO  : Completed compiling command(queryId=hive_20191107193833_6aecc322-ab4c-47b3-8303-a31f57c87af9); Time taken: 0.499 seconds
INFO  : Concurrency mode is disabled, not creating a lock manager
INFO  : Executing command(queryId=hive_20191107193833_6aecc322-ab4c-47b3-8303-a31f57c87af9): 
select
   a.*,b.bu
from
(
   select
       *
   from
       ods.ods_gp_group_df
   where
       pt='2019-11-06'
       and status=2
) a
inner join (
   select
       *
   from
       ods.ods_gp_activity_info_df
   where
       pt='2019-11-06'
       and act_tag!=1
 ) b
on
   a.act_id=b.id
WARN  : 
INFO  : Query ID = hive_20191107193833_6aecc322-ab4c-47b3-8303-a31f57c87af9
INFO  : Total jobs = 1
INFO  : Starting task [Stage-4:MAPREDLOCAL] in serial mode
INFO  : Execution completed successfully
INFO  : MapredLocal task succeeded
INFO  : Launching Job 1 out of 1
INFO  : Starting task [Stage-3:MAPRED] in serial mode
INFO  : Number of reduce tasks is set to 0 since there's no reduce operator
INFO  : number of splits:1
INFO  : Submitting tokens for job: job_1572267407778_209320
INFO  : Executing with tokens: [Kind: HDFS_DELEGATION_TOKEN, Service: ha-hdfs:nameservice1, Ident: (token for hive: HDFS_DELEGATION_TOKEN owner=hive/zmbd-pm-server01@FAYSON.COM, renewer=yarn, realUser=, issueDate=1573126723071, maxDate=1573731523071, sequenceNumber=1577554, masterKeyId=230)]
INFO  : The url to track the job: http://zmbd-vm02:8088/proxy/application_1572267407778_209320/
INFO  : Starting Job = job_1572267407778_209320, Tracking URL = http://zmbd-vm02:8088/proxy/application_1572267407778_209320/
INFO  : Kill Command = /opt/cloudera/parcels/CDH-6.2.0-1.cdh6.2.0.p0.967373/lib/hadoop/bin/hadoop job  -kill job_1572267407778_209320
INFO  : Hadoop job information for Stage-3: number of mappers: 1; number of reducers: 0
INFO  : 2019-11-07 19:38:55,196 Stage-3 map = 0%,  reduce = 0%
INFO  : 2019-11-07 19:39:35,539 Stage-3 map = 100%,  reduce = 0%, Cumulative CPU 7.56 sec
INFO  : MapReduce Total cumulative CPU time: 7 seconds 560 msec
INFO  : Ended Job = job_1572267407778_209320
INFO  : MapReduce Jobs Launched: 
INFO  : Stage-Stage-3: Map: 1   Cumulative CPU: 7.56 sec   HDFS Read: 2539123 HDFS Write: 1237143 HDFS EC Read: 0 SUCCESS
INFO  : Total MapReduce CPU Time Spent: 7 seconds 560 msec
INFO  : Completed executing command(queryId=hive_20191107193833_6aecc322-ab4c-47b3-8303-a31f57c87af9); Time taken: 63.615 seconds
INFO  : OK
```
### 运行日志2
```
INFO  : Compiling command(queryId=hive_20191107200001_ca033117-9930-4283-8504-8c2ddf7a1d8d): 
select
    
   /*+ MAPJOIN(b)*/ a.*,b.bu
from
(
   select
       *
   from
       ods.ods_gp_group_df
   where
       pt='2019-11-06'
       and status=2
) a
inner join (
   select
       *
   from
       ods.ods_gp_activity_info_df
   where
       pt='2019-11-06'
       and act_tag!=1
 ) b
on
   a.act_id=b.id
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:a.id, type:int, comment:null), FieldSchema(name:a.group_no, type:string, comment:null), FieldSchema(name:a.open_time, type:string, comment:null), FieldSchema(name:a.close_time, type:string, comment:null), FieldSchema(name:a.act_name, type:string, comment:null), FieldSchema(name:a.captain, type:string, comment:null), FieldSchema(name:a.captain_id, type:bigint, comment:null), FieldSchema(name:a.member_num, type:int, comment:null), FieldSchema(name:a.act_id, type:int, comment:null), FieldSchema(name:a.status, type:tinyint, comment:null), FieldSchema(name:a.create_time, type:string, comment:null), FieldSchema(name:a.update_time, type:string, comment:null), FieldSchema(name:a.pt, type:string, comment:null), FieldSchema(name:b.bu, type:tinyint, comment:null)], properties:null)
INFO  : Completed compiling command(queryId=hive_20191107200001_ca033117-9930-4283-8504-8c2ddf7a1d8d); Time taken: 0.487 seconds
INFO  : Concurrency mode is disabled, not creating a lock manager
INFO  : Executing command(queryId=hive_20191107200001_ca033117-9930-4283-8504-8c2ddf7a1d8d): 
select
    
   /*+ MAPJOIN(b)*/ a.*,b.bu
from
(
   select
       *
   from
       ods.ods_gp_group_df
   where
       pt='2019-11-06'
       and status=2
) a
inner join (
   select
       *
   from
       ods.ods_gp_activity_info_df
   where
       pt='2019-11-06'
       and act_tag!=1
 ) b
on
   a.act_id=b.id
WARN  : 
INFO  : Query ID = hive_20191107200001_ca033117-9930-4283-8504-8c2ddf7a1d8d
INFO  : Total jobs = 1
INFO  : Starting task [Stage-4:MAPREDLOCAL] in serial mode
INFO  : Execution completed successfully
INFO  : MapredLocal task succeeded
INFO  : Launching Job 1 out of 1
INFO  : Starting task [Stage-3:MAPRED] in serial mode
INFO  : Number of reduce tasks is set to 0 since there's no reduce operator
INFO  : number of splits:1
INFO  : Submitting tokens for job: job_1572267407778_209643
INFO  : Executing with tokens: [Kind: HDFS_DELEGATION_TOKEN, Service: ha-hdfs:nameservice1, Ident: (token for hive: HDFS_DELEGATION_TOKEN owner=hive/zmbd-pm-server01@FAYSON.COM, renewer=yarn, realUser=, issueDate=1573128010794, maxDate=1573732810794, sequenceNumber=1578125, masterKeyId=230)]
INFO  : The url to track the job: http://zmbd-vm02:8088/proxy/application_1572267407778_209643/
INFO  : Starting Job = job_1572267407778_209643, Tracking URL = http://zmbd-vm02:8088/proxy/application_1572267407778_209643/
INFO  : Kill Command = /opt/cloudera/parcels/CDH-6.2.0-1.cdh6.2.0.p0.967373/lib/hadoop/bin/hadoop job  -kill job_1572267407778_209643
INFO  : Hadoop job information for Stage-3: number of mappers: 1; number of reducers: 0
INFO  : 2019-11-07 20:00:51,618 Stage-3 map = 0%,  reduce = 0%
INFO  : 2019-11-07 20:01:25,628 Stage-3 map = 100%,  reduce = 0%, Cumulative CPU 8.79 sec
INFO  : MapReduce Total cumulative CPU time: 8 seconds 790 msec
INFO  : Ended Job = job_1572267407778_209643
INFO  : MapReduce Jobs Launched: 
INFO  : Stage-Stage-3: Map: 1   Cumulative CPU: 8.79 sec   HDFS Read: 2539140 HDFS Write: 1237143 HDFS EC Read: 0 SUCCESS
INFO  : Total MapReduce CPU Time Spent: 8 seconds 790 msec
INFO  : Completed executing command(queryId=hive_20191107200001_ca033117-9930-4283-8504-8c2ddf7a1d8d); Time taken: 85.474 seconds
INFO  : OK
```