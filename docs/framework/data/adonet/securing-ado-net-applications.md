---
title: 設定應用程式的安全性
ms.date: 03/30/2017
ms.assetid: 005a1d43-6ee5-471e-ad98-1d30a44d49d5
ms.openlocfilehash: af184f64b43c2d3dc39f8c0add08940d3b002c24
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90550751"
---
# <a name="securing-adonet-applications"></a><span data-ttu-id="b708e-102">保護 ADO.NET 應用程式</span><span class="sxs-lookup"><span data-stu-id="b708e-102">Securing ADO.NET applications</span></span>

<span data-ttu-id="b708e-103">撰寫安全的 ADO.NET 應用程式並不只是為了避免常見的編碼錯誤，例如未驗證使用者輸入。</span><span class="sxs-lookup"><span data-stu-id="b708e-103">Writing a secure ADO.NET application involves more than avoiding common coding pitfalls such as not validating user input.</span></span> <span data-ttu-id="b708e-104">存取資料的應用程式有許多攻擊者可以用於擷取、操作或破壞敏感性資料的潛在錯誤點。</span><span class="sxs-lookup"><span data-stu-id="b708e-104">An application that accesses data has many potential points of failure that an attacker can exploit to retrieve, manipulate, or destroy sensitive data.</span></span> <span data-ttu-id="b708e-105">因此，了解安全性的所有面向就相當重要，從應用程式設計階段期間的威脅模組處理，到最終的部署以及進行中的作業，都包括在內。</span><span class="sxs-lookup"><span data-stu-id="b708e-105">It is therefore important to understand all aspects of security, from the process of threat modeling during the design phase of your application, to its eventual deployment and ongoing maintenance.</span></span>  
  
<span data-ttu-id="b708e-106">.NET Framework 提供許多有用的類別 (Class)、服務和工具，能用於保護及管理資料庫應用程式。</span><span class="sxs-lookup"><span data-stu-id="b708e-106">The .NET Framework provides many useful classes, services, and tools for securing and administering database applications.</span></span> <span data-ttu-id="b708e-107">Common Language Runtime (CLR) 提供型別安全的環境，讓您在其中執行程式碼，方法是使用程式碼存取安全性 (CAS)，進一步限制 Managed 程式碼的使用權限。</span><span class="sxs-lookup"><span data-stu-id="b708e-107">The common language runtime (CLR) provides a type-safe environment for code to run in, with code access security (CAS) to restrict further the permissions of managed code.</span></span> <span data-ttu-id="b708e-108">遵循安全資料存取編碼實務，可限制潛在的攻擊者所可能造成的損害。</span><span class="sxs-lookup"><span data-stu-id="b708e-108">Following secure data access coding practices limits the damage that can be inflicted by a potential attacker.</span></span>  
  
