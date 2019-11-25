---
title: .NET Framework 中的安全性變更
ms.date: 03/30/2017
helpviewer_keywords:
- Allow Partially Trusted Callers attribute
- .NET Framework 4, security changes
- .NET Framework security
- security-transparent code
- security-critical code
- code access security, changes
ms.assetid: 5e87881c-9c13-4b52-8ad1-e34bb46e8aaa
author: mairaw
ms.author: mairaw
ms.openlocfilehash: af2869e5ca3b41778c094b7a78a9493e74868811
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204498"
---
# <a name="security-changes-in-the-net-framework"></a><span data-ttu-id="96aac-102">.NET Framework 中的安全性變更</span><span class="sxs-lookup"><span data-stu-id="96aac-102">Security Changes in the .NET Framework</span></span>

<span data-ttu-id="96aac-103">The most important change to security in the .NET Framework 4.5 is in strong naming.</span><span class="sxs-lookup"><span data-stu-id="96aac-103">The most important change to security in the .NET Framework 4.5 is in strong naming.</span></span> <span data-ttu-id="96aac-104">如需這些變更的說明，請參閱 [Enhanced Strong Naming](../../standard/assembly/enhanced-strong-naming.md) 。</span><span class="sxs-lookup"><span data-stu-id="96aac-104">See [Enhanced Strong Naming](../../standard/assembly/enhanced-strong-naming.md) for a description of those changes.</span></span>  
  
<span data-ttu-id="96aac-105">.NET Framework 提供 Managed 應用程式的兩層式安全性模型。</span><span class="sxs-lookup"><span data-stu-id="96aac-105">The .NET Framework provides a two-tier security model for managed applications.</span></span> <span data-ttu-id="96aac-106">Windows 8.x Store apps run in a Windows security container that limits access to resources.</span><span class="sxs-lookup"><span data-stu-id="96aac-106">Windows 8.x Store apps run in a Windows security container that limits access to resources.</span></span> <span data-ttu-id="96aac-107">在該容器內，Managed 應用程式會在完全受信任的情況下執行。</span><span class="sxs-lookup"><span data-stu-id="96aac-107">Within that container, managed applications run fully trusted.</span></span> <span data-ttu-id="96aac-108">從程式碼存取安全性 (CAS) 的觀點來看，開發人員不管做什麼也都無法提高權限。</span><span class="sxs-lookup"><span data-stu-id="96aac-108">From a code access security (CAS) perspective, there is nothing a developer can do to elevate privileges.</span></span> <span data-ttu-id="96aac-109">如需 Windows 授與之權限的詳細資訊，請參閱 Windows 開發人員中心的 [應用程式功能宣告 (Windows 市集應用程式)](https://go.microsoft.com/fwlink/?LinkId=230436) 。</span><span class="sxs-lookup"><span data-stu-id="96aac-109">For information about the privileges granted by Windows, see [App capability declarations (Windows Store apps)](https://go.microsoft.com/fwlink/?LinkId=230436) in the Windows Dev Center.</span></span> <span data-ttu-id="96aac-110">For information about creating a Windows 8.x Store app, see [Create your first Windows Store app using C# or Visual Basic](https://go.microsoft.com/fwlink/?LinkId=230461).</span><span class="sxs-lookup"><span data-stu-id="96aac-110">For information about creating a Windows 8.x Store app, see [Create your first Windows Store app using C# or Visual Basic](https://go.microsoft.com/fwlink/?LinkId=230461).</span></span>
