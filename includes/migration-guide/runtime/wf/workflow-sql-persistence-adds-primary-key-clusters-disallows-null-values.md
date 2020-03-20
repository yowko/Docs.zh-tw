---
ms.openlocfilehash: 566a3e0455b30e901b09be88b4256ffe67bdc2b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "67802562"
---
### <a name="workflow-sql-persistence-adds-primary-key-clusters-and-disallows-null-values-in-some-columns"></a><span data-ttu-id="099d5-101">工作流程 SQL 持續性會新增叢集主索引鍵，且在某些資料行中不允許有 Null 值</span><span class="sxs-lookup"><span data-stu-id="099d5-101">Workflow SQL persistence adds primary key clusters and disallows null values in some columns</span></span>

|   |   |
|---|---|
|<span data-ttu-id="099d5-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="099d5-102">Details</span></span>|<span data-ttu-id="099d5-103">從 .NET Framework 4.7 開始，SqlWorkflowInstanceStoreSchema.sql 指令碼針對 SQL 工作流程執行個體存放區 (SWIS) 所建立的資料表使用叢集主索引鍵。</span><span class="sxs-lookup"><span data-stu-id="099d5-103">Starting with the .NET Framework 4.7, the tables created for the SQL Workflow Instance Store (SWIS) by the SqlWorkflowInstanceStoreSchema.sql script use clustered primary keys.</span></span> <span data-ttu-id="099d5-104">因此，識別不支援 <code>null</code> 值。</span><span class="sxs-lookup"><span data-stu-id="099d5-104">Because of this, identities do not support <code>null</code> values.</span></span> <span data-ttu-id="099d5-105">SWIS 的作業不會受到這項變更影響。</span><span class="sxs-lookup"><span data-stu-id="099d5-105">The operation of SWIS is not impacted by this change.</span></span> <span data-ttu-id="099d5-106">已進行更新以支援 SQL Server 異動複寫。</span><span class="sxs-lookup"><span data-stu-id="099d5-106">The updates were made to support SQL Server Transactional Replication.</span></span>|
|<span data-ttu-id="099d5-107">建議</span><span class="sxs-lookup"><span data-stu-id="099d5-107">Suggestion</span></span>|<span data-ttu-id="099d5-108">必須將 SQL 檔案 SqlWorkflowInstanceStoreSchemaUpgrade.sql 套用到現有安裝，才能體驗這項變更。</span><span class="sxs-lookup"><span data-stu-id="099d5-108">The SQL file SqlWorkflowInstanceStoreSchemaUpgrade.sql must be applied to existing installations in order to experience this change.</span></span> <span data-ttu-id="099d5-109">新的資料庫安裝將會自動進行此變更。</span><span class="sxs-lookup"><span data-stu-id="099d5-109">New database installations will automatically have the change.</span></span>|
|<span data-ttu-id="099d5-110">影響範圍</span><span class="sxs-lookup"><span data-stu-id="099d5-110">Scope</span></span>|<span data-ttu-id="099d5-111">Edge</span><span class="sxs-lookup"><span data-stu-id="099d5-111">Edge</span></span>|
|<span data-ttu-id="099d5-112">版本</span><span class="sxs-lookup"><span data-stu-id="099d5-112">Version</span></span>|<span data-ttu-id="099d5-113">4.7</span><span class="sxs-lookup"><span data-stu-id="099d5-113">4.7</span></span>|
|<span data-ttu-id="099d5-114">類型</span><span class="sxs-lookup"><span data-stu-id="099d5-114">Type</span></span>|<span data-ttu-id="099d5-115">執行階段</span><span class="sxs-lookup"><span data-stu-id="099d5-115">Runtime</span></span>|