<span data-ttu-id="b708e-109">撰寫安全的程式碼，並不能防衛在使用 Unmanged 資源 (例如資料庫) 時自身造成的安全性漏洞。</span><span class="sxs-lookup"><span data-stu-id="b708e-109">Writing secure code does not guard against self-inflicted security holes when working with unmanaged resources such as databases.</span></span> <span data-ttu-id="b708e-110">大部分的伺服器資料庫 (例如 SQL Server) 都擁有自己的安全性系統，如果實作正確即可提升安全性。</span><span class="sxs-lookup"><span data-stu-id="b708e-110">Most server databases, such as SQL Server, have their own security systems, which enhance security when implemented correctly.</span></span> <span data-ttu-id="b708e-111">不過，即使是具有嚴密安全性系統的資料來源，如果設定不正確，也可能在攻擊中受損。</span><span class="sxs-lookup"><span data-stu-id="b708e-111">However, even a data source with a robust security system can be victimized in an attack if it is not configured appropriately.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b708e-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="b708e-112">In this section</span></span>

 [<span data-ttu-id="b708e-113">安全性概觀</span><span class="sxs-lookup"><span data-stu-id="b708e-113">Security Overview</span></span>](security-overview.md)  
 <span data-ttu-id="b708e-114">針對設計安全的 ADO. NET 應用程式提供建議。</span><span class="sxs-lookup"><span data-stu-id="b708e-114">Provides recommendations for designing secure ADO.NET applications.</span></span>  
  
 [<span data-ttu-id="b708e-115">安全存取資料</span><span class="sxs-lookup"><span data-stu-id="b708e-115">Secure Data Access</span></span>](secure-data-access.md)  
 <span data-ttu-id="b708e-116">說明如何使用安全資料來源的資料。</span><span class="sxs-lookup"><span data-stu-id="b708e-116">Describes how to work with data from a secured data source.</span></span>  
  
 [<span data-ttu-id="b708e-117">保護用戶端應用程式的安全</span><span class="sxs-lookup"><span data-stu-id="b708e-117">Secure Client Applications</span></span>](secure-client-applications.md)  
 <span data-ttu-id="b708e-118">說明用戶端應用程式的安全性考量。</span><span class="sxs-lookup"><span data-stu-id="b708e-118">Describes security considerations for client applications.</span></span>  
  
 [<span data-ttu-id="b708e-119">程式碼存取安全性和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b708e-119">Code Access Security and ADO.NET</span></span>](code-access-security.md)  
 <span data-ttu-id="b708e-120">說明 CAS 如何協助保護 ADO.NET 程式碼，</span><span class="sxs-lookup"><span data-stu-id="b708e-120">Describes how CAS can help protect ADO.NET code.</span></span> <span data-ttu-id="b708e-121">也將討論如何使用部分信任。</span><span class="sxs-lookup"><span data-stu-id="b708e-121">Also discusses how to work with partial trust.</span></span>  
  
 [<span data-ttu-id="b708e-122">隱私權和資料安全性</span><span class="sxs-lookup"><span data-stu-id="b708e-122">Privacy and Data Security</span></span>](privacy-and-data-security.md)  
 <span data-ttu-id="b708e-123">說明 ADO. NET 應用程式的加密選項。</span><span class="sxs-lookup"><span data-stu-id="b708e-123">Describes encryption options for ADO.NET applications.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b708e-124">相關章節</span><span class="sxs-lookup"><span data-stu-id="b708e-124">Related sections</span></span>

 [<span data-ttu-id="b708e-125">DataSet 和 DataTable 安全性指引</span><span class="sxs-lookup"><span data-stu-id="b708e-125">DataSet and DataTable security guidance</span></span>](dataset-datatable-dataview/security-guidance.md)  
 <span data-ttu-id="b708e-126">提供和的安全性 <xref:System.Data.DataSet> 指引 <xref:System.Data.DataTable> 。</span><span class="sxs-lookup"><span data-stu-id="b708e-126">Provides security guidance for <xref:System.Data.DataSet> and <xref:System.Data.DataTable>.</span></span>

 [<span data-ttu-id="b708e-127">SQL Server 安全性</span><span class="sxs-lookup"><span data-stu-id="b708e-127">SQL Server Security</span></span>](./sql/sql-server-security.md)  
 <span data-ttu-id="b708e-128">從開發人員的觀點說明 SQL Server 安全性功能。</span><span class="sxs-lookup"><span data-stu-id="b708e-128">Describes SQL Server security features from a developer's perspective.</span></span>  
  
 [<span data-ttu-id="b708e-129">安全性考量</span><span class="sxs-lookup"><span data-stu-id="b708e-129">Security Considerations</span></span>](./ef/security-considerations.md)  
 <span data-ttu-id="b708e-130">描述 Entity Framework 應用程式的安全性。</span><span class="sxs-lookup"><span data-stu-id="b708e-130">Describes security for Entity Framework applications.</span></span>  
  
 [<span data-ttu-id="b708e-131">安全性</span><span class="sxs-lookup"><span data-stu-id="b708e-131">Security</span></span>](../../../standard/security/index.md)  
 <span data-ttu-id="b708e-132">包含說明 .NET 中所有安全性層面的文章連結。</span><span class="sxs-lookup"><span data-stu-id="b708e-132">Contains links to articles describing all aspects of security in .NET.</span></span>  
  
 <span data-ttu-id="b708e-133">[安全性工具](/previous-versions/visualstudio/visual-studio-2008/7w3fd0wb(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="b708e-133">[Security Tools](/previous-versions/visualstudio/visual-studio-2008/7w3fd0wb(v=vs.90))</span></span>  
 <span data-ttu-id="b708e-134">保護及管理安全性原則的 .NET Framework 工具。</span><span class="sxs-lookup"><span data-stu-id="b708e-134">.NET Framework tools for securing and administering security policy.</span></span>  
  
 <span data-ttu-id="b708e-135">[建立安全應用程式的資源](/previous-versions/visualstudio/visual-studio-2010/ms165101(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b708e-135">[Resources for Creating Secure Applications](/previous-versions/visualstudio/visual-studio-2010/ms165101(v=vs.100))</span></span>  
 <span data-ttu-id="b708e-136">提供建立安全應用程式之文章的連結。</span><span class="sxs-lookup"><span data-stu-id="b708e-136">Provides links to articles for creating secure applications.</span></span>  
  
 [<span data-ttu-id="b708e-137">安全性參考書目</span><span class="sxs-lookup"><span data-stu-id="b708e-137">Security Bibliography</span></span>](/visualstudio/ide/securing-applications)  
 <span data-ttu-id="b708e-138">提供可線上使用及列印版本的外部資源連結。</span><span class="sxs-lookup"><span data-stu-id="b708e-138">Provides links to external resources available online and in print.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b708e-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b708e-139">See also</span></span>

- [<span data-ttu-id="b708e-140">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b708e-140">ADO.NET</span></span>](index.md)
- <span data-ttu-id="b708e-141">[ADO.NET 概觀](ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="b708e-141">[ADO.NET Overview](ado-net-overview.md)</span></span>
