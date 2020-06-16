---
title: .NET 的安全性
description: 瞭解 .NET 中的安全性。 請遵循描述主要安全性概念、以角色為基礎的安全性、密碼編譯模型，以及安全程式碼撰寫方針的連結。
ms.date: 06/04/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- .NET, security
- security [.NET], about security
- application development [.NET], security
- security [.NET Framework]
- security [.NET]
ms.assetid: 9a9621d7-8883-4a4f-a874-65e8e09e20a6
ms.openlocfilehash: 21511b580a4f922d2aef04cc79f5d551f0406b45
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2020
ms.locfileid: "84767815"
---
# <a name="security-in-net"></a><span data-ttu-id="0fadd-104">.NET 的安全性</span><span class="sxs-lookup"><span data-stu-id="0fadd-104">Security in .NET</span></span>

<span data-ttu-id="0fadd-105">Common language runtime 和 .NET 提供許多有用的類別和服務，可讓開發人員輕鬆地撰寫安全的程式碼，並讓系統管理員自訂授與程式碼的許可權，使其可以存取受保護的資源。</span><span class="sxs-lookup"><span data-stu-id="0fadd-105">The common language runtime and the .NET provide many useful classes and services that enable developers to easily write secure code and enable system administrators to customize the permissions granted to code so that it can access protected resources.</span></span> <span data-ttu-id="0fadd-106">此外，執行時間和 .NET 提供有用的類別和服務，可協助您使用加密和以角色為基礎的安全性。</span><span class="sxs-lookup"><span data-stu-id="0fadd-106">In addition, the runtime and the .NET provide useful classes and services that facilitate the use of cryptography and role-based security.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="0fadd-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="0fadd-107">In this section</span></span>

- [<span data-ttu-id="0fadd-108">重要的安全性概念</span><span class="sxs-lookup"><span data-stu-id="0fadd-108">Key Security Concepts</span></span>](key-security-concepts.md)  
<span data-ttu-id="0fadd-109">提供 Common Language Runtime 安全性功能的概觀。</span><span class="sxs-lookup"><span data-stu-id="0fadd-109">Provides an overview of common language runtime security features.</span></span> <span data-ttu-id="0fadd-110">這個章節適用於開發人員和系統管理員。</span><span class="sxs-lookup"><span data-stu-id="0fadd-110">This section is of interest to developers and system administrators.</span></span>

- [<span data-ttu-id="0fadd-111">以角色為基礎的安全性</span><span class="sxs-lookup"><span data-stu-id="0fadd-111">Role-Based Security</span></span>](role-based-security.md)  
<span data-ttu-id="0fadd-112">描述如何和在程式碼中以角色為基礎的安全性互動。</span><span class="sxs-lookup"><span data-stu-id="0fadd-112">Describes how to interact with role-based security in your code.</span></span> <span data-ttu-id="0fadd-113">本節適用於開發人員。</span><span class="sxs-lookup"><span data-stu-id="0fadd-113">This section is of interest to developers.</span></span>

- [<span data-ttu-id="0fadd-114">加密模型</span><span class="sxs-lookup"><span data-stu-id="0fadd-114">Cryptography Model</span></span>](cryptography-model.md)  
<span data-ttu-id="0fadd-115">提供 .NET 所提供的密碼編譯服務的總覽。</span><span class="sxs-lookup"><span data-stu-id="0fadd-115">Provides an overview of cryptographic services provided by .NET.</span></span> <span data-ttu-id="0fadd-116">本節適用於開發人員。</span><span class="sxs-lookup"><span data-stu-id="0fadd-116">This section is of interest to developers.</span></span>

- [<span data-ttu-id="0fadd-117">安全程式碼撰寫方針</span><span class="sxs-lookup"><span data-stu-id="0fadd-117">Secure Coding Guidelines</span></span>](secure-coding-guidelines.md)  
<span data-ttu-id="0fadd-118">說明建立可靠 .NET 應用程式的一些最佳作法。</span><span class="sxs-lookup"><span data-stu-id="0fadd-118">Describes some of the best practices for creating reliable .NET applications.</span></span> <span data-ttu-id="0fadd-119">本節適用於開發人員。</span><span class="sxs-lookup"><span data-stu-id="0fadd-119">This section is of interest to developers.</span></span>

## <a name="related-sections"></a><span data-ttu-id="0fadd-120">相關章節</span><span class="sxs-lookup"><span data-stu-id="0fadd-120">Related sections</span></span>

[<span data-ttu-id="0fadd-121">開發指南</span><span class="sxs-lookup"><span data-stu-id="0fadd-121">Development Guide</span></span>](../../framework/development-guide.md)  
<span data-ttu-id="0fadd-122">提供應用程式開發所有主要技術領域和工作的指引，包括建立、設定、偵錯、保護及部署您的應用程式，以及有關動態程式設計、互通性、擴充性、記憶體管理和執行緒的資訊。</span><span class="sxs-lookup"><span data-stu-id="0fadd-122">Provides a guide to all key technology areas and tasks for application development, including creating, configuring, debugging, securing, and deploying your application, and information about dynamic programming, interoperability, extensibility, memory management, and threading.</span></span>
