---
title: 使用應用程式定義域
ms.date: 03/30/2017
helpviewer_keywords:
- application domains, about
- common language runtime, application domains
- runtime, application domains
ms.assetid: c6d99815-e022-4d2c-9420-1d7ab5b9d504
ms.openlocfilehash: d6bbc2648608e9542158e0f281984174447633a4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119730"
---
# <a name="using-application-domains"></a><span data-ttu-id="702fc-102">使用應用程式定義域</span><span class="sxs-lookup"><span data-stu-id="702fc-102">Using Application Domains</span></span>

<span data-ttu-id="702fc-103">應用程式定義域為 Common Language Runtime 提供隔離單位。</span><span class="sxs-lookup"><span data-stu-id="702fc-103">Application domains provide a unit of isolation for the common language runtime.</span></span> <span data-ttu-id="702fc-104">它們是在處理序內建立和執行。</span><span class="sxs-lookup"><span data-stu-id="702fc-104">They are created and run inside a process.</span></span> <span data-ttu-id="702fc-105">應用程式定義域通常是由執行階段主機所建立，這是負責將執行階段載入處理序以及在應用程式定義域中執行使用者程式碼的應用程式。</span><span class="sxs-lookup"><span data-stu-id="702fc-105">Application domains are usually created by a runtime host, which is an application responsible for loading the runtime into a process and executing user code within an application domain.</span></span> <span data-ttu-id="702fc-106">執行階段主機會建立處理序和預設的應用程式定義域，在內部執行 Managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="702fc-106">The runtime host creates a process and a default application domain, and runs managed code inside it.</span></span> <span data-ttu-id="702fc-107">執行階段主機包括 ASP.NET、Microsoft Internet Explorer 和 Windows 殼層。</span><span class="sxs-lookup"><span data-stu-id="702fc-107">Runtime hosts include ASP.NET, Microsoft Internet Explorer, and the Windows shell.</span></span>  
  
<span data-ttu-id="702fc-108">大部分的應用程式不需要建立自己的應用程式定義域，執行階段主機會為您建立任何必要的應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="702fc-108">For most applications, you do not need to create your own application domain; the runtime host creates any necessary application domains for you.</span></span> <span data-ttu-id="702fc-109">但如果您的應用程式需要隔離程式碼或使用及卸載 DLL，您可以建立及設定其他應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="702fc-109">However, you can create and configure additional application domains if your application needs to isolate code or to use and unload DLLs.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="702fc-110">本章節內容</span><span class="sxs-lookup"><span data-stu-id="702fc-110">In This Section</span></span>  

[<span data-ttu-id="702fc-111">操作說明：建立應用程式定義域</span><span class="sxs-lookup"><span data-stu-id="702fc-111">How to: Create an Application Domain</span></span>](how-to-create-an-application-domain.md)  
<span data-ttu-id="702fc-112">描述如何以程式設計方式建立應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="702fc-112">Describes how to programmatically create an application domain.</span></span>  
  
[<span data-ttu-id="702fc-113">操作說明：卸載應用程式定義域</span><span class="sxs-lookup"><span data-stu-id="702fc-113">How to: Unload an Application Domain</span></span>](how-to-unload-an-application-domain.md)  
<span data-ttu-id="702fc-114">描述如何以程式設計方式卸載應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="702fc-114">Describes how to programmatically unload an application domain.</span></span>  
  
[<span data-ttu-id="702fc-115">操作說明：設定應用程式定義域</span><span class="sxs-lookup"><span data-stu-id="702fc-115">How to: Configure an Application Domain</span></span>](how-to-configure-an-application-domain.md)  
<span data-ttu-id="702fc-116">提供設定應用程式定義域的簡介。</span><span class="sxs-lookup"><span data-stu-id="702fc-116">Provides an introduction to configuring an application domain.</span></span>  
  
[<span data-ttu-id="702fc-117">從應用程式定義域擷取安裝資訊</span><span class="sxs-lookup"><span data-stu-id="702fc-117">Retrieving Setup Information from an Application Domain</span></span>](retrieve-setup-information.md)  
<span data-ttu-id="702fc-118">說明如何從應用程式定義域擷取安裝資訊。</span><span class="sxs-lookup"><span data-stu-id="702fc-118">Describes how to retrieve setup information from an application domain.</span></span>  
  
[<span data-ttu-id="702fc-119">操作說明：將組件載入應用程式定義域</span><span class="sxs-lookup"><span data-stu-id="702fc-119">How to: Load Assemblies into an Application Domain</span></span>](how-to-load-assemblies-into-an-application-domain.md)  
<span data-ttu-id="702fc-120">說明如何將組件載入應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="702fc-120">Describes how to load an assembly into an application domain.</span></span>  
  
