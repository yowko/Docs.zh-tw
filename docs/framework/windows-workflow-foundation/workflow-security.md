---
title: 工作流程安全性
ms.date: 03/30/2017
helpviewer_keywords:
- programming [WF], workflow security
ms.assetid: d712a566-f435-44c0-b8c0-49298e84b114
ms.openlocfilehash: d2d8556b1ed2ac0a2b030a88d6bfc0ad48ed6f5c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557511"
---
# <a name="workflow-security"></a><span data-ttu-id="9981e-102">工作流程安全性</span><span class="sxs-lookup"><span data-stu-id="9981e-102">Workflow Security</span></span>
<span data-ttu-id="9981e-103">Windows Workflow Foundation (WF) 與數種不同的技術整合，例如 Microsoft SQL Server 和 Windows Communication Foundation (WCF) 。</span><span class="sxs-lookup"><span data-stu-id="9981e-103">Windows Workflow Foundation (WF) is integrated with several different technologies, such as Microsoft SQL Server and Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="9981e-104">如果與這些技術互動的方式不適當，可能會造成工作流程上的安全性問題。</span><span class="sxs-lookup"><span data-stu-id="9981e-104">Interacting with these technologies may introduce security issues into your workflow if done improperly.</span></span>

## <a name="persistence-security-concerns"></a><span data-ttu-id="9981e-105">持續性安全性考量</span><span class="sxs-lookup"><span data-stu-id="9981e-105">Persistence Security Concerns</span></span>

1. <span data-ttu-id="9981e-106">使用 <xref:System.Activities.Statements.Delay> 活動和持續性的工作流程需要由服務重新啟動。</span><span class="sxs-lookup"><span data-stu-id="9981e-106">Workflows that use a <xref:System.Activities.Statements.Delay> activity and persistence need to be reactivated by a service.</span></span> <span data-ttu-id="9981e-107">Windows AppFabric 使用工作流程管理服務 (WMS) 來重新啟動具有過期計時器的工作流程。</span><span class="sxs-lookup"><span data-stu-id="9981e-107">Windows AppFabric uses the Workflow Management Service (WMS) to reactivate workflows with expired timers.</span></span> <span data-ttu-id="9981e-108">WMS 會建立 <xref:System.ServiceModel.WorkflowServiceHost> 以裝載重新啟動的工作流程。</span><span class="sxs-lookup"><span data-stu-id="9981e-108">WMS creates a <xref:System.ServiceModel.WorkflowServiceHost> to host the reactivated workflow.</span></span> <span data-ttu-id="9981e-109">如果 WMS 服務停止，當工作流程的計時器過期，保存的工作流程將不會重新啟動。</span><span class="sxs-lookup"><span data-stu-id="9981e-109">If the WMS service is stopped, persisted workflows will not be reactivated when their timers expire.</span></span>

2. <span data-ttu-id="9981e-110">永久性執行個體的存取應受到保護，免受惡意的外部實體存取應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="9981e-110">Access to durable instancing should be protected against malicious entities external to the application domain.</span></span> <span data-ttu-id="9981e-111">此外，開發人員應確保惡意程式碼不能與永久性執行個體程式碼在同一個應用程式定義域中執行。</span><span class="sxs-lookup"><span data-stu-id="9981e-111">In addition, developers should ensure that malicious code can't be executed in the same application domain as the durable instancing code.</span></span>

3. <span data-ttu-id="9981e-112">不應該以更高 (管理員) 權限執行永久性執行個體。</span><span class="sxs-lookup"><span data-stu-id="9981e-112">Durable instancing should not be run with elevated (Administrator) permissions.</span></span>

4. <span data-ttu-id="9981e-113">應該保護位於應用程式定義域之外，正在接受處理的資料。</span><span class="sxs-lookup"><span data-stu-id="9981e-113">Data being processed outside the application domain should be protected.</span></span>

