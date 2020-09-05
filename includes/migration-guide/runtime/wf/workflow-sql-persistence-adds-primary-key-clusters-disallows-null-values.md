---
ms.openlocfilehash: cb9305f623044233082286863d2f2d2c7e9d665a
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497358"
---
### <a name="workflow-sql-persistence-adds-primary-key-clusters-and-disallows-null-values-in-some-columns"></a>工作流程 SQL 持續性會新增叢集主索引鍵，且在某些資料行中不允許有 Null 值

#### <a name="details"></a>詳細資料

從 .NET Framework 4.7 開始，SqlWorkflowInstanceStoreSchema.sql 指令碼針對 SQL 工作流程執行個體存放區 (SWIS) 所建立的資料表使用叢集主索引鍵。 因此，識別不支援 <code>null</code> 值。 SWIS 的作業不會受到這項變更影響。 已進行更新以支援 SQL Server 異動複寫。

#### <a name="suggestion"></a>建議

必須將 SQL 檔案 SqlWorkflowInstanceStoreSchemaUpgrade.sql 套用到現有安裝，才能體驗這項變更。 新的資料庫安裝將會自動進行此變更。

| 名稱    | 值       |
|:--------|:------------|
| 範圍   |Edge|
|版本|4.7|
|類型|執行階段|

#### <a name="affected-apis"></a>受影響的 API

無法透過 API 分析偵測。

<!--

#### Affected APIs

Not detectable via API analysis.

-->
