---
ms.openlocfilehash: 9e98d3bca645cf82bf4fe99160dd096b0e274ef7
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760405"
---
### <a name="workflow-sql-persistence-adds-primary-key-clusters-and-disallows-null-values-in-some-columns"></a><span data-ttu-id="0e8ea-101">工作流程 SQL 持續性會新增叢集主索引鍵，且在某些資料行中不允許有 Null 值</span><span class="sxs-lookup"><span data-stu-id="0e8ea-101">Workflow SQL persistence adds primary key clusters and disallows null values in some columns</span></span>

|   |   |
|---|---|
|<span data-ttu-id="0e8ea-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="0e8ea-102">Details</span></span>|<span data-ttu-id="0e8ea-103">從 .NET Framework 4.7 開始，SqlWorkflowInstanceStoreSchema.sql 指令碼針對 SQL 工作流程執行個體存放區 (SWIS) 所建立的資料表使用叢集主索引鍵。</span><span class="sxs-lookup"><span data-stu-id="0e8ea-103">Starting with the .NET Framework 4.7, the tables created for the SQL Workflow Instance Store (SWIS) by the SqlWorkflowInstanceStoreSchema.sql script use clustered primary keys.</span></span> <span data-ttu-id="0e8ea-104">因此，識別不支援 <code>null</code> 值。</span><span class="sxs-lookup"><span data-stu-id="0e8ea-104">Because of this, identities do not support <code>null</code> values.</span></span> <span data-ttu-id="0e8ea-105">SWIS 的作業不會受到這項變更影響。</span><span class="sxs-lookup"><span data-stu-id="0e8ea-105">The operation of SWIS is not impacted by this change.</span></span> <span data-ttu-id="0e8ea-106">已進行更新以支援 SQL Server 異動複寫。</span><span class="sxs-lookup"><span data-stu-id="0e8ea-106">The updates were made to support SQL Server Transactional Replication.</span></span>|
|<span data-ttu-id="0e8ea-107">建議</span><span class="sxs-lookup"><span data-stu-id="0e8ea-107">Suggestion</span></span>|<span data-ttu-id="0e8ea-108">必須將 SQL 檔案 SqlWorkflowInstanceStoreSchemaUpgrade.sql 套用到現有安裝，才能體驗這項變更。</span><span class="sxs-lookup"><span data-stu-id="0e8ea-108">The SQL file SqlWorkflowInstanceStoreSchemaUpgrade.sql must be applied to existing installations in order to experience this change.</span></span> <span data-ttu-id="0e8ea-109">新的資料庫安裝將會自動進行此變更。</span><span class="sxs-lookup"><span data-stu-id="0e8ea-109">New database installations will automatically have the change.</span></span>|
|<span data-ttu-id="0e8ea-110">範圍</span><span class="sxs-lookup"><span data-stu-id="0e8ea-110">Scope</span></span>|<span data-ttu-id="0e8ea-111">Edge</span><span class="sxs-lookup"><span data-stu-id="0e8ea-111">Edge</span></span>|
|<span data-ttu-id="0e8ea-112">版本</span><span class="sxs-lookup"><span data-stu-id="0e8ea-112">Version</span></span>|<span data-ttu-id="0e8ea-113">4.7</span><span class="sxs-lookup"><span data-stu-id="0e8ea-113">4.7</span></span>|
|<span data-ttu-id="0e8ea-114">類型</span><span class="sxs-lookup"><span data-stu-id="0e8ea-114">Type</span></span>|<span data-ttu-id="0e8ea-115">執行階段</span><span class="sxs-lookup"><span data-stu-id="0e8ea-115">Runtime</span></span>|

