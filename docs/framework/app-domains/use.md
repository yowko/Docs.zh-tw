---
title: 使用應用程式定義域
description: 使用應用程式域，提供 common language runtime (CLR) 的隔離單位。 應用程式域會在進程內建立和執行。
ms.date: 03/30/2017
helpviewer_keywords:
- application domains, about
- common language runtime, application domains
- runtime, application domains
ms.assetid: c6d99815-e022-4d2c-9420-1d7ab5b9d504
ms.openlocfilehash: 36bfc60a55c8b0374a7e542b590aa7c030ceaed6
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96272263"
---
# <a name="using-application-domains"></a><span data-ttu-id="d37bb-104">使用應用程式定義域</span><span class="sxs-lookup"><span data-stu-id="d37bb-104">Using Application Domains</span></span>

<span data-ttu-id="d37bb-105">應用程式定義域為 Common Language Runtime 提供隔離單位。</span><span class="sxs-lookup"><span data-stu-id="d37bb-105">Application domains provide a unit of isolation for the common language runtime.</span></span> <span data-ttu-id="d37bb-106">它們是在處理序內建立和執行。</span><span class="sxs-lookup"><span data-stu-id="d37bb-106">They are created and run inside a process.</span></span> <span data-ttu-id="d37bb-107">應用程式定義域通常是由執行階段主機所建立，這是負責將執行階段載入處理序以及在應用程式定義域中執行使用者程式碼的應用程式。</span><span class="sxs-lookup"><span data-stu-id="d37bb-107">Application domains are usually created by a runtime host, which is an application responsible for loading the runtime into a process and executing user code within an application domain.</span></span> <span data-ttu-id="d37bb-108">執行階段主機會建立處理序和預設的應用程式定義域，在內部執行 Managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="d37bb-108">The runtime host creates a process and a default application domain, and runs managed code inside it.</span></span> <span data-ttu-id="d37bb-109">執行階段主機包括 ASP.NET、Microsoft Internet Explorer 和 Windows 殼層。</span><span class="sxs-lookup"><span data-stu-id="d37bb-109">Runtime hosts include ASP.NET, Microsoft Internet Explorer, and the Windows shell.</span></span>  
  
<span data-ttu-id="d37bb-110">大部分的應用程式不需要建立自己的應用程式定義域，執行階段主機會為您建立任何必要的應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="d37bb-110">For most applications, you do not need to create your own application domain; the runtime host creates any necessary application domains for you.</span></span> <span data-ttu-id="d37bb-111">但如果您的應用程式需要隔離程式碼或使用及卸載 DLL，您可以建立及設定其他應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="d37bb-111">However, you can create and configure additional application domains if your application needs to isolate code or to use and unload DLLs.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d37bb-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="d37bb-112">In This Section</span></span>  

[<span data-ttu-id="d37bb-113">作法：建立應用程式定義域</span><span class="sxs-lookup"><span data-stu-id="d37bb-113">How to: Create an Application Domain</span></span>](how-to-create-an-application-domain.md)  
<span data-ttu-id="d37bb-114">描述如何以程式設計方式建立應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="d37bb-114">Describes how to programmatically create an application domain.</span></span>  
  
[<span data-ttu-id="d37bb-115">作法：卸載應用程式定義域</span><span class="sxs-lookup"><span data-stu-id="d37bb-115">How to: Unload an Application Domain</span></span>](how-to-unload-an-application-domain.md)  
<span data-ttu-id="d37bb-116">描述如何以程式設計方式卸載應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="d37bb-116">Describes how to programmatically unload an application domain.</span></span>  
  
[<span data-ttu-id="d37bb-117">作法：設定應用程式定義域</span><span class="sxs-lookup"><span data-stu-id="d37bb-117">How to: Configure an Application Domain</span></span>](how-to-configure-an-application-domain.md)  
<span data-ttu-id="d37bb-118">提供設定應用程式定義域的簡介。</span><span class="sxs-lookup"><span data-stu-id="d37bb-118">Provides an introduction to configuring an application domain.</span></span>  
  
[<span data-ttu-id="d37bb-119">從應用程式定義域擷取安裝資訊</span><span class="sxs-lookup"><span data-stu-id="d37bb-119">Retrieving Setup Information from an Application Domain</span></span>](retrieve-setup-information.md)  
<span data-ttu-id="d37bb-120">說明如何從應用程式定義域擷取安裝資訊。</span><span class="sxs-lookup"><span data-stu-id="d37bb-120">Describes how to retrieve setup information from an application domain.</span></span>  
  
[<span data-ttu-id="d37bb-121">作法：將組件載入應用程式定義域</span><span class="sxs-lookup"><span data-stu-id="d37bb-121">How to: Load Assemblies into an Application Domain</span></span>](how-to-load-assemblies-into-an-application-domain.md)  
<span data-ttu-id="d37bb-122">說明如何將組件載入應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="d37bb-122">Describes how to load an assembly into an application domain.</span></span>  
  
