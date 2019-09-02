---
title: 使用應用程式定義域
ms.date: 03/30/2017
helpviewer_keywords:
- application domains, about
- common language runtime, application domains
- runtime, application domains
ms.assetid: c6d99815-e022-4d2c-9420-1d7ab5b9d504
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5ebd1de46eb2757098a369b58dd9a6c0009e5b95
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2019
ms.locfileid: "61674882"
---
# <a name="using-application-domains"></a><span data-ttu-id="79074-102">使用應用程式定義域</span><span class="sxs-lookup"><span data-stu-id="79074-102">Using Application Domains</span></span>
<span data-ttu-id="79074-103">應用程式定義域為 Common Language Runtime 提供隔離單位。</span><span class="sxs-lookup"><span data-stu-id="79074-103">Application domains provide a unit of isolation for the common language runtime.</span></span> <span data-ttu-id="79074-104">它們是在處理序內建立和執行。</span><span class="sxs-lookup"><span data-stu-id="79074-104">They are created and run inside a process.</span></span> <span data-ttu-id="79074-105">應用程式定義域通常是由執行階段主機所建立，這是負責將執行階段載入處理序以及在應用程式定義域中執行使用者程式碼的應用程式。</span><span class="sxs-lookup"><span data-stu-id="79074-105">Application domains are usually created by a runtime host, which is an application responsible for loading the runtime into a process and executing user code within an application domain.</span></span> <span data-ttu-id="79074-106">執行階段主機會建立處理序和預設的應用程式定義域，在內部執行 Managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="79074-106">The runtime host creates a process and a default application domain, and runs managed code inside it.</span></span> <span data-ttu-id="79074-107">執行階段主機包括 ASP.NET、Microsoft Internet Explorer 和 Windows 殼層。</span><span class="sxs-lookup"><span data-stu-id="79074-107">Runtime hosts include ASP.NET, Microsoft Internet Explorer, and the Windows shell.</span></span>  
  
 <span data-ttu-id="79074-108">大部分的應用程式不需要建立自己的應用程式定義域，執行階段主機會為您建立任何必要的應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="79074-108">For most applications, you do not need to create your own application domain; the runtime host creates any necessary application domains for you.</span></span> <span data-ttu-id="79074-109">但如果您的應用程式需要隔離程式碼或使用及卸載 DLL，您可以建立及設定其他應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="79074-109">However, you can create and configure additional application domains if your application needs to isolate code or to use and unload DLLs.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="79074-110">本節內容</span><span class="sxs-lookup"><span data-stu-id="79074-110">In This Section</span></span>  
 [<span data-ttu-id="79074-111">如何：建立應用程式定義域</span><span class="sxs-lookup"><span data-stu-id="79074-111">How to: Create an Application Domain</span></span>](../../../docs/framework/app-domains/how-to-create-an-application-domain.md)  
 <span data-ttu-id="79074-112">描述如何以程式設計方式建立應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="79074-112">Describes how to programmatically create an application domain.</span></span>  
  
 [<span data-ttu-id="79074-113">如何：卸載應用程式定義域</span><span class="sxs-lookup"><span data-stu-id="79074-113">How to: Unload an Application Domain</span></span>](../../../docs/framework/app-domains/how-to-unload-an-application-domain.md)  
 <span data-ttu-id="79074-114">描述如何以程式設計方式卸載應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="79074-114">Describes how to programmatically unload an application domain.</span></span>  
  
 [<span data-ttu-id="79074-115">如何：設定應用程式定義域</span><span class="sxs-lookup"><span data-stu-id="79074-115">How to: Configure an Application Domain</span></span>](../../../docs/framework/app-domains/how-to-configure-an-application-domain.md)  
 <span data-ttu-id="79074-116">提供設定應用程式定義域的簡介。</span><span class="sxs-lookup"><span data-stu-id="79074-116">Provides an introduction to configuring an application domain.</span></span>  
  
 [<span data-ttu-id="79074-117">從應用程式定義域擷取安裝資訊</span><span class="sxs-lookup"><span data-stu-id="79074-117">Retrieving Setup Information from an Application Domain</span></span>](../../../docs/framework/app-domains/retrieve-setup-information.md)  
 <span data-ttu-id="79074-118">說明如何從應用程式定義域擷取安裝資訊。</span><span class="sxs-lookup"><span data-stu-id="79074-118">Describes how to retrieve setup information from an application domain.</span></span>  
  
 [<span data-ttu-id="79074-119">如何：將組件載入應用程式定義域</span><span class="sxs-lookup"><span data-stu-id="79074-119">How to: Load Assemblies into an Application Domain</span></span>](../../../docs/framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)  
 <span data-ttu-id="79074-120">說明如何將組件載入應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="79074-120">Describes how to load an assembly into an application domain.</span></span>  
  
 [<span data-ttu-id="79074-121">如何：從組件中取得類型和成員資訊</span><span class="sxs-lookup"><span data-stu-id="79074-121">How to: Obtain Type and Member Information from an Assembly</span></span>](../../../docs/framework/app-domains/how-to-obtain-type-and-member-information-from-an-assembly.md)  
 <span data-ttu-id="79074-122">說明如何擷取組件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="79074-122">Describes how to retrieve information about an assembly.</span></span>  
  
 [<span data-ttu-id="79074-123">陰影複製組件</span><span class="sxs-lookup"><span data-stu-id="79074-123">Shadow Copying Assemblies</span></span>](../../../docs/framework/app-domains/shadow-copy-assemblies.md)  
 <span data-ttu-id="79074-124">說明陰影複製如何在使用組件時更新組件，以及如何設定陰影複製。</span><span class="sxs-lookup"><span data-stu-id="79074-124">Describes how shadow copying allows updates to assemblies while they are in use, and how to configure shadow copying.</span></span>  
  
 [<span data-ttu-id="79074-125">如何：接收第一個可能發生的例外狀況通知</span><span class="sxs-lookup"><span data-stu-id="79074-125">How to: Receive First-Chance Exception Notifications</span></span>](../../../docs/framework/app-domains/how-to-receive-first-chance-exception-notifications.md)  
 <span data-ttu-id="79074-126">說明您如何在 Common Language Runtime 開始搜尋例外狀況處理常式之前，收到已擲回例外狀況的通知。</span><span class="sxs-lookup"><span data-stu-id="79074-126">Explains how you can receive a notification that an exception has been thrown, before the common language runtime has begun searching for exception handlers.</span></span>  
  
 [<span data-ttu-id="79074-127">解析組件載入</span><span class="sxs-lookup"><span data-stu-id="79074-127">Resolving Assembly Loads</span></span>](../../../docs/framework/app-domains/resolve-assembly-loads.md)  
 <span data-ttu-id="79074-128">提供使用 <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> 事件解析組件載入失敗的指引。</span><span class="sxs-lookup"><span data-stu-id="79074-128">Provides guidance on using the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event to resolve assembly load failures.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="79074-129">參考資料</span><span class="sxs-lookup"><span data-stu-id="79074-129">Reference</span></span>  
 <xref:System.AppDomain>  
 <span data-ttu-id="79074-130">代表應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="79074-130">Represents an application domain.</span></span> <span data-ttu-id="79074-131">提供建立及控制應用程式定義域的方法。</span><span class="sxs-lookup"><span data-stu-id="79074-131">Provides methods for creating and controlling application domains.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="79074-132">相關章節</span><span class="sxs-lookup"><span data-stu-id="79074-132">Related Sections</span></span>  
 [<span data-ttu-id="79074-133">Common Language Runtime 中的組件</span><span class="sxs-lookup"><span data-stu-id="79074-133">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 <span data-ttu-id="79074-134">提供組件執行函式的概觀。</span><span class="sxs-lookup"><span data-stu-id="79074-134">Provides an overview of the functions performed by assemblies.</span></span>  
  
 [<span data-ttu-id="79074-135">使用組件設計程式</span><span class="sxs-lookup"><span data-stu-id="79074-135">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 <span data-ttu-id="79074-136">描述如何建立和簽署組件，以及如何設定組件屬性。</span><span class="sxs-lookup"><span data-stu-id="79074-136">Describes how to create, sign, and set attributes on assemblies.</span></span>  
  
 [<span data-ttu-id="79074-137">發出動態方法和組件</span><span class="sxs-lookup"><span data-stu-id="79074-137">Emitting Dynamic Methods and Assemblies</span></span>](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
 <span data-ttu-id="79074-138">描述如何建立動態組件。</span><span class="sxs-lookup"><span data-stu-id="79074-138">Describes how to create dynamic assemblies.</span></span>  
  
 [<span data-ttu-id="79074-139">應用程式定義域</span><span class="sxs-lookup"><span data-stu-id="79074-139">Application Domains</span></span>](../../../docs/framework/app-domains/application-domains.md)  
 <span data-ttu-id="79074-140">提供應用程式定義域的概觀。</span><span class="sxs-lookup"><span data-stu-id="79074-140">Provides a conceptual overview of application domains.</span></span>  
  
 [<span data-ttu-id="79074-141">反映概觀</span><span class="sxs-lookup"><span data-stu-id="79074-141">Reflection Overview</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)  
 <span data-ttu-id="79074-142">描述如何使用「反映」  類別，以取得組件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="79074-142">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
