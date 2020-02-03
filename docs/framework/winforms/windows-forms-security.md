---
title: 安全性
ms.date: 03/30/2017
helpviewer_keywords:
- designer access security [Windows Forms]
- permissions [Windows Forms], Windows Forms
- Windows Forms, security
- security [Windows Forms]
- access control [Windows Forms], Windows Forms
- security policy [Windows Forms], Windows Forms
ms.assetid: 932d438a-5285-46d8-a958-8c93d0ad6cae
ms.openlocfilehash: a3debf487b9b2a04277d9ce3007f28662fa4899e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734498"
---
# <a name="windows-forms-security"></a><span data-ttu-id="9e286-102">Windows Form 安全性</span><span class="sxs-lookup"><span data-stu-id="9e286-102">Windows Forms Security</span></span>
<span data-ttu-id="9e286-103">Windows Forms 是以程式碼為基礎的安全性模型（無論執行程式碼的使用者為何，都會為程式碼設定安全性層級）。</span><span class="sxs-lookup"><span data-stu-id="9e286-103">Windows Forms features a security model that is code-based (security levels are set for code, regardless of the user running the code).</span></span> <span data-ttu-id="9e286-104">這是除了您的電腦系統上可能已存在的任何安全性架構。</span><span class="sxs-lookup"><span data-stu-id="9e286-104">This is in addition to any security schemas that may be in place already on your computer system.</span></span> <span data-ttu-id="9e286-105">這些可能會包含在瀏覽器中（例如 Internet Explorer 中可用的區域型安全性）或作業系統（例如 Windows NT 的認證安全性）。</span><span class="sxs-lookup"><span data-stu-id="9e286-105">These can include those in the browser (such as the zone-based security available in Internet Explorer) or the operating system (such as the credential-based security of Windows NT).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9e286-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="9e286-106">In This Section</span></span>  
 [<span data-ttu-id="9e286-107">Windows Forms 中的安全性概觀</span><span class="sxs-lookup"><span data-stu-id="9e286-107">Security in Windows Forms Overview</span></span>](security-in-windows-forms-overview.md)  
 <span data-ttu-id="9e286-108">簡要說明 .NET Framework 安全性模型，以及確保應用程式中的 Windows Forms 安全所需的基本步驟。</span><span class="sxs-lookup"><span data-stu-id="9e286-108">Briefly explains the .NET Framework security model and the basic steps necessary to ensure the Windows Forms in your application are secure.</span></span>  
  
 [<span data-ttu-id="9e286-109">Windows Forms 中更安全的檔案和資料存取</span><span class="sxs-lookup"><span data-stu-id="9e286-109">More Secure File and Data Access in Windows Forms</span></span>](more-secure-file-and-data-access-in-windows-forms.md)  
 <span data-ttu-id="9e286-110">描述如何在不受信任的環境中存取檔案和資料。</span><span class="sxs-lookup"><span data-stu-id="9e286-110">Describes how to access files and data in a semi-trusted environment.</span></span>  
  
 [<span data-ttu-id="9e286-111">Windows Forms 中更安全的列印</span><span class="sxs-lookup"><span data-stu-id="9e286-111">More Secure Printing in Windows Forms</span></span>](more-secure-printing-in-windows-forms.md)  
 <span data-ttu-id="9e286-112">描述如何存取不完全信任環境中的列印功能。</span><span class="sxs-lookup"><span data-stu-id="9e286-112">Describes how to access printing features in a semi-trusted environment.</span></span>  
  
 [<span data-ttu-id="9e286-113">Windows Forms 中的其他安全性考量</span><span class="sxs-lookup"><span data-stu-id="9e286-113">Additional Security Considerations in Windows Forms</span></span>](additional-security-considerations-in-windows-forms.md)  
 <span data-ttu-id="9e286-114">描述如何使用剪貼簿來執行視窗操作，以及在不受信任的環境中呼叫非受控碼。</span><span class="sxs-lookup"><span data-stu-id="9e286-114">Describes performing window manipulation, using the Clipboard, and making calls to unmanaged code in a semi-trusted environment.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9e286-115">相關章節</span><span class="sxs-lookup"><span data-stu-id="9e286-115">Related Sections</span></span>  
 <span data-ttu-id="9e286-116">[預設安全性原則](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/03kwzyfc(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9e286-116">[Default Security Policy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/03kwzyfc(v=vs.100))</span></span>  
 <span data-ttu-id="9e286-117">列出在「完全信任」、「近端內部網路」和「網際網路」許可權集合中授與的預設許可權。</span><span class="sxs-lookup"><span data-stu-id="9e286-117">Lists the default permissions granted in the Full Trust, Local Intranet, and Internet permission sets.</span></span>  
  
 <span data-ttu-id="9e286-118">[一般安全性原則管理](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ed5htz45(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9e286-118">[General Security Policy Administration](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ed5htz45(v=vs.100))</span></span>  
 <span data-ttu-id="9e286-119">提供有關管理 .NET Framework 安全性原則和提升許可權的資訊。</span><span class="sxs-lookup"><span data-stu-id="9e286-119">Gives information about the administering the .NET Framework security policy and elevating permissions.</span></span>  
  
 [<span data-ttu-id="9e286-120">危險的許可權和原則管理</span><span class="sxs-lookup"><span data-stu-id="9e286-120">Dangerous Permissions and Policy Administration</span></span>](../misc/dangerous-permissions-and-policy-administration.md)  
 <span data-ttu-id="9e286-121">討論一些可能允許規避安全性系統的 the.NET 架構許可權。</span><span class="sxs-lookup"><span data-stu-id="9e286-121">Discusses some of the.NET Framework permissions that can potentially allow the security system to be circumvented.</span></span>  
  
 [<span data-ttu-id="9e286-122">安全程式碼撰寫方針</span><span class="sxs-lookup"><span data-stu-id="9e286-122">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)  
 <span data-ttu-id="9e286-123">說明安全地針對 .NET Framework 撰寫程式碼之最佳作法的主題連結。</span><span class="sxs-lookup"><span data-stu-id="9e286-123">Links to topics that explain the best practices for securely writing code against the .NET Framework.</span></span>  
  
 <span data-ttu-id="9e286-124">[要求許可權](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/yd267cce(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9e286-124">[Requesting Permissions](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/yd267cce(v=vs.100))</span></span>  
 <span data-ttu-id="9e286-125">討論屬性的使用，讓執行時間知道您的程式碼需要執行哪些許可權。</span><span class="sxs-lookup"><span data-stu-id="9e286-125">Discusses the use of attributes to let the runtime know what permissions your code needs to run.</span></span>  
  
 [<span data-ttu-id="9e286-126">重要的安全性概念</span><span class="sxs-lookup"><span data-stu-id="9e286-126">Key Security Concepts</span></span>](../../standard/security/key-security-concepts.md)  
 <span data-ttu-id="9e286-127">涵蓋程式碼安全性基本層面的主題連結。</span><span class="sxs-lookup"><span data-stu-id="9e286-127">Links to topics that cover the basic aspects of code security.</span></span>  
  
 [<span data-ttu-id="9e286-128">程式碼存取安全性的基本概念</span><span class="sxs-lookup"><span data-stu-id="9e286-128">Code Access Security Basics</span></span>](../misc/code-access-security-basics.md)  
 <span data-ttu-id="9e286-129">討論使用「.NET Framework 執行時間」安全性原則的基本概念。</span><span class="sxs-lookup"><span data-stu-id="9e286-129">Discusses the basics of working with the .NET Framework run time security policy.</span></span>  
  
 <span data-ttu-id="9e286-130">[判斷何時修改安全性原則](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xky659fc(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9e286-130">[Determining When to Modify Security Policy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xky659fc(v=vs.100))</span></span>  
 <span data-ttu-id="9e286-131">說明如何判斷您的應用程式需要從預設安全性原則中分離的時機。</span><span class="sxs-lookup"><span data-stu-id="9e286-131">Explains how to determine when your applications need to diverge from the default security policy.</span></span>  
  
 <span data-ttu-id="9e286-132">[部署安全性原則](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/13wcxx6y(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9e286-132">[Deploying Security Policy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/13wcxx6y(v=vs.100))</span></span>  
 <span data-ttu-id="9e286-133">討論部署安全性原則變更的最佳方式。</span><span class="sxs-lookup"><span data-stu-id="9e286-133">Discusses the best manner for deploying security policy changes.</span></span>
