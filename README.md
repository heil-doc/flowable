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
| ACT_EVT_LOG | | |
| ACT_FO_DATABASECHANGELOG | | |
| ACT_FO_DATABASECHANGELOGLOCK | | |
| ACT_FO_FORM_DEFINITION | | |
| ACT_FO_FORM_DEPLOYMENT | | |
| ACT_FO_FORM_INSTANCE | | |
| ACT_FO_FORM_RESOURCE | | |
| ACT_GE_BYTEARRAY | | |
| ACT_GE_PROPERTY | | |
| ACT_HI_ACTINST | | |
| ACT_HI_ATTACHMENT | | |
| ACT_HI_COMMENT | | |
| ACT_HI_DETAIL | | |
| ACT_HI_IDENTITYLINK | | |
| ACT_HI_PROCINST | | |
| ACT_HI_TASKINST | | |
| ACT_HI_VARINST | | |
| ACT_ID_BYTEARRAY | | |
| ACT_ID_GROUP | | |
| ACT_ID_INFO | | |
| ACT_ID_MEMBERSHIP | | |
| ACT_ID_PRIV | | |
| ACT_ID_PRIV_MAPPING | | |
| ACT_ID_PROPERTY | | |
| ACT_ID_TOKEN | | |
| ACT_ID_USER | | |
| ACT_PROCDEF_INFO | | |
| ACT_RE_DEPLOYMENT | | |
| ACT_RE_MODEL | | |
| ACT_RE_PROCDEF | | |
| ACT_RU_DEADLETTER_JOB | | |
| ACT_RU_EVENT_SUBSCR | | |
| ACT_RU_EXECUTION | | |
| ACT_RU_HISTORY_JOB | | |
| ACT_RU_IDENTITYLINK | | |
| ACT_RU_JOB | | |
| ACT_RU_SUSPENDED_JOB | | |
| ACT_RU_TASK | | |
| ACT_RU_TIMER_JOB | | |
| ACT_RU_VARIABLE | | |

# 三、数据字典

## ACT_CMMN_CASEDEF

| 字段 | 类型 | 是否为主键 | 是否允许为空 | 默认值 | 说明 | 备注 |  
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |  
| ID_ | varchar(255) | Y | N | 主键 | | |  
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
| ID_ | varchar(255) | Y | N | 主键 | | |  
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
| ID_ | int(11) | Y | N | 主键 | | |  
| LOCKED | bit(1) | N | N | | | |  
| LOCKGRANTED | datetime | N | Y | NULL | | |  
| LOCKEDBY | varchar(255) | N | Y | NULL | | |  

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
| ID_ | varchar(255) | Y | N | 主键 | | |  
| NAME_ | varchar(255) | N | Y | NULL | 名称 | |  
| CATEGORY_ | varchar(255) | N | Y | NULL | 类别 | |  
| KEY_ | varchar(255) | N | Y | NULL | | |  
| DEPLOY_TIME_ | datetime | N | Y | NULL | 部署时间 | |  
| PARENT_DEPLOYMENT_ID_ | varchar(255) | N | Y | NULL | | |  
| TENANT_ID_ | varchar(255) | N | Y |  | 空字符串 | |  

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
| ID_ | varchar(255) | Y | N | 主键 | | |  
| NAME_ | varchar(255) | N | Y | NULL | 名称 | |  
| DEPLOYMENT_ID_ | varchar(255) | N | Y | NULL | 关联ACT_DMN_DEPLOYMENT表ID | |  
| RESOURCE_BYTES_ | longblob | N | Y | | 源码 | |  
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
| ID_ | varchar(255) | Y | N | 主键 | | |  
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
| ID_ | varchar(255) | Y | N | 主键 | | |  
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
| ID_ | varchar(255) | Y | N | 主键 | | |  
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
| ID_ | varchar(255) | Y | N | 主键 | | |  
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
| ID_ | varchar(255) | Y | N | 主键 | | |  
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
| ID_ | varchar(255) | Y | N | 主键 | | |  
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
