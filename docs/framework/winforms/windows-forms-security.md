---
title: Windows Form 安全性
ms.date: 03/30/2017
helpviewer_keywords:
- designer access security [Windows Forms]
- permissions [Windows Forms], Windows Forms
- Windows Forms, security
- security [Windows Forms]
- access control [Windows Forms], Windows Forms
- security policy [Windows Forms], Windows Forms
ms.assetid: 932d438a-5285-46d8-a958-8c93d0ad6cae
ms.openlocfilehash: 75016e9e04cf47782add18c87f7c677931743a4e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43556174"
---
# <a name="windows-forms-security"></a><span data-ttu-id="afaae-102">Windows Form 安全性</span><span class="sxs-lookup"><span data-stu-id="afaae-102">Windows Forms Security</span></span>
<span data-ttu-id="afaae-103">Windows Form 的特色是程式碼為基礎 （安全性層級所設定的程式碼，不論執行的程式碼的使用者） 的安全性模型。</span><span class="sxs-lookup"><span data-stu-id="afaae-103">Windows Forms features a security model that is code-based (security levels are set for code, regardless of the user running the code).</span></span> <span data-ttu-id="afaae-104">這是除了可能已在您的電腦系統上的位置中的任何安全性結構描述。</span><span class="sxs-lookup"><span data-stu-id="afaae-104">This is in addition to any security schemas that may be in place already on your computer system.</span></span> <span data-ttu-id="afaae-105">這些可能包括瀏覽器 （例如區域為基礎的安全性提供 Internet Explorer） 或作業系統 （例如 Windows NT 的認證為基礎的安全性） 中。</span><span class="sxs-lookup"><span data-stu-id="afaae-105">These can include those in the browser (such as the zone-based security available in Internet Explorer) or the operating system (such as the credential-based security of Windows NT).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="afaae-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="afaae-106">In This Section</span></span>  
 [<span data-ttu-id="afaae-107">Windows Forms 中的安全性概觀</span><span class="sxs-lookup"><span data-stu-id="afaae-107">Security in Windows Forms Overview</span></span>](../../../docs/framework/winforms/security-in-windows-forms-overview.md)  
 <span data-ttu-id="afaae-108">簡短說明.NET Framework 安全性模型，基本步驟，以確保您的應用程式在 Windows Form 是安全的。</span><span class="sxs-lookup"><span data-stu-id="afaae-108">Briefly explains the .NET Framework security model and the basic steps necessary to ensure the Windows Forms in your application are secure.</span></span>  
  
 [<span data-ttu-id="afaae-109">Windows Forms 中更安全的檔案和資料存取</span><span class="sxs-lookup"><span data-stu-id="afaae-109">More Secure File and Data Access in Windows Forms</span></span>](../../../docs/framework/winforms/more-secure-file-and-data-access-in-windows-forms.md)  
 <span data-ttu-id="afaae-110">描述如何存取檔案和非完全信任環境中的資料。</span><span class="sxs-lookup"><span data-stu-id="afaae-110">Describes how to access files and data in a semi-trusted environment.</span></span>  
  
 [<span data-ttu-id="afaae-111">Windows Forms 中更安全的列印</span><span class="sxs-lookup"><span data-stu-id="afaae-111">More Secure Printing in Windows Forms</span></span>](../../../docs/framework/winforms/more-secure-printing-in-windows-forms.md)  
 <span data-ttu-id="afaae-112">描述如何存取在非完全信任環境中的列印功能。</span><span class="sxs-lookup"><span data-stu-id="afaae-112">Describes how to access printing features in a semi-trusted environment.</span></span>  
  
 [<span data-ttu-id="afaae-113">Windows Forms 中的其他安全性考量</span><span class="sxs-lookup"><span data-stu-id="afaae-113">Additional Security Considerations in Windows Forms</span></span>](../../../docs/framework/winforms/additional-security-considerations-in-windows-forms.md)  
 <span data-ttu-id="afaae-114">描述執行視窗操作、 使用剪貼簿，並在非完全信任環境中進行呼叫 unmanaged 程式碼。</span><span class="sxs-lookup"><span data-stu-id="afaae-114">Describes performing window manipulation, using the Clipboard, and making calls to unmanaged code in a semi-trusted environment.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="afaae-115">相關章節</span><span class="sxs-lookup"><span data-stu-id="afaae-115">Related Sections</span></span>  
 [<span data-ttu-id="afaae-116">NIB： 預設的安全性原則</span><span class="sxs-lookup"><span data-stu-id="afaae-116">NIB: Default Security Policy</span></span>](https://msdn.microsoft.com/library/2c086873-0894-4f4d-8f7e-47427c1a3b55)  
 <span data-ttu-id="afaae-117">列出在完全信任、 近端內部網路和網際網路權限集授與的預設權限。</span><span class="sxs-lookup"><span data-stu-id="afaae-117">Lists the default permissions granted in the Full Trust, Local Intranet, and Internet permission sets.</span></span>  
  
 [<span data-ttu-id="afaae-118">NIB： 一般安全性原則管理</span><span class="sxs-lookup"><span data-stu-id="afaae-118">NIB: General Security Policy Administration</span></span>](https://msdn.microsoft.com/library/5121fe35-f0e3-402c-94ab-4f35b0a87b4b)  
 <span data-ttu-id="afaae-119">提供.NET Framework 安全性原則管理和提高權限的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="afaae-119">Gives information about the administering the .NET Framework security policy and elevating permissions.</span></span>  
  
 [<span data-ttu-id="afaae-120">危險的使用權限和原則管理</span><span class="sxs-lookup"><span data-stu-id="afaae-120">Dangerous Permissions and Policy Administration</span></span>](../../../docs/framework/misc/dangerous-permissions-and-policy-administration.md)  
 <span data-ttu-id="afaae-121">討論一些可能會允許安全性系統受到危害的.net Framework 權限。</span><span class="sxs-lookup"><span data-stu-id="afaae-121">Discusses some of the.NET Framework permissions that can potentially allow the security system to be circumvented.</span></span>  
  
 [<span data-ttu-id="afaae-122">安全程式碼撰寫方針</span><span class="sxs-lookup"><span data-stu-id="afaae-122">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)  
 <span data-ttu-id="afaae-123">說明安全地撰寫針對.NET Framework 的程式碼的最佳作法的主題連結。</span><span class="sxs-lookup"><span data-stu-id="afaae-123">Links to topics that explain the best practices for securely writing code against the .NET Framework.</span></span>  
  
 [<span data-ttu-id="afaae-124">NIB： 要求權限</span><span class="sxs-lookup"><span data-stu-id="afaae-124">NIB: Requesting Permissions</span></span>](https://msdn.microsoft.com/library/0447c49d-8cba-45e4-862c-ff0b59bebdc2)  
 <span data-ttu-id="afaae-125">討論使用的屬性，讓執行階段知道您的程式碼需要執行哪些權限。</span><span class="sxs-lookup"><span data-stu-id="afaae-125">Discusses the use of attributes to let the runtime know what permissions your code needs to run.</span></span>  
  
 [<span data-ttu-id="afaae-126">重要的安全性概念</span><span class="sxs-lookup"><span data-stu-id="afaae-126">Key Security Concepts</span></span>](../../../docs/standard/security/key-security-concepts.md)  
 <span data-ttu-id="afaae-127">涵蓋的程式碼安全性的基本概念的主題連結。</span><span class="sxs-lookup"><span data-stu-id="afaae-127">Links to topics that cover the basic aspects of code security.</span></span>  
  
 [<span data-ttu-id="afaae-128">程式碼存取安全性的基本概念</span><span class="sxs-lookup"><span data-stu-id="afaae-128">Code Access Security Basics</span></span>](../../../docs/framework/misc/code-access-security-basics.md)  
 <span data-ttu-id="afaae-129">討論使用.NET Framework 執行階段安全性原則的基本概念。</span><span class="sxs-lookup"><span data-stu-id="afaae-129">Discusses the basics of working with the .NET Framework run time security policy.</span></span>  
  
 [<span data-ttu-id="afaae-130">NIB： 判斷何時要修改安全性原則</span><span class="sxs-lookup"><span data-stu-id="afaae-130">NIB: Determining When to Modify Security Policy</span></span>](https://msdn.microsoft.com/library/af749b17-e461-409d-84b9-a3d44789db16)  
 <span data-ttu-id="afaae-131">說明如何判斷您的應用程式需要從預設的安全性原則會分離開來。</span><span class="sxs-lookup"><span data-stu-id="afaae-131">Explains how to determine when your applications need to diverge from the default security policy.</span></span>  
  
 [<span data-ttu-id="afaae-132">NIB： 部署的安全性原則</span><span class="sxs-lookup"><span data-stu-id="afaae-132">NIB: Deploying Security Policy</span></span>](https://msdn.microsoft.com/library/f936c1e5-033b-4bd9-a3bd-a39ba733a681)  
 <span data-ttu-id="afaae-133">討論部署的安全性原則變更的最佳方式。</span><span class="sxs-lookup"><span data-stu-id="afaae-133">Discusses the best manner for deploying security policy changes.</span></span>
