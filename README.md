# 一、Flowable数据库表命名规则 按字典顺序整理
ACT_CMMN_* : 待整理  
ACT_CO_* : 待整理  
ACT_DMN_* : 待整理  
ACT_EVT_LOG : 事件日志  
ACT_FO_* : 待整理整理  
ACT_GE_* : 普通数据，各种情况都使用的数据。  
ACT_HI_* : ’HI’表示history。就是这些表包含着历史的相关数据，如结束的流程实例，变量，任务，等等。  
ACT_ID_* : ’ID’表示identity(组织机构)。这些表包含标识的信息，如用户，用户组，等等。  
ACT_FROCDEE_INFO : 待整理  
ACT_RE_* : ’RE’表示repository（存储）。RepositoryService接口操作的表。带此前缀的表包含的是静态信息，如，流程定义，流程的资源（图片，规则等）。  
ACT_RU_* : ’RU’表示runtime。这是运行时的表存储着流程变量，用户任务，变量，职责（job）等运行时的数据。flowable只存储实例执行期间的运行时数据，当流程实例结束时，将删除这些记录。这就保证了这些运行时的表小且快。  

# 二、数据库表结构

| 表名 | 说明 | 备注 |
| :-- | :-- | :-- |
| ACT_CMMN_CASEDEF |  |  |
| ACT_CMMN_DATABASECHANGELOG | | |
| ACT_CMMN_DATABASECHANGELOGLOCK | | |
| ACT_CMMN_DEPLOYMENT  | | |
| ACT_CMMN_DEPLOYMENT_RESOURCE | | |
| ACT_CMMN_HI_CASE_INST | | |
| ACT_CMMN_HI_MIL_INST | | |
| ACT_CMMN_RU_CASE_INST | | |
| ACT_CMMN_RU_MIL_INST | | |
| ACT_CMMN_RU_PLAN_ITEM_INST | | |
| ACT_CMMN_RU_SENTRY_PART_INST | | |
| ACT_CO_CONTENT_ITEM | | |
| ACT_CO_DATABASECHANGELOG | | |
| ACT_CO_DATABASECHANGELOGLOCK | | |
| ACT_DMN_DATABASECHANGELOG | | |
| ACT_DMN_DATABASECHANGELOGLOCK | | |
| ACT_DMN_DECISION_TABLE | | |
| ACT_DMN_DEPLOYMENT | | |
| ACT_DMN_DEPLOYMENT_RESOURCE | | |
| ACT_DMN_HI_DECISION_EXECUTION | | |
| ACT_EVT_LOG | 事件日志表 | |
| ACT_FO_DATABASECHANGELOG | | |
| ACT_FO_DATABASECHANGELOGLOCK | | |
| ACT_FO_FORM_DEFINITION | | |
| ACT_FO_FORM_DEPLOYMENT | | |
| ACT_FO_FORM_INSTANCE | | |
| ACT_FO_FORM_RESOURCE | | |
| ACT_GE_BYTEARRAY | 通用的流程定义和流程资源 | |
| ACT_GE_PROPERTY | 系统相关属性 | |
| ACT_HI_ACTINST | 历史的行为实例 | |
| ACT_HI_ATTACHMENT | 历史的流程附件 | |
| ACT_HI_COMMENT | 历史的说明性信息 | |
| ACT_HI_DETAIL | 历史的流程运行中的细节信息 | |
| ACT_HI_IDENTITYLINK | 历史的流程运行过程中用户关系 | |
| ACT_HI_PROCINST | 历史的流程实例 | |
| ACT_HI_TASKINST | 历史的任务实例 | |
| ACT_HI_VARINST | 历史的流程运行中的变量信息 | |
| ACT_ID_BYTEARRAY | 用户二进制数据表 | |
| ACT_ID_GROUP | 用户组信息表 | |
| ACT_ID_INFO | 用户信息详情表 | |
| ACT_ID_MEMBERSHIP | 用户与用户组关系表 | |
| ACT_ID_PRIV | 用户权限表 | |
| ACT_ID_PRIV_MAPPING | 用户或组权限关系表 | |
| ACT_ID_PROPERTY | 用户属性表 | |
| ACT_ID_TOKEN | 用户系统登录日志表 | |
| ACT_ID_USER | 用户表 | |
| ACT_PROCDEF_INFO | 流程定义信息 | |
| ACT_RE_DEPLOYMENT | 署单数据表 | |
| ACT_RE_MODEL | 流程设计模型部署表 | |
| ACT_RE_PROCDEF | 流程定义表 | |
| ACT_RU_DEADLETTER_JOB | 正在运行的任务表 | |
| ACT_RU_EVENT_SUBSCR | 运行时事件 | |
| ACT_RU_EXECUTION | 运行时流程执行实例 | |
| ACT_RU_HISTORY_JOB | 历史作业表 | |
| ACT_RU_IDENTITYLINK | 运行时用户关系信息 | |
| ACT_RU_JOB | 运行时作业表（一般工作表） | |
| ACT_RU_SUSPENDED_JOB | 暂停作业表 | |
| ACT_RU_TASK | 运行时任务表 | |
| ACT_RU_TIMER_JOB | 定时作业表 | |
| ACT_RU_VARIABLE | 运行时变量表 | |

# 三、数据字典

## ACT_CMMN_CASEDEF

| 字段 | 类型 | 是否为主键 | 是否允许为空 | 默认值 | 说明 | 备注 |  
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |  
| ID_ | varchar(255) | Y | N | | 主键 | |  
| REV_ | int(11) | N | N | | | |  
| NAME_ | varchar(255) | N | Y | NULL | 名称 | |  
| KEY_ | varchar(255) | N | N | | | |  
| VERSION_ | int(11) | N | N | | | |  
| CATEGORY_ | varchar(255) | N | Y | NULL | 类别 | |  
| DEPLOYMENT_ID_ | varchar(255) | N | Y | NULL | 关联ACT_CMMN_DEPLOYMENT表ID | |  
| RESOURCE_NAME_ | varchar(4000) | N | Y | NULL | | |  
| DESCRIPTION_| varchar(4000) | N | Y | NULL | | |  
| HAS_GRAPHICAL_NOTATION_| bit(1) | N | Y | NULL | | |  
| TENANT_ID_ | varchar(255) | N | Y | 空字符串 | | |  
| DGRM_RESOURCE_NAME_ | varchar(4000) | N | Y | NULL | | |  
| HAS_START_FORM_KEY_| bit(1) | N | Y | NULL | | |  

> SQL  

~~~
--
-- 表的结构 `ACT_CMMN_CASEDEF`
--