5. <span data-ttu-id="9981e-114">需要安全性隔離的應用程式不應共用結構描述抽象的同一執行個體。</span><span class="sxs-lookup"><span data-stu-id="9981e-114">Applications that require security isolation should not share the same instance of the schema abstraction.</span></span> <span data-ttu-id="9981e-115">此類應用程式應使用不同的存放區提供者，或是已設定要使用不同存放區具現化的存放區提供者。</span><span class="sxs-lookup"><span data-stu-id="9981e-115">Such applications should use different store providers, or store providers configured to use different store instantiations.</span></span>

## <a name="sql-server-security-concerns"></a><span data-ttu-id="9981e-116">SQL Server 安全性考量</span><span class="sxs-lookup"><span data-stu-id="9981e-116">SQL Server Security Concerns</span></span>

- <span data-ttu-id="9981e-117">當使用大量子活動、位置、書籤、主機延伸或範圍時，或當使用有大量承載的書籤時，可能會耗盡記憶體，或在持續性期間過度配置不當的資料庫空間。</span><span class="sxs-lookup"><span data-stu-id="9981e-117">When large numbers of child activities, locations, bookmarks, host extensions, or scopes are used, or when bookmarks with very large payloads are used, memory can be exhausted, or undue amounts of database space can be allocated during persistence.</span></span> <span data-ttu-id="9981e-118">可使用物件層級與資料庫層級的安全性來減少這種情況。</span><span class="sxs-lookup"><span data-stu-id="9981e-118">This can be mitigated by using object-level and database-level security.</span></span>

- <span data-ttu-id="9981e-119">使用 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 時，必須保護執行個體存放區的安全。</span><span class="sxs-lookup"><span data-stu-id="9981e-119">When using <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, the instance store must be secured.</span></span>

- <span data-ttu-id="9981e-120">應加密執行個體存放區中的敏感資料。</span><span class="sxs-lookup"><span data-stu-id="9981e-120">Sensitive data in the instance store should be encrypted.</span></span> <span data-ttu-id="9981e-121">如需詳細資訊，請參閱 [SQL Server 加密](/sql/relational-databases/security/encryption/sql-server-encryption)。</span><span class="sxs-lookup"><span data-stu-id="9981e-121">For more information, see [SQL Server Encryption](/sql/relational-databases/security/encryption/sql-server-encryption).</span></span>

- <span data-ttu-id="9981e-122">因為資料庫連接字串通常包含在組態檔中，應該使用 Windows 層級的安全性 (ACL) 以確保組態檔 (通常為 Web.Config) 是安全的，且登入和密碼資訊沒有包含在連接字串中。</span><span class="sxs-lookup"><span data-stu-id="9981e-122">Since the database connection string is often included in a configuration file, windows-level security (ACL) should be used to ensure that the configuration file (Web.Config usually) is secure, and that login and password information are not included in the connection string.</span></span> <span data-ttu-id="9981e-123">資料庫和 Web 伺服器之間應改用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="9981e-123">Windows authentication should be used between the database and the web server instead.</span></span>

## <a name="considerations-for-workflowservicehost"></a><span data-ttu-id="9981e-124">WorkflowServiceHost 的考量</span><span class="sxs-lookup"><span data-stu-id="9981e-124">Considerations for WorkflowServiceHost</span></span>

