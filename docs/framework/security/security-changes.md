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
ms.openlocfilehash: c62a469b3e31283e5790c747092a8fe504ef8c2a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43733335"
---
# <a name="security-changes-in-the-net-framework"></a><span data-ttu-id="bed1f-102">.NET Framework 中的安全性變更</span><span class="sxs-lookup"><span data-stu-id="bed1f-102">Security Changes in the .NET Framework</span></span>
<span data-ttu-id="bed1f-103">在 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 中對於安全性最重要的變更為強式命名。</span><span class="sxs-lookup"><span data-stu-id="bed1f-103">The most important change to security in the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] is in strong naming.</span></span> <span data-ttu-id="bed1f-104">如需這些變更的說明，請參閱 [Enhanced Strong Naming](../../../docs/framework/app-domains/enhanced-strong-naming.md) 。</span><span class="sxs-lookup"><span data-stu-id="bed1f-104">See [Enhanced Strong Naming](../../../docs/framework/app-domains/enhanced-strong-naming.md) for a description of those changes.</span></span>  
  
 <span data-ttu-id="bed1f-105">.NET Framework 提供 Managed 應用程式的兩層式安全性模型。</span><span class="sxs-lookup"><span data-stu-id="bed1f-105">The .NET Framework provides a two-tier security model for managed applications.</span></span> [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]<span data-ttu-id="bed1f-106"> 應用程式會在限制存取資源的 Windows 安全性容器內執行。</span><span class="sxs-lookup"><span data-stu-id="bed1f-106"> apps run in a Windows security container that limits access to resources.</span></span> <span data-ttu-id="bed1f-107">在該容器內，Managed 應用程式會在完全受信任的情況下執行。</span><span class="sxs-lookup"><span data-stu-id="bed1f-107">Within that container, managed applications run fully trusted.</span></span> <span data-ttu-id="bed1f-108">從程式碼存取安全性 (CAS) 的觀點來看，開發人員不管做什麼也都無法提高權限。</span><span class="sxs-lookup"><span data-stu-id="bed1f-108">From a code access security (CAS) perspective, there is nothing a developer can do to elevate privileges.</span></span> <span data-ttu-id="bed1f-109">如需 Windows 授與之權限的詳細資訊，請參閱 Windows 開發人員中心的 [應用程式功能宣告 (Windows 市集應用程式)](https://go.microsoft.com/fwlink/?LinkId=230436) 。</span><span class="sxs-lookup"><span data-stu-id="bed1f-109">For information about the privileges granted by Windows, see [App capability declarations (Windows Store apps)](https://go.microsoft.com/fwlink/?LinkId=230436) in the Windows Dev Center.</span></span> <span data-ttu-id="bed1f-110">如需建立 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式的詳細資訊，請參閱 [使用 C# 或 Visual Basic 建立您的第一個 Windows 市集應用程式](https://go.microsoft.com/fwlink/?LinkId=230461)。</span><span class="sxs-lookup"><span data-stu-id="bed1f-110">For information about creating a [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app, see [Create your first Windows Store app using C# or Visual Basic](https://go.microsoft.com/fwlink/?LinkId=230461).</span></span>