CREATE TABLE `ACT_CMMN_CASEDEF` (
  `ID_` varchar(255) NOT NULL,
  `REV_` int(11) NOT NULL,
  `NAME_` varchar(255) DEFAULT NULL,
  `KEY_` varchar(255) NOT NULL,
  `VERSION_` int(11) NOT NULL,
  `CATEGORY_` varchar(255) DEFAULT NULL,
  `DEPLOYMENT_ID_` varchar(255) DEFAULT NULL,
  `RESOURCE_NAME_` varchar(4000) DEFAULT NULL,
  `DESCRIPTION_` varchar(4000) DEFAULT NULL,
  `HAS_GRAPHICAL_NOTATION_` bit(1) DEFAULT NULL,
  `TENANT_ID_` varchar(255) DEFAULT '',
  `DGRM_RESOURCE_NAME_` varchar(4000) DEFAULT NULL,
  `HAS_START_FORM_KEY_` bit(1) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

--
-- 转储表的索引
--

--
-- 表的索引 `ACT_CMMN_CASEDEF`
--
ALTER TABLE `ACT_CMMN_CASEDEF`
  ADD PRIMARY KEY (`ID_`),
  ADD KEY `ACT_IDX_CASE_DEF_DPLY` (`DEPLOYMENT_ID_`);

--
-- 限制导出的表
--

--
-- 限制表 `ACT_CMMN_CASEDEF`
--
ALTER TABLE `ACT_CMMN_CASEDEF`
  ADD CONSTRAINT `ACT_FK_CASE_DEF_DPLY` FOREIGN KEY (`DEPLOYMENT_ID_`) REFERENCES `ACT_CMMN_DEPLOYMENT` (`ID_`);
COMMIT;
~~~

## ACT_CMMN_DATABASECHANGELOG

| 字段 | 类型 | 是否为主键 | 是否允许为空 | 默认值 | 说明 | 备注 |  
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |  
| ID | varchar(255) | N | N | | | |  
| AUTHOR | varchar(255) | N | N | | 操作人 | |  
| FILENAME | varchar(255) | N | N | | 文件名 | |  
| DATEEXECUTED | datetime | N | N | | 执行时间 | |
| ORDEREXECUTED | int(11) | N | N | | 执行顺序 | |
| EXECTYPE | varchar(10) | N | N | | | |
| MD5SUM | varchar(35) | N | Y | NULL | | |
| DESCRIPTION | varchar(255) | N | Y | NULL | 描述 | |
| COMMENTS | varchar(255) | N | Y | NULL | | |
| TAG | varchar(255) | N | Y | NULL | 标签 | |
| LIQUIBASE | varchar(20) | N | Y | NULL | | |
| CONTEXTS | varchar(255) | N | Y | NULL | | |
| LABELS | varchar(255) | N | Y | NULL | | |
| DEPLOYMENT_ID | varchar(10) | N | Y | NULL | | |

> SQL  

~~~
--
-- 表的结构 `ACT_CMMN_DATABASECHANGELOG`
--

CREATE TABLE `ACT_CMMN_DATABASECHANGELOG` (
  `ID` varchar(255) NOT NULL,
  `AUTHOR` varchar(255) NOT NULL,
  `FILENAME` varchar(255) NOT NULL,
  `DATEEXECUTED` datetime NOT NULL,
  `ORDEREXECUTED` int(11) NOT NULL,
  `EXECTYPE` varchar(10) NOT NULL,
  `MD5SUM` varchar(35) DEFAULT NULL,
  `DESCRIPTION` varchar(255) DEFAULT NULL,
  `COMMENTS` varchar(255) DEFAULT NULL,
  `TAG` varchar(255) DEFAULT NULL,
  `LIQUIBASE` varchar(20) DEFAULT NULL,
  `CONTEXTS` varchar(255) DEFAULT NULL,
  `LABELS` varchar(255) DEFAULT NULL,
  `DEPLOYMENT_ID` varchar(10) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
~~~

## ACT_CMMN_DATABASECHANGELOGLOCK

| 字段 | 类型 | 是否为主键 | 是否允许为空 | 默认值 | 说明 | 备注 |  
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |  
| ID_ | int(11) | Y | N | | 主键 | |  
| LOCKED | bit(1) | N | N | | | |  
| LOCKGRANTED | datetime | N | Y | NULL | 锁定时间 | |  
| LOCKEDBY | varchar(255) | N | Y | NULL | 锁定人 | |  

> SQL  

~~~
--
-- 表的结构 `ACT_CMMN_DATABASECHANGELOGLOCK`
--

CREATE TABLE `ACT_CMMN_DATABASECHANGELOGLOCK` (
  `ID` int(11) NOT NULL,
  `LOCKED` bit(1) NOT NULL,
  `LOCKGRANTED` datetime DEFAULT NULL,
  `LOCKEDBY` varchar(255) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

--
-- 转储表的索引
--

--
-- 表的索引 `ACT_CMMN_DATABASECHANGELOGLOCK`
--
ALTER TABLE `ACT_CMMN_DATABASECHANGELOGLOCK`
  ADD PRIMARY KEY (`ID`);
COMMIT;
~~~

## ACT_CMMN_DEPLOYMENT

| 字段 | 类型 | 是否为主键 | 是否允许为空 | 默认值 | 说明 | 备注 |  
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |  
| ID_ | varchar(255) | Y | N | | 主键 | |  
| NAME_ | varchar(255) | N | Y | NULL | 名称 | |  
| CATEGORY_ | varchar(255) | N | Y | NULL | 类别 | |  
| KEY_ | varchar(255) | N | Y | NULL | | |  
| DEPLOY_TIME_ | datetime | N | Y | NULL | 部署时间 | |  
| PARENT_DEPLOYMENT_ID_ | varchar(255) | N | Y | NULL | | |  
| TENANT_ID_ | varchar(255) | N | Y | 空字符串 | | |  

> SQL  

~~~
--
-- 表的结构 `ACT_CMMN_DEPLOYMENT`
--

CREATE TABLE `ACT_CMMN_DEPLOYMENT` (
  `ID_` varchar(255) NOT NULL,
  `NAME_` varchar(255) DEFAULT NULL,
  `CATEGORY_` varchar(255) DEFAULT NULL,
  `KEY_` varchar(255) DEFAULT NULL,
  `DEPLOY_TIME_` datetime DEFAULT NULL,
  `PARENT_DEPLOYMENT_ID_` varchar(255) DEFAULT NULL,
  `TENANT_ID_` varchar(255) DEFAULT ''
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

--
-- 转储表的索引
--

--
-- 表的索引 `ACT_CMMN_DEPLOYMENT`
--
ALTER TABLE `ACT_CMMN_DEPLOYMENT`
  ADD PRIMARY KEY (`ID_`);
COMMIT;
~~~

## ACT_CMMN_DEPLOYMENT_RESOURCE

| 字段 | 类型 | 是否为主键 | 是否允许为空 | 默认值 | 说明 | 备注 |  
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |  
| ID_ | varchar(255) | Y | N | | 主键 | |  
| NAME_ | varchar(255) | N | Y | NULL | 名称 | |  
| DEPLOYMENT_ID_ | varchar(255) | N | Y | NULL | 关联ACT_DMN_DEPLOYMENT表ID | |  
| RESOURCE_BYTES_ | longblob | N | Y | NULL | 源码 | |  
| GENERATED_ | bit(1) | N | Y | NULL | | |  

> SQL  

~~~
--
-- 表的结构 `ACT_CMMN_DEPLOYMENT_RESOURCE`
--

CREATE TABLE `ACT_CMMN_DEPLOYMENT_RESOURCE` (
  `ID_` varchar(255) NOT NULL,
  `NAME_` varchar(255) DEFAULT NULL,
  `DEPLOYMENT_ID_` varchar(255) DEFAULT NULL,
  `RESOURCE_BYTES_` longblob,
  `GENERATED_` bit(1) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

--
-- 转储表的索引
--

--
-- 表的索引 `ACT_CMMN_DEPLOYMENT_RESOURCE`
--
ALTER TABLE `ACT_CMMN_DEPLOYMENT_RESOURCE`
  ADD PRIMARY KEY (`ID_`),
  ADD KEY `ACT_IDX_CMMN_RSRC_DPL` (`DEPLOYMENT_ID_`);

--
-- 限制导出的表
--

--
-- 限制表 `ACT_CMMN_DEPLOYMENT_RESOURCE`
--
ALTER TABLE `ACT_CMMN_DEPLOYMENT_RESOURCE`
  ADD CONSTRAINT `ACT_FK_CMMN_RSRC_DPL` FOREIGN KEY (`DEPLOYMENT_ID_`) REFERENCES `ACT_CMMN_DEPLOYMENT` (`ID_`);
COMMIT;
~~~

## ACT_CMMN_HI_CASE_INST

| 字段 | 类型 | 是否为主键 | 是否允许为空 | 默认值 | 说明 | 备注 |  
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |  
| ID_ | varchar(255) | Y | N | | 主键 | |  
| REV_ | int(11) | N | N | | | |  
| BUSINESS_KEY_ | varchar(255) | N | Y | NULL | | |  
| NAME_ | varchar(255) | N | Y | NULL | 名称 | |
| PARENT_ID_ | varchar(255) | N | Y | NULL | | |  
| CASE_DEF_ID_ | varchar(255) | N | Y | NULL | | |  
| STATE_ | varchar(255) | N | Y | NULL | 状态 | |  
| START_TIME_ | datetime | N | Y | NULL | 开始时间 | |  
| END_TIME_ | datetime | N | Y | NULL | 结束时间 | |  
| START_USER_ID_ | varchar(255) | N | Y | NULL | 开始用户ID | |  
| CALLBACK_ID_ | varchar(255) | N | Y | NULL | 回调ID | |  
| CALLBACK_TYPE_ | varchar(255) | N | Y | NULL | 回调类别 | |  
| TENANT_ID_ | varchar(255) | N | Y | 空字符串 | | |  

> SQL  

~~~
--
-- 表的结构 `ACT_CMMN_HI_CASE_INST`
--

CREATE TABLE `ACT_CMMN_HI_CASE_INST` (
  `ID_` varchar(255) NOT NULL,
  `REV_` int(11) NOT NULL,
  `BUSINESS_KEY_` varchar(255) DEFAULT NULL,
  `NAME_` varchar(255) DEFAULT NULL,
  `PARENT_ID_` varchar(255) DEFAULT NULL,
  `CASE_DEF_ID_` varchar(255) DEFAULT NULL,
  `STATE_` varchar(255) DEFAULT NULL,
  `START_TIME_` datetime DEFAULT NULL,
  `END_TIME_` datetime DEFAULT NULL,
  `START_USER_ID_` varchar(255) DEFAULT NULL,
  `CALLBACK_ID_` varchar(255) DEFAULT NULL,
  `CALLBACK_TYPE_` varchar(255) DEFAULT NULL,
  `TENANT_ID_` varchar(255) DEFAULT ''
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

--
-- 转储表的索引
--

--
-- 表的索引 `ACT_CMMN_HI_CASE_INST`
--
ALTER TABLE `ACT_CMMN_HI_CASE_INST`
  ADD PRIMARY KEY (`ID_`);
COMMIT;
~~~

## ACT_CMMN_HI_MIL_INST

| 字段 | 类型 | 是否为主键 | 是否允许为空 | 默认值 | 说明 | 备注 |  
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |  
| ID_ | varchar(255) | Y | N | | 主键 | |  
| REV_ | int(11) | N | N | | | |  
| NAME_ | varchar(255) | N | N | | 名称 | |  
| TIME_STAMP_ | datetime | N | N | | 时间戳 | |  
| CASE_INST_ID_ | varchar(255) | N | N | | | |  
| CASE_DEF_ID_| varchar(255) | N | N | | | |  
| ELEMENT_ID_ | varchar(255) | N | N | | | |  

> SQL  

~~~
--
-- 表的结构 `ACT_CMMN_HI_MIL_INST`
--

CREATE TABLE `ACT_CMMN_HI_MIL_INST` (
  `ID_` varchar(255) NOT NULL,
  `REV_` int(11) NOT NULL,
  `NAME_` varchar(255) NOT NULL,
  `TIME_STAMP_` datetime NOT NULL,
  `CASE_INST_ID_` varchar(255) NOT NULL,
  `CASE_DEF_ID_` varchar(255) NOT NULL,
  `ELEMENT_ID_` varchar(255) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

--
-- 转储表的索引
--

--
-- 表的索引 `ACT_CMMN_HI_MIL_INST`
--
ALTER TABLE `ACT_CMMN_HI_MIL_INST`
  ADD PRIMARY KEY (`ID_`);
COMMIT;
~~~

## ACT_CMMN_RU_CASE_INST

| 字段 | 类型 | 是否为主键 | 是否允许为空 | 默认值 | 说明 | 备注 |  
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |  
| ID_ | varchar(255) | Y | N | | 主键 | |  
| REV_ | int(11) | N | N | | | |  
| BUSINESS_KEY_ | varchar(255) | N | Y | NULL | | |  
| NAME_ | varchar(255) | N | Y | NULL | 名称 | |  
| PARENT_ID_ | varchar(255) | N | Y | NULL | | |  
| CASE_DEF_ID_ | varchar(255) | N | Y | NULL | | |  
| STATE_ | varchar(255) | N | Y | NULL | 状态 | |  
| START_TIME_ | datetime | N | Y | NULL | 开始时间 | |  
| START_USER_ID_ | varchar(255) | N | Y | NULL | 开始用户ID | |  
| CALLBACK_ID_  | varchar(255) | N | Y | NULL | 回调ID | |  
| CALLBACK_TYPE_ | varchar(255) | N | Y | NULL | 回调类别 | |  
| TENANT_ID_ | varchar(255) | N | Y | 空字符串 | | |  
| LOCK_TIME_ | datetime | N | Y | NULL | | |  
| IS_COMPLETEABLE_ | bit(1) | N | Y | NULL | | |  

> SQL  

~~~
--
-- 表的结构 `ACT_CMMN_RU_CASE_INST`
--

CREATE TABLE `ACT_CMMN_RU_CASE_INST` (
  `ID_` varchar(255) NOT NULL,
  `REV_` int(11) NOT NULL,
  `BUSINESS_KEY_` varchar(255) DEFAULT NULL,
  `NAME_` varchar(255) DEFAULT NULL,
  `PARENT_ID_` varchar(255) DEFAULT NULL,
  `CASE_DEF_ID_` varchar(255) DEFAULT NULL,
  `STATE_` varchar(255) DEFAULT NULL,
  `START_TIME_` datetime DEFAULT NULL,
  `START_USER_ID_` varchar(255) DEFAULT NULL,
  `CALLBACK_ID_` varchar(255) DEFAULT NULL,
  `CALLBACK_TYPE_` varchar(255) DEFAULT NULL,
  `TENANT_ID_` varchar(255) DEFAULT '',
  `LOCK_TIME_` datetime DEFAULT NULL,
  `IS_COMPLETEABLE_` bit(1) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

--
-- 转储表的索引
--

--
-- 表的索引 `ACT_CMMN_RU_CASE_INST`
--
ALTER TABLE `ACT_CMMN_RU_CASE_INST`
  ADD PRIMARY KEY (`ID_`),
  ADD KEY `ACT_IDX_CASE_INST_CASE_DEF` (`CASE_DEF_ID_`),
  ADD KEY `ACT_IDX_CASE_INST_PARENT` (`PARENT_ID_`);

--
-- 限制导出的表
--

--
-- 限制表 `ACT_CMMN_RU_CASE_INST`
--
ALTER TABLE `ACT_CMMN_RU_CASE_INST`
  ADD CONSTRAINT `ACT_FK_CASE_INST_CASE_DEF` FOREIGN KEY (`CASE_DEF_ID_`) REFERENCES `ACT_CMMN_CASEDEF` (`ID_`);
COMMIT;
~~~

## ACT_CMMN_RU_MIL_INST

| 字段 | 类型 | 是否为主键 | 是否允许为空 | 默认值 | 说明 | 备注 |  
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |  
| ID_ | varchar(255) | Y | N | | 主键 | |  
| NAME_ | varchar(255) | N | N | | 名称 | |  
| TIME_STAMP_ | datetime | N | N | | 时间戳 | |  
| CASE_INST_ID_ | varchar(255) | N | N | | | |  
| CASE_DEF_ID | varchar(255) | N | N | | | |  
| ELEMENT_ID_ | varchar(255) | N | N | | | |  

> SQL  

~~~
--
-- 表的结构 `ACT_CMMN_RU_MIL_INST`
--

CREATE TABLE `ACT_CMMN_RU_MIL_INST` (
  `ID_` varchar(255) NOT NULL,
  `NAME_` varchar(255) NOT NULL,
  `TIME_STAMP_` datetime NOT NULL,
  `CASE_INST_ID_` varchar(255) NOT NULL,
  `CASE_DEF_ID_` varchar(255) NOT NULL,
  `ELEMENT_ID_` varchar(255) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

--
-- 转储表的索引
--

--
-- 表的索引 `ACT_CMMN_RU_MIL_INST`
--
ALTER TABLE `ACT_CMMN_RU_MIL_INST`
  ADD PRIMARY KEY (`ID_`),
  ADD KEY `ACT_IDX_MIL_CASE_DEF` (`CASE_DEF_ID_`),
  ADD KEY `ACT_IDX_MIL_CASE_INST` (`CASE_INST_ID_`);

--
-- 限制导出的表
--

--
-- 限制表 `ACT_CMMN_RU_MIL_INST`
--
ALTER TABLE `ACT_CMMN_RU_MIL_INST`
  ADD CONSTRAINT `ACT_FK_MIL_CASE_DEF` FOREIGN KEY (`CASE_DEF_ID_`) REFERENCES `ACT_CMMN_CASEDEF` (`ID_`),
  ADD CONSTRAINT `ACT_FK_MIL_CASE_INST` FOREIGN KEY (`CASE_INST_ID_`) REFERENCES `ACT_CMMN_RU_CASE_INST` (`ID_`);
COMMIT;
~~~

## ACT_CMMN_RU_PLAN_ITEM_INST

| 字段 | 类型 | 是否为主键 | 是否允许为空 | 默认值 | 说明 | 备注 |  
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |  
| ID_ | varchar(255) | Y | N | | 主键 | |  
| REV_ | int(11) | N | N | | | |  
| CASE_DEF_ID_ | varchar(255) | N | Y | NULL | 关联ACT_CMMN_CASEDEF表ID | |  
| CASE_INST_ID_ | varchar(255) | N | Y | NULL | 关联ACT_CMMN_RU_CASE_INST表ID | |  
| STAGE_INST_ID_ | varchar(255) | N | Y | NULL | | |  
| IS_STAGE_ | bit(1) | N | Y | NULL | | |  
| ELEMENT_ID_ | varchar(255) | N | Y | NULL | | |  
| NAME_ | varchar(255) | N | Y | NULL | 名称 | |  
| STATE_ | varchar(255) | N | Y | NULL | 状态 | |  
| START_TIME_ | datetime | N | Y | NULL | 开始时间 | |  
| START_USER_ID_ | varchar(255) | N | Y | NULL | 开始用户ID | |  
| REFERENCE_ID_ | varchar(255) | N | Y | NULL | | |  
| REFERENCE_TYPE_ | varchar(255) | N | Y | NULL | | |  
| TENANT_ID_ | varchar(255) | N | Y | 空字符串 | | |  
| ITEM_DEFINITION_ID_ | varchar(255) | N | Y | NULL | | |  
| ITEM_DEFINITION_TYPE_ | varchar(255) | N | Y | NULL | | |  
| IS_COMPLETEABLE_ | bit(1) | N | Y | NULL | | |  
| IS_COUNT_ENABLED_ | bit(1) | N | Y | NULL | | |  

> SQL  

~~~
--
-- 表的结构 `ACT_CMMN_RU_PLAN_ITEM_INST`
--

CREATE TABLE `ACT_CMMN_RU_PLAN_ITEM_INST` (
  `ID_` varchar(255) NOT NULL,
  `REV_` int(11) NOT NULL,
  `CASE_DEF_ID_` varchar(255) DEFAULT NULL,
  `CASE_INST_ID_` varchar(255) DEFAULT NULL,
  `STAGE_INST_ID_` varchar(255) DEFAULT NULL,
  `IS_STAGE_` bit(1) DEFAULT NULL,
  `ELEMENT_ID_` varchar(255) DEFAULT NULL,
  `NAME_` varchar(255) DEFAULT NULL,
  `STATE_` varchar(255) DEFAULT NULL,
  `START_TIME_` datetime DEFAULT NULL,
  `START_USER_ID_` varchar(255) DEFAULT NULL,
  `REFERENCE_ID_` varchar(255) DEFAULT NULL,
  `REFERENCE_TYPE_` varchar(255) DEFAULT NULL,
  `TENANT_ID_` varchar(255) DEFAULT '',
  `ITEM_DEFINITION_ID_` varchar(255) DEFAULT NULL,
  `ITEM_DEFINITION_TYPE_` varchar(255) DEFAULT NULL,
  `IS_COMPLETEABLE_` bit(1) DEFAULT NULL,
  `IS_COUNT_ENABLED_` bit(1) DEFAULT NULL,
  `VAR_COUNT_` int(11) DEFAULT NULL,
  `SENTRY_PART_INST_COUNT_` int(11) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

--
-- 转储表的索引
--

--
-- 表的索引 `ACT_CMMN_RU_PLAN_ITEM_INST`
--
ALTER TABLE `ACT_CMMN_RU_PLAN_ITEM_INST`
  ADD PRIMARY KEY (`ID_`),
  ADD KEY `ACT_IDX_PLAN_ITEM_CASE_DEF` (`CASE_DEF_ID_`),
  ADD KEY `ACT_IDX_PLAN_ITEM_CASE_INST` (`CASE_INST_ID_`),
  ADD KEY `ACT_IDX_PLAN_ITEM_STAGE_INST` (`STAGE_INST_ID_`);

--
-- 限制导出的表
--

--
-- 限制表 `ACT_CMMN_RU_PLAN_ITEM_INST`
--
ALTER TABLE `ACT_CMMN_RU_PLAN_ITEM_INST`
  ADD CONSTRAINT `ACT_FK_PLAN_ITEM_CASE_DEF` FOREIGN KEY (`CASE_DEF_ID_`) REFERENCES `ACT_CMMN_CASEDEF` (`ID_`),
  ADD CONSTRAINT `ACT_FK_PLAN_ITEM_CASE_INST` FOREIGN KEY (`CASE_INST_ID_`) REFERENCES `ACT_CMMN_RU_CASE_INST` (`ID_`);
COMMIT;
~~~

## ACT_CMMN_RU_SENTRY_PART_INST

| 字段 | 类型 | 是否为主键 | 是否允许为空 | 默认值 | 说明 | 备注 |  
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |  
| ID_ | varchar(255) | Y | N | | 主键 | |  
| REV_ | int(11) | N | N | | | |  
| CASE_DEF_ID_ | varchar(255) | N | Y | NULL | 关联ACT_CMMN_CASEDEF表ID | |  
| CASE_INST_ID_ | varchar(255) | N | Y | NULL | 关联ACT_CMMN_RU_CASE_INST表ID | |  
| PLAN_ITEM_INST_ID_ | varchar(255) | N | Y | NULL | 关联ACT_CMMN_RU_PLAN_ITEM_INST表ID | |  
| ON_PART_ID_ | varchar(255) | N | Y | NULL | | |  
| IF_PART_ID_ | varchar(255) | N | Y | NULL | | |  
| TIME_STAMP_ | datetime | N | Y | NULL | 时间戳 | |  

> SQL  

~~~
--
-- 表的结构 `ACT_CMMN_RU_SENTRY_PART_INST`
--

CREATE TABLE `ACT_CMMN_RU_SENTRY_PART_INST` (
  `ID_` varchar(255) NOT NULL,
  `REV_` int(11) NOT NULL,
  `CASE_DEF_ID_` varchar(255) DEFAULT NULL,
  `CASE_INST_ID_` varchar(255) DEFAULT NULL,
  `PLAN_ITEM_INST_ID_` varchar(255) DEFAULT NULL,
  `ON_PART_ID_` varchar(255) DEFAULT NULL,
  `IF_PART_ID_` varchar(255) DEFAULT NULL,
  `TIME_STAMP_` datetime DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

--
-- 转储表的索引
--

--
-- 表的索引 `ACT_CMMN_RU_SENTRY_PART_INST`
--
ALTER TABLE `ACT_CMMN_RU_SENTRY_PART_INST`
  ADD PRIMARY KEY (`ID_`),
  ADD KEY `ACT_IDX_SENTRY_CASE_DEF` (`CASE_DEF_ID_`),
  ADD KEY `ACT_IDX_SENTRY_CASE_INST` (`CASE_INST_ID_`),
  ADD KEY `ACT_IDX_SENTRY_PLAN_ITEM` (`PLAN_ITEM_INST_ID_`);

--
-- 限制导出的表
--

--
-- 限制表 `ACT_CMMN_RU_SENTRY_PART_INST`
--
ALTER TABLE `ACT_CMMN_RU_SENTRY_PART_INST`
  ADD CONSTRAINT `ACT_FK_SENTRY_CASE_DEF` FOREIGN KEY (`CASE_DEF_ID_`) REFERENCES `ACT_CMMN_CASEDEF` (`ID_`),
  ADD CONSTRAINT `ACT_FK_SENTRY_CASE_INST` FOREIGN KEY (`CASE_INST_ID_`) REFERENCES `ACT_CMMN_RU_CASE_INST` (`ID_`),
  ADD CONSTRAINT `ACT_FK_SENTRY_PLAN_ITEM` FOREIGN KEY (`PLAN_ITEM_INST_ID_`) REFERENCES `ACT_CMMN_RU_PLAN_ITEM_INST` (`ID_`);
COMMIT;
~~~

## ACT_CO_CONTENT_ITEM

| 字段 | 类型 | 是否为主键 | 是否允许为空 | 默认值 | 说明 | 备注 |  
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |  
| ID_ | varchar(255) | Y | N | | 主键 | |  
| NAME_ | varchar(255) | N | N | | 名称 | |  
| MIME_TYPE_ | varchar(255) | N | N | | | |  
| TASK_ID_ | varchar(255) | N | N | | | |  
| PROC_INST_ID_ | varchar(255) | N | N | | | |  
| CONTENT_STORE_ID_ | varchar(255) | N | N | | | |  
| CONTENT_STORE_NAME_ | varchar(255) | N | N | | | |  
| FIELD_ | varchar(400) | N | N | | | |  
| CONTENT_AVAILABLE_ | bit(1) | N | Y | b'0' | | |  
| CREATED_ | timestamp(6) | N | Y | NULL | 创建时间 | |  
| CREATED_BY_ | varchar(255) | N | Y | NULL | 创建者 | |  
| LAST_MODIFIED_ | timestamp(6) | N | Y | NULL | 最新修改时间 | |  
| LAST_MODIFIED_BY_ | varchar(255) | N | Y | NULL | 最新修改者 | |  
| CONTENT_SIZE_ | bigint(20) | N | Y | 0 | 内容大小 | |  
| TENANT_ID_ | varchar(255) | N | Y | NULL | | |  
| SCOPE_ID_ | varchar(255) | N | Y | NULL | | |  
| SCOPE_TYPE_ | varchar(255) | N | Y | NULL | | |  

> SQL  

~~~
--
-- 表的结构 `ACT_CO_CONTENT_ITEM`
--

CREATE TABLE `ACT_CO_CONTENT_ITEM` (
  `ID_` varchar(255) NOT NULL,
  `NAME_` varchar(255) NOT NULL,
  `MIME_TYPE_` varchar(255) DEFAULT NULL,
  `TASK_ID_` varchar(255) DEFAULT NULL,
  `PROC_INST_ID_` varchar(255) DEFAULT NULL,
  `CONTENT_STORE_ID_` varchar(255) DEFAULT NULL,
  `CONTENT_STORE_NAME_` varchar(255) DEFAULT NULL,
  `FIELD_` varchar(400) DEFAULT NULL,
  `CONTENT_AVAILABLE_` bit(1) DEFAULT b'0',
  `CREATED_` timestamp(6) NULL DEFAULT NULL,
  `CREATED_BY_` varchar(255) DEFAULT NULL,
  `LAST_MODIFIED_` timestamp(6) NULL DEFAULT NULL,
  `LAST_MODIFIED_BY_` varchar(255) DEFAULT NULL,
  `CONTENT_SIZE_` bigint(20) DEFAULT '0',
  `TENANT_ID_` varchar(255) DEFAULT NULL,
  `SCOPE_ID_` varchar(255) DEFAULT NULL,
  `SCOPE_TYPE_` varchar(255) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

--
-- 转储表的索引
--

--
-- 表的索引 `ACT_CO_CONTENT_ITEM`
--
ALTER TABLE `ACT_CO_CONTENT_ITEM`
  ADD PRIMARY KEY (`ID_`),
  ADD KEY `idx_contitem_taskid` (`TASK_ID_`),
  ADD KEY `idx_contitem_procid` (`PROC_INST_ID_`),
  ADD KEY `idx_contitem_scope` (`SCOPE_ID_`,`SCOPE_TYPE_`);
COMMIT;
~~~

## ACT_CO_DATABASECHANGELOG

| 字段 | 类型 | 是否为主键 | 是否允许为空 | 默认值 | 说明 | 备注 |  
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |  
| ID | varchar(255) | N | N | | | |  
| AUTHOR | varchar(255) | N | N | | 操作人 | |  
| FILENAME | varchar(255) | N | N | | 文件名 | |  
| DATEEXECUTED | datetime | N | N | | 执行时间 | |  
| ORDEREXECUTED | int(11) | N | N | | 执行顺序 | |  
| EXECTYPE | varchar(10) | N | N | | | |  
| MD5SUM | varchar(35) | N | N | | | |  
| DESCRIPTION | varchar(255) | N | Y | NULL | 描述 | |  
| COMMENTS | varchar(255) | N | Y | NULL | | |  
| TAG | varchar(255) | N | Y | NULL | 标签 | |  
| LIQUIBASE | varchar(20) | N | Y | NULL | | |  
| CONTEXTS | varchar(255) | N | Y | NULL | | |  
| LABELS | varchar(255) | N | Y | NULL | 标签 | |  
| DEPLOYMENT_ID | varchar(10) | N | Y | NULL | | |  

> SQL  

~~~
--
-- 表的结构 `ACT_CO_DATABASECHANGELOG`
--

CREATE TABLE `ACT_CO_DATABASECHANGELOG` (
  `ID` varchar(255) NOT NULL,
  `AUTHOR` varchar(255) NOT NULL,
  `FILENAME` varchar(255) NOT NULL,
  `DATEEXECUTED` datetime NOT NULL,
  `ORDEREXECUTED` int(11) NOT NULL,
  `EXECTYPE` varchar(10) NOT NULL,
  `MD5SUM` varchar(35) DEFAULT NULL,
  `DESCRIPTION` varchar(255) DEFAULT NULL,
  `COMMENTS` varchar(255) DEFAULT NULL,
  `TAG` varchar(255) DEFAULT NULL,
  `LIQUIBASE` varchar(20) DEFAULT NULL,
  `CONTEXTS` varchar(255) DEFAULT NULL,
  `LABELS` varchar(255) DEFAULT NULL,
  `DEPLOYMENT_ID` varchar(10) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
~~~

## ACT_CO_DATABASECHANGELOG

| 字段 | 类型 | 是否为主键 | 是否允许为空 | 默认值 | 说明 | 备注 |  
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |  
| ID | int(11) | Y | N | | 主键 | |  
| LOCKED | bit(1) | N | N | | | |  
| LOCKGRANTED | datetime | N | Y | NULL | 锁定时间 | |  
| LOCKEDBY | varchar(255) | N | Y | NULL | 锁定者 | |  

> SQL  

~~~
--
-- 表的结构 `ACT_CO_DATABASECHANGELOGLOCK`
--

CREATE TABLE `ACT_CO_DATABASECHANGELOGLOCK` (
  `ID` int(11) NOT NULL,
  `LOCKED` bit(1) NOT NULL,
  `LOCKGRANTED` datetime DEFAULT NULL,
  `LOCKEDBY` varchar(255) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

--
-- 转储表的索引
--

--
-- 表的索引 `ACT_CO_DATABASECHANGELOGLOCK`
--
ALTER TABLE `ACT_CO_DATABASECHANGELOGLOCK`
  ADD PRIMARY KEY (`ID`);
COMMIT;
~~~

## ACT_DMN_DATABASECHANGELOG

| 字段 | 类型 | 是否为主键 | 是否允许为空 | 默认值 | 说明 | 备注 |  
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |  
| ID | varchar(255) | N | N | | | |  
| AUTHOR | varchar(255) | N | N | | 操作人 | |  
| FILENAME | varchar(255) | N | N | | 文件名 | |  
| DATEEXECUTED | datetime | N | N | | 执行时间 | |  
| ORDEREXECUTED | int(11) | N | N | | 执行顺序 | |  
| EXECTYPE | varchar(10) | N | N | | | |  
| MD5SUM | varchar(35) | N | N | | | |  
| DESCRIPTION | varchar(255) | N | Y | NULL | 描述 | |  
| COMMENTS | varchar(255) | N | Y | NULL | | |  
| TAG | varchar(255) | N | Y | NULL | 标签 | |  
| LIQUIBASE | varchar(20) | N | Y | NULL | | |  
| CONTEXTS | varchar(255) | N | Y | NULL | | |  
| LABELS | varchar(255) | N | Y | NULL | 标签 | |  
| DEPLOYMENT_ID | varchar(10) | N | Y | NULL | | |  


> SQL  

~~~
--
-- 表的结构 `ACT_DMN_DATABASECHANGELOG`
--

CREATE TABLE `ACT_DMN_DATABASECHANGELOG` (
  `ID` varchar(255) NOT NULL,
  `AUTHOR` varchar(255) NOT NULL,
  `FILENAME` varchar(255) NOT NULL,
  `DATEEXECUTED` datetime NOT NULL,
  `ORDEREXECUTED` int(11) NOT NULL,
  `EXECTYPE` varchar(10) NOT NULL,
  `MD5SUM` varchar(35) DEFAULT NULL,
  `DESCRIPTION` varchar(255) DEFAULT NULL,
  `COMMENTS` varchar(255) DEFAULT NULL,
  `TAG` varchar(255) DEFAULT NULL,
  `LIQUIBASE` varchar(20) DEFAULT NULL,
  `CONTEXTS` varchar(255) DEFAULT NULL,
  `LABELS` varchar(255) DEFAULT NULL,
  `DEPLOYMENT_ID` varchar(10) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
~~~

## ACT_DMN_DATABASECHANGELOGLOCK

| 字段 | 类型 | 是否为主键 | 是否允许为空 | 默认值 | 说明 | 备注 |  
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |  
| ID | int(11) | Y | N | | 主键 | |  
| LOCKED | bit(1) | N | N | | | |  
| LOCKGRANTED | datetime | N | Y | NULL | 锁定时间 | |  
| LOCKEDBY | varchar(255) | N | Y | NULL | 锁定者 | |  

> SQL  

~~~
--
-- 表的结构 `ACT_DMN_DATABASECHANGELOGLOCK`
--

CREATE TABLE `ACT_DMN_DATABASECHANGELOGLOCK` (
  `ID` int(11) NOT NULL,
  `LOCKED` bit(1) NOT NULL,
  `LOCKGRANTED` datetime DEFAULT NULL,
  `LOCKEDBY` varchar(255) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

--
-- 转储表的索引
--

--
-- 表的索引 `ACT_DMN_DATABASECHANGELOGLOCK`
--
ALTER TABLE `ACT_DMN_DATABASECHANGELOGLOCK`
  ADD PRIMARY KEY (`ID`);
COMMIT;
~~~

## ACT_DMN_DECISION_TABLE

| 字段 | 类型 | 是否为主键 | 是否允许为空 | 默认值 | 说明 | 备注 |  
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |  
| ID_ | varchar(255) | Y | N | | 主键 | |  
| NAME_ | varchar(255) | N | Y | NULL | 名称 | |  
| VERSION_ | int(11) | N | Y | NULL | | |  
| KEY_ | varchar(255) | N | Y | NULL | | |  
| CATEGORY_ | varchar(255) | N | Y | NULL | 类别 | |  
| DEPLOYMENT_ID_ | varchar(255) | N | Y | NULL | | |  
| PARENT_DEPLOYMENT_ID_ | varchar(255) | N | Y | NULL | | |  
| TENANT_ID_ | varchar(255) | N | Y | NULL | | |  
| RESOURCE_NAME_ | varchar(255) | N | Y | NULL | | |  
| DESCRIPTION_ | varchar(255) | N | Y | NULL | 描述 | |  

> SQL  

~~~
--
-- 表的结构 `ACT_DMN_DECISION_TABLE`
--

CREATE TABLE `ACT_DMN_DECISION_TABLE` (
  `ID_` varchar(255) NOT NULL,
  `NAME_` varchar(255) DEFAULT NULL,
  `VERSION_` int(11) DEFAULT NULL,
  `KEY_` varchar(255) DEFAULT NULL,
  `CATEGORY_` varchar(255) DEFAULT NULL,
  `DEPLOYMENT_ID_` varchar(255) DEFAULT NULL,
  `PARENT_DEPLOYMENT_ID_` varchar(255) DEFAULT NULL,
  `TENANT_ID_` varchar(255) DEFAULT NULL,
  `RESOURCE_NAME_` varchar(255) DEFAULT NULL,
  `DESCRIPTION_` varchar(255) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

--
-- 转储表的索引
--

--
-- 表的索引 `ACT_DMN_DECISION_TABLE`
--
ALTER TABLE `ACT_DMN_DECISION_TABLE`
  ADD PRIMARY KEY (`ID_`);
COMMIT;
~~~

## ACT_DMN_DEPLOYMENT

| 字段 | 类型 | 是否为主键 | 是否允许为空 | 默认值 | 说明 | 备注 |  
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |  
| ID_ | varchar(255) | Y | N | | 主键 | |  
| NAME_ | varchar(255) | N | Y | NULL | 名称 | |  
| CATEGORY_ | varchar(255) | N | Y | NULL | 类别 | |  
| DEPLOY_TIME_ | datetime | N | Y | NULL | | |  
| TENANT_ID_ | varchar(255) | N | Y | NULL | | |  
| PARENT_DEPLOYMENT_ID_ | varchar(255) | N | Y | NULL | | |  

> SQL  

~~~
--
-- 表的结构 `ACT_DMN_DEPLOYMENT`
--

CREATE TABLE `ACT_DMN_DEPLOYMENT` (
  `ID_` varchar(255) NOT NULL,
  `NAME_` varchar(255) DEFAULT NULL,
  `CATEGORY_` varchar(255) DEFAULT NULL,
  `DEPLOY_TIME_` datetime DEFAULT NULL,
  `TENANT_ID_` varchar(255) DEFAULT NULL,
  `PARENT_DEPLOYMENT_ID_` varchar(255) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

--
-- 转储表的索引
--

--
-- 表的索引 `ACT_DMN_DEPLOYMENT`
--
ALTER TABLE `ACT_DMN_DEPLOYMENT`
  ADD PRIMARY KEY (`ID_`);
COMMIT;
~~~

## ACT_DMN_DEPLOYMENT_RESOURCE

| 字段 | 类型 | 是否为主键 | 是否允许为空 | 默认值 | 说明 | 备注 |  
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |  
| ID_ | varchar(255) | Y | N | | 主键 | |  
| NAME_ | varchar(255) | N | Y | NULL | 名称 | |  
| DEPLOYMENT_ID_ | varchar(255) | N | Y | NULL | | |  
| RESOURCE_BYTES_ | varchar(255) | N | Y | NULL | | |  

> SQL  

~~~
--
-- 表的结构 `ACT_DMN_DEPLOYMENT_RESOURCE`
--

CREATE TABLE `ACT_DMN_DEPLOYMENT_RESOURCE` (
  `ID_` varchar(255) NOT NULL,
  `NAME_` varchar(255) DEFAULT NULL,
  `DEPLOYMENT_ID_` varchar(255) DEFAULT NULL,
  `RESOURCE_BYTES_` longblob
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

--
-- 转储表的索引
--

--
-- 表的索引 `ACT_DMN_DEPLOYMENT_RESOURCE`
--
ALTER TABLE `ACT_DMN_DEPLOYMENT_RESOURCE`
  ADD PRIMARY KEY (`ID_`);
COMMIT;
~~~

## ACT_DMN_DEPLOYMENT_RESOURCE

| 字段 | 类型 | 是否为主键 | 是否允许为空 | 默认值 | 说明 | 备注 |  
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |  
| ID_ | varchar(255) | Y | N | | 主键 | |  
| DECISION_DEFINITION_ID_ | varchar(255) | N | Y | NULL | | |  
| DEPLOYMENT_ID_ | varchar(255) | N | Y | NULL | | |  
| START_TIME_ | datetime | N | Y | NULL | 开始时间 | |  
| END_TIME_ | datetime | N | Y | NULL | 结束时间 | |  
| INSTANCE_ID_ | varchar(255) | N | Y | NULL | | |  
| EXECUTION_ID_ | varchar(255) | N | Y | NULL | | |  
| ACTIVITY_ID_ | varchar(255) | N | Y | NULL | | |  
| FAILED_ | bit(1) | N | Y | b'0' | | |  
| TENANT_ID_ | varchar(255) | N | Y | NULL | | |  
| EXECUTION_JSON_ | longtext | N | Y | NULL | | |  
| SCOPE_TYPE_ | varchar(255) | N | Y | NULL | | |  

> SQL  

~~~
--
-- 表的结构 `ACT_DMN_HI_DECISION_EXECUTION`
--

CREATE TABLE `ACT_DMN_HI_DECISION_EXECUTION` (
  `ID_` varchar(255) NOT NULL,
  `DECISION_DEFINITION_ID_` varchar(255) DEFAULT NULL,
  `DEPLOYMENT_ID_` varchar(255) DEFAULT NULL,
  `START_TIME_` datetime DEFAULT NULL,
  `END_TIME_` datetime DEFAULT NULL,
  `INSTANCE_ID_` varchar(255) DEFAULT NULL,
  `EXECUTION_ID_` varchar(255) DEFAULT NULL,
  `ACTIVITY_ID_` varchar(255) DEFAULT NULL,
  `FAILED_` bit(1) DEFAULT b'0',
  `TENANT_ID_` varchar(255) DEFAULT NULL,
  `EXECUTION_JSON_` longtext,
  `SCOPE_TYPE_` varchar(255) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

--
-- 转储表的索引
--

--
-- 表的索引 `ACT_DMN_HI_DECISION_EXECUTION`
--
ALTER TABLE `ACT_DMN_HI_DECISION_EXECUTION`
  ADD PRIMARY KEY (`ID_`);
COMMIT;
~~~

## ACT_EVT_LOG 事件日志表

| 字段 | 类型 | 是否为主键 | 是否允许为空 | 默认值 | 说明 | 备注 |  
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |  
| LOG_NR_ | bigint(20) | Y | N | | 主键 | |  
| TYPE_ | varchar(64) | N | Y | NULL | | |  
| PROC_DEF_ID_ | varchar(64) | N | Y | NULL | | |  
| PROC_INST_ID_ | varchar(64) | N | Y | NULL | | |  
| EXECUTION_ID_ | varchar(64) | N | Y | NULL | | |  
| TASK_ID_ | varchar(64) | N | Y | NULL | | |  
| TIME_STAMP_ | timestamp(3) | N | N | | 时间戳 | |  
| USER_ID_ | varchar(255) | N | Y | NULL | | |  
| DATA_ | longblob | N | Y | NULL | | |  
| LOCK_OWNER_ | varchar(255) | N | Y | NULL | | |  
| LOCK_TIME_ | timestamp(3) | N | Y | NULL | | |  
| IS_PROCESSED_ | tinyint(4) | N | Y | 0 | | |  

> SQL  

~~~
--
-- 表的结构 `ACT_EVT_LOG`
--

CREATE TABLE `ACT_EVT_LOG` (
  `LOG_NR_` bigint(20) NOT NULL,
  `TYPE_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `PROC_DEF_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `PROC_INST_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `EXECUTION_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `TASK_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `TIME_STAMP_` timestamp(3) NOT NULL,
  `USER_ID_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `DATA_` longblob,
  `LOCK_OWNER_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `LOCK_TIME_` timestamp(3) NULL DEFAULT NULL,
  `IS_PROCESSED_` tinyint(4) DEFAULT '0'
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_bin;

--
-- 转储表的索引
--

--
-- 表的索引 `ACT_EVT_LOG`
--
ALTER TABLE `ACT_EVT_LOG`
  ADD PRIMARY KEY (`LOG_NR_`);

--
-- 在导出的表使用AUTO_INCREMENT
--

--
-- 使用表AUTO_INCREMENT `ACT_EVT_LOG`
--
ALTER TABLE `ACT_EVT_LOG`
  MODIFY `LOG_NR_` bigint(20) NOT NULL AUTO_INCREMENT;
COMMIT;
~~~

## ACT_FO_DATABASECHANGELOG

| 字段 | 类型 | 是否为主键 | 是否允许为空 | 默认值 | 说明 | 备注 |  
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |  
| ID | varchar(255) | N | N | | | |  
| AUTHOR | varchar(255) | N | N | | 操作人 | |  
| FILENAME | varchar(255) | N | N | | 文件名 | |  
| DATEEXECUTED | datetime | N | N | | 执行时间 | |  
| ORDEREXECUTED | int(11) | N | N | | 执行顺序 | |  
| EXECTYPE | varchar(10) | N | N | | | |  
| MD5SUM | varchar(35) | N | N | | | |  
| DESCRIPTION | varchar(255) | N | Y | NULL | 描述 | |  
| COMMENTS | varchar(255) | N | Y | NULL | | |  
| TAG | varchar(255) | N | Y | NULL | 标签 | |  
| LIQUIBASE | varchar(20) | N | Y | NULL | | |  
| CONTEXTS | varchar(255) | N | Y | NULL | | |  
| LABELS | varchar(255) | N | Y | NULL | 标签 | |  
| DEPLOYMENT_ID | varchar(10) | N | Y | NULL | | |  


> SQL  

~~~
--
-- 表的结构 `ACT_FO_DATABASECHANGELOG`
--

CREATE TABLE `ACT_FO_DATABASECHANGELOG` (
  `ID` varchar(255) NOT NULL,
  `AUTHOR` varchar(255) NOT NULL,
  `FILENAME` varchar(255) NOT NULL,
  `DATEEXECUTED` datetime NOT NULL,
  `ORDEREXECUTED` int(11) NOT NULL,
  `EXECTYPE` varchar(10) NOT NULL,
  `MD5SUM` varchar(35) DEFAULT NULL,
  `DESCRIPTION` varchar(255) DEFAULT NULL,
  `COMMENTS` varchar(255) DEFAULT NULL,
  `TAG` varchar(255) DEFAULT NULL,
  `LIQUIBASE` varchar(20) DEFAULT NULL,
  `CONTEXTS` varchar(255) DEFAULT NULL,
  `LABELS` varchar(255) DEFAULT NULL,
  `DEPLOYMENT_ID` varchar(10) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
~~~

## ACT_FO_DATABASECHANGELOGLOCK

| 字段 | 类型 | 是否为主键 | 是否允许为空 | 默认值 | 说明 | 备注 |  
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |  
| ID | int(11) | Y | N | | 主键 | |  
| LOCKED | bit(1) | N | N | | | |  
| LOCKGRANTED | datetime | N | Y | NULL | 锁定时间 | |  
| LOCKEDBY | varchar(255) | N | Y | NULL | 锁定者 | |  

> SQL  

~~~
--
-- 表的结构 `ACT_FO_DATABASECHANGELOGLOCK`
--

CREATE TABLE `ACT_FO_DATABASECHANGELOGLOCK` (
  `ID` int(11) NOT NULL,
  `LOCKED` bit(1) NOT NULL,
  `LOCKGRANTED` datetime DEFAULT NULL,
  `LOCKEDBY` varchar(255) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

--
-- 转储表的索引
--

--
-- 表的索引 `ACT_FO_DATABASECHANGELOGLOCK`
--
ALTER TABLE `ACT_FO_DATABASECHANGELOGLOCK`
  ADD PRIMARY KEY (`ID`);
COMMIT;
~~~

## ACT_FO_FORM_DEFINITION

| 字段 | 类型 | 是否为主键 | 是否允许为空 | 默认值 | 说明 | 备注 |  
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |  
| ID_ | varchar(255) | Y | N | | 主键 | |  
| NAME_ | varchar(255) | N | Y | NULL | 名称 | |  
| VERSION_ | int(11) | N | Y | NULL | | |  
| KEY_ | varchar(255) | N | Y | NULL | | |  
| CATEGORY_ | varchar(255) | N | Y | 类别 | | |  
| DEPLOYMENT_ID_ | varchar(255) | N | Y | | | |  
| PARENT_DEPLOYMENT_ID_ | varchar(255) | N | Y | | | |  
| TENANT_ID_ | varchar(255) | N | Y | | | |  
| RESOURCE_NAME_ | varchar(255) | N | Y | | | |  
| DESCRIPTION_ | varchar(255) | N | Y | | | |  

> SQL  

~~~
--
-- 表的结构 `ACT_FO_FORM_DEFINITION`
--

CREATE TABLE `ACT_FO_FORM_DEFINITION` (
  `ID_` varchar(255) NOT NULL,
  `NAME_` varchar(255) DEFAULT NULL,
  `VERSION_` int(11) DEFAULT NULL,
  `KEY_` varchar(255) DEFAULT NULL,
  `CATEGORY_` varchar(255) DEFAULT NULL,
  `DEPLOYMENT_ID_` varchar(255) DEFAULT NULL,
  `PARENT_DEPLOYMENT_ID_` varchar(255) DEFAULT NULL,
  `TENANT_ID_` varchar(255) DEFAULT NULL,
  `RESOURCE_NAME_` varchar(255) DEFAULT NULL,
  `DESCRIPTION_` varchar(255) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

--
-- 转储表的索引
--

--
-- 表的索引 `ACT_FO_FORM_DEFINITION`
--
ALTER TABLE `ACT_FO_FORM_DEFINITION`
  ADD PRIMARY KEY (`ID_`);
COMMIT;
~~~


## ACT_FO_FORM_DEPLOYMENT

| 字段 | 类型 | 是否为主键 | 是否允许为空 | 默认值 | 说明 | 备注 |  
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |  
| ID_ | varchar(255) | Y | N | | 主键 | |  
| NAME_ | varchar(255) | N | Y | NULL | 名称 | |  
| CATEGORY_ | varchar(255) | N | Y | NULL | 类别 | |  
| DEPLOY_TIME_ | datetime | N | Y | NULL | | |  
| TENANT_ID_ | varchar(255) | N | Y | NULL | | |  
| PARENT_DEPLOYMENT_ID_ | varchar(255) | N | Y | NULL | | |  

~~~
--
-- 表的结构 `ACT_FO_FORM_DEPLOYMENT`
--

CREATE TABLE `ACT_FO_FORM_DEPLOYMENT` (
  `ID_` varchar(255) NOT NULL,
  `NAME_` varchar(255) DEFAULT NULL,
  `CATEGORY_` varchar(255) DEFAULT NULL,
  `DEPLOY_TIME_` datetime DEFAULT NULL,
  `TENANT_ID_` varchar(255) DEFAULT NULL,
  `PARENT_DEPLOYMENT_ID_` varchar(255) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

--
-- 转储表的索引
--

--
-- 表的索引 `ACT_FO_FORM_DEPLOYMENT`
--
ALTER TABLE `ACT_FO_FORM_DEPLOYMENT`
  ADD PRIMARY KEY (`ID_`);
COMMIT;
~~~

## ACT_FO_FORM_INSTANCE

| 字段 | 类型 | 是否为主键 | 是否允许为空 | 默认值 | 说明 | 备注 |  
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |  
| ID_ | varchar(255) | Y | N | | 主键 | |  
| FORM_DEFINITION_ID_ | varchar(255) | N | Y | NULL | | |  
| TASK_ID_ | varchar(255) | N | Y | NULL | | |  
| PROC_INST_ID_ | varchar(255) | N | Y | NULL | | |  
| PROC_DEF_ID_ | varchar(255) | N | Y | NULL | | |  
| SUBMITTED_DATE_ | datetime | N | Y | NULL | | |  
| SUBMITTED_BY_ | varchar(255)| N | Y | NULL | | |  
| FORM_VALUES_ID_ | varchar(255)| N | Y | NULL | | |  
| TENANT_ID_ | varchar(255) | N | Y | NULL | | |  
| SCOPE_ID_ | varchar(255) | N | Y | NULL | | |  
| SCOPE_TYPE_ | varchar(255) | N | Y | NULL | | |  
| SCOPE_DEFINITION_ID_ | varchar(255) | N | Y | NULL | | |  

> SQL  

~~~
--
-- 表的结构 `ACT_FO_FORM_INSTANCE`
--

CREATE TABLE `ACT_FO_FORM_INSTANCE` (
  `ID_` varchar(255) NOT NULL,
  `FORM_DEFINITION_ID_` varchar(255) NOT NULL,
  `TASK_ID_` varchar(255) DEFAULT NULL,
  `PROC_INST_ID_` varchar(255) DEFAULT NULL,
  `PROC_DEF_ID_` varchar(255) DEFAULT NULL,
  `SUBMITTED_DATE_` datetime DEFAULT NULL,
  `SUBMITTED_BY_` varchar(255) DEFAULT NULL,
  `FORM_VALUES_ID_` varchar(255) DEFAULT NULL,
  `TENANT_ID_` varchar(255) DEFAULT NULL,
  `SCOPE_ID_` varchar(255) DEFAULT NULL,
  `SCOPE_TYPE_` varchar(255) DEFAULT NULL,
  `SCOPE_DEFINITION_ID_` varchar(255) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

--
-- 转储表的索引
--

--
-- 表的索引 `ACT_FO_FORM_INSTANCE`
--
ALTER TABLE `ACT_FO_FORM_INSTANCE`
  ADD PRIMARY KEY (`ID_`);
COMMIT;
~~~

## ACT_FO_FORM_RESOURCE

| 字段 | 类型 | 是否为主键 | 是否允许为空 | 默认值 | 说明 | 备注 |  
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |  
| ID_ | varchar(255) | Y | N | | 主键 | |  
| NAME_ | varchar(255) | N | Y | NULL | 名称 | | 
| DEPLOYMENT_ID_ | varchar(255) | N | Y | NULL | | | 
| RESOURCE_BYTES_ | longblob | N | Y | NULL | | | 

~~~
--
-- 表的结构 `ACT_FO_FORM_RESOURCE`
--

CREATE TABLE `ACT_FO_FORM_RESOURCE` (
  `ID_` varchar(255) NOT NULL,
  `NAME_` varchar(255) DEFAULT NULL,
  `DEPLOYMENT_ID_` varchar(255) DEFAULT NULL,
  `RESOURCE_BYTES_` longblob
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

--
-- 转储表的索引
--

--
-- 表的索引 `ACT_FO_FORM_RESOURCE`
--
ALTER TABLE `ACT_FO_FORM_RESOURCE`
  ADD PRIMARY KEY (`ID_`);
COMMIT;
~~~

## ACT_GE_BYTEARRAY 通用的流程定义和流程资源

| 字段 | 类型 | 是否为主键 | 是否允许为空 | 默认值 | 说明 | 备注 |  
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |  
| ID_ | varchar(64) | Y | N | | 主键 | |  
| REV_ | int(11) | N | Y | NULL | 数据版本号 | Activiti有可能会被频繁修改数据库表，加入字段，用来表示该数据被操作的次数 | 
| NAME_ | varchar(255) | N | Y | NULL | 名称 | | 
| DEPLOYMENT_ID_ | varchar(64) | N | Y | NULL | 部署序号 | 部署序号,一次部署可以部署多个资源,该字段与部署表ACT_RE_DEPLOYMENT的主键关联 | 
| BYTES_ | longblob | N | Y | NULL | 资源内容 | | 
| GENERATED_ | tinyint(4) | N | Y | NULL | 是否是由activiti自动产生的资源 | 0:否，1:是 | 

> SQL  

~~~
--
-- 表的结构 `ACT_GE_BYTEARRAY`
--

CREATE TABLE `ACT_GE_BYTEARRAY` (
  `ID_` varchar(64) COLLATE utf8_bin NOT NULL DEFAULT '',
  `REV_` int(11) DEFAULT NULL,
  `NAME_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `DEPLOYMENT_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `BYTES_` longblob,
  `GENERATED_` tinyint(4) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_bin;

--
-- 转储表的索引
--

--
-- 表的索引 `ACT_GE_BYTEARRAY`
--
ALTER TABLE `ACT_GE_BYTEARRAY`
  ADD PRIMARY KEY (`ID_`),
  ADD KEY `ACT_FK_BYTEARR_DEPL` (`DEPLOYMENT_ID_`);

--
-- 限制导出的表
--

--
-- 限制表 `ACT_GE_BYTEARRAY`
--
ALTER TABLE `ACT_GE_BYTEARRAY`
  ADD CONSTRAINT `ACT_FK_BYTEARR_DEPL` FOREIGN KEY (`DEPLOYMENT_ID_`) REFERENCES `ACT_RE_DEPLOYMENT` (`ID_`);
COMMIT;
~~~

## ACT_GE_PROPERTY 系统相关属性

| 字段 | 类型 | 是否为主键 | 是否允许为空 | 默认值 | 说明 | 备注 |  
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |  
| NAME_ | varchar(64) | Y | N | 空字符串 | 属性名称 | 主键 |  
| VALUE_ | varchar(300) | N | Y | NULL | 属性值 | | 
| REV_ | int(11) | N | Y | NULL | 数据版本号 | | 

> SQL  

~~~
--
-- 表的结构 `ACT_GE_PROPERTY`
--

CREATE TABLE `ACT_GE_PROPERTY` (
  `NAME_` varchar(64) COLLATE utf8_bin NOT NULL DEFAULT '',
  `VALUE_` varchar(300) COLLATE utf8_bin DEFAULT NULL,
  `REV_` int(11) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_bin;

--
-- 转储表的索引
--

--
-- 表的索引 `ACT_GE_PROPERTY`
--
ALTER TABLE `ACT_GE_PROPERTY`
  ADD PRIMARY KEY (`NAME_`);
COMMIT;
~~~

## ACT_HI_ACTINST 历史行为表

| 字段 | 类型 | 是否为主键 | 是否允许为空 | 默认值 | 说明 | 备注 |  
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |  
| ID_ | varchar(64) | Y | N | | 主键 | |  
| REV_ | int(11) | N | Y | 1 | | | 
| PROC_DEF_ID_ | varchar(64) | N | N | | 流程定义ID | | 
| PROC_INST_ID_ | varchar(64) | N | N | | 流程实例ID | | 
| EXECUTION_ID_ | varchar(64) | N | N | | 执行ID | | 
| ACT_ID_ | varchar(255) | N | N | | 节点实例ID | | 
| TASK_ID_ | varchar(64) | N | Y | NULL | 任务ID | | 
| CALL_PROC_INST_ID_ | varchar(64) | N | Y | NULL | 调用外部的流程实例ID | | 
| ACT_NAME_ | varchar(255) | N | Y | NULL | 节点名称 | | 
| ACT_TYPE_ | varchar(255) | N | N | | 节点类型 | | 
| ASSIGNEE_ | varchar(255) | N | Y | NULL | 节点签收人 | | 
| START_TIME_ | datetime(3) | N | N | | 开始时间 | | 
| END_TIME_ | datetime(3) | N | Y | NULL | 结束时间 | | 
| DURATION_ | bigint(20) | N | Y | NULL | 耗时 | | 
| DELETE_REASON_ | varchar(4000) | N | Y | NULL | 删除原因 | | 
| TENANT_ID_ | varchar(255) | N | Y | 空字符串 | | | 

> SQL  

~~~
--
-- 表的结构 `ACT_HI_ACTINST`
--

CREATE TABLE `ACT_HI_ACTINST` (
  `ID_` varchar(64) COLLATE utf8_bin NOT NULL,
  `REV_` int(11) DEFAULT '1',
  `PROC_DEF_ID_` varchar(64) COLLATE utf8_bin NOT NULL,
  `PROC_INST_ID_` varchar(64) COLLATE utf8_bin NOT NULL,
  `EXECUTION_ID_` varchar(64) COLLATE utf8_bin NOT NULL,
  `ACT_ID_` varchar(255) COLLATE utf8_bin NOT NULL,
  `TASK_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `CALL_PROC_INST_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `ACT_NAME_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `ACT_TYPE_` varchar(255) COLLATE utf8_bin NOT NULL,
  `ASSIGNEE_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `START_TIME_` datetime(3) NOT NULL,
  `END_TIME_` datetime(3) DEFAULT NULL,
  `DURATION_` bigint(20) DEFAULT NULL,
  `DELETE_REASON_` varchar(4000) COLLATE utf8_bin DEFAULT NULL,
  `TENANT_ID_` varchar(255) COLLATE utf8_bin DEFAULT ''
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_bin;

--
-- 转储表的索引
--

--
-- 表的索引 `ACT_HI_ACTINST`
--
ALTER TABLE `ACT_HI_ACTINST`
  ADD PRIMARY KEY (`ID_`),
  ADD KEY `ACT_IDX_HI_ACT_INST_START` (`START_TIME_`),
  ADD KEY `ACT_IDX_HI_ACT_INST_END` (`END_TIME_`),
  ADD KEY `ACT_IDX_HI_ACT_INST_PROCINST` (`PROC_INST_ID_`,`ACT_ID_`),
  ADD KEY `ACT_IDX_HI_ACT_INST_EXEC` (`EXECUTION_ID_`,`ACT_ID_`);
COMMIT;
~~~

## ACT_HI_ATTACHMENT 附件表

| 字段 | 类型 | 是否为主键 | 是否允许为空 | 默认值 | 说明 | 备注 |  
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |  
| ID_ | varchar(64) | Y | N | | 主键 | |  
| REV_ | int(11) | N | Y | NULL | 数据版本号 | | 
| USER_ID | varchar(255) | N | Y | NULL | 用户ID | | 
| NAME_ | varchar(255) | N | Y | NULL | 名称 | | 
| DESCRIPTION_ | varchar(4000) | N | Y | NULL | 描述 | | 
| TYPE_ | varchar(255) | N | Y | NULL | 类型 | | 
| TASK_ID_ | varchar(64) | N | Y | NULL | 任务ID | | 
| PROC_INST_ID_ | varchar(64) | N | Y | NULL | 流程实例ID | | 
| URL_ | varchar(4000) | N | Y | NULL | | | 
| CONTENT_ID_ | varchar(64) | N | Y | NULL | 字节表的ID | | 
| TIME_ | datetime(3) | N | Y | NULL | 时间 | | 

> SQL  

~~~
--
-- 表的结构 `ACT_HI_ATTACHMENT`
--

CREATE TABLE `ACT_HI_ATTACHMENT` (
  `ID_` varchar(64) COLLATE utf8_bin NOT NULL,
  `REV_` int(11) DEFAULT NULL,
  `USER_ID_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `NAME_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `DESCRIPTION_` varchar(4000) COLLATE utf8_bin DEFAULT NULL,
  `TYPE_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `TASK_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `PROC_INST_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `URL_` varchar(4000) COLLATE utf8_bin DEFAULT NULL,
  `CONTENT_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `TIME_` datetime(3) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_bin;

--
-- 转储表的索引
--

--
-- 表的索引 `ACT_HI_ATTACHMENT`
--
ALTER TABLE `ACT_HI_ATTACHMENT`
  ADD PRIMARY KEY (`ID_`);
COMMIT;
~~~

## ACT_HI_COMMENT 评论表

| 字段 | 类型 | 是否为主键 | 是否允许为空 | 默认值 | 说明 | 备注 |  
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |  
| ID_ | varchar(64) | Y | N | | 主键 | |  
| TYPE_ | varchar(255) | N | Y | NULL | 类型:event（事件）、comment（意见） | | 
| TIME_ | datetime(3) | N | N | | 时间 | | 
| USER_ID_ | varchar(255) | N | Y | NULL | 用户ID | | 
| TASK_ID_ | varchar(64) | N | Y | NULL | 任务ID | | 
| PROC_INST_ID_ | varchar(64) | N | Y | NULL | 流程实例ID | | 
| ACTION_ | varchar(255) | N | Y | NULL | 行为类型 | | 
| MESSAGE_ | varchar(4000) | N | Y | NULL | 信息 | 用于存放流程产生的信息，比如审批意见 | 
| FULL_MSG_ | longblob | N | Y | NULL | 全部内容 | | 

> SQL  

~~~
--
-- 表的结构 `ACT_HI_COMMENT`
--

CREATE TABLE `ACT_HI_COMMENT` (
  `ID_` varchar(64) COLLATE utf8_bin NOT NULL,
  `TYPE_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `TIME_` datetime(3) NOT NULL,
  `USER_ID_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `TASK_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `PROC_INST_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `ACTION_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `MESSAGE_` varchar(4000) COLLATE utf8_bin DEFAULT NULL,
  `FULL_MSG_` longblob
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_bin;

--
-- 转储表的索引
--

--
-- 表的索引 `ACT_HI_COMMENT`
--
ALTER TABLE `ACT_HI_COMMENT`
  ADD PRIMARY KEY (`ID_`);
COMMIT;
~~~

## ACT_HI_DETAIL 历史的流程运行中的细节信息

| 字段 | 类型 | 是否为主键 | 是否允许为空 | 默认值 | 说明 | 备注 |  
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |  
| ID_ | varchar(64) | Y | N | | 主键 | |  
| TYPE_ | varchar(255) | N | N | | 类型 | | 
| PROC_INST_ID_ | varchar(64) | N | Y | NULL | 流程实例ID | | 
| EXECUTION_ID_ | varchar(64) | N | Y | NULL | 执行ID | | 
| TASK_ID_ | varchar(64) | N | Y | NULL | 任务ID | | 
| ACT_INST_ID_ | varchar(64) | N | Y | NULL | 节点实例ID | | 
| NAME_ | varchar(255) | N | N | | 名称 | | 
| VAR_TYPE_ | varchar(255) | N | Y | NULL | 参数类型 | | 
| REV_ | int(11) | N | Y | NULL | 数据版本号 | | 
| TIME_ | datetime(3) | N | N | | 时间戳 | | 
| BYTEARRAY_ID_ | varchar(64) | N | Y | NULL | 字节表ID | | 
| DOUBLE_ | varchar(64) | N | Y | NULL | 存储变量类型为Double | | 
| LONG_ | bigint(20) | N | Y | NULL | 存储变量类型为long | | 
| TEXT_ | varchar(4000) | N | Y | NULL | 存储变量值类型为String | | 
| TEXT2_ | varchar(4000) | N | Y | NULL | 此处存储的是JPA持久化对象时，才会有值。此值为对象ID | | 

> SQL  

~~~
--
-- 表的结构 `ACT_HI_DETAIL`
--

CREATE TABLE `ACT_HI_DETAIL` (
  `ID_` varchar(64) COLLATE utf8_bin NOT NULL,
  `TYPE_` varchar(255) COLLATE utf8_bin NOT NULL,
  `PROC_INST_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `EXECUTION_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `TASK_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `ACT_INST_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `NAME_` varchar(255) COLLATE utf8_bin NOT NULL,
  `VAR_TYPE_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `REV_` int(11) DEFAULT NULL,
  `TIME_` datetime(3) NOT NULL,
  `BYTEARRAY_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `DOUBLE_` double DEFAULT NULL,
  `LONG_` bigint(20) DEFAULT NULL,
  `TEXT_` varchar(4000) COLLATE utf8_bin DEFAULT NULL,
  `TEXT2_` varchar(4000) COLLATE utf8_bin DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_bin;

--
-- 转储表的索引
--

--
-- 表的索引 `ACT_HI_DETAIL`
--
ALTER TABLE `ACT_HI_DETAIL`
  ADD PRIMARY KEY (`ID_`),
  ADD KEY `ACT_IDX_HI_DETAIL_PROC_INST` (`PROC_INST_ID_`),
  ADD KEY `ACT_IDX_HI_DETAIL_ACT_INST` (`ACT_INST_ID_`),
  ADD KEY `ACT_IDX_HI_DETAIL_TIME` (`TIME_`),
  ADD KEY `ACT_IDX_HI_DETAIL_NAME` (`NAME_`),
  ADD KEY `ACT_IDX_HI_DETAIL_TASK_ID` (`TASK_ID_`);
COMMIT;
~~~

## ACT_HI_IDENTITYLINK  历史的流程运行过程中用户关系

| 字段 | 类型 | 是否为主键 | 是否允许为空 | 默认值 | 说明 | 备注 |  
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |  
| ID_ | varchar(64) | Y | N | 空字符串 | 主键 | |  
| GROUP_ID_ | varchar(255) | N | Y | NULL | 组ID | | 
| TYPE_ | varchar(255) | N | Y | NULL | 类型 | | 
| USER_ID_ | varchar(255) | N | Y | NULL | 用户ID | | 
| TASK_ID_ | varchar(64) | N | Y | NULL | 任务ID | | 
| CREATE_TIME_ | datetime(3) | N | Y | NULL | | | 
| PROC_INST_ID_ | varchar(64) | N | Y | NULL | 流程实例ID | | 
| SCOPE_ID_ | varchar(255) | N | Y | NULL | | | 
| SCOPE_TYPE_ | varchar(255) | N | Y | NULL | | | 
| SCOPE_DEFINITION_ID_ | varchar(255) | N | Y | NULL | | | 


> SQL  

~~~
--
-- 表的结构 `ACT_HI_IDENTITYLINK`
--

CREATE TABLE `ACT_HI_IDENTITYLINK` (
  `ID_` varchar(64) COLLATE utf8_bin NOT NULL DEFAULT '',
  `GROUP_ID_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `TYPE_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `USER_ID_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `TASK_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `CREATE_TIME_` datetime(3) DEFAULT NULL,
  `PROC_INST_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `SCOPE_ID_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `SCOPE_TYPE_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `SCOPE_DEFINITION_ID_` varchar(255) COLLATE utf8_bin DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_bin;

--
-- 转储表的索引
--

--
-- 表的索引 `ACT_HI_IDENTITYLINK`
--
ALTER TABLE `ACT_HI_IDENTITYLINK`
  ADD PRIMARY KEY (`ID_`),
  ADD KEY `ACT_IDX_HI_IDENT_LNK_USER` (`USER_ID_`),
  ADD KEY `ACT_IDX_HI_IDENT_LNK_SCOPE` (`SCOPE_ID_`,`SCOPE_TYPE_`),
  ADD KEY `ACT_IDX_HI_IDENT_LNK_SCOPE_DEF` (`SCOPE_DEFINITION_ID_`,`SCOPE_TYPE_`),
  ADD KEY `ACT_IDX_HI_IDENT_LNK_TASK` (`TASK_ID_`),
  ADD KEY `ACT_IDX_HI_IDENT_LNK_PROCINST` (`PROC_INST_ID_`);
COMMIT;
~~~

## ACT_HI_PROCINST 历史的流程实例

| 字段 | 类型 | 是否为主键 | 是否允许为空 | 默认值 | 说明 | 备注 |  
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |  
| ID_ | varchar(64) | Y | N | | 主键 | |  
| REV_ | int(11) | N | Y | 1 | | | 
| PROC_INST_ID_ | varchar(64) | N | N | | 流程实例ID | | 
| BUSINESS_KEY_ | varchar(255) | N | Y | NULL | 业务主键 | | 
| PROC_DEF_ID_ | varchar(64) | N | N | | 属性ID | | 
| START_TIME_ | datetime(3) | N | Y | NULL | 开始时间 | | 
| END_TIME_ | datetime(3) | N | Y | NULL | 结束时间 | | 
| DURATION_ | bigint(20) | N | Y | NULL | 耗时 | | 
| START_USER_ID_ | varchar(255) | N | Y | NULL | 起始人ID | | 
| START_ACT_ID_ | varchar(255) | N | Y | NULL | 起始节点 | | 
| END_ACT_ID_ | varchar(255) | N | Y | NULL | 结束节点 | | 
| SUPER_PROCESS_INSTANCE_ID_ | varchar(64) | N | Y | NULL | 父流程实例ID | | 
| DELETE_REASON_ | varchar(4000) | N | Y | NULL | 删除原因 | | 
| TENANT_ID_ | varchar(255) | N | Y | 空字符串 | | | 
| NAME_ | varchar(255) | N | Y | NULL | 名称 | | 
| CALLBACK_ID_ | varchar(255) | N | Y | NULL | | | 
| CALLBACK_TYPE_ | varchar(255) | N | Y | NULL | | | 

> SQL  

~~~
--
-- 表的结构 `ACT_HI_PROCINST`
--

CREATE TABLE `ACT_HI_PROCINST` (
  `ID_` varchar(64) COLLATE utf8_bin NOT NULL,
  `REV_` int(11) DEFAULT '1',
  `PROC_INST_ID_` varchar(64) COLLATE utf8_bin NOT NULL,
  `BUSINESS_KEY_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `PROC_DEF_ID_` varchar(64) COLLATE utf8_bin NOT NULL,
  `START_TIME_` datetime(3) NOT NULL,
  `END_TIME_` datetime(3) DEFAULT NULL,
  `DURATION_` bigint(20) DEFAULT NULL,
  `START_USER_ID_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `START_ACT_ID_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `END_ACT_ID_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `SUPER_PROCESS_INSTANCE_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `DELETE_REASON_` varchar(4000) COLLATE utf8_bin DEFAULT NULL,
  `TENANT_ID_` varchar(255) COLLATE utf8_bin DEFAULT '',
  `NAME_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `CALLBACK_ID_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `CALLBACK_TYPE_` varchar(255) COLLATE utf8_bin DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_bin;

--
-- 转储表的索引
--

--
-- 表的索引 `ACT_HI_PROCINST`
--
ALTER TABLE `ACT_HI_PROCINST`
  ADD PRIMARY KEY (`ID_`),
  ADD UNIQUE KEY `PROC_INST_ID_` (`PROC_INST_ID_`),
  ADD KEY `ACT_IDX_HI_PRO_INST_END` (`END_TIME_`),
  ADD KEY `ACT_IDX_HI_PRO_I_BUSKEY` (`BUSINESS_KEY_`);
COMMIT;
~~~

## ACT_HI_TASKINST 历史的任务实例表

| 字段 | 类型 | 是否为主键 | 是否允许为空 | 默认值 | 说明 | 备注 |  
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |  
| ID_ | varchar(64) | Y | N | | 主键 | |  
| REV_ | int(11) | N | Y | 1 | | | 
| PROC_DEF_ID_ | varchar(64) | N | Y | NULL | 流程定义ID | | 
| TASK_DEF_ID_| varchar(64) | N | Y | NULL | 任务定义的ID值 | | 
| PROC_INST_ID_ | varchar(64) | N | Y | NULL | 流程实例ID | | 
| EXECUTION_ID_ | varchar(64) | N | Y | NULL | 执行ID | | 
| SCOPE_ID_ | varchar(255) | N | Y | NULL | | | 
| SUB_SCOPE_ID_ | varchar(255) | N | Y | NULL | | | 
| SCOPE_TYPE_ | varchar(255) | N | Y | NULL | | | 
| SCOPE_DEFINITION_ID_ | varchar(255) | N | Y | NULL | | | 
| NAME_| varchar(255) | N | Y | NULL | 名称 | | 
| PARENT_TASK_ID_ | varchar(64) | N | Y | NULL | 父任务ID | | 
| DESCRIPTION_ | varchar(4000) | N | Y | NULL | 说明 | | 
| OWNER_ | varchar(255) | N | Y | NULL | 实际签收人 任务的拥有者 | 签收人（默认为空，只有在委托时才有值） | 
| ASSIGNEE_ | varchar(255) | N | Y | NULL | 被指派执行该任务的人 | | 
| START_TIME_ | datetime(3) | N | N | | 开始时间 | | 
| CLAIM_TIME_ | datetime(3) | N | Y | NULL | 提醒时间 | | 
| END_TIME_ | datetime(3) | N | Y | NULL | 结束时间 | | 
| DURATION_ | bigint(20) | N | Y | NULL | 耗时 | | 
| DELETE_REASON_ | varchar(4000) | N | Y | NULL | 删除原因 | | 
| PRIORITY_ | int(11) | N | Y | NULL | 优先级别 | | 
| DUE_DATE_ | datetime(3) | N | Y | NULL | 过期时间 | | 
| FORM_KEY_ | varchar(255) | N | Y | NULL | 节点定义的formkey | | 
| CATEGORY_ | varchar(255) | N | Y | NULL | 类别 | | 
| TENANT_ID_ | varchar(255) | N | Y | 空字符串 | | | 
| LAST_UPDATED_TIME_ | datetime(3) | N | Y | NULL | | | 

~~~

--
-- 表的结构 `ACT_HI_TASKINST`
--

CREATE TABLE `ACT_HI_TASKINST` (
  `ID_` varchar(64) COLLATE utf8_bin NOT NULL,
  `REV_` int(11) DEFAULT '1',
  `PROC_DEF_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `TASK_DEF_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `TASK_DEF_KEY_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `PROC_INST_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `EXECUTION_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `SCOPE_ID_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `SUB_SCOPE_ID_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `SCOPE_TYPE_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `SCOPE_DEFINITION_ID_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `NAME_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `PARENT_TASK_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `DESCRIPTION_` varchar(4000) COLLATE utf8_bin DEFAULT NULL,
  `OWNER_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `ASSIGNEE_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `START_TIME_` datetime(3) NOT NULL,
  `CLAIM_TIME_` datetime(3) DEFAULT NULL,
  `END_TIME_` datetime(3) DEFAULT NULL,
  `DURATION_` bigint(20) DEFAULT NULL,
  `DELETE_REASON_` varchar(4000) COLLATE utf8_bin DEFAULT NULL,
  `PRIORITY_` int(11) DEFAULT NULL,
  `DUE_DATE_` datetime(3) DEFAULT NULL,
  `FORM_KEY_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `CATEGORY_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `TENANT_ID_` varchar(255) COLLATE utf8_bin DEFAULT '',
  `LAST_UPDATED_TIME_` datetime(3) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_bin;

--
-- 转储表的索引
--

--
-- 表的索引 `ACT_HI_TASKINST`
--
ALTER TABLE `ACT_HI_TASKINST`
  ADD PRIMARY KEY (`ID_`),
  ADD KEY `ACT_IDX_HI_TASK_SCOPE` (`SCOPE_ID_`,`SCOPE_TYPE_`),
  ADD KEY `ACT_IDX_HI_TASK_SUB_SCOPE` (`SUB_SCOPE_ID_`,`SCOPE_TYPE_`),
  ADD KEY `ACT_IDX_HI_TASK_SCOPE_DEF` (`SCOPE_DEFINITION_ID_`,`SCOPE_TYPE_`),
  ADD KEY `ACT_IDX_HI_TASK_INST_PROCINST` (`PROC_INST_ID_`);
COMMIT;
~~~

## ACT_HI_VARINST 历史的流程运行中的变量信息

| 字段 | 类型 | 是否为主键 | 是否允许为空 | 默认值 | 说明 | 备注 |  
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |  
| ID_ | varchar(64) | Y | N | | 主键 | |  
| REV_ | int(11) | N | Y | 1 | 数据版本号 | | 
| PROC_INST_ID_ | varchar(64) | N | Y | NULL | 流程实例ID | | 
| EXECUTION_ID_ | varchar(64) | N | Y | NULL | 执行ID | | 
| TASK_ID | varchar(64) | N | Y | NULL | 任务ID | | 
| NAME_ | varchar(255) | N | Y | | 名称 | | 
| VAR_TYPE_ | varchar(100) | N | Y | NULL | 参数类型 | | 
| SCOPE_ID_ | varchar(255) | N | Y | NULL | | | 
| SUB_SCOPE_ID_ | varchar(255) | N | Y | NULL | | | 
| SCOPE_TYPE_ | varchar(255) | N | Y | NULL | | | 
| BYTEARRAY_ID_ | varchar(64) | N | Y | NULL | 参数类型 | | 
| DOUBLE_ | double | N | Y | NULL | 存储double类型数据 | | 
| LONG_ | bigint(20) | N | Y | NULL | 存储long类型数据 | | 
| TEXT_ | varchar(4000) | N | Y | NULL | | | 
| TEXT2_ | varchar(4000) | N | Y | NULL | | | 
| LAST_UPDATED_TIME_ | datetime(3) | N | Y | NULL | | | 

> SQL  

~~~
--
-- 表的结构 `ACT_HI_VARINST`
--

CREATE TABLE `ACT_HI_VARINST` (
  `ID_` varchar(64) COLLATE utf8_bin NOT NULL,
  `REV_` int(11) DEFAULT '1',
  `PROC_INST_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `EXECUTION_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `TASK_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `NAME_` varchar(255) COLLATE utf8_bin NOT NULL,
  `VAR_TYPE_` varchar(100) COLLATE utf8_bin DEFAULT NULL,
  `SCOPE_ID_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `SUB_SCOPE_ID_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `SCOPE_TYPE_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `BYTEARRAY_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `DOUBLE_` double DEFAULT NULL,
  `LONG_` bigint(20) DEFAULT NULL,
  `TEXT_` varchar(4000) COLLATE utf8_bin DEFAULT NULL,
  `TEXT2_` varchar(4000) COLLATE utf8_bin DEFAULT NULL,
  `CREATE_TIME_` datetime(3) DEFAULT NULL,
  `LAST_UPDATED_TIME_` datetime(3) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_bin;

--
-- 转储表的索引
--

--
-- 表的索引 `ACT_HI_VARINST`
--
ALTER TABLE `ACT_HI_VARINST`
  ADD PRIMARY KEY (`ID_`),
  ADD KEY `ACT_IDX_HI_PROCVAR_NAME_TYPE` (`NAME_`,`VAR_TYPE_`),
  ADD KEY `ACT_IDX_HI_VAR_SCOPE_ID_TYPE` (`SCOPE_ID_`,`SCOPE_TYPE_`),
  ADD KEY `ACT_IDX_HI_VAR_SUB_ID_TYPE` (`SUB_SCOPE_ID_`,`SCOPE_TYPE_`),
  ADD KEY `ACT_IDX_HI_PROCVAR_PROC_INST` (`PROC_INST_ID_`),
  ADD KEY `ACT_IDX_HI_PROCVAR_TASK_ID` (`TASK_ID_`),
  ADD KEY `ACT_IDX_HI_PROCVAR_EXE` (`EXECUTION_ID_`);
COMMIT;
~~~

## ACT_ID_BYTEARRAY 用户二进制数据表

| 字段 | 类型 | 是否为主键 | 是否允许为空 | 默认值 | 说明 | 备注 |  
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |  
| ID_ | varchar(64) | Y | N | 空字符串 | 主键 | |  
| REV_ | int(11) | N | Y | NULL | 数据版本号 | |
| NAME_ | varchar(255) | N | Y | NULL | 名称 | |
| BYTES_ | longblob | N | Y | NULL | 二进制字节数据 | |

> SQL  

~~~
--
-- 表的结构 `ACT_ID_BYTEARRAY`
--

CREATE TABLE `ACT_ID_BYTEARRAY` (
  `ID_` varchar(64) COLLATE utf8_bin NOT NULL DEFAULT '',
  `REV_` int(11) DEFAULT NULL,
  `NAME_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `BYTES_` longblob
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_bin;

--
-- 转储表的索引
--

--
-- 表的索引 `ACT_ID_BYTEARRAY`
--
ALTER TABLE `ACT_ID_BYTEARRAY`
  ADD PRIMARY KEY (`ID_`);
COMMIT;
~~~

## ACT_ID_GROUP 用户组信息表

| 字段 | 类型 | 是否为主键 | 是否允许为空 | 默认值 | 说明 | 备注 |  
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |  
| ID_ | varchar(64) | Y | N | 空字符串 | 主键 | |  
| REV_ | int(11) | N | Y | NULL | 数据版本号 | |
| NAME_ | varchar(255) | N | Y | NULL | 名称 | |
| TYPE_ | varchar(255) | N | Y | NULL | 类型 | |

> SQL  

~~~
--
-- 表的结构 `ACT_ID_GROUP`
--

CREATE TABLE `ACT_ID_GROUP` (
  `ID_` varchar(64) COLLATE utf8_bin NOT NULL DEFAULT '',
  `REV_` int(11) DEFAULT NULL,
  `NAME_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `TYPE_` varchar(255) COLLATE utf8_bin DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_bin;

--
-- 转储表的索引
--

--
-- 表的索引 `ACT_ID_GROUP`
--
ALTER TABLE `ACT_ID_GROUP`
  ADD PRIMARY KEY (`ID_`);
COMMIT;
~~~

## ACT_ID_INFO 用户信息详情表

| 字段 | 类型 | 是否为主键 | 是否允许为空 | 默认值 | 说明 | 备注 |  
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |  
| ID_ | varchar(64) | Y | N | 空字符串 | 主键 | |  
| REV_ | int(11) | N | Y | NULL | 数据版本号 | |
| USER_ID_ | varchar(64) | N | Y | NULL | 对应用户表主键 | |
| TYPE_ | varchar(64) | N | Y | NULL | 信息类型 | 当前可以设置用户帐号(account)、用户信息(userinfo)和NULL三种值 |
| KEY_ | varchar(255) | N | Y | NULL | 数据的键 | |
| VALUE_ | varchar(255) | N | Y | NULL | 数据的值 | |
| PASSWORD_ | longblob | N | Y | NULL | 用户密码 | |
| PARENT_ID_ | varchar(255) | N | Y | NULL | 父信息ID | |

> SQL  

~~~
--
-- 表的结构 `ACT_ID_INFO`
--

CREATE TABLE `ACT_ID_INFO` (
  `ID_` varchar(64) COLLATE utf8_bin NOT NULL DEFAULT '',
  `REV_` int(11) DEFAULT NULL,
  `USER_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `TYPE_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `KEY_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `VALUE_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `PASSWORD_` longblob,
  `PARENT_ID_` varchar(255) COLLATE utf8_bin DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_bin;

--
-- 转储表的索引
--

--
-- 表的索引 `ACT_ID_INFO`
--
ALTER TABLE `ACT_ID_INFO`
  ADD PRIMARY KEY (`ID_`);
COMMIT;
~~~

## ACT_ID_MEMBERSHIP 用户与用户组关系表

| 字段 | 类型 | 是否为主键 | 是否允许为空 | 默认值 | 说明 | 备注 |  
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |  
| USER_ID_ | varchar(64) | Y | N | 空字符串 | | |  
| GROUP_ID_ | varchar(64) | N | N | 空字符串 | | |

> SQL  

~~~
--
-- 表的结构 `ACT_ID_MEMBERSHIP`
--

CREATE TABLE `ACT_ID_MEMBERSHIP` (
  `USER_ID_` varchar(64) COLLATE utf8_bin NOT NULL DEFAULT '',
  `GROUP_ID_` varchar(64) COLLATE utf8_bin NOT NULL DEFAULT ''
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_bin;

--
-- 转储表的索引
--

--
-- 表的索引 `ACT_ID_MEMBERSHIP`
--
ALTER TABLE `ACT_ID_MEMBERSHIP`
  ADD PRIMARY KEY (`USER_ID_`,`GROUP_ID_`),
  ADD KEY `ACT_FK_MEMB_GROUP` (`GROUP_ID_`);

--
-- 限制导出的表
--

--
-- 限制表 `ACT_ID_MEMBERSHIP`
--
ALTER TABLE `ACT_ID_MEMBERSHIP`
  ADD CONSTRAINT `ACT_FK_MEMB_GROUP` FOREIGN KEY (`GROUP_ID_`) REFERENCES `ACT_ID_GROUP` (`ID_`),
  ADD CONSTRAINT `ACT_FK_MEMB_USER` FOREIGN KEY (`USER_ID_`) REFERENCES `ACT_ID_USER` (`ID_`);
COMMIT;
~~~

## ACT_ID_PRIV 权限表

| 字段 | 类型 | 是否为主键 | 是否允许为空 | 默认值 | 说明 | 备注 |  
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |  
| ID_ | varchar(64) | Y | N | | 主键 | |  
| NAME_ | varchar(255) | N | N | | 名称 | |

> SQL  

~~~
--
-- 表的结构 `ACT_ID_PRIV`
--

CREATE TABLE `ACT_ID_PRIV` (
  `ID_` varchar(64) COLLATE utf8_bin NOT NULL,
  `NAME_` varchar(255) COLLATE utf8_bin NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_bin;

--
-- 转储表的索引
--

--
-- 表的索引 `ACT_ID_PRIV`
--
ALTER TABLE `ACT_ID_PRIV`
  ADD PRIMARY KEY (`ID_`),
  ADD UNIQUE KEY `ACT_UNIQ_PRIV_NAME` (`NAME_`);
COMMIT;
~~~

## ACT_ID_PRIV_MAPPING 用户或组权限关系表

| 字段 | 类型 | 是否为主键 | 是否允许为空 | 默认值 | 说明 | 备注 |  
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |  
| ID_ | varchar(64) | Y | N | | 主键 | |  
| PRIV_ID_ | varchar(64) | N | N | | 权限ID | |
| USER_ID_ | varchar(255) | N | N | | 用户ID | |
| GROUP_ID_ | varchar(255) | N | N | | 用户组ID | |

> SQL  

~~~
--
-- 表的结构 `ACT_ID_PRIV_MAPPING`
--

CREATE TABLE `ACT_ID_PRIV_MAPPING` (
  `ID_` varchar(64) COLLATE utf8_bin NOT NULL,
  `PRIV_ID_` varchar(64) COLLATE utf8_bin NOT NULL,
  `USER_ID_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `GROUP_ID_` varchar(255) COLLATE utf8_bin DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_bin;

--
-- 转储表的索引
--

--
-- 表的索引 `ACT_ID_PRIV_MAPPING`
--
ALTER TABLE `ACT_ID_PRIV_MAPPING`
  ADD PRIMARY KEY (`ID_`),
  ADD KEY `ACT_FK_PRIV_MAPPING` (`PRIV_ID_`),
  ADD KEY `ACT_IDX_PRIV_USER` (`USER_ID_`),
  ADD KEY `ACT_IDX_PRIV_GROUP` (`GROUP_ID_`);

--
-- 限制导出的表
--

--
-- 限制表 `ACT_ID_PRIV_MAPPING`
--
ALTER TABLE `ACT_ID_PRIV_MAPPING`
  ADD CONSTRAINT `ACT_FK_PRIV_MAPPING` FOREIGN KEY (`PRIV_ID_`) REFERENCES `ACT_ID_PRIV` (`ID_`);
COMMIT;
~~~

## ACT_ID_PROPERTY 用户属性表

| 字段 | 类型 | 是否为主键 | 是否允许为空 | 默认值 | 说明 | 备注 |  
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |  
| NAME_ | varchar(64) | Y | N | 空字符串 | 主键 | |  
| VALUE_ | varchar(300) | N | Y | NULL | | |
| REV_ | int(11) | N | Y | NULL | 数据版本号 | |

> SQL  

~~~
--
-- 表的结构 `ACT_ID_PROPERTY`
--

CREATE TABLE `ACT_ID_PROPERTY` (
  `NAME_` varchar(64) COLLATE utf8_bin NOT NULL DEFAULT '',
  `VALUE_` varchar(300) COLLATE utf8_bin DEFAULT NULL,
  `REV_` int(11) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_bin;

--
-- 转储表的索引
--

--
-- 表的索引 `ACT_ID_PROPERTY`
--
ALTER TABLE `ACT_ID_PROPERTY`
  ADD PRIMARY KEY (`NAME_`);
COMMIT;
~~~

## ACT_ID_TOKEN 用户系统登录日志表 

| 字段 | 类型 | 是否为主键 | 是否允许为空 | 默认值 | 说明 | 备注 |  
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |  
| ID_ | varchar(64) | Y | N | | 主键 | |  
| REV_ | int(11) | N | Y | NULL | 数据版本号 | |
| TOKEN_VALUE_ | varchar(255) | N | Y | NULL | | |
| TOKEN_DATE_ | timestamp(3) | N | Y | NULL | | |
| IP_ADDRESS_ | varchar(255) | N | Y | NULL | | |
| USER_AGENT_ | varchar(255) | N | Y | NULL | | |
| USER_ID_ | varchar(255) | N | Y | NULL | | |
| TOKEN_DATA_ | varchar(2000) | N | Y | NULL | | |

> SQL  

~~~
--
-- 表的结构 `ACT_ID_TOKEN`
--

CREATE TABLE `ACT_ID_TOKEN` (
  `ID_` varchar(64) COLLATE utf8_bin NOT NULL,
  `REV_` int(11) DEFAULT NULL,
  `TOKEN_VALUE_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `TOKEN_DATE_` timestamp(3) NULL DEFAULT NULL,
  `IP_ADDRESS_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `USER_AGENT_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `USER_ID_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `TOKEN_DATA_` varchar(2000) COLLATE utf8_bin DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_bin;

--
-- 转储表的索引
--

--
-- 表的索引 `ACT_ID_TOKEN`
--
ALTER TABLE `ACT_ID_TOKEN`
  ADD PRIMARY KEY (`ID_`);
COMMIT;
~~~

## ACT_ID_USER 用户表

| 字段 | 类型 | 是否为主键 | 是否允许为空 | 默认值 | 说明 | 备注 |  
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |  
| ID_ | varchar(64) | Y | N | 空字符串 | 主键 | |  
| REV_ | int(11) | N | Y | NULL | 数据版本号 | |
| FIRST_ | varchar(255) | N | Y | NULL | 名字 | |
| LAST_ | varchar(255) | N | Y | NULL | | 姓氏 |
| EMAIL_ | varchar(255) | N | Y | NULL | 邮箱 | |
| PWD_ | varchar(255) | N | Y | NULL | 用户密码 | |
| PICTURE_ID_ | varchar(64) | N | Y | NULL | 图片ID | |
| TENANT_ID_ | varchar(255) | N | Y | 空字符串 | | |

> SQL  

~~~
--
-- 表的结构 `ACT_ID_USER`
--

CREATE TABLE `ACT_ID_USER` (
  `ID_` varchar(64) COLLATE utf8_bin NOT NULL DEFAULT '',
  `REV_` int(11) DEFAULT NULL,
  `FIRST_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `LAST_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `EMAIL_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `PWD_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `PICTURE_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `TENANT_ID_` varchar(255) COLLATE utf8_bin DEFAULT ''
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_bin;

--
-- 转储表的索引
--

--
-- 表的索引 `ACT_ID_USER`
--
ALTER TABLE `ACT_ID_USER`
  ADD PRIMARY KEY (`ID_`);
COMMIT;
~~~

## ACT_PROCDEF_INFO 流程定义信息

| 字段 | 类型 | 是否为主键 | 是否允许为空 | 默认值 | 说明 | 备注 |  
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |  
| ID_ | varchar(64) | Y | N | | 主键 | |  
| PROC_DEF_ID_ | varchar(64) | N | N | | 流程定义ID | |
| REV_ | int(11) | N | Y | NULL | 数据版本号 | |
| INFO_JSON_ID_ | varchar(64) | N | Y | NULL | | |

> SQL  

~~~
--
-- 表的结构 `ACT_PROCDEF_INFO`
--

CREATE TABLE `ACT_PROCDEF_INFO` (
  `ID_` varchar(64) COLLATE utf8_bin NOT NULL,
  `PROC_DEF_ID_` varchar(64) COLLATE utf8_bin NOT NULL,
  `REV_` int(11) DEFAULT NULL,
  `INFO_JSON_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_bin;

--
-- 转储表的索引
--

--
-- 表的索引 `ACT_PROCDEF_INFO`
--
ALTER TABLE `ACT_PROCDEF_INFO`
  ADD PRIMARY KEY (`ID_`),
  ADD UNIQUE KEY `ACT_UNIQ_INFO_PROCDEF` (`PROC_DEF_ID_`),
  ADD KEY `ACT_IDX_INFO_PROCDEF` (`PROC_DEF_ID_`),
  ADD KEY `ACT_FK_INFO_JSON_BA` (`INFO_JSON_ID_`);

--
-- 限制导出的表
--

--
-- 限制表 `ACT_PROCDEF_INFO`
--
ALTER TABLE `ACT_PROCDEF_INFO`
  ADD CONSTRAINT `ACT_FK_INFO_JSON_BA` FOREIGN KEY (`INFO_JSON_ID_`) REFERENCES `ACT_GE_BYTEARRAY` (`ID_`),
  ADD CONSTRAINT `ACT_FK_INFO_PROCDEF` FOREIGN KEY (`PROC_DEF_ID_`) REFERENCES `ACT_RE_PROCDEF` (`ID_`);
COMMIT;
~~~

## ACT_RE_DEPLOYMENT 部署数据表

| 字段 | 类型 | 是否为主键 | 是否允许为空 | 默认值 | 说明 | 备注 |  
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |  
| ID_ | varchar(64) | Y | N | 空字符串 | 主键 | |  
| NAME_ | varchar(255) | N | Y | NULL | 名称 | |
| CATEGORY_ | varchar(255) | N | Y | NULL | 类别 | 流程定义的Namespace就是类别 |
| KEY_ | varchar(255) | N | Y | NULL | 流程定义ID | |
| TENANT_ID_ | varchar(255) | N | Y | 空字符串 | | |
| DEPLOY_TIME_ | timestamp(3) | N | Y | NULL | 部署时间 | |
| DERIVED_FROM_ | varchar(64) | N | Y | NULL | | |
| DERIVED_FROM_ROOT_ | varchar(64) | N | Y | NULL | | |
| ENGINE_VERSION_ | varchar(255) | N | Y | NULL | 引擎版本 | |

> SQL  

~~~
--
-- 表的结构 `ACT_RE_DEPLOYMENT`
--

CREATE TABLE `ACT_RE_DEPLOYMENT` (
  `ID_` varchar(64) COLLATE utf8_bin NOT NULL DEFAULT '',
  `NAME_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `CATEGORY_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `KEY_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `TENANT_ID_` varchar(255) COLLATE utf8_bin DEFAULT '',
  `DEPLOY_TIME_` timestamp(3) NULL DEFAULT NULL,
  `DERIVED_FROM_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `DERIVED_FROM_ROOT_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `ENGINE_VERSION_` varchar(255) COLLATE utf8_bin DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_bin;

--
-- 转储表的索引
--

--
-- 表的索引 `ACT_RE_DEPLOYMENT`
--
ALTER TABLE `ACT_RE_DEPLOYMENT`
  ADD PRIMARY KEY (`ID_`);
COMMIT;
~~~

## ACT_RE_MODEL 流程设计模型部署表

| 字段 | 类型 | 是否为主键 | 是否允许为空 | 默认值 | 说明 | 备注 |  
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |  
| ID_ | varchar(64) | Y | N | | 主键 | |  
| REV_ | int(11) | N | Y | NULL | 数据版本号 | |
| NAME_ | varchar(255) | N | Y | NULL | 名称 | |
| KEY_ | varchar(255) | N | Y | NULL | | |
| CATEGORY_ | varchar(255) | N | Y | NULL | 分类 | |
| CREATE_TIME_ | timestamp(3) | N | Y | NULL | 创建时间 | |
| LAST_UPDATE_TIME_ | timestamp(3) | N | Y | NULL | 最后更新时间 | |
| VERSION_ | int(11) | N | Y | NULL | 版本 | |
| META_INFO_ | varchar(4000) | N | Y | NULL | 以json格式保存流程定义的信息 | |
| DEPLOYMENT_ID_ | varchar(64) | N | Y | NULL | 部署ID | |
| EDITOR_SOURCE_VALUE_ID_ | varchar(64) | N | Y | NULL | | |
| EDITOR_SOURCE_EXTRA_VALUE_ID_ | varchar(64) | N | Y | NULL | | |
| TENANT_ID_ | varchar(255) | N | Y | 空字符串 | | |

> SQL  

~~~
--
-- 表的结构 `ACT_RE_MODEL`
--

CREATE TABLE `ACT_RE_MODEL` (
  `ID_` varchar(64) COLLATE utf8_bin NOT NULL,
  `REV_` int(11) DEFAULT NULL,
  `NAME_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `KEY_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `CATEGORY_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `CREATE_TIME_` timestamp(3) NULL DEFAULT NULL,
  `LAST_UPDATE_TIME_` timestamp(3) NULL DEFAULT NULL,
  `VERSION_` int(11) DEFAULT NULL,
  `META_INFO_` varchar(4000) COLLATE utf8_bin DEFAULT NULL,
  `DEPLOYMENT_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `EDITOR_SOURCE_VALUE_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `EDITOR_SOURCE_EXTRA_VALUE_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `TENANT_ID_` varchar(255) COLLATE utf8_bin DEFAULT ''
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_bin;

--
-- 转储表的索引
--

--
-- 表的索引 `ACT_RE_MODEL`
--
ALTER TABLE `ACT_RE_MODEL`
  ADD PRIMARY KEY (`ID_`),
  ADD KEY `ACT_FK_MODEL_SOURCE` (`EDITOR_SOURCE_VALUE_ID_`),
  ADD KEY `ACT_FK_MODEL_SOURCE_EXTRA` (`EDITOR_SOURCE_EXTRA_VALUE_ID_`),
  ADD KEY `ACT_FK_MODEL_DEPLOYMENT` (`DEPLOYMENT_ID_`);

--
-- 限制导出的表
--

--
-- 限制表 `ACT_RE_MODEL`
--
ALTER TABLE `ACT_RE_MODEL`
  ADD CONSTRAINT `ACT_FK_MODEL_DEPLOYMENT` FOREIGN KEY (`DEPLOYMENT_ID_`) REFERENCES `ACT_RE_DEPLOYMENT` (`ID_`),
  ADD CONSTRAINT `ACT_FK_MODEL_SOURCE` FOREIGN KEY (`EDITOR_SOURCE_VALUE_ID_`) REFERENCES `ACT_GE_BYTEARRAY` (`ID_`),
  ADD CONSTRAINT `ACT_FK_MODEL_SOURCE_EXTRA` FOREIGN KEY (`EDITOR_SOURCE_EXTRA_VALUE_ID_`) REFERENCES `ACT_GE_BYTEARRAY` (`ID_`);
COMMIT;
~~~

## ACT_RE_PROCDEF 流程定义表

| 字段 | 类型 | 是否为主键 | 是否允许为空 | 默认值 | 说明 | 备注 |  
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |  
| ID_ | varchar(64) | Y | N | | 主键 | |  
| REV_ | int(11) | N | Y | NULL | 数据版本号 | |
| CATEGORY_ | varchar(255) | N | Y | NULL | 流程定义分类 | 读取xml文件中程的targetNamespace值 |
| NAME_ | varchar(255) | N | Y | NULL | 流程定义的名称 | 读取流程文件中process元素的name属性 |
| KEY_ | varchar(255) | N | N | | 流程定义的名称 | 读取流程文件中process元素的id属性 |
| VERSION_ | int(11) | N | N | | 版本 | |
| DEPLOYMENT_ID_ | varchar(64) | N | Y | NULL | 部署ID | 流程定义对应的部署数据ID |
| RESOURCE_NAME_ | varchar(4000) | N | Y | NULL | bpmn文件名称 | 一般为流程文件的相对路径 |
| DGRM_RESOURCE_NAME_ | varchar(4000) | N | Y | NULL | 流程定义对应的流程图资源名称 | |
| DESCRIPTION_ | varchar(4000) | N | Y | NULL | 说明 | |
| HAS_START_FORM_KEY_ | tinyint(4) | N | Y | NULL | 是否存在开始节点formKey | start节点是否存在formKey 0否 1是 |
| HAS_GRAPHICAL_NOTATION_ | tinyint(4) | N | Y | NULL | | |
| SUSPENSION_STATE_ | int(11) | N | Y | NULL | 流程定义状态 | 1激活、2中止 |
| TENANT_ID_ | varchar(255) | N | Y | 空字符串 | | |
| ENGINE_VERSION_ | varchar(255) | N | Y | NULL | 引擎版本 | |
| DERIVED_FROM_ | varchar(64) | N | Y | NULL | | |
| DERIVED_FROM_ROOT_ | varchar(64) | N | Y | NULL | | |
| DERIVED_VERSION_ | int(11) | N | N | 0 | | |

>SQL  

~~~
--
-- 表的结构 `ACT_RE_PROCDEF`
--

CREATE TABLE `ACT_RE_PROCDEF` (
  `ID_` varchar(64) COLLATE utf8_bin NOT NULL,
  `REV_` int(11) DEFAULT NULL,
  `CATEGORY_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `NAME_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `KEY_` varchar(255) COLLATE utf8_bin NOT NULL,
  `VERSION_` int(11) NOT NULL,
  `DEPLOYMENT_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `RESOURCE_NAME_` varchar(4000) COLLATE utf8_bin DEFAULT NULL,
  `DGRM_RESOURCE_NAME_` varchar(4000) COLLATE utf8_bin DEFAULT NULL,
  `DESCRIPTION_` varchar(4000) COLLATE utf8_bin DEFAULT NULL,
  `HAS_START_FORM_KEY_` tinyint(4) DEFAULT NULL,
  `HAS_GRAPHICAL_NOTATION_` tinyint(4) DEFAULT NULL,
  `SUSPENSION_STATE_` int(11) DEFAULT NULL,
  `TENANT_ID_` varchar(255) COLLATE utf8_bin DEFAULT '',
  `ENGINE_VERSION_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `DERIVED_FROM_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `DERIVED_FROM_ROOT_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `DERIVED_VERSION_` int(11) NOT NULL DEFAULT '0'
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_bin;

--
-- 转储表的索引
--

--
-- 表的索引 `ACT_RE_PROCDEF`
--
ALTER TABLE `ACT_RE_PROCDEF`
  ADD PRIMARY KEY (`ID_`),
  ADD UNIQUE KEY `ACT_UNIQ_PROCDEF` (`KEY_`,`VERSION_`,`DERIVED_VERSION_`,`TENANT_ID_`);
COMMIT;
~~~

## ACT_RU_DEADLETTER_JOB 正在运行的任务表

| 字段 | 类型 | 是否为主键 | 是否允许为空 | 默认值 | 说明 | 备注 |  
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |  
| ID_ | varchar(64) | Y | N | | 主键 | |  
| REV_ | int(11) | N | Y | NULL | 数据版本号 | |
| TYPE_ | varchar(255) | N | N | | 类型 | |
| EXCLUSIVE_ | tinyint(255) | N | Y | NULL | | |
| EXECUTION_ID_ | varchar(64) | N | Y | NULL | 执行实例ID | |
| PROCESS_INSTANCE_ID_ | varchar(64) | N | Y | NULL | 流程实例ID | |
| PROC_DEF_ID_ | varchar(64) | N | Y | NULL | 流程定义ID | |
| SCOPE_ID_ | varchar(255) | N | Y | NULL | | |
| SUB_SCOPE_ID_ | varchar(255) | N | Y | NULL | | |
| SCOPE_TYPE_ | varchar(255) | N | Y | NULL | | |
| SCOPE_DEFINITION_ID_ | varchar(255) | N | Y | NULL | | |
| EXCEPTION_STACK_ID_ | varchar(64) | N | Y | NULL | 异常信息ID | |
| EXCEPTION_MSG_ | varchar(4000) | N | Y | NULL | 异常信息 | |
| DUEDATE_ | timestamp(3) | N | Y | NULL | 到期时间 | |
| REPEAT_ | varchar(255) | N | Y | NULL | 重复 | |
| HANDLER_TYPE_ | varchar(255) | N | Y | NULL | 处理类型 | |
| HANDLER_CFG_ | varchar(4000) | N | Y | NULL | | |
| CUSTOM_VALUES_ID_ | varchar(64) | N | Y | NULL | | |
| CREATE_TIME_ | timestamp(3) | N | Y | NULL | | |
| TENANT_ID_ | varchar(255) | N | Y | 空字符串 | | |

> SQL  

~~~
--
-- 表的结构 `ACT_RU_DEADLETTER_JOB`
--

CREATE TABLE `ACT_RU_DEADLETTER_JOB` (
  `ID_` varchar(64) COLLATE utf8_bin NOT NULL,
  `REV_` int(11) DEFAULT NULL,
  `TYPE_` varchar(255) COLLATE utf8_bin NOT NULL,
  `EXCLUSIVE_` tinyint(1) DEFAULT NULL,
  `EXECUTION_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `PROCESS_INSTANCE_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `PROC_DEF_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `SCOPE_ID_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `SUB_SCOPE_ID_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `SCOPE_TYPE_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `SCOPE_DEFINITION_ID_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `EXCEPTION_STACK_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `EXCEPTION_MSG_` varchar(4000) COLLATE utf8_bin DEFAULT NULL,
  `DUEDATE_` timestamp(3) NULL DEFAULT NULL,
  `REPEAT_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `HANDLER_TYPE_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `HANDLER_CFG_` varchar(4000) COLLATE utf8_bin DEFAULT NULL,
  `CUSTOM_VALUES_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `CREATE_TIME_` timestamp(3) NULL DEFAULT NULL,
  `TENANT_ID_` varchar(255) COLLATE utf8_bin DEFAULT ''
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_bin;

--
-- 转储表的索引
--

--
-- 表的索引 `ACT_RU_DEADLETTER_JOB`
--
ALTER TABLE `ACT_RU_DEADLETTER_JOB`
  ADD PRIMARY KEY (`ID_`),
  ADD KEY `ACT_IDX_DEADLETTER_JOB_EXCEPTION_STACK_ID` (`EXCEPTION_STACK_ID_`),
  ADD KEY `ACT_IDX_DEADLETTER_JOB_CUSTOM_VALUES_ID` (`CUSTOM_VALUES_ID_`),
  ADD KEY `ACT_IDX_DJOB_SCOPE` (`SCOPE_ID_`,`SCOPE_TYPE_`),
  ADD KEY `ACT_IDX_DJOB_SUB_SCOPE` (`SUB_SCOPE_ID_`,`SCOPE_TYPE_`),
  ADD KEY `ACT_IDX_DJOB_SCOPE_DEF` (`SCOPE_DEFINITION_ID_`,`SCOPE_TYPE_`),
  ADD KEY `ACT_FK_DEADLETTER_JOB_EXECUTION` (`EXECUTION_ID_`),
  ADD KEY `ACT_FK_DEADLETTER_JOB_PROCESS_INSTANCE` (`PROCESS_INSTANCE_ID_`),
  ADD KEY `ACT_FK_DEADLETTER_JOB_PROC_DEF` (`PROC_DEF_ID_`);

--
-- 限制导出的表
--

--
-- 限制表 `ACT_RU_DEADLETTER_JOB`
--
ALTER TABLE `ACT_RU_DEADLETTER_JOB`
  ADD CONSTRAINT `ACT_FK_DEADLETTER_JOB_CUSTOM_VALUES` FOREIGN KEY (`CUSTOM_VALUES_ID_`) REFERENCES `ACT_GE_BYTEARRAY` (`ID_`),
  ADD CONSTRAINT `ACT_FK_DEADLETTER_JOB_EXCEPTION` FOREIGN KEY (`EXCEPTION_STACK_ID_`) REFERENCES `ACT_GE_BYTEARRAY` (`ID_`),
  ADD CONSTRAINT `ACT_FK_DEADLETTER_JOB_EXECUTION` FOREIGN KEY (`EXECUTION_ID_`) REFERENCES `ACT_RU_EXECUTION` (`ID_`),
  ADD CONSTRAINT `ACT_FK_DEADLETTER_JOB_PROCESS_INSTANCE` FOREIGN KEY (`PROCESS_INSTANCE_ID_`) REFERENCES `ACT_RU_EXECUTION` (`ID_`),
  ADD CONSTRAINT `ACT_FK_DEADLETTER_JOB_PROC_DEF` FOREIGN KEY (`PROC_DEF_ID_`) REFERENCES `ACT_RE_PROCDEF` (`ID_`);
COMMIT;
~~~

## ACT_RU_EVENT_SUBSCR 运行时事件表

| 字段 | 类型 | 是否为主键 | 是否允许为空 | 默认值 | 说明 | 备注 |  
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |  
| ID_ | varchar(64) | Y | N | | 主键 | |  
| REV_ | int(11) | N | Y | NULL | 数据版本号 | |
| EVENT_TYPE_ | varchar(255) | N | N | | 类型 | |
| EVENT_NAME_ | varchar(255) | N | Y | NULL | 名称 | |
| EXECUTION_ID_ | varchar(64) | N | Y | NULL | 执行ID | |
| PROC_INST_ID_ | varchar(64) | N | Y | NULL | 流程定义ID | |
| ACTIVITY_ID_ | varchar(64) | N | Y | NULL | 具体事件ID | |
| CONFIGURATION_ | varchar(255) | N | Y | NULL | 事件的配置属性 | |
| CREATED_ | timestamp(3) | N | N | 当前时间 | 创建时间 | |
| PROC_DEF_ID_ | varchar(64) | N | Y | NULL | 属性ID | |
| TENANT_ID_ | varchar(255) | N | Y | 空字符串 | | |

> SQL  

~~~
--
-- 表的结构 `ACT_RU_EVENT_SUBSCR`
--

CREATE TABLE `ACT_RU_EVENT_SUBSCR` (
  `ID_` varchar(64) COLLATE utf8_bin NOT NULL,
  `REV_` int(11) DEFAULT NULL,
  `EVENT_TYPE_` varchar(255) COLLATE utf8_bin NOT NULL,
  `EVENT_NAME_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `EXECUTION_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `PROC_INST_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `ACTIVITY_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `CONFIGURATION_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `CREATED_` timestamp(3) NOT NULL DEFAULT CURRENT_TIMESTAMP(3),
  `PROC_DEF_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `TENANT_ID_` varchar(255) COLLATE utf8_bin DEFAULT ''
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_bin;

--
-- 转储表的索引
--

--
-- 表的索引 `ACT_RU_EVENT_SUBSCR`
--
ALTER TABLE `ACT_RU_EVENT_SUBSCR`
  ADD PRIMARY KEY (`ID_`),
  ADD KEY `ACT_IDX_EVENT_SUBSCR_CONFIG_` (`CONFIGURATION_`),
  ADD KEY `ACT_FK_EVENT_EXEC` (`EXECUTION_ID_`);

--
-- 限制导出的表
--

--
-- 限制表 `ACT_RU_EVENT_SUBSCR`
--
ALTER TABLE `ACT_RU_EVENT_SUBSCR`
  ADD CONSTRAINT `ACT_FK_EVENT_EXEC` FOREIGN KEY (`EXECUTION_ID_`) REFERENCES `ACT_RU_EXECUTION` (`ID_`);
COMMIT;
~~~

## ACT_RU_EXECUTION 运行时流程执行实例表

| 字段 | 类型 | 是否为主键 | 是否允许为空 | 默认值 | 说明 | 备注 |  
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |  
| ID_ | varchar(64) | Y | N | 空字符串 | 主键 | |  
| REV_ | int(11) | N | Y | NULL | 数据版本号 | |
| PROC_INST_ID_ | varchar(64) | N | Y | NULL | 流程实例ID | |
| BUSINESS_KEY_ | varchar(255) | N | Y | NULL | 业务主键ID | |
| PARENT_ID_ | varchar(64) | N | Y | NULL | 父执行流的ID | |
| PROC_DEF_ID_ | varchar(64) | N | Y | NULL | 流程定义的数据ID | |
| SUPER_EXEC_ | varchar(64) | N | Y | NULL | | |
| ROOT_PROC_INST_ID_ | varchar(64) | N | Y | NULL | | |
| ACT_ID_ | varchar(255) | N | Y | NULL | 节点实例ID | |
| IS_ACTIVE_ | tinyint(4) | N | Y | NULL | 是否激活 | |
| IS_CONCURRENT_ | tinyint(4) | N | Y | NULL | 执行流是否正在并行 | |
| IS_SCOPE_ | tinyint(4) | N | Y | NULL | | |
| IS_EVENT_SCOPE_ | tinyint(4) | N | Y | NULL | | |
| IS_MI_ROOT_ | tinyint(4) | N | Y | NULL | | |
| SUSPENSION_STATE_ | int(11) | N | Y | NULL | 流程终端状态 | |
| CACHED_ENT_STATE_ | int(11) | N | Y | NULL | | |
| TENANT_ID_ | varchar(255) | N | Y | 空字符串 | | |
| NAME_ | varchar(255) | N | Y | NULL | | |
| START_ACT_ID_ | varchar(255) | N | Y | NULL | | |
| START_TIME_ | datetime(3) | N | Y | NULL | 开始时间 | |
| START_USER_ID_ | varchar(255) | N | Y | NULL | | |
| LOCK_TIME_ | timestamp(3) | N | Y | NULL | | |
| IS_COUNT_ENABLED_ | tinyint(4) | N | Y | NULL | | |
| EVT_SUBSCR_COUNT_ | int(11) | N | Y | NULL | | |
| TASK_COUNT_ | int(11) | N | Y | NULL | | |
| JOB_COUNT_ | int(11) | N | Y | NULL | | |
| TIMER_JOB_COUNT_ | int(11) | N | Y | NULL | | |
| SUSP_JOB_COUNT_ | int(11) | N | Y | NULL | | |
| DEADLETTER_JOB_COUNT_ | int(11) | N | Y | NULL | | |
| VAR_COUNT_ | int(11) | N | Y | NULL | | |
| ID_LINK_COUNT_ | int(11) | N | Y | NULL | | |
| CALLBACK_ID_ | varchar(255) | N | Y | NULL | | |
| CALLBACK_TYPE_ | varchar(255) | N | Y | NULL | | |

> SQL  

~~~
--
-- 表的结构 `ACT_RU_EXECUTION`
--

CREATE TABLE `ACT_RU_EXECUTION` (
  `ID_` varchar(64) COLLATE utf8_bin NOT NULL DEFAULT '',
  `REV_` int(11) DEFAULT NULL,
  `PROC_INST_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `BUSINESS_KEY_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `PARENT_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `PROC_DEF_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `SUPER_EXEC_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `ROOT_PROC_INST_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `ACT_ID_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `IS_ACTIVE_` tinyint(4) DEFAULT NULL,
  `IS_CONCURRENT_` tinyint(4) DEFAULT NULL,
  `IS_SCOPE_` tinyint(4) DEFAULT NULL,
  `IS_EVENT_SCOPE_` tinyint(4) DEFAULT NULL,
  `IS_MI_ROOT_` tinyint(4) DEFAULT NULL,
  `SUSPENSION_STATE_` int(11) DEFAULT NULL,
  `CACHED_ENT_STATE_` int(11) DEFAULT NULL,
  `TENANT_ID_` varchar(255) COLLATE utf8_bin DEFAULT '',
  `NAME_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `START_ACT_ID_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `START_TIME_` datetime(3) DEFAULT NULL,
  `START_USER_ID_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `LOCK_TIME_` timestamp(3) NULL DEFAULT NULL,
  `IS_COUNT_ENABLED_` tinyint(4) DEFAULT NULL,
  `EVT_SUBSCR_COUNT_` int(11) DEFAULT NULL,
  `TASK_COUNT_` int(11) DEFAULT NULL,
  `JOB_COUNT_` int(11) DEFAULT NULL,
  `TIMER_JOB_COUNT_` int(11) DEFAULT NULL,
  `SUSP_JOB_COUNT_` int(11) DEFAULT NULL,
  `DEADLETTER_JOB_COUNT_` int(11) DEFAULT NULL,
  `VAR_COUNT_` int(11) DEFAULT NULL,
  `ID_LINK_COUNT_` int(11) DEFAULT NULL,
  `CALLBACK_ID_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `CALLBACK_TYPE_` varchar(255) COLLATE utf8_bin DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_bin;

--
-- 转储表的索引
--

--
-- 表的索引 `ACT_RU_EXECUTION`
--
ALTER TABLE `ACT_RU_EXECUTION`
  ADD PRIMARY KEY (`ID_`),
  ADD KEY `ACT_IDX_EXEC_BUSKEY` (`BUSINESS_KEY_`),
  ADD KEY `ACT_IDC_EXEC_ROOT` (`ROOT_PROC_INST_ID_`),
  ADD KEY `ACT_FK_EXE_PROCINST` (`PROC_INST_ID_`),
  ADD KEY `ACT_FK_EXE_PARENT` (`PARENT_ID_`),
  ADD KEY `ACT_FK_EXE_SUPER` (`SUPER_EXEC_`),
  ADD KEY `ACT_FK_EXE_PROCDEF` (`PROC_DEF_ID_`);

--
-- 限制导出的表
--

--
-- 限制表 `ACT_RU_EXECUTION`
--
ALTER TABLE `ACT_RU_EXECUTION`
  ADD CONSTRAINT `ACT_FK_EXE_PARENT` FOREIGN KEY (`PARENT_ID_`) REFERENCES `ACT_RU_EXECUTION` (`ID_`) ON DELETE CASCADE,
  ADD CONSTRAINT `ACT_FK_EXE_PROCDEF` FOREIGN KEY (`PROC_DEF_ID_`) REFERENCES `ACT_RE_PROCDEF` (`ID_`),
  ADD CONSTRAINT `ACT_FK_EXE_PROCINST` FOREIGN KEY (`PROC_INST_ID_`) REFERENCES `ACT_RU_EXECUTION` (`ID_`) ON DELETE CASCADE ON UPDATE CASCADE,
  ADD CONSTRAINT `ACT_FK_EXE_SUPER` FOREIGN KEY (`SUPER_EXEC_`) REFERENCES `ACT_RU_EXECUTION` (`ID_`) ON DELETE CASCADE;
COMMIT;
~~~

## ACT_RU_HISTORY_JOB 历史作业表


| 字段 | 类型 | 是否为主键 | 是否允许为空 | 默认值 | 说明 | 备注 |  
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |  
| ID_ | varchar(64) | Y | N | | 主键 | |  
| REV_ | int(11) | N | Y | NULL | 数据版本号 | |
| LOCK_EXP_TIME_ | timestamp(3) | N | Y | NULL | | |
| LOCK_OWNER_ | varchar(255) | N | Y | NULL | | |
| RETRIES_ | int(11) | N | Y | NULL | | |
| EXCEPTION_STACK_ID_ | varchar(64) | N | Y | NULL | | |
| EXCEPTION_MSG_ | varchar(4000) | N | Y | NULL | | |
| HANDLER_TYPE_ | varchar(255) | N | Y | NULL | | |
| HANDLER_CFG_ | varchar(4000) | N | Y | NULL | | |
| CUSTOM_VALUES_ID_ | varchar(64) | N | Y | NULL | | |
| ADV_HANDLER_CFG_ID_ | varchar(64) | N | Y | NULL | | |
| CREATE_TIME_ | timestamp(3) | N | Y | NULL | | |
| TENANT_ID_ | varchar(255) | N | Y | 空字符串 | | |

> SQL  

~~~
--
-- 表的结构 `ACT_RU_HISTORY_JOB`
--

CREATE TABLE `ACT_RU_HISTORY_JOB` (
  `ID_` varchar(64) COLLATE utf8_bin NOT NULL,
  `REV_` int(11) DEFAULT NULL,
  `LOCK_EXP_TIME_` timestamp(3) NULL DEFAULT NULL,
  `LOCK_OWNER_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `RETRIES_` int(11) DEFAULT NULL,
  `EXCEPTION_STACK_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `EXCEPTION_MSG_` varchar(4000) COLLATE utf8_bin DEFAULT NULL,
  `HANDLER_TYPE_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `HANDLER_CFG_` varchar(4000) COLLATE utf8_bin DEFAULT NULL,
  `CUSTOM_VALUES_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `ADV_HANDLER_CFG_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `CREATE_TIME_` timestamp(3) NULL DEFAULT NULL,
  `TENANT_ID_` varchar(255) COLLATE utf8_bin DEFAULT ''
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_bin;

--
-- 转储表的索引
--

--
-- 表的索引 `ACT_RU_HISTORY_JOB`
--
ALTER TABLE `ACT_RU_HISTORY_JOB`
  ADD PRIMARY KEY (`ID_`);
COMMIT;
~~~

## ACT_RU_IDENTITYLINK 运行时用户关系信息

| 字段 | 类型 | 是否为主键 | 是否允许为空 | 默认值 | 说明 | 备注 |  
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |  
| ID_ | varchar(64) | Y | N | 空字符串 | 主键 | |  
| REV_ | int(11) | N | Y | NULL | 数据版本号 | |  
| GROUP_ID_ | varchar(255) | N | Y | NULL | 用户组ID | |  
| TYPE_ | varchar(255) | N | Y | NULL | 关系数据类型 | assignee支配人(组)、candidate候选人(组)、owner拥有人 |  
| USER_ID_ | varchar(255) | N | Y | NULL | 用户ID | |  
| TASK_ID_ | varchar(64) | N | Y | NULL | 任务ID | |  
| PROC_INST_ID_ | varchar(64) | N | Y | NULL | 流程定义ID | |  
| PROC_DEF_ID_ | varchar(64) | N | Y | NULL | 属性ID | |  
| SCOPE_ID_ | varchar(255) | N | Y | NULL | | |  
| SCOPE_TYPE_ | varchar(255) | N | Y | NULL | | |  
| SCOPE_DEFINITION_ID_ | varchar(255) | N | Y | NULL | | |  


> SQL  

~~~
--
-- 表的结构 `ACT_RU_IDENTITYLINK`
--

CREATE TABLE `ACT_RU_IDENTITYLINK` (
  `ID_` varchar(64) COLLATE utf8_bin NOT NULL DEFAULT '',
  `REV_` int(11) DEFAULT NULL,
  `GROUP_ID_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `TYPE_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `USER_ID_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `TASK_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `PROC_INST_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `PROC_DEF_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `SCOPE_ID_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `SCOPE_TYPE_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `SCOPE_DEFINITION_ID_` varchar(255) COLLATE utf8_bin DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_bin;

--
-- 转储表的索引
--

--
-- 表的索引 `ACT_RU_IDENTITYLINK`
--
ALTER TABLE `ACT_RU_IDENTITYLINK`
  ADD PRIMARY KEY (`ID_`),
  ADD KEY `ACT_IDX_IDENT_LNK_USER` (`USER_ID_`),
  ADD KEY `ACT_IDX_IDENT_LNK_GROUP` (`GROUP_ID_`),
  ADD KEY `ACT_IDX_IDENT_LNK_SCOPE` (`SCOPE_ID_`,`SCOPE_TYPE_`),
  ADD KEY `ACT_IDX_IDENT_LNK_SCOPE_DEF` (`SCOPE_DEFINITION_ID_`,`SCOPE_TYPE_`),
  ADD KEY `ACT_IDX_ATHRZ_PROCEDEF` (`PROC_DEF_ID_`),
  ADD KEY `ACT_FK_TSKASS_TASK` (`TASK_ID_`),
  ADD KEY `ACT_FK_IDL_PROCINST` (`PROC_INST_ID_`);

--
-- 限制导出的表
--

--
-- 限制表 `ACT_RU_IDENTITYLINK`
--
ALTER TABLE `ACT_RU_IDENTITYLINK`
  ADD CONSTRAINT `ACT_FK_ATHRZ_PROCEDEF` FOREIGN KEY (`PROC_DEF_ID_`) REFERENCES `ACT_RE_PROCDEF` (`ID_`),
  ADD CONSTRAINT `ACT_FK_IDL_PROCINST` FOREIGN KEY (`PROC_INST_ID_`) REFERENCES `ACT_RU_EXECUTION` (`ID_`),
  ADD CONSTRAINT `ACT_FK_TSKASS_TASK` FOREIGN KEY (`TASK_ID_`) REFERENCES `ACT_RU_TASK` (`ID_`);
COMMIT;
~~~

## ACT_RU_JOB 运行时作业表（一般工作表）

| 字段 | 类型 | 是否为主键 | 是否允许为空 | 默认值 | 说明 | 备注 |  
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |  
| ID_ | varchar(64) | Y | N | | 主键 | |  
| REV_ | int(11) | N | Y | NULL | 数据版本号 | |  
| TYPE_ | varchar(255) | N | N | | 类型 | |  
| LOCK_EXP_TIME_ | timestamp(3) | N | Y | NULL | 锁定释放时间 | |  
| LOCK_OWNER_ | varchar(255) | N | Y | NULL | 挂起者 | |  
| EXCLUSIVE_ | tinyint(1) | N | Y | NULL | | |  
| EXECUTION_ID_ | varchar(64) | N | Y | NULL | 执行实例ID | |  
| PROCESS_INSTANCE_ID_ | varchar(64) | N | Y | NULL | 流程实例ID | |  
| PROC_DEF_ID_ | varchar(64) | N | Y | NULL | 流程定义ID | |  
| SCOPE_ID_ | varchar(255) | N | Y | NULL | | |  
| SUB_SCOPE_ID_ | varchar(255) | N | Y | NULL | | |  
| SCOPE_TYPE_ | varchar(255) | N | Y | NULL | | |  
| SCOPE_DEFINITION_ID_ | varchar(255) | N | Y | NULL | | |  
| RETRIES_ | int(11) | N | Y | NULL | | |  
| EXCEPTION_STACK_ID_ | varchar(64) | N | Y | NULL | 异常信息ID | |  
| EXCEPTION_MSG_ | varchar(4000) | N | Y | NULL | 异常信息 | |  
| DUEDATE_ | timestamp(3) | N | Y | NULL | 到期时间 | |  
| REPEAT_ | varchar(255) | N | Y | NULL | 重复 | |  
| HANDLER_TYPE_ | varchar(255) | N | Y | NULL | 处理类型 | |  
| HANDLER_CFG_ | varchar(4000) | N | Y | NULL | | |  
| CUSTOM_VALUES_ID_| varchar(64) | N | Y | NULL | | |  
| CREATE_TIME_ | timestamp(3) | N | Y | NULL | | |  
| TENANT_ID_ | varchar(255) | N | Y | 空字符串 | | |  

> SQL  

~~~
--
-- 表的结构 `ACT_RU_JOB`
--

CREATE TABLE `ACT_RU_JOB` (
  `ID_` varchar(64) COLLATE utf8_bin NOT NULL,
  `REV_` int(11) DEFAULT NULL,
  `TYPE_` varchar(255) COLLATE utf8_bin NOT NULL,
  `LOCK_EXP_TIME_` timestamp(3) NULL DEFAULT NULL,
  `LOCK_OWNER_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `EXCLUSIVE_` tinyint(1) DEFAULT NULL,
  `EXECUTION_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `PROCESS_INSTANCE_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `PROC_DEF_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `SCOPE_ID_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `SUB_SCOPE_ID_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `SCOPE_TYPE_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `SCOPE_DEFINITION_ID_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `RETRIES_` int(11) DEFAULT NULL,
  `EXCEPTION_STACK_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `EXCEPTION_MSG_` varchar(4000) COLLATE utf8_bin DEFAULT NULL,
  `DUEDATE_` timestamp(3) NULL DEFAULT NULL,
  `REPEAT_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `HANDLER_TYPE_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `HANDLER_CFG_` varchar(4000) COLLATE utf8_bin DEFAULT NULL,
  `CUSTOM_VALUES_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `CREATE_TIME_` timestamp(3) NULL DEFAULT NULL,
  `TENANT_ID_` varchar(255) COLLATE utf8_bin DEFAULT ''
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_bin;

--
-- 转储表的索引
--

--
-- 表的索引 `ACT_RU_JOB`
--
ALTER TABLE `ACT_RU_JOB`
  ADD PRIMARY KEY (`ID_`),
  ADD KEY `ACT_IDX_JOB_EXCEPTION_STACK_ID` (`EXCEPTION_STACK_ID_`),
  ADD KEY `ACT_IDX_JOB_CUSTOM_VALUES_ID` (`CUSTOM_VALUES_ID_`),
  ADD KEY `ACT_IDX_JOB_SCOPE` (`SCOPE_ID_`,`SCOPE_TYPE_`),
  ADD KEY `ACT_IDX_JOB_SUB_SCOPE` (`SUB_SCOPE_ID_`,`SCOPE_TYPE_`),
  ADD KEY `ACT_IDX_JOB_SCOPE_DEF` (`SCOPE_DEFINITION_ID_`,`SCOPE_TYPE_`),
  ADD KEY `ACT_FK_JOB_EXECUTION` (`EXECUTION_ID_`),
  ADD KEY `ACT_FK_JOB_PROCESS_INSTANCE` (`PROCESS_INSTANCE_ID_`),
  ADD KEY `ACT_FK_JOB_PROC_DEF` (`PROC_DEF_ID_`);

--
-- 限制导出的表
--

--
-- 限制表 `ACT_RU_JOB`
--
ALTER TABLE `ACT_RU_JOB`
  ADD CONSTRAINT `ACT_FK_JOB_CUSTOM_VALUES` FOREIGN KEY (`CUSTOM_VALUES_ID_`) REFERENCES `ACT_GE_BYTEARRAY` (`ID_`),
  ADD CONSTRAINT `ACT_FK_JOB_EXCEPTION` FOREIGN KEY (`EXCEPTION_STACK_ID_`) REFERENCES `ACT_GE_BYTEARRAY` (`ID_`),
  ADD CONSTRAINT `ACT_FK_JOB_EXECUTION` FOREIGN KEY (`EXECUTION_ID_`) REFERENCES `ACT_RU_EXECUTION` (`ID_`),
  ADD CONSTRAINT `ACT_FK_JOB_PROCESS_INSTANCE` FOREIGN KEY (`PROCESS_INSTANCE_ID_`) REFERENCES `ACT_RU_EXECUTION` (`ID_`),
  ADD CONSTRAINT `ACT_FK_JOB_PROC_DEF` FOREIGN KEY (`PROC_DEF_ID_`) REFERENCES `ACT_RE_PROCDEF` (`ID_`);
COMMIT;
~~~

## ACT_RU_SUSPENDED_JOB 暂停作业表

| 字段 | 类型 | 是否为主键 | 是否允许为空 | 默认值 | 说明 | 备注 |  
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |  
| ID_ | varchar(64) | Y | N | | 主键 | |  
| REV_ | int(11) | N | Y | NULL | 数据版本号 | |  
| TYPE_ | varchar(255) | N | N | | 类型 | |  
| EXCLUSIVE_ | tinyint(1) | N | Y | NULL | | |  
| EXECUTION_ID_ | varchar(64) | N | Y | NULL | 执行实例ID | |  
| PROCESS_INSTANCE_ID_ | varchar(64) | N | Y | NULL | 流程实例ID | |  
| PROC_DEF_ID_ | varchar(64) | N | Y | NULL | 流程定义ID | |  
| SCOPE_ID_ | varchar(255) | N | Y | NULL | | |  
| SUB_SCOPE_ID_ | varchar(255) | N | Y | NULL | | |  
| SCOPE_TYPE_ | varchar(255) | N | Y | NULL | | |  
| SCOPE_DEFINITION_ID_ | varchar(255) | N | Y | NULL | | |  
| RETRIES_ | int(11) | N | Y | NULL | | |  
| EXCEPTION_STACK_ID_ | varchar(64) | N | Y | NULL | 异常信息ID | |  
| EXCEPTION_MSG_ | varchar(4000) | N | Y | NULL | 异常信息 | |  
| DUEDATE_ | timestamp(3) | N | Y | NULL | 到期时间 | |  
| REPEAT_ | varchar(255) | N | Y | NULL | 重复 | |  
| HANDLER_TYPE_ | varchar(255) | N | Y | NULL | 处理类型 | |  
| HANDLER_CFG_ | varchar(4000) | N | Y | NULL | | |  
| CUSTOM_VALUES_ID_ | varchar(64) | N | Y | NULL | | |  
| CREATE_TIME_ | timestamp(3) | N | Y | NULL | | |  
| TENANT_ID_ | varchar(255) | N | Y | 空字符串 | | |  

> SQL  

~~~
--
-- 表的结构 `ACT_RU_SUSPENDED_JOB`
--

CREATE TABLE `ACT_RU_SUSPENDED_JOB` (
  `ID_` varchar(64) COLLATE utf8_bin NOT NULL,
  `REV_` int(11) DEFAULT NULL,
  `TYPE_` varchar(255) COLLATE utf8_bin NOT NULL,
  `EXCLUSIVE_` tinyint(1) DEFAULT NULL,
  `EXECUTION_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `PROCESS_INSTANCE_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `PROC_DEF_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `SCOPE_ID_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `SUB_SCOPE_ID_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `SCOPE_TYPE_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `SCOPE_DEFINITION_ID_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `RETRIES_` int(11) DEFAULT NULL,
  `EXCEPTION_STACK_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `EXCEPTION_MSG_` varchar(4000) COLLATE utf8_bin DEFAULT NULL,
  `DUEDATE_` timestamp(3) NULL DEFAULT NULL,
  `REPEAT_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `HANDLER_TYPE_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `HANDLER_CFG_` varchar(4000) COLLATE utf8_bin DEFAULT NULL,
  `CUSTOM_VALUES_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `CREATE_TIME_` timestamp(3) NULL DEFAULT NULL,
  `TENANT_ID_` varchar(255) COLLATE utf8_bin DEFAULT ''
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_bin;

--
-- 转储表的索引
--

--
-- 表的索引 `ACT_RU_SUSPENDED_JOB`
--
ALTER TABLE `ACT_RU_SUSPENDED_JOB`
  ADD PRIMARY KEY (`ID_`),
  ADD KEY `ACT_IDX_SUSPENDED_JOB_EXCEPTION_STACK_ID` (`EXCEPTION_STACK_ID_`),
  ADD KEY `ACT_IDX_SUSPENDED_JOB_CUSTOM_VALUES_ID` (`CUSTOM_VALUES_ID_`),
  ADD KEY `ACT_IDX_SJOB_SCOPE` (`SCOPE_ID_`,`SCOPE_TYPE_`),
  ADD KEY `ACT_IDX_SJOB_SUB_SCOPE` (`SUB_SCOPE_ID_`,`SCOPE_TYPE_`),
  ADD KEY `ACT_IDX_SJOB_SCOPE_DEF` (`SCOPE_DEFINITION_ID_`,`SCOPE_TYPE_`),
  ADD KEY `ACT_FK_SUSPENDED_JOB_EXECUTION` (`EXECUTION_ID_`),
  ADD KEY `ACT_FK_SUSPENDED_JOB_PROCESS_INSTANCE` (`PROCESS_INSTANCE_ID_`),
  ADD KEY `ACT_FK_SUSPENDED_JOB_PROC_DEF` (`PROC_DEF_ID_`);

--
-- 限制导出的表
--

--
-- 限制表 `ACT_RU_SUSPENDED_JOB`
--
ALTER TABLE `ACT_RU_SUSPENDED_JOB`
  ADD CONSTRAINT `ACT_FK_SUSPENDED_JOB_CUSTOM_VALUES` FOREIGN KEY (`CUSTOM_VALUES_ID_`) REFERENCES `ACT_GE_BYTEARRAY` (`ID_`),
  ADD CONSTRAINT `ACT_FK_SUSPENDED_JOB_EXCEPTION` FOREIGN KEY (`EXCEPTION_STACK_ID_`) REFERENCES `ACT_GE_BYTEARRAY` (`ID_`),
  ADD CONSTRAINT `ACT_FK_SUSPENDED_JOB_EXECUTION` FOREIGN KEY (`EXECUTION_ID_`) REFERENCES `ACT_RU_EXECUTION` (`ID_`),
  ADD CONSTRAINT `ACT_FK_SUSPENDED_JOB_PROCESS_INSTANCE` FOREIGN KEY (`PROCESS_INSTANCE_ID_`) REFERENCES `ACT_RU_EXECUTION` (`ID_`),
  ADD CONSTRAINT `ACT_FK_SUSPENDED_JOB_PROC_DEF` FOREIGN KEY (`PROC_DEF_ID_`) REFERENCES `ACT_RE_PROCDEF` (`ID_`);
COMMIT;
~~~

## ACT_RU_TASK  运行时任务表

| 字段 | 类型 | 是否为主键 | 是否允许为空 | 默认值 | 说明 | 备注 |  
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |  
| ID_ | varchar(64) | Y | N | 空字符串 | 主键 | |  
| REV_ | int(11) | N | Y | NULL | 数据版本号 | |  
| EXECUTION_ID_ | varchar(64) | N | Y | NULL | 任务所在的执行流ID | |  
| PROC_INST_ID_ | varchar(64) | N | Y | NULL | 流程实例ID | |  
| PROC_DEF_ID_ | varchar(64) | N | Y | NULL | 流程定义数据ID | |  
| TASK_DEF_ID_ | varchar(64) | N | Y | NULL | | |  
| SCOPE_ID_ | varchar(255) | N | Y | NULL | | |  
| SUB_SCOPE_ID_ | varchar(255) | N | Y | NULL | | |  
| SCOPE_TYPE_ | varchar(255) | N | Y | NULL | | |  
| SCOPE_DEFINITION_ID_ | varchar(255) | N | Y | NULL | | |  
| NAME_ | varchar(255) | N | Y | NULL | 任务名称 | |  
| PARENT_TASK_ID_ | varchar(64) | N | Y | NULL | 父任务ID | |  
| DESCRIPTION_ | varchar(4000) | N | Y | NULL | 说明 | |  
| TASK_DEF_KEY_ | varchar(255) | N | Y | NULL | 任务定义的ID值 | |  
| OWNER_ | varchar(255) | N | Y | NULL | 任务拥有人 | |  
| ASSIGNEE_ | varchar(255) | N | Y | NULL | 被指派执行该任务的人 | |  
| DELEGATION_ | varchar(64) | N | Y | NULL | | |  
| PRIORITY_ | int(11) | N | Y | NULL | | |  
| CREATE_TIME_ | timestamp(3) | N | Y | NULL | 创建时间 | |  
| DUE_DATE_ | datetime(3) | N | Y | NULL | 耗时 | |  
| CATEGORY_ | varchar(255) | N | Y | NULL | | |  
| SUSPENSION_STATE_ | int(11) | N | Y | NULL | 是否挂起 | 1代表激活 2代表挂起 |  
| TENANT_ID_ | varchar(255) | N | Y | 空字符串 | | |  
| FORM_KEY_ | varchar(255) | N | Y | NULL | | |  
| CLAIM_TIME_ | datetime(3) | N | Y | NULL | | |  
| IS_COUNT_ENABLED_ | tinyint(4) | N | Y | NULL | | |  
| VAR_COUNT_ | int(11) | N | Y | NULL | | |  
| ID_LINK_COUNT_ | int(11) | N | Y | NULL | | |  
| SUB_TASK_COUNT_ | int(11) | N | Y | NULL | | |  

> SQL  

~~~
--
-- 表的结构 `ACT_RU_TASK`
--

CREATE TABLE `ACT_RU_TASK` (
  `ID_` varchar(64) COLLATE utf8_bin NOT NULL DEFAULT '',
  `REV_` int(11) DEFAULT NULL,
  `EXECUTION_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `PROC_INST_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `PROC_DEF_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `TASK_DEF_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `SCOPE_ID_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `SUB_SCOPE_ID_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `SCOPE_TYPE_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `SCOPE_DEFINITION_ID_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `NAME_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `PARENT_TASK_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `DESCRIPTION_` varchar(4000) COLLATE utf8_bin DEFAULT NULL,
  `TASK_DEF_KEY_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `OWNER_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `ASSIGNEE_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `DELEGATION_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `PRIORITY_` int(11) DEFAULT NULL,
  `CREATE_TIME_` timestamp(3) NULL DEFAULT NULL,
  `DUE_DATE_` datetime(3) DEFAULT NULL,
  `CATEGORY_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `SUSPENSION_STATE_` int(11) DEFAULT NULL,
  `TENANT_ID_` varchar(255) COLLATE utf8_bin DEFAULT '',
  `FORM_KEY_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `CLAIM_TIME_` datetime(3) DEFAULT NULL,
  `IS_COUNT_ENABLED_` tinyint(4) DEFAULT NULL,
  `VAR_COUNT_` int(11) DEFAULT NULL,
  `ID_LINK_COUNT_` int(11) DEFAULT NULL,
  `SUB_TASK_COUNT_` int(11) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_bin;

--
-- 转储表的索引
--

--
-- 表的索引 `ACT_RU_TASK`
--
ALTER TABLE `ACT_RU_TASK`
  ADD PRIMARY KEY (`ID_`),
  ADD KEY `ACT_IDX_TASK_CREATE` (`CREATE_TIME_`),
  ADD KEY `ACT_IDX_TASK_SCOPE` (`SCOPE_ID_`,`SCOPE_TYPE_`),
  ADD KEY `ACT_IDX_TASK_SUB_SCOPE` (`SUB_SCOPE_ID_`,`SCOPE_TYPE_`),
  ADD KEY `ACT_IDX_TASK_SCOPE_DEF` (`SCOPE_DEFINITION_ID_`,`SCOPE_TYPE_`),
  ADD KEY `ACT_FK_TASK_EXE` (`EXECUTION_ID_`),
  ADD KEY `ACT_FK_TASK_PROCINST` (`PROC_INST_ID_`),
  ADD KEY `ACT_FK_TASK_PROCDEF` (`PROC_DEF_ID_`);

--
-- 限制导出的表
--

--
-- 限制表 `ACT_RU_TASK`
--
ALTER TABLE `ACT_RU_TASK`
  ADD CONSTRAINT `ACT_FK_TASK_EXE` FOREIGN KEY (`EXECUTION_ID_`) REFERENCES `ACT_RU_EXECUTION` (`ID_`),
  ADD CONSTRAINT `ACT_FK_TASK_PROCDEF` FOREIGN KEY (`PROC_DEF_ID_`) REFERENCES `ACT_RE_PROCDEF` (`ID_`),
  ADD CONSTRAINT `ACT_FK_TASK_PROCINST` FOREIGN KEY (`PROC_INST_ID_`) REFERENCES `ACT_RU_EXECUTION` (`ID_`);
COMMIT;
~~~

## ACT_RU_TIMER_JOB 定时作业表

| 字段 | 类型 | 是否为主键 | 是否允许为空 | 默认值 | 说明 | 备注 |  
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |  
| ID_ | varchar(64) | Y | N | | 主键 | |  
| REV_ | int(11) | N | Y | NULL | 数据版本号 | |  
| TYPE_ | varchar(255) | N | N | | 类型 | |  
| LOCK_EXP_TIME_ | timestamp(3) | N | Y | NULL | | |  
| LOCK_OWNER_ | varchar(255) | N | Y | NULL | | |  
| EXCLUSIVE_ | tinyint(1) | N | Y | NULL | | |  
| EXECUTION_ID_ | varchar(64) | N | Y | NULL | 执行实例ID | |  
| PROCESS_INSTANCE_ID_ | varchar(64) | N | Y | NULL | 流程实例ID | |  
| PROC_DEF_ID_ | varchar(64) | N | Y | NULL | 流程定义ID | |  
| SCOPE_ID_ | varchar(255) | N | Y | NULL | | |  
| SUB_SCOPE_ID_ | varchar(255) | N | Y | NULL | | |  
| SCOPE_TYPE_ | varchar(255) | N | Y | NULL | | |  
| SCOPE_DEFINITION_ID_ | varchar(255) | N | Y | NULL | | |  
| RETRIES_ | int(11) | N | Y | NULL | | |  
| EXCEPTION_STACK_ID_ | varchar(64) | N | Y | NULL | 异常信息ID | |  
| EXCEPTION_MSG_ | varchar(4000) | N | Y | NULL | 异常信息 | |  
| DUEDATE_ | timestamp(3) | N | Y | NULL | 到期时间 | |  
| REPEAT_ | varchar(255) | N | Y | NULL | 重复 | |  
| HANDLER_TYPE_ | varchar(255) | N | Y | NULL | 处理类型 | |  
| HANDLER_CFG_ | varchar(4000) | N | Y | NULL | | |  
| CUSTOM_VALUES_ID_ | varchar(64) | N | Y | NULL | | |  
| CREATE_TIME_ | timestamp(3) | N | Y | NULL | | |  
| TENANT_ID_ | timestamp(3) | N | Y | 空字符串 | | |  

> SQL  

~~~
--
-- 表的结构 `ACT_RU_TIMER_JOB`
--

CREATE TABLE `ACT_RU_TIMER_JOB` (
  `ID_` varchar(64) COLLATE utf8_bin NOT NULL,
  `REV_` int(11) DEFAULT NULL,
  `TYPE_` varchar(255) COLLATE utf8_bin NOT NULL,
  `LOCK_EXP_TIME_` timestamp(3) NULL DEFAULT NULL,
  `LOCK_OWNER_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `EXCLUSIVE_` tinyint(1) DEFAULT NULL,
  `EXECUTION_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `PROCESS_INSTANCE_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `PROC_DEF_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `SCOPE_ID_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `SUB_SCOPE_ID_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `SCOPE_TYPE_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `SCOPE_DEFINITION_ID_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `RETRIES_` int(11) DEFAULT NULL,
  `EXCEPTION_STACK_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `EXCEPTION_MSG_` varchar(4000) COLLATE utf8_bin DEFAULT NULL,
  `DUEDATE_` timestamp(3) NULL DEFAULT NULL,
  `REPEAT_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `HANDLER_TYPE_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `HANDLER_CFG_` varchar(4000) COLLATE utf8_bin DEFAULT NULL,
  `CUSTOM_VALUES_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `CREATE_TIME_` timestamp(3) NULL DEFAULT NULL,
  `TENANT_ID_` varchar(255) COLLATE utf8_bin DEFAULT ''
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_bin;

--
-- 转储表的索引
--

--
-- 表的索引 `ACT_RU_TIMER_JOB`
--
ALTER TABLE `ACT_RU_TIMER_JOB`
  ADD PRIMARY KEY (`ID_`),
  ADD KEY `ACT_IDX_TIMER_JOB_EXCEPTION_STACK_ID` (`EXCEPTION_STACK_ID_`),
  ADD KEY `ACT_IDX_TIMER_JOB_CUSTOM_VALUES_ID` (`CUSTOM_VALUES_ID_`),
  ADD KEY `ACT_IDX_TJOB_SCOPE` (`SCOPE_ID_`,`SCOPE_TYPE_`),
  ADD KEY `ACT_IDX_TJOB_SUB_SCOPE` (`SUB_SCOPE_ID_`,`SCOPE_TYPE_`),
  ADD KEY `ACT_IDX_TJOB_SCOPE_DEF` (`SCOPE_DEFINITION_ID_`,`SCOPE_TYPE_`),
  ADD KEY `ACT_FK_TIMER_JOB_EXECUTION` (`EXECUTION_ID_`),
  ADD KEY `ACT_FK_TIMER_JOB_PROCESS_INSTANCE` (`PROCESS_INSTANCE_ID_`),
  ADD KEY `ACT_FK_TIMER_JOB_PROC_DEF` (`PROC_DEF_ID_`);

--
-- 限制导出的表
--

--
-- 限制表 `ACT_RU_TIMER_JOB`
--
ALTER TABLE `ACT_RU_TIMER_JOB`
  ADD CONSTRAINT `ACT_FK_TIMER_JOB_CUSTOM_VALUES` FOREIGN KEY (`CUSTOM_VALUES_ID_`) REFERENCES `ACT_GE_BYTEARRAY` (`ID_`),
  ADD CONSTRAINT `ACT_FK_TIMER_JOB_EXCEPTION` FOREIGN KEY (`EXCEPTION_STACK_ID_`) REFERENCES `ACT_GE_BYTEARRAY` (`ID_`),
  ADD CONSTRAINT `ACT_FK_TIMER_JOB_EXECUTION` FOREIGN KEY (`EXECUTION_ID_`) REFERENCES `ACT_RU_EXECUTION` (`ID_`),
  ADD CONSTRAINT `ACT_FK_TIMER_JOB_PROCESS_INSTANCE` FOREIGN KEY (`PROCESS_INSTANCE_ID_`) REFERENCES `ACT_RU_EXECUTION` (`ID_`),
  ADD CONSTRAINT `ACT_FK_TIMER_JOB_PROC_DEF` FOREIGN KEY (`PROC_DEF_ID_`) REFERENCES `ACT_RE_PROCDEF` (`ID_`);
COMMIT;
~~~

## ACT_RU_VARIABLE 运行时变量表

| 字段 | 类型 | 是否为主键 | 是否允许为空 | 默认值 | 说明 | 备注 |  
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |  
| ID_ | varchar(64) | Y | N | | 主键 | |  
| REV_ | int(11) | N | Y | NULL | 数据版本号 | |  
| TYPE_ | varchar(255) | N | N | | 参数类型 | 可以是基本的类型，也可以用户自行扩展 |  
| NAME_ | varchar(255) | N | N | | 参数名称 | |  
| EXECUTION_ID_ | varchar(64) | N | Y | NULL | 参数执行ID | |  
| PROC_INST_ID_ | varchar(64) | N | Y | NULL | 流程实例ID | |  
| TASK_ID_ | varchar(64) | N | Y | NULL | 任务ID | |  
| SCOPE_ID_ | varchar(255) | N | Y | NULL | | |  
| SUB_SCOPE_ID_ | varchar(255) | N | Y | NULL | | |  
| SCOPE_TYPE_ | varchar(255) | N | Y | NULL | | |  
| BYTEARRAY_ID_ | varchar(64) | N | Y | NULL | 资源ID | |  
| DOUBLE_ | double | N | Y | NULL | 参数为double，则保存在该字段中 | |  
| LONG_ | bigint(20) | N | Y | NULL | 参数为long，则保存在该字段中 | |  
| TEXT_ | varchar(4000) | N | Y | NULL | 用户保存文本类型的参数值 | |  
| TEXT2_ | varchar(4000) | N | Y | NULL | 用户保存文本类型的参数值	 | |  

> SQL  

~~~
--
-- 表的结构 `ACT_RU_VARIABLE`
--

CREATE TABLE `ACT_RU_VARIABLE` (
  `ID_` varchar(64) COLLATE utf8_bin NOT NULL,
  `REV_` int(11) DEFAULT NULL,
  `TYPE_` varchar(255) COLLATE utf8_bin NOT NULL,
  `NAME_` varchar(255) COLLATE utf8_bin NOT NULL,
  `EXECUTION_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `PROC_INST_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `TASK_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `SCOPE_ID_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `SUB_SCOPE_ID_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `SCOPE_TYPE_` varchar(255) COLLATE utf8_bin DEFAULT NULL,
  `BYTEARRAY_ID_` varchar(64) COLLATE utf8_bin DEFAULT NULL,
  `DOUBLE_` double DEFAULT NULL,
  `LONG_` bigint(20) DEFAULT NULL,
  `TEXT_` varchar(4000) COLLATE utf8_bin DEFAULT NULL,
  `TEXT2_` varchar(4000) COLLATE utf8_bin DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_bin;

--
-- 转储表的索引
--

--
-- 表的索引 `ACT_RU_VARIABLE`
--
ALTER TABLE `ACT_RU_VARIABLE`
  ADD PRIMARY KEY (`ID_`),
  ADD KEY `ACT_IDX_RU_VAR_SCOPE_ID_TYPE` (`SCOPE_ID_`,`SCOPE_TYPE_`),
  ADD KEY `ACT_IDX_RU_VAR_SUB_ID_TYPE` (`SUB_SCOPE_ID_`,`SCOPE_TYPE_`),
  ADD KEY `ACT_FK_VAR_BYTEARRAY` (`BYTEARRAY_ID_`),
  ADD KEY `ACT_IDX_VARIABLE_TASK_ID` (`TASK_ID_`),
  ADD KEY `ACT_FK_VAR_EXE` (`EXECUTION_ID_`),
  ADD KEY `ACT_FK_VAR_PROCINST` (`PROC_INST_ID_`);

--
-- 限制导出的表
--

--
-- 限制表 `ACT_RU_VARIABLE`
--
ALTER TABLE `ACT_RU_VARIABLE`
  ADD CONSTRAINT `ACT_FK_VAR_BYTEARRAY` FOREIGN KEY (`BYTEARRAY_ID_`) REFERENCES `ACT_GE_BYTEARRAY` (`ID_`),
  ADD CONSTRAINT `ACT_FK_VAR_EXE` FOREIGN KEY (`EXECUTION_ID_`) REFERENCES `ACT_RU_EXECUTION` (`ID_`),
  ADD CONSTRAINT `ACT_FK_VAR_PROCINST` FOREIGN KEY (`PROC_INST_ID_`) REFERENCES `ACT_RU_EXECUTION` (`ID_`);
COMMIT;
~~~
