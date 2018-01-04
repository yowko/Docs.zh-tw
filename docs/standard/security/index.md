---
title: ".NET Framework 中的安全性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET Framework, security
- security [.NET Framework], about security
- application development [.NET Framework], security
- security [.NET Framework]
ms.assetid: 9a9621d7-8883-4a4f-a874-65e8e09e20a6
caps.latest.revision: "37"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 7f8600da624ff75ce2dbd5c417f886d6b3b1ac37
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="security-in-the-net-framework"></a><span data-ttu-id="af54e-102">.NET Framework 中的安全性</span><span class="sxs-lookup"><span data-stu-id="af54e-102">Security in the .NET Framework</span></span>
<span data-ttu-id="af54e-103">Common Language Runtime 和 .NET Framework 提供了許多有用的類別和服務，可讓開發人員輕鬆地撰寫安全程式碼，以及讓系統管理員自訂權限授與程式碼，使其可以存取受保護的資源。</span><span class="sxs-lookup"><span data-stu-id="af54e-103">The common language runtime and the .NET Framework provide many useful classes and services that enable developers to easily write secure code and enable system administrators to customize the permissions granted to code so that it can access protected resources.</span></span> <span data-ttu-id="af54e-104">此外，執行階段和 .NET Framework 提供實用的類別和服務，方便使用密碼編譯和以角色為基礎的安全性。</span><span class="sxs-lookup"><span data-stu-id="af54e-104">In addition, the runtime and the .NET Framework provide useful classes and services that facilitate the use of cryptography and role-based security.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="af54e-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="af54e-105">In This Section</span></span>  
 [<span data-ttu-id="af54e-106">安全性變更</span><span class="sxs-lookup"><span data-stu-id="af54e-106">Security Changes</span></span>](../../../docs/framework/security/security-changes.md)  
 <span data-ttu-id="af54e-107">描述 .NET Framework 安全性系統的重要變更。</span><span class="sxs-lookup"><span data-stu-id="af54e-107">Describes important changes to the .NET Framework security system.</span></span>  
  
 [<span data-ttu-id="af54e-108">重要的安全性概念</span><span class="sxs-lookup"><span data-stu-id="af54e-108">Key Security Concepts</span></span>](../../../docs/standard/security/key-security-concepts.md)  
 <span data-ttu-id="af54e-109">提供 Common Language Runtime 安全性功能的概觀。</span><span class="sxs-lookup"><span data-stu-id="af54e-109">Provides an overview of common language runtime security features.</span></span> <span data-ttu-id="af54e-110">這個章節適用於開發人員和系統管理員。</span><span class="sxs-lookup"><span data-stu-id="af54e-110">This section is of interest to developers and system administrators.</span></span>  
  
 [<span data-ttu-id="af54e-111">以角色為基礎的安全性</span><span class="sxs-lookup"><span data-stu-id="af54e-111">Role-Based Security</span></span>](../../../docs/standard/security/role-based-security.md)  
 <span data-ttu-id="af54e-112">描述如何和在程式碼中以角色為基礎的安全性互動。</span><span class="sxs-lookup"><span data-stu-id="af54e-112">Describes how to interact with role-based security in your code.</span></span> <span data-ttu-id="af54e-113">本節適用於開發人員。</span><span class="sxs-lookup"><span data-stu-id="af54e-113">This section is of interest to developers.</span></span>  
  
 [<span data-ttu-id="af54e-114">加密模型</span><span class="sxs-lookup"><span data-stu-id="af54e-114">Cryptography Model</span></span>](../../../docs/standard/security/cryptography-model.md)  
 <span data-ttu-id="af54e-115">提供 .NET Framework 所提供密碼編譯服務的概觀。</span><span class="sxs-lookup"><span data-stu-id="af54e-115">Provides an overview of cryptographic services provided by the .NET Framework.</span></span> <span data-ttu-id="af54e-116">本節適用於開發人員。</span><span class="sxs-lookup"><span data-stu-id="af54e-116">This section is of interest to developers.</span></span>  
  
 [<span data-ttu-id="af54e-117">安全程式碼撰寫方針</span><span class="sxs-lookup"><span data-stu-id="af54e-117">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)  
 <span data-ttu-id="af54e-118">描述一些建立可靠的 .NET Framework 應用程式的最佳作法。</span><span class="sxs-lookup"><span data-stu-id="af54e-118">Describes some of the best practices for creating reliable .NET Framework applications.</span></span> <span data-ttu-id="af54e-119">本節適用於開發人員。</span><span class="sxs-lookup"><span data-stu-id="af54e-119">This section is of interest to developers.</span></span>  
  
 [<span data-ttu-id="af54e-120">Unmanaged 程式碼的安全程式碼撰寫方針</span><span class="sxs-lookup"><span data-stu-id="af54e-120">Secure Coding Guidelines for Unmanaged Code</span></span>](../../../docs/framework/security/secure-coding-guidelines-for-unmanaged-code.md)  
 <span data-ttu-id="af54e-121">描述在呼叫 Unmanaged 程式碼時的一些最佳作法與安全性考量。</span><span class="sxs-lookup"><span data-stu-id="af54e-121">Describes some of the best practices and security concerns when calling unmanaged code.</span></span>  
  
 [<span data-ttu-id="af54e-122">Windows Identity Foundation</span><span class="sxs-lookup"><span data-stu-id="af54e-122">Windows Identity Foundation</span></span>](../../../docs/framework/security/index.md)  
 <span data-ttu-id="af54e-123">描述如何在應用程式中實作宣告型識別。</span><span class="sxs-lookup"><span data-stu-id="af54e-123">Describes how you can implement claims-based identity in your applications.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="af54e-124">相關章節</span><span class="sxs-lookup"><span data-stu-id="af54e-124">Related Sections</span></span>  
 [<span data-ttu-id="af54e-125">開發指南</span><span class="sxs-lookup"><span data-stu-id="af54e-125">Development Guide</span></span>](../../../docs/framework/development-guide.md)  
 <span data-ttu-id="af54e-126">提供應用程式開發所有主要技術領域和工作的指引，包括建立、設定、偵錯、保護及部署您的應用程式，以及有關動態程式設計、互通性、擴充性、記憶體管理和執行緒的資訊。</span><span class="sxs-lookup"><span data-stu-id="af54e-126">Provides a guide to all key technology areas and tasks for application development, including creating, configuring, debugging, securing, and deploying your application, and information about dynamic programming, interoperability, extensibility, memory management, and threading.</span></span>
