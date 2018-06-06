---
title: .NET 的安全性
ms.date: 06/04/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- .NET, security
- security [.NET], about security
- application development [.NET], security
- security [.NET Framework]
- security [.NET]
ms.assetid: 9a9621d7-8883-4a4f-a874-65e8e09e20a6
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0e60f463d5a691cb84a30c169e471aa905b2db17
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34728585"
---
# <a name="security-in-net"></a><span data-ttu-id="39d1e-102">.NET 的安全性</span><span class="sxs-lookup"><span data-stu-id="39d1e-102">Security in .NET</span></span>
<span data-ttu-id="39d1e-103">Common language runtime 和.NET 提供許多實用的類別和服務，可讓開發人員輕鬆地撰寫安全程式碼，以及讓系統管理員自訂權限授與程式碼，使其可以存取受保護的資源。</span><span class="sxs-lookup"><span data-stu-id="39d1e-103">The common language runtime and the .NET provide many useful classes and services that enable developers to easily write secure code and enable system administrators to customize the permissions granted to code so that it can access protected resources.</span></span> <span data-ttu-id="39d1e-104">此外，執行階段和.NET 提供實用的類別和服務，方便使用密碼編譯和以角色為基礎的安全性。</span><span class="sxs-lookup"><span data-stu-id="39d1e-104">In addition, the runtime and the .NET provide useful classes and services that facilitate the use of cryptography and role-based security.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="39d1e-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="39d1e-105">In This Section</span></span>  

 [<span data-ttu-id="39d1e-106">重要的安全性概念</span><span class="sxs-lookup"><span data-stu-id="39d1e-106">Key Security Concepts</span></span>](../../../docs/standard/security/key-security-concepts.md)  
 <span data-ttu-id="39d1e-107">提供 Common Language Runtime 安全性功能的概觀。</span><span class="sxs-lookup"><span data-stu-id="39d1e-107">Provides an overview of common language runtime security features.</span></span> <span data-ttu-id="39d1e-108">這個章節適用於開發人員和系統管理員。</span><span class="sxs-lookup"><span data-stu-id="39d1e-108">This section is of interest to developers and system administrators.</span></span>  
  
 [<span data-ttu-id="39d1e-109">以角色為基礎的安全性</span><span class="sxs-lookup"><span data-stu-id="39d1e-109">Role-Based Security</span></span>](../../../docs/standard/security/role-based-security.md)  
 <span data-ttu-id="39d1e-110">描述如何和在程式碼中以角色為基礎的安全性互動。</span><span class="sxs-lookup"><span data-stu-id="39d1e-110">Describes how to interact with role-based security in your code.</span></span> <span data-ttu-id="39d1e-111">本節適用於開發人員。</span><span class="sxs-lookup"><span data-stu-id="39d1e-111">This section is of interest to developers.</span></span>  
  
 [<span data-ttu-id="39d1e-112">加密模型</span><span class="sxs-lookup"><span data-stu-id="39d1e-112">Cryptography Model</span></span>](../../../docs/standard/security/cryptography-model.md)  
 <span data-ttu-id="39d1e-113">提供密碼編譯服務提供的.NET 的概觀。</span><span class="sxs-lookup"><span data-stu-id="39d1e-113">Provides an overview of cryptographic services provided by .NET.</span></span> <span data-ttu-id="39d1e-114">本節適用於開發人員。</span><span class="sxs-lookup"><span data-stu-id="39d1e-114">This section is of interest to developers.</span></span>  
  
 [<span data-ttu-id="39d1e-115">安全程式碼撰寫方針</span><span class="sxs-lookup"><span data-stu-id="39d1e-115">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)  
 <span data-ttu-id="39d1e-116">描述一些建立可靠的.NET 應用程式的最佳作法。</span><span class="sxs-lookup"><span data-stu-id="39d1e-116">Describes some of the best practices for creating reliable .NET applications.</span></span> <span data-ttu-id="39d1e-117">本節適用於開發人員。</span><span class="sxs-lookup"><span data-stu-id="39d1e-117">This section is of interest to developers.</span></span>  
  
 [<span data-ttu-id="39d1e-118">Unmanaged 程式碼的安全程式碼撰寫方針</span><span class="sxs-lookup"><span data-stu-id="39d1e-118">Secure Coding Guidelines for Unmanaged Code</span></span>](../../../docs/framework/security/secure-coding-guidelines-for-unmanaged-code.md)  
 <span data-ttu-id="39d1e-119">描述在呼叫 Unmanaged 程式碼時的一些最佳作法與安全性考量。</span><span class="sxs-lookup"><span data-stu-id="39d1e-119">Describes some of the best practices and security concerns when calling unmanaged code.</span></span>  
  
 [<span data-ttu-id="39d1e-120">Windows Identity Foundation</span><span class="sxs-lookup"><span data-stu-id="39d1e-120">Windows Identity Foundation</span></span>](../../../docs/framework/security/index.md)  
 <span data-ttu-id="39d1e-121">描述如何在應用程式中實作宣告型識別。</span><span class="sxs-lookup"><span data-stu-id="39d1e-121">Describes how you can implement claims-based identity in your applications.</span></span>  

<span data-ttu-id="39d1e-122">[安全性變更](../../../docs/framework/security/security-changes.md)描述.NET Framework 安全性系統的重要變更。</span><span class="sxs-lookup"><span data-stu-id="39d1e-122">[Security Changes](../../../docs/framework/security/security-changes.md) Describes important changes to the .NET Framework security system.</span></span>

## <a name="related-sections"></a><span data-ttu-id="39d1e-123">相關章節</span><span class="sxs-lookup"><span data-stu-id="39d1e-123">Related Sections</span></span>  
 [<span data-ttu-id="39d1e-124">開發指南</span><span class="sxs-lookup"><span data-stu-id="39d1e-124">Development Guide</span></span>](../../../docs/framework/development-guide.md)  
 <span data-ttu-id="39d1e-125">提供應用程式開發所有主要技術領域和工作的指引，包括建立、設定、偵錯、保護及部署您的應用程式，以及有關動態程式設計、互通性、擴充性、記憶體管理和執行緒的資訊。</span><span class="sxs-lookup"><span data-stu-id="39d1e-125">Provides a guide to all key technology areas and tasks for application development, including creating, configuring, debugging, securing, and deploying your application, and information about dynamic programming, interoperability, extensibility, memory management, and threading.</span></span>
