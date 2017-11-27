---
title: "SQL Server 安全性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9053724d-a1fb-4f0f-b9dc-7f6dd893e8ff
caps.latest.revision: "8"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 4f41a794916c63672ca0c844f086629f77b90aa0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="sql-server-security"></a><span data-ttu-id="120e0-102">SQL Server 安全性</span><span class="sxs-lookup"><span data-stu-id="120e0-102">SQL Server Security</span></span>
[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]<span data-ttu-id="120e0-103"> 具有許多功能，可支援安全資料庫應用程式的建立。</span><span class="sxs-lookup"><span data-stu-id="120e0-103"> has many features that support creating secure database applications.</span></span>  
  
 <span data-ttu-id="120e0-104">資料竊取或破壞等一般的安全性考量，則適用於所有的 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 版本。</span><span class="sxs-lookup"><span data-stu-id="120e0-104">Common security considerations, such as data theft or vandalism, apply regardless of the version of [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] you are using.</span></span> <span data-ttu-id="120e0-105">資料完整性也應視為安全性問題。</span><span class="sxs-lookup"><span data-stu-id="120e0-105">Data integrity should also be considered as a security issue.</span></span> <span data-ttu-id="120e0-106">如果資料未受保護，可以對其進行臨機操作 (Ad Hoc)，或用能夠用錯誤的值不小心或惡意地加以修改或全部刪除，資料就可能變得毫無價值。</span><span class="sxs-lookup"><span data-stu-id="120e0-106">If data is not protected, it is possible that it could become worthless if ad hoc data manipulation is permitted and the data is inadvertently or maliciously modified with incorrect values or deleted entirely.</span></span> <span data-ttu-id="120e0-107">此外，也經常會有必須遵循的法律需求，例如機密資訊的正確儲存方式等。</span><span class="sxs-lookup"><span data-stu-id="120e0-107">In addition, there are often legal requirements that must be adhered to, such as the correct storage of confidential information.</span></span> <span data-ttu-id="120e0-108">依照特定管轄區適用的法律而定，某些類型的個人資料可能完全不得儲存。</span><span class="sxs-lookup"><span data-stu-id="120e0-108">Storing some kinds of personal data is proscribed entirely, depending on the laws that apply in a particular jurisdiction.</span></span>  
  
 <span data-ttu-id="120e0-109">每個 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 版本和每個 Windows 版本一樣都具有不同的安全性功能，而越新的版本功能越強。</span><span class="sxs-lookup"><span data-stu-id="120e0-109">Each version of [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] has different security features, as does each version of Windows, with later versions having enhanced functionality over earlier ones.</span></span> <span data-ttu-id="120e0-110">單靠安全性功能並不足以確保資料庫應用程式的安全，瞭解這點是很重要的。</span><span class="sxs-lookup"><span data-stu-id="120e0-110">It is important to understand that security features alone cannot guarantee a secure database application.</span></span> <span data-ttu-id="120e0-111">每個資料庫應用程式的需求、執行環境、部署模型、實體位置和使用者族群都有其獨特性。</span><span class="sxs-lookup"><span data-stu-id="120e0-111">Each database application is unique in its requirements, execution environment, deployment model, physical location, and user population.</span></span> <span data-ttu-id="120e0-112">某些具有本機範圍的應用程式可能只需要最低的安全性，而其他的本機應用程式或透過 Internet 部署的應用程式卻可能需要嚴謹的安全性措施及持續不斷的監控和評估。</span><span class="sxs-lookup"><span data-stu-id="120e0-112">Some applications that are local in scope may need only minimal security whereas other local applications or applications deployed over the Internet may require stringent security measures and ongoing monitoring and evaluation.</span></span>  
  
 <span data-ttu-id="120e0-113">您應該在設計階段就考量 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 資料庫應用程式的安全性需求，而不是事後才加以考量。</span><span class="sxs-lookup"><span data-stu-id="120e0-113">The security requirements of a [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] database application should be considered at design time, not as an afterthought.</span></span> <span data-ttu-id="120e0-114">提早在開發週期中評估威脅，可增加在偵測到安全性漏洞時減少可能損害的機會。</span><span class="sxs-lookup"><span data-stu-id="120e0-114">Evaluating threats early in the development cycle gives you the opportunity to mitigate potential damage wherever a vulnerability is detected.</span></span>  
  
 <span data-ttu-id="120e0-115">即使一開始的應用程式設計安全無虞，隨著系統的演進，新的威脅也可能會出現。</span><span class="sxs-lookup"><span data-stu-id="120e0-115">Even if the initial design of an application is sound, new threats may emerge as the system evolves.</span></span> <span data-ttu-id="120e0-116">藉由在資料庫周圍築起多道防線，您可以將安全性破壞所造成的損傷減至最少。</span><span class="sxs-lookup"><span data-stu-id="120e0-116">By creating multiple lines of defense around your database, you can minimize the damage inflicted by a security breach.</span></span> <span data-ttu-id="120e0-117">您的第一道防線是絕不授與比絕對必要多的權限，藉此而減少可能受到攻擊的表面區域。</span><span class="sxs-lookup"><span data-stu-id="120e0-117">Your first line of defense is to reduce the attack surface area by never to granting more permissions than are absolutely necessary.</span></span>  
  
 <span data-ttu-id="120e0-118">本節中的主題簡要說明與開發人員相關的 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 安全性功能，並提供連結至《[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 線上叢書》中的相關主題以及提供更深入探討的其他資源。</span><span class="sxs-lookup"><span data-stu-id="120e0-118">The topics in this section briefly describe the security features in [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] that are relevant for developers, with links to relevant topics in [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Books Online and other resources that provide more detailed coverage.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="120e0-119">本章節內容</span><span class="sxs-lookup"><span data-stu-id="120e0-119">In This Section</span></span>  
 [<span data-ttu-id="120e0-120">SQL Server 安全性概觀</span><span class="sxs-lookup"><span data-stu-id="120e0-120">Overview of SQL Server Security</span></span>](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 <span data-ttu-id="120e0-121">說明 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 的架構和安全性功能。</span><span class="sxs-lookup"><span data-stu-id="120e0-121">Describes the architecture and security features of [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="120e0-122">SQL Server 中的應用程式安全性案例</span><span class="sxs-lookup"><span data-stu-id="120e0-122">Application Security Scenarios in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 <span data-ttu-id="120e0-123">包含討論 ADO.NET 和 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 應用程式之各種應用程式安全性案例的主題。</span><span class="sxs-lookup"><span data-stu-id="120e0-123">Contains topics discussing various application security scenarios for ADO.NET and [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] applications.</span></span>  
  
 [<span data-ttu-id="120e0-124">SQL Server Express 安全性</span><span class="sxs-lookup"><span data-stu-id="120e0-124">SQL Server Express Security</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-express-security.md)  
 <span data-ttu-id="120e0-125">說明 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Express 的安全性考量。</span><span class="sxs-lookup"><span data-stu-id="120e0-125">Describes security considerations for [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Express.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="120e0-126">相關章節</span><span class="sxs-lookup"><span data-stu-id="120e0-126">Related Sections</span></span>  
 <span data-ttu-id="120e0-127">[安全性與保護 (Database Engine)](http://msdn2.microsoft.com/library/bb510589\(SQL.100\).aspx.)</span><span class="sxs-lookup"><span data-stu-id="120e0-127">[Security and Protection (Database Engine)](http://msdn2.microsoft.com/library/bb510589\(SQL.100\).aspx.)</span></span>  
 <span data-ttu-id="120e0-128">《[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 線上叢書》安全性主題。</span><span class="sxs-lookup"><span data-stu-id="120e0-128">[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Books Online security topics.</span></span>  
  
 [<span data-ttu-id="120e0-129">SQL Server 的安全性考量</span><span class="sxs-lookup"><span data-stu-id="120e0-129">Security Considerations for SQL Server</span></span>](http://go.microsoft.com/fwlink/?LinkId=98587)  
 <span data-ttu-id="120e0-130">《[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 線上叢書》安全性主題。</span><span class="sxs-lookup"><span data-stu-id="120e0-130">[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Books Online security topics.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="120e0-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="120e0-131">See Also</span></span>  
 [<span data-ttu-id="120e0-132">設定 ADO.NET 應用程式的安全性</span><span class="sxs-lookup"><span data-stu-id="120e0-132">Securing ADO.NET Applications</span></span>](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [<span data-ttu-id="120e0-133">SQL Server 和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="120e0-133">SQL Server and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/index.md)  
 [<span data-ttu-id="120e0-134">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="120e0-134">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
