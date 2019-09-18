---
title: 使用應用程式定義域和組件設計程式
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
- application domains, programming
- programming application domains
ms.assetid: 96d3b8e3-bef8-4da0-9a81-9841e23a94e9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 84d674f7ae8e80d7a5e6a40539e3330fcfa9b563
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053121"
---
# <a name="programming-with-application-domains-and-assemblies"></a><span data-ttu-id="c1429-102">使用應用程式定義域和組件設計程式</span><span class="sxs-lookup"><span data-stu-id="c1429-102">Programming with Application Domains and Assemblies</span></span>

<span data-ttu-id="c1429-103">Microsoft Internet Explorer、ASP.NET 和 Windows 殼層這類主機會在執行 .NET Framework 應用程式時將通用語言執行平台載入至處理序、在該處理序中建立[應用程式定義域](application-domains.md)，然後在該應用程式定義域中載入並執行使用者程式碼。</span><span class="sxs-lookup"><span data-stu-id="c1429-103">Hosts such as Microsoft Internet Explorer, ASP.NET, and the Windows shell load the common language runtime into a process, create an [application domain](application-domains.md) in that process, and then load and execute user code in that application domain when running a .NET Framework application.</span></span> <span data-ttu-id="c1429-104">在大部分情況下，您不必操心如何建立應用程式定義域並載入組件，因為執行階段主機會執行這些工作。</span><span class="sxs-lookup"><span data-stu-id="c1429-104">In most cases, you do not have to worry about creating application domains and loading assemblies into them because the runtime host performs those tasks.</span></span>  
  
<span data-ttu-id="c1429-105">不過，如果您要建立將裝載通用語言執行平台的應用程式、建立您想要以程式設計方式卸載的工具或程式碼，或建立可即時卸載並重新載入的隨插即用元件，您就要建立您自己的應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="c1429-105">However, if you are creating an application that will host the common language runtime, creating tools or code you want to unload programmatically, or creating pluggable components that can be unloaded and reloaded on the fly, you will be creating your own application domains.</span></span> <span data-ttu-id="c1429-106">即使您沒有建立執行階段主機，本節仍會提供如何使用應用程式定義域，以及使用在這些應用程式定義域中載入之組件的重要資訊。</span><span class="sxs-lookup"><span data-stu-id="c1429-106">Even if you are not creating a runtime host, this section provides important information on how to work with application domains and assemblies loaded in these application domains.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c1429-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="c1429-107">In This Section</span></span>  

[<span data-ttu-id="c1429-108">應用程式定義域和組件操作說明主題</span><span class="sxs-lookup"><span data-stu-id="c1429-108">Application Domains and Assemblies How-to Topics</span></span>](application-domains-and-assemblies-how-to-topics.md)  
<span data-ttu-id="c1429-109">提供使用應用程式定義域和組件設計程式之概念文件中所有操作說明主題的連結。</span><span class="sxs-lookup"><span data-stu-id="c1429-109">Provides links to all How-to topics found in the conceptual documentation for programming with application domains and assemblies.</span></span>  
  
[<span data-ttu-id="c1429-110">使用應用程式定義域</span><span class="sxs-lookup"><span data-stu-id="c1429-110">Using Application Domains</span></span>](use.md)  
<span data-ttu-id="c1429-111">提供建立、設定及使用應用程式定義域的範例。</span><span class="sxs-lookup"><span data-stu-id="c1429-111">Provides examples of creating, configuring, and using application domains.</span></span>  
  
[<span data-ttu-id="c1429-112">使用組件設計程式</span><span class="sxs-lookup"><span data-stu-id="c1429-112">Programming with Assemblies</span></span>](../../standard/assembly/program.md)  
<span data-ttu-id="c1429-113">描述如何建立和簽署組件，以及如何設定組件屬性。</span><span class="sxs-lookup"><span data-stu-id="c1429-113">Describes how to create, sign, and set attributes on assemblies.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c1429-114">相關章節</span><span class="sxs-lookup"><span data-stu-id="c1429-114">Related Sections</span></span>  

[<span data-ttu-id="c1429-115">發出動態方法和組件</span><span class="sxs-lookup"><span data-stu-id="c1429-115">Emitting Dynamic Methods and Assemblies</span></span>](../reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
<span data-ttu-id="c1429-116">描述如何建立動態組件。</span><span class="sxs-lookup"><span data-stu-id="c1429-116">Describes how to create dynamic assemblies.</span></span>  
  
[<span data-ttu-id="c1429-117">.NET 中的組件</span><span class="sxs-lookup"><span data-stu-id="c1429-117">Assemblies in .NET</span></span>](../../standard/assembly/index.md)  
<span data-ttu-id="c1429-118">提供組件的概觀。</span><span class="sxs-lookup"><span data-stu-id="c1429-118">Provides a conceptual overview of assemblies.</span></span>  
  
[<span data-ttu-id="c1429-119">應用程式定義域</span><span class="sxs-lookup"><span data-stu-id="c1429-119">Application Domains</span></span>](application-domains.md)  
<span data-ttu-id="c1429-120">提供應用程式定義域的概觀。</span><span class="sxs-lookup"><span data-stu-id="c1429-120">Provides a conceptual overview of application domains.</span></span>  
  
[<span data-ttu-id="c1429-121">反映概觀</span><span class="sxs-lookup"><span data-stu-id="c1429-121">Reflection Overview</span></span>](../reflection-and-codedom/reflection.md)  
<span data-ttu-id="c1429-122">描述如何使用「反映」類別，以取得組件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="c1429-122">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