- <span data-ttu-id="9981e-125">Windows Communication Foundation 應保護工作流程中所使用的 WCF) 端點 (。</span><span class="sxs-lookup"><span data-stu-id="9981e-125">Windows Communication Foundation (WCF) endpoints used in workflows should be secured.</span></span> <span data-ttu-id="9981e-126">如需詳細資訊，請參閱 [WCF 安全性概觀](../wcf/feature-details/security-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="9981e-126">For more information, see [WCF Security Overview](../wcf/feature-details/security-overview.md).</span></span>

- <span data-ttu-id="9981e-127">可使用 <xref:System.ServiceModel.ServiceAuthorizationManager> 實作主機層級授權。</span><span class="sxs-lookup"><span data-stu-id="9981e-127">Host-level authorization can be implemented by using <xref:System.ServiceModel.ServiceAuthorizationManager>.</span></span> <span data-ttu-id="9981e-128">請參閱 how [To：為服務建立自訂授權管理員](../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md) 以取得詳細資料。</span><span class="sxs-lookup"><span data-stu-id="9981e-128">See [How To: Create a Custom Authorization Manager for a Service](../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md) for details.</span></span>

- <span data-ttu-id="9981e-129">傳入訊息的 ServiceSecurityContext 也可在工作流程內取得，方法是存取 OperationContext。</span><span class="sxs-lookup"><span data-stu-id="9981e-129">The ServiceSecurityContext for the incoming message is also available from within workflow by accessing OperationContext.</span></span>

## <a name="wf-security-pack-ctp"></a><span data-ttu-id="9981e-130">WF Security Pack CTP</span><span class="sxs-lookup"><span data-stu-id="9981e-130">WF Security Pack CTP</span></span>
 <span data-ttu-id="9981e-131">Microsoft WF Security Pack 社區技術預覽版 (CTP) 1 是一組活動及其執行方式，以[.NET Framework 4](/previous-versions/dotnet/netframework-4.0/w0x726c2(v=vs.100)) (WF 4) 和[Windows IDENTITY Foundation (WIF) ](/previous-versions/dotnet/framework/security/index)中的[Windows Workflow Foundation](index.md)為基礎。</span><span class="sxs-lookup"><span data-stu-id="9981e-131">The Microsoft WF Security Pack community technology preview (CTP) 1 is a set of activities and their implementation based on [Windows Workflow Foundation](index.md) in [.NET Framework 4](/previous-versions/dotnet/netframework-4.0/w0x726c2(v=vs.100)) (WF 4) and [Windows Identity Foundation (WIF)](/previous-versions/dotnet/framework/security/index).</span></span> <span data-ttu-id="9981e-132">Microsoft WF Security Pack CTP 1 包含活動及其設計工具，說明如何使用工作流程輕鬆進行各種安全性相關的案例，包括：</span><span class="sxs-lookup"><span data-stu-id="9981e-132">The Microsoft WF Security Pack CTP 1 contains both activities and their designers which illustrate how to easily enable various security-related scenarios using workflow, including:</span></span>

1. <span data-ttu-id="9981e-133">在工作流程中模擬用戶端身分識別</span><span class="sxs-lookup"><span data-stu-id="9981e-133">Impersonating a client identity in the workflow</span></span>

2. <span data-ttu-id="9981e-134">工作流程中的授權，例如 PrincipalPermission 和宣告的驗證</span><span class="sxs-lookup"><span data-stu-id="9981e-134">In-workflow authorization, such as PrincipalPermission and validation of Claims</span></span>

3. <span data-ttu-id="9981e-135">通過驗證的傳訊，其使用工作流程中指定的 ClientCredentials，例如使用者名稱/密碼或從安全性權杖服務 (STS) 擷取的權杖。</span><span class="sxs-lookup"><span data-stu-id="9981e-135">Authenticated messaging using ClientCredentials specified in the workflow, such as username/password or a token retrieved from a Security Token Service (STS)</span></span>

4. <span data-ttu-id="9981e-136">使用 WS-Trust ActAs 將用戶端安全性權杖傳到後端服務 (以宣告為基礎的委派)</span><span class="sxs-lookup"><span data-stu-id="9981e-136">Flowing a client security token to a back-end service (claims-based delegation) using WS-Trust ActAs</span></span>

<span data-ttu-id="9981e-137">如需詳細資訊及下載 WF Security Pack CTP，請參閱： [Wf Security PACK ctp](https://archive.codeplex.com/?p=wf)</span><span class="sxs-lookup"><span data-stu-id="9981e-137">For more information and to download the WF Security Pack CTP, see: [WF Security Pack CTP](https://archive.codeplex.com/?p=wf)</span></span>
