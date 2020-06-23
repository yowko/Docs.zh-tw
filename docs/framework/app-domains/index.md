---
title: 使用應用程式定義域和組件設計程式
description: 瞭解如何在 .NET 中使用應用程式域和元件進行程式設計。 如需建立應用程式域 & 元件 & 範例，請參閱 how to 主題的連結。
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
- application domains, programming
- programming application domains
ms.assetid: 96d3b8e3-bef8-4da0-9a81-9841e23a94e9
ms.openlocfilehash: 1c28fe0abeb279a1dbbc6dcf043c1780c72d79df
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903434"
---
# <a name="programming-with-application-domains-and-assemblies"></a><span data-ttu-id="0f7dc-104">使用應用程式定義域和組件設計程式</span><span class="sxs-lookup"><span data-stu-id="0f7dc-104">Programming with Application Domains and Assemblies</span></span>

<span data-ttu-id="0f7dc-105">Microsoft Internet Explorer、ASP.NET 和 Windows 殼層這類主機會在執行 .NET Framework 應用程式時將通用語言執行平台載入至處理序、在該處理序中建立[應用程式定義域](application-domains.md)，然後在該應用程式定義域中載入並執行使用者程式碼。</span><span class="sxs-lookup"><span data-stu-id="0f7dc-105">Hosts such as Microsoft Internet Explorer, ASP.NET, and the Windows shell load the common language runtime into a process, create an [application domain](application-domains.md) in that process, and then load and execute user code in that application domain when running a .NET Framework application.</span></span> <span data-ttu-id="0f7dc-106">在大部分情況下，您不必操心如何建立應用程式定義域並載入組件，因為執行階段主機會執行這些工作。</span><span class="sxs-lookup"><span data-stu-id="0f7dc-106">In most cases, you do not have to worry about creating application domains and loading assemblies into them because the runtime host performs those tasks.</span></span>  
  
<span data-ttu-id="0f7dc-107">不過，如果您要建立將裝載通用語言執行平台的應用程式、建立您想要以程式設計方式卸載的工具或程式碼，或建立可即時卸載並重新載入的隨插即用元件，您就要建立您自己的應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="0f7dc-107">However, if you are creating an application that will host the common language runtime, creating tools or code you want to unload programmatically, or creating pluggable components that can be unloaded and reloaded on the fly, you will be creating your own application domains.</span></span> <span data-ttu-id="0f7dc-108">即使您沒有建立執行階段主機，本節仍會提供如何使用應用程式定義域，以及使用在這些應用程式定義域中載入之組件的重要資訊。</span><span class="sxs-lookup"><span data-stu-id="0f7dc-108">Even if you are not creating a runtime host, this section provides important information on how to work with application domains and assemblies loaded in these application domains.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0f7dc-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="0f7dc-109">In This Section</span></span>  

[<span data-ttu-id="0f7dc-110">應用程式定義域和組件 HOW TO 主題</span><span class="sxs-lookup"><span data-stu-id="0f7dc-110">Application Domains and Assemblies How-to Topics</span></span>](application-domains-and-assemblies-how-to-topics.md)  
<span data-ttu-id="0f7dc-111">提供使用應用程式定義域和組件設計程式之概念文件中所有操作說明主題的連結。</span><span class="sxs-lookup"><span data-stu-id="0f7dc-111">Provides links to all How-to topics found in the conceptual documentation for programming with application domains and assemblies.</span></span>  
  
[<span data-ttu-id="0f7dc-112">使用應用程式定義域</span><span class="sxs-lookup"><span data-stu-id="0f7dc-112">Using Application Domains</span></span>](use.md)  
<span data-ttu-id="0f7dc-113">提供建立、設定及使用應用程式定義域的範例。</span><span class="sxs-lookup"><span data-stu-id="0f7dc-113">Provides examples of creating, configuring, and using application domains.</span></span>  
  
[<span data-ttu-id="0f7dc-114">使用組件設計程式</span><span class="sxs-lookup"><span data-stu-id="0f7dc-114">Programming with Assemblies</span></span>](../../standard/assembly/index.md)  
<span data-ttu-id="0f7dc-115">描述如何建立和簽署組件，以及如何設定組件屬性。</span><span class="sxs-lookup"><span data-stu-id="0f7dc-115">Describes how to create, sign, and set attributes on assemblies.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0f7dc-116">相關章節</span><span class="sxs-lookup"><span data-stu-id="0f7dc-116">Related Sections</span></span>  

[<span data-ttu-id="0f7dc-117">發出動態方法和組件</span><span class="sxs-lookup"><span data-stu-id="0f7dc-117">Emitting Dynamic Methods and Assemblies</span></span>](../reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
<span data-ttu-id="0f7dc-118">描述如何建立動態組件。</span><span class="sxs-lookup"><span data-stu-id="0f7dc-118">Describes how to create dynamic assemblies.</span></span>  
  
[<span data-ttu-id="0f7dc-119">.NET 中的組件</span><span class="sxs-lookup"><span data-stu-id="0f7dc-119">Assemblies in .NET</span></span>](../../standard/assembly/index.md)  
<span data-ttu-id="0f7dc-120">提供組件的概觀。</span><span class="sxs-lookup"><span data-stu-id="0f7dc-120">Provides a conceptual overview of assemblies.</span></span>  
  
[<span data-ttu-id="0f7dc-121">應用程式定義域</span><span class="sxs-lookup"><span data-stu-id="0f7dc-121">Application Domains</span></span>](application-domains.md)  
<span data-ttu-id="0f7dc-122">提供應用程式定義域的概觀。</span><span class="sxs-lookup"><span data-stu-id="0f7dc-122">Provides a conceptual overview of application domains.</span></span>  
  
[<span data-ttu-id="0f7dc-123">反映概觀</span><span class="sxs-lookup"><span data-stu-id="0f7dc-123">Reflection Overview</span></span>](../reflection-and-codedom/reflection.md)  
<span data-ttu-id="0f7dc-124">描述如何使用「反映」\*\*\*\* 類別，以取得組件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="0f7dc-124">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
