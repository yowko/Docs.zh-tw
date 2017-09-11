---
title: "使用應用程式定義域和組件設計程式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
- application domains, programming
- programming application domains
ms.assetid: 96d3b8e3-bef8-4da0-9a81-9841e23a94e9
caps.latest.revision: 11
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 6dcf8e4c9bf2401309b1d80d2306bd619b96460d
ms.contentlocale: zh-tw
ms.lasthandoff: 09/05/2017

---
# <a name="programming-with-application-domains-and-assemblies"></a><span data-ttu-id="d06cd-102">使用應用程式定義域和組件設計程式</span><span class="sxs-lookup"><span data-stu-id="d06cd-102">Programming with Application Domains and Assemblies</span></span>
<span data-ttu-id="d06cd-103">Microsoft Internet Explorer、ASP.NET 和 Windows 殼層這類主機會在執行 .NET Framework 應用程式時將通用語言執行平台載入至處理序、在該處理序中建立[應用程式定義域](../../../docs/framework/app-domains/application-domains.md)，然後在該應用程式定義域中載入並執行使用者程式碼。</span><span class="sxs-lookup"><span data-stu-id="d06cd-103">Hosts such as Microsoft Internet Explorer, ASP.NET, and the Windows shell load the common language runtime into a process, create an [application domain](../../../docs/framework/app-domains/application-domains.md) in that process, and then load and execute user code in that application domain when running a .NET Framework application.</span></span> <span data-ttu-id="d06cd-104">在大部分情況下，您不必操心如何建立應用程式定義域並載入組件，因為執行階段主機會執行這些工作。</span><span class="sxs-lookup"><span data-stu-id="d06cd-104">In most cases, you do not have to worry about creating application domains and loading assemblies into them because the runtime host performs those tasks.</span></span>  
  
 <span data-ttu-id="d06cd-105">不過，如果您要建立將裝載通用語言執行平台的應用程式、建立您想要以程式設計方式卸載的工具或程式碼，或建立可即時卸載並重新載入的隨插即用元件，您就要建立您自己的應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="d06cd-105">However, if you are creating an application that will host the common language runtime, creating tools or code you want to unload programmatically, or creating pluggable components that can be unloaded and reloaded on the fly, you will be creating your own application domains.</span></span> <span data-ttu-id="d06cd-106">即使您沒有建立執行階段主機，本節仍會提供如何使用應用程式定義域，以及使用在這些應用程式定義域中載入之組件的重要資訊。</span><span class="sxs-lookup"><span data-stu-id="d06cd-106">Even if you are not creating a runtime host, this section provides important information on how to work with application domains and assemblies loaded in these application domains.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d06cd-107">本章節內容</span><span class="sxs-lookup"><span data-stu-id="d06cd-107">In This Section</span></span>  
 [<span data-ttu-id="d06cd-108">應用程式定義域和組件操作說明主題</span><span class="sxs-lookup"><span data-stu-id="d06cd-108">Application Domains and Assemblies How-to Topics</span></span>](../../../docs/framework/app-domains/application-domains-and-assemblies-how-to-topics.md)  
 <span data-ttu-id="d06cd-109">提供使用應用程式定義域和組件設計程式之概念文件中所有操作說明主題的連結。</span><span class="sxs-lookup"><span data-stu-id="d06cd-109">Provides links to all How-to topics found in the conceptual documentation for programming with application domains and assemblies.</span></span>  
  
 [<span data-ttu-id="d06cd-110">使用應用程式定義域</span><span class="sxs-lookup"><span data-stu-id="d06cd-110">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)  
 <span data-ttu-id="d06cd-111">提供建立、設定及使用應用程式定義域的範例。</span><span class="sxs-lookup"><span data-stu-id="d06cd-111">Provides examples of creating, configuring, and using application domains.</span></span>  
  
 [<span data-ttu-id="d06cd-112">使用組件設計程式</span><span class="sxs-lookup"><span data-stu-id="d06cd-112">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 <span data-ttu-id="d06cd-113">描述如何建立和簽署組件，以及如何設定組件屬性。</span><span class="sxs-lookup"><span data-stu-id="d06cd-113">Describes how to create, sign, and set attributes on assemblies.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d06cd-114">相關章節</span><span class="sxs-lookup"><span data-stu-id="d06cd-114">Related Sections</span></span>  
 [<span data-ttu-id="d06cd-115">發出動態方法和組件</span><span class="sxs-lookup"><span data-stu-id="d06cd-115">Emitting Dynamic Methods and Assemblies</span></span>](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
 <span data-ttu-id="d06cd-116">描述如何建立動態組件。</span><span class="sxs-lookup"><span data-stu-id="d06cd-116">Describes how to create dynamic assemblies.</span></span>  
  
 [<span data-ttu-id="d06cd-117">Common Language Runtime 中的組件</span><span class="sxs-lookup"><span data-stu-id="d06cd-117">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 <span data-ttu-id="d06cd-118">提供組件的概觀。</span><span class="sxs-lookup"><span data-stu-id="d06cd-118">Provides a conceptual overview of assemblies.</span></span>  
  
 [<span data-ttu-id="d06cd-119">應用程式定義域</span><span class="sxs-lookup"><span data-stu-id="d06cd-119">Application Domains</span></span>](../../../docs/framework/app-domains/application-domains.md)  
 <span data-ttu-id="d06cd-120">提供應用程式定義域的概觀。</span><span class="sxs-lookup"><span data-stu-id="d06cd-120">Provides a conceptual overview of application domains.</span></span>  
  
 [<span data-ttu-id="d06cd-121">反映概觀</span><span class="sxs-lookup"><span data-stu-id="d06cd-121">Reflection Overview</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)  
 <span data-ttu-id="d06cd-122">描述如何使用「反映」類別，以取得組件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="d06cd-122">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>