[<span data-ttu-id="702fc-121">操作說明：從組件中取得類型和成員資訊</span><span class="sxs-lookup"><span data-stu-id="702fc-121">How to: Obtain Type and Member Information from an Assembly</span></span>](../reflection-and-codedom/get-type-member-information.md)  
<span data-ttu-id="702fc-122">說明如何擷取組件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="702fc-122">Describes how to retrieve information about an assembly.</span></span>  
  
[<span data-ttu-id="702fc-123">陰影複製組件</span><span class="sxs-lookup"><span data-stu-id="702fc-123">Shadow Copying Assemblies</span></span>](shadow-copy-assemblies.md)  
<span data-ttu-id="702fc-124">說明陰影複製如何在使用組件時更新組件，以及如何設定陰影複製。</span><span class="sxs-lookup"><span data-stu-id="702fc-124">Describes how shadow copying allows updates to assemblies while they are in use, and how to configure shadow copying.</span></span>  
  
[<span data-ttu-id="702fc-125">操作說明：接收第一個可能發生的例外狀況通知</span><span class="sxs-lookup"><span data-stu-id="702fc-125">How to: Receive First-Chance Exception Notifications</span></span>](how-to-receive-first-chance-exception-notifications.md)  
<span data-ttu-id="702fc-126">說明您如何在 Common Language Runtime 開始搜尋例外狀況處理常式之前，收到已擲回例外狀況的通知。</span><span class="sxs-lookup"><span data-stu-id="702fc-126">Explains how you can receive a notification that an exception has been thrown, before the common language runtime has begun searching for exception handlers.</span></span>  
  
[<span data-ttu-id="702fc-127">解析組件載入</span><span class="sxs-lookup"><span data-stu-id="702fc-127">Resolving Assembly Loads</span></span>](../../standard/assembly/resolve-loads.md)  
<span data-ttu-id="702fc-128">提供使用 <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> 事件解析組件載入失敗的指引。</span><span class="sxs-lookup"><span data-stu-id="702fc-128">Provides guidance on using the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event to resolve assembly load failures.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="702fc-129">參考資料</span><span class="sxs-lookup"><span data-stu-id="702fc-129">Reference</span></span>  

<xref:System.AppDomain>  
<span data-ttu-id="702fc-130">代表應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="702fc-130">Represents an application domain.</span></span> <span data-ttu-id="702fc-131">提供建立及控制應用程式定義域的方法。</span><span class="sxs-lookup"><span data-stu-id="702fc-131">Provides methods for creating and controlling application domains.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="702fc-132">相關章節</span><span class="sxs-lookup"><span data-stu-id="702fc-132">Related Sections</span></span>  
[<span data-ttu-id="702fc-133">.NET 中的組件</span><span class="sxs-lookup"><span data-stu-id="702fc-133">Assemblies in .NET</span></span>](../../standard/assembly/index.md)  
<span data-ttu-id="702fc-134">提供組件執行函式的概觀。</span><span class="sxs-lookup"><span data-stu-id="702fc-134">Provides an overview of the functions performed by assemblies.</span></span>  
  
[<span data-ttu-id="702fc-135">使用組件設計程式</span><span class="sxs-lookup"><span data-stu-id="702fc-135">Programming with Assemblies</span></span>](../../standard/assembly/program.md)  
<span data-ttu-id="702fc-136">描述如何建立和簽署組件，以及如何設定組件屬性。</span><span class="sxs-lookup"><span data-stu-id="702fc-136">Describes how to create, sign, and set attributes on assemblies.</span></span>  
  
[<span data-ttu-id="702fc-137">發出動態方法和組件</span><span class="sxs-lookup"><span data-stu-id="702fc-137">Emitting Dynamic Methods and Assemblies</span></span>](../reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
<span data-ttu-id="702fc-138">描述如何建立動態組件。</span><span class="sxs-lookup"><span data-stu-id="702fc-138">Describes how to create dynamic assemblies.</span></span>  
  
[<span data-ttu-id="702fc-139">應用程式定義域</span><span class="sxs-lookup"><span data-stu-id="702fc-139">Application Domains</span></span>](application-domains.md)  
<span data-ttu-id="702fc-140">提供應用程式定義域的概觀。</span><span class="sxs-lookup"><span data-stu-id="702fc-140">Provides a conceptual overview of application domains.</span></span>  
  
[<span data-ttu-id="702fc-141">反映概觀</span><span class="sxs-lookup"><span data-stu-id="702fc-141">Reflection Overview</span></span>](../reflection-and-codedom/reflection.md)  
<span data-ttu-id="702fc-142">描述如何使用「反映」類別，以取得組件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="702fc-142">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
