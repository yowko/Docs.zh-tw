---
title: "設定 ADO.NET 應用程式的安全性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 005a1d43-6ee5-471e-ad98-1d30a44d49d5
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 143447020f41368a3553a0c8cda78e80806b75ba
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="securing-adonet-applications"></a><span data-ttu-id="e772d-102">設定 ADO.NET 應用程式的安全性</span><span class="sxs-lookup"><span data-stu-id="e772d-102">Securing ADO.NET Applications</span></span>
<span data-ttu-id="e772d-103">撰寫安全的 ADO.NET 應用程式並不只是為了避免常見的編碼錯誤，例如未驗證使用者輸入。</span><span class="sxs-lookup"><span data-stu-id="e772d-103">Writing a secure ADO.NET application involves more than avoiding common coding pitfalls such as not validating user input.</span></span> <span data-ttu-id="e772d-104">用於存取資料的應用程式有許多潛在的錯誤，攻擊者可以利用這些錯誤來擷取、管理或毀損機密資料。</span><span class="sxs-lookup"><span data-stu-id="e772d-104">An application that accesses data has many potential points of failure that an attacker can exploit to retrieve, manipulate, or destroy sensitive data.</span></span> <span data-ttu-id="e772d-105">因此，了解安全性的所有面向就相當重要，從應用程式設計階段期間的威脅模組處理，到最終的部署以及進行中的作業，都包括在內。</span><span class="sxs-lookup"><span data-stu-id="e772d-105">It is therefore important to understand all aspects of security, from the process of threat modeling during the design phase of your application, to its eventual deployment and ongoing maintenance.</span></span>  
  
 <span data-ttu-id="e772d-106">.NET Framework 提供許多有用的類別 (Class)、服務和工具，能用於保護及管理資料庫應用程式。</span><span class="sxs-lookup"><span data-stu-id="e772d-106">The .NET Framework provides many useful classes, services, and tools for securing and administering database applications.</span></span> <span data-ttu-id="e772d-107">Common Language Runtime (CLR) 提供型別安全的環境，讓您在其中執行程式碼，方法是使用程式碼存取安全性 (CAS)，進一步限制 Managed 程式碼的使用權限。</span><span class="sxs-lookup"><span data-stu-id="e772d-107">The common language runtime (CLR) provides a type-safe environment for code to run in, with code access security (CAS) to restrict further the permissions of managed code.</span></span> <span data-ttu-id="e772d-108">遵循安全資料存取編碼實務，可限制潛在的攻擊者所可能造成的損害。</span><span class="sxs-lookup"><span data-stu-id="e772d-108">Following secure data access coding practices limits the damage that can be inflicted by a potential attacker.</span></span>  
  
 <span data-ttu-id="e772d-109">撰寫安全的程式碼，並不能防衛在使用 Unmanged 資源 (例如資料庫) 時自身造成的安全性漏洞。</span><span class="sxs-lookup"><span data-stu-id="e772d-109">Writing secure code does not guard against self-inflicted security holes when working with unmanaged resources such as databases.</span></span> <span data-ttu-id="e772d-110">大部分的伺服器資料庫 (例如 SQL Server) 都擁有自己的安全性系統，如果實作正確即可提升安全性。</span><span class="sxs-lookup"><span data-stu-id="e772d-110">Most server databases, such as SQL Server, have their own security systems, which enhance security when implemented correctly.</span></span> <span data-ttu-id="e772d-111">不過，即使是具有嚴密安全性系統的資料來源，如果設定不正確，也可能在攻擊中受損。</span><span class="sxs-lookup"><span data-stu-id="e772d-111">However, even a data source with a robust security system can be victimized in an attack if it is not configured appropriately.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e772d-112">本章節內容</span><span class="sxs-lookup"><span data-stu-id="e772d-112">In This Section</span></span>  
 [<span data-ttu-id="e772d-113">安全性概觀</span><span class="sxs-lookup"><span data-stu-id="e772d-113">Security Overview</span></span>](../../../../docs/framework/data/adonet/security-overview.md)  
 <span data-ttu-id="e772d-114">針對設計安全的 ADO. NET 應用程式提供建議。</span><span class="sxs-lookup"><span data-stu-id="e772d-114">Provides recommendations for designing secure ADO.NET applications.</span></span>  
  
 [<span data-ttu-id="e772d-115">安全資料存取</span><span class="sxs-lookup"><span data-stu-id="e772d-115">Secure Data Access</span></span>](../../../../docs/framework/data/adonet/secure-data-access.md)  
 <span data-ttu-id="e772d-116">說明如何使用安全資料來源的資料。</span><span class="sxs-lookup"><span data-stu-id="e772d-116">Describes how to work with data from a secured data source.</span></span>  
  
 [<span data-ttu-id="e772d-117">保護用戶端應用程式</span><span class="sxs-lookup"><span data-stu-id="e772d-117">Secure Client Applications</span></span>](../../../../docs/framework/data/adonet/secure-client-applications.md)  
 <span data-ttu-id="e772d-118">說明用戶端應用程式的安全性考量。</span><span class="sxs-lookup"><span data-stu-id="e772d-118">Describes security considerations for client applications.</span></span>  
  
 [<span data-ttu-id="e772d-119">程式碼存取安全性和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e772d-119">Code Access Security and ADO.NET</span></span>](../../../../docs/framework/data/adonet/code-access-security.md)  
 <span data-ttu-id="e772d-120">說明 CAS 如何協助保護 ADO.NET 程式碼，</span><span class="sxs-lookup"><span data-stu-id="e772d-120">Describes how CAS can help protect ADO.NET code.</span></span> <span data-ttu-id="e772d-121">也將討論如何使用部分信任。</span><span class="sxs-lookup"><span data-stu-id="e772d-121">Also discusses how to work with partial trust.</span></span>  
  
 [<span data-ttu-id="e772d-122">隱私權與資料安全性</span><span class="sxs-lookup"><span data-stu-id="e772d-122">Privacy and Data Security</span></span>](../../../../docs/framework/data/adonet/privacy-and-data-security.md)  
 <span data-ttu-id="e772d-123">說明 ADO. NET 應用程式的加密選項。</span><span class="sxs-lookup"><span data-stu-id="e772d-123">Describes encryption options for ADO.NET applications.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e772d-124">相關章節</span><span class="sxs-lookup"><span data-stu-id="e772d-124">Related Sections</span></span>  
 [<span data-ttu-id="e772d-125">SQL Server 安全性</span><span class="sxs-lookup"><span data-stu-id="e772d-125">SQL Server Security</span></span>](../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 <span data-ttu-id="e772d-126">從開發人員的觀點說明 SQL Server 安全性功能。</span><span class="sxs-lookup"><span data-stu-id="e772d-126">Describes SQL Server security features from a developer's perspective.</span></span>  
  
 [<span data-ttu-id="e772d-127">安全性考量</span><span class="sxs-lookup"><span data-stu-id="e772d-127">Security Considerations</span></span>](../../../../docs/framework/data/adonet/ef/security-considerations.md)  
 <span data-ttu-id="e772d-128">描述 Entity Framework 應用程式的安全性。</span><span class="sxs-lookup"><span data-stu-id="e772d-128">Describes security for Entity Framework applications.</span></span>  
  
 [<span data-ttu-id="e772d-129">安全性</span><span class="sxs-lookup"><span data-stu-id="e772d-129">Security</span></span>](../../../../docs/standard/security/index.md)  
 <span data-ttu-id="e772d-130">包含說明 .NET Framework 中所有安全性面向的主題連結。</span><span class="sxs-lookup"><span data-stu-id="e772d-130">Contains links to topics describing all aspects of security in the .NET Framework.</span></span>  
  
 [<span data-ttu-id="e772d-131">安全性工具</span><span class="sxs-lookup"><span data-stu-id="e772d-131">Security Tools</span></span>](http://msdn.microsoft.com/en-us/2a3eb98a-2de6-4fba-b41c-01a74d354c11)  
 <span data-ttu-id="e772d-132">保護及管理安全性原則的 .NET Framework 工具。</span><span class="sxs-lookup"><span data-stu-id="e772d-132">.NET Framework tools for securing and administering security policy.</span></span>  
  
 [<span data-ttu-id="e772d-133">建立安全應用程式資源</span><span class="sxs-lookup"><span data-stu-id="e772d-133">Resources for Creating Secure Applications</span></span>](http://msdn.microsoft.com/en-us/0ebf5f69-76f2-498a-a2df-83cf3443e132)  
 <span data-ttu-id="e772d-134">提供建立安全應用程式的主題連結。</span><span class="sxs-lookup"><span data-stu-id="e772d-134">Provides links to topics for creating secure applications.</span></span>  
  
 [<span data-ttu-id="e772d-135">安全性參考書目</span><span class="sxs-lookup"><span data-stu-id="e772d-135">Security Bibliography</span></span>](/visualstudio/ide/security-bibliography)  
 <span data-ttu-id="e772d-136">提供可線上使用及列印版本的外部資源連結。</span><span class="sxs-lookup"><span data-stu-id="e772d-136">Provides links to external resources available online and in print.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e772d-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e772d-137">See Also</span></span>  
 [<span data-ttu-id="e772d-138">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e772d-138">ADO.NET</span></span>](../../../../docs/framework/data/adonet/index.md)  
 [<span data-ttu-id="e772d-139">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="e772d-139">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