[<span data-ttu-id="d37bb-123">操作說明：從組件中取得類型和成員資訊</span><span class="sxs-lookup"><span data-stu-id="d37bb-123">How to: Obtain Type and Member Information from an Assembly</span></span>](../reflection-and-codedom/get-type-member-information.md)  
<span data-ttu-id="d37bb-124">說明如何擷取組件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="d37bb-124">Describes how to retrieve information about an assembly.</span></span>  
  
[<span data-ttu-id="d37bb-125">陰影複製組件</span><span class="sxs-lookup"><span data-stu-id="d37bb-125">Shadow Copying Assemblies</span></span>](shadow-copy-assemblies.md)  
<span data-ttu-id="d37bb-126">說明陰影複製如何在使用組件時更新組件，以及如何設定陰影複製。</span><span class="sxs-lookup"><span data-stu-id="d37bb-126">Describes how shadow copying allows updates to assemblies while they are in use, and how to configure shadow copying.</span></span>  
  
[<span data-ttu-id="d37bb-127">作法：接收第一個可能發生的例外狀況通知</span><span class="sxs-lookup"><span data-stu-id="d37bb-127">How to: Receive First-Chance Exception Notifications</span></span>](how-to-receive-first-chance-exception-notifications.md)  
<span data-ttu-id="d37bb-128">說明您如何在 Common Language Runtime 開始搜尋例外狀況處理常式之前，收到已擲回例外狀況的通知。</span><span class="sxs-lookup"><span data-stu-id="d37bb-128">Explains how you can receive a notification that an exception has been thrown, before the common language runtime has begun searching for exception handlers.</span></span>  
  
[<span data-ttu-id="d37bb-129">解析組件載入</span><span class="sxs-lookup"><span data-stu-id="d37bb-129">Resolving Assembly Loads</span></span>](../../standard/assembly/resolve-loads.md)  
<span data-ttu-id="d37bb-130">提供使用 <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> 事件解析組件載入失敗的指引。</span><span class="sxs-lookup"><span data-stu-id="d37bb-130">Provides guidance on using the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event to resolve assembly load failures.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="d37bb-131">參考</span><span class="sxs-lookup"><span data-stu-id="d37bb-131">Reference</span></span>  

<xref:System.AppDomain>  
<span data-ttu-id="d37bb-132">代表應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="d37bb-132">Represents an application domain.</span></span> <span data-ttu-id="d37bb-133">提供建立及控制應用程式定義域的方法。</span><span class="sxs-lookup"><span data-stu-id="d37bb-133">Provides methods for creating and controlling application domains.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d37bb-134">相關章節</span><span class="sxs-lookup"><span data-stu-id="d37bb-134">Related Sections</span></span>  

[<span data-ttu-id="d37bb-135">.NET 中的組件</span><span class="sxs-lookup"><span data-stu-id="d37bb-135">Assemblies in .NET</span></span>](../../standard/assembly/index.md)  
<span data-ttu-id="d37bb-136">提供組件執行函式的概觀。</span><span class="sxs-lookup"><span data-stu-id="d37bb-136">Provides an overview of the functions performed by assemblies.</span></span>  
  
[<span data-ttu-id="d37bb-137">使用組件設計程式</span><span class="sxs-lookup"><span data-stu-id="d37bb-137">Programming with Assemblies</span></span>](../../standard/assembly/index.md)  
<span data-ttu-id="d37bb-138">描述如何建立和簽署組件，以及如何設定組件屬性。</span><span class="sxs-lookup"><span data-stu-id="d37bb-138">Describes how to create, sign, and set attributes on assemblies.</span></span>  
  
[<span data-ttu-id="d37bb-139">發出動態方法和組件</span><span class="sxs-lookup"><span data-stu-id="d37bb-139">Emitting Dynamic Methods and Assemblies</span></span>](../reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
<span data-ttu-id="d37bb-140">描述如何建立動態組件。</span><span class="sxs-lookup"><span data-stu-id="d37bb-140">Describes how to create dynamic assemblies.</span></span>  
  
[<span data-ttu-id="d37bb-141">應用程式定義域</span><span class="sxs-lookup"><span data-stu-id="d37bb-141">Application Domains</span></span>](application-domains.md)  
<span data-ttu-id="d37bb-142">提供應用程式定義域的概觀。</span><span class="sxs-lookup"><span data-stu-id="d37bb-142">Provides a conceptual overview of application domains.</span></span>  
  
[<span data-ttu-id="d37bb-143">反映概觀</span><span class="sxs-lookup"><span data-stu-id="d37bb-143">Reflection Overview</span></span>](../reflection-and-codedom/reflection.md)  
<span data-ttu-id="d37bb-144">描述如何使用「反映」類別，以取得組件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="d37bb-144">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
