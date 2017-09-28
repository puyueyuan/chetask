## 1.程序设计流程图

![](/assets/清查系统.png)

## 2.数据库设计

### 1.任务表

CREATE TABLE \`checktask\_new\_obj\` \(

\`id\` bigint\(10\) unsigned NOT NULL AUTO\_INCREMENT,

\`search\_type\` tinyint\(1\) NOT NULL,

\`stime\` timestamp NOT NULL DEFAULT '0000-00-00 00:00:00',

\`etime\` timestamp NOT NULL DEFAULT '0000-00-00 00:00:00',

\`status\` tinyint\(1\) NOT NULL DEFAULT '0',

\`staff\` char\(40\) COLLATE utf8\_bin NOT NULL,

\`filename\` varchar\(200\) COLLATE utf8\_bin NOT NULL DEFAULT '',

\`items\` varchar\(100\) COLLATE utf8\_bin NOT NULL DEFAULT '',

\`created\_at\` timestamp NOT NULL DEFAULT CURRENT\_TIMESTAMP,

PRIMARY KEY \(\`id\`\)

\) ENGINE=InnoDB AUTO\_INCREMENT=7 DEFAULT CHARSET=utf8 COLLATE=utf8\_bin;

表结构说明：

1. search\_type 为搜索类型（单词,关键词id，文件）。
2. stime，etime为任务开始结束时间。

3. status为任务状态0 1 2 分别为导入中，审核未完成，可下载。

4. staff为操作人。

5. filename 为下载文件名称。

6. items 为搜索条件详情格式为（全部元素\|全部微博\|周星驰）。

7. created\_at 为任务创建时间。

8. id为任务表task—\_id

### 2.任务详情表

CREATE TABLE \`checktask\_new\_details\` \(

\`id\` int\(10\) unsigned NOT NULL AUTO\_INCREMENT COMMENT '??id',

\`mid\` bigint\(32\) unsigned NOT NULL DEFAULT '0' COMMENT '????id',

\`ctime\` timestamp NOT NULL DEFAULT '2000-01-01 00:00:00' COMMENT '??????',

\`uid\` bigint\(20\) unsigned NOT NULL DEFAULT '0' COMMENT '??UID',

\`verified\_type\` tinyint\(3\) NOT NULL DEFAULT '-1' COMMENT '????',

\`head\_level\` tinyint\(3\) unsigned NOT NULL DEFAULT '0' COMMENT '????',

\`status\` smallint\(5\) unsigned NOT NULL DEFAULT '0' COMMENT '????:0???,12????...',

\`task\_id\` bigint\(10\) NOT NULL DEFAULT '0',

\`check\_status\` tinyint\(4\) NOT NULL DEFAULT '0',

PRIMARY KEY \(\`id\`\),

KEY \`idx\_taskid\_status\_head\_verified\` \(\`verified\_type\`,\`head\_level\`,\`status\`,\`task\_id\`,\`check\_status\`\) USING BTREE

\) ENGINE=InnoDB AUTO\_INCREMENT=5016 DEFAULT CHARSET=utf8 COMMENT='?????-????????';

