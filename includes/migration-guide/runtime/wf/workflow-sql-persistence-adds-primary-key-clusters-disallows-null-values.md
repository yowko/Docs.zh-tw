---
ms.openlocfilehash: cb9305f623044233082286863d2f2d2c7e9d665a
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497358"
---
### <a name="workflow-sql-persistence-adds-primary-key-clusters-and-disallows-null-values-in-some-columns"></a><span data-ttu-id="45b58-101">工作流程 SQL 持續性會新增叢集主索引鍵，且在某些資料行中不允許有 Null 值</span><span class="sxs-lookup"><span data-stu-id="45b58-101">Workflow SQL persistence adds primary key clusters and disallows null values in some columns</span></span>

#### <a name="details"></a><span data-ttu-id="45b58-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="45b58-102">Details</span></span>

<span data-ttu-id="45b58-103">從 .NET Framework 4.7 開始，SqlWorkflowInstanceStoreSchema.sql 指令碼針對 SQL 工作流程執行個體存放區 (SWIS) 所建立的資料表使用叢集主索引鍵。</span><span class="sxs-lookup"><span data-stu-id="45b58-103">Starting with the .NET Framework 4.7, the tables created for the SQL Workflow Instance Store (SWIS) by the SqlWorkflowInstanceStoreSchema.sql script use clustered primary keys.</span></span> <span data-ttu-id="45b58-104">因此，識別不支援 <code>null</code> 值。</span><span class="sxs-lookup"><span data-stu-id="45b58-104">Because of this, identities do not support <code>null</code> values.</span></span> <span data-ttu-id="45b58-105">SWIS 的作業不會受到這項變更影響。</span><span class="sxs-lookup"><span data-stu-id="45b58-105">The operation of SWIS is not impacted by this change.</span></span> <span data-ttu-id="45b58-106">已進行更新以支援 SQL Server 異動複寫。</span><span class="sxs-lookup"><span data-stu-id="45b58-106">The updates were made to support SQL Server Transactional Replication.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="45b58-107">建議</span><span class="sxs-lookup"><span data-stu-id="45b58-107">Suggestion</span></span>

<span data-ttu-id="45b58-108">必須將 SQL 檔案 SqlWorkflowInstanceStoreSchemaUpgrade.sql 套用到現有安裝，才能體驗這項變更。</span><span class="sxs-lookup"><span data-stu-id="45b58-108">The SQL file SqlWorkflowInstanceStoreSchemaUpgrade.sql must be applied to existing installations in order to experience this change.</span></span> <span data-ttu-id="45b58-109">新的資料庫安裝將會自動進行此變更。</span><span class="sxs-lookup"><span data-stu-id="45b58-109">New database installations will automatically have the change.</span></span>

| <span data-ttu-id="45b58-110">名稱</span><span class="sxs-lookup"><span data-stu-id="45b58-110">Name</span></span>    | <span data-ttu-id="45b58-111">值</span><span class="sxs-lookup"><span data-stu-id="45b58-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="45b58-112">範圍</span><span class="sxs-lookup"><span data-stu-id="45b58-112">Scope</span></span>   |<span data-ttu-id="45b58-113">Edge</span><span class="sxs-lookup"><span data-stu-id="45b58-113">Edge</span></span>|
|<span data-ttu-id="45b58-114">版本</span><span class="sxs-lookup"><span data-stu-id="45b58-114">Version</span></span>|<span data-ttu-id="45b58-115">4.7</span><span class="sxs-lookup"><span data-stu-id="45b58-115">4.7</span></span>|
|<span data-ttu-id="45b58-116">類型</span><span class="sxs-lookup"><span data-stu-id="45b58-116">Type</span></span>|<span data-ttu-id="45b58-117">執行階段</span><span class="sxs-lookup"><span data-stu-id="45b58-117">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="45b58-118">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="45b58-118">Affected APIs</span></span>

<span data-ttu-id="45b58-119">無法透過 API 分析偵測。</span><span class="sxs-lookup"><span data-stu-id="45b58-119">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
