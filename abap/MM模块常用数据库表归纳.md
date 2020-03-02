 # MM模块常用数据库表归纳

## 基础信息

| TABLE | DESCRIPTION            |
| ----- | ---------------------- |
| T001L | 仓储地点               |
| T001W | 工厂/分支机构          |
| T024  | 采购组                 |
| T024E | 采购组织               |
| T024W | 工厂的有效采购组织     |
| T024Z | 采购组织               |
| T023  | 物料组                 |
| T156  | 移动类型               |
| T157H | 移动类型的帮助文本     |
| MLAN  | 物料的税分类           |
| LFA1  | 供应商主数据(一般地区) |
| LFB1  | 供应商主数据(公司代码) |
| LFC1  | 供应商主数据(业务额)   |



## 物料凭证

| TABLE | DESCRIPTION |
| ----- | ----------- |
| MKPF  | 抬头        |
| MSEG  | 行项目      |



## 采购订单

| TABLE | DESCRIPTION |
| ----- | ----------- |
| EBAN  | 采购申请    |
| EKKO  | 抬头        |
| EKPO  | 行项目      |



## 销售订单

| TABLE | DESCRIPTION |
| ----- | ----------- |
| VBKA  | 抬头        |
| VBAP  | 行项目      |



## 交货订单

| TABLE | DESCRIPTION |
| ----- | ----------- |
| LIKP  | 抬头        |
| LIPS  | 行项        |
| VTTK  | 装运抬头    |
|       |             |



## 价格数据

| TABLE | DESCRIPTION |
| ----- | ----------- |
| KNOH  | 抬头        |
| KNOP  | 行项        |
| KNOV  | 单据的价格  |



## 发票

| TABLE | DESCRIPTION |
| ----- | ----------- |
| VBRK  | 抬头        |
| VBRP  | 行项        |

