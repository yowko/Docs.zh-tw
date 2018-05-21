---
title: 如何：載入和卸載組件 (C#)
ms.date: 07/20/2015
ms.assetid: 6a4f490f-3576-471f-9533-003737cad4a3
ms.openlocfilehash: fe9f78e145e6b7bc8ef138ff5cdb98aa345b90c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-load-and-unload-assemblies-c"></a><span data-ttu-id="a5df7-102">如何：載入和卸載組件 (C#)</span><span class="sxs-lookup"><span data-stu-id="a5df7-102">How to: Load and Unload Assemblies (C#)</span></span>
<span data-ttu-id="a5df7-103">您的程式所參考的組件會在建置時自動載入，不過您也可以在執行階段，將特定組件載入目前的應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="a5df7-103">The assemblies referenced by your program will automatically be loaded at build time, but it is also possible to load specific assemblies into the current application domain at runtime.</span></span> <span data-ttu-id="a5df7-104">如需詳細資訊，請參閱[如何：將組件載入應用程式定義域](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)。</span><span class="sxs-lookup"><span data-stu-id="a5df7-104">For more information, see [How to: Load Assemblies into an Application Domain](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).</span></span>  
  
 <span data-ttu-id="a5df7-105">若要卸載個別組件，您必須先卸載所有包含該組件的應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="a5df7-105">There is no way to unload an individual assembly without unloading all of the application domains that contain it.</span></span> <span data-ttu-id="a5df7-106">即使組件超出範圍，實際組件檔仍會保持載入狀態，直到卸載所有包含該組件的應用程式定義域為止。</span><span class="sxs-lookup"><span data-stu-id="a5df7-106">Even if the assembly goes out of scope, the actual assembly file will remain loaded until all application domains that contain it are unloaded.</span></span>  
  
 <span data-ttu-id="a5df7-107">如果您只想要卸載其中一部分組件，請考慮建立新的應用程式定義域、在該定義域內執行程式碼，然後卸載該應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="a5df7-107">If you want to unload some assemblies but not others, consider creating a new application domain, executing the code inside that domain, and then unloading that application domain.</span></span> <span data-ttu-id="a5df7-108">如需詳細資訊，請參閱[如何：卸載應用程式定義域](../../../../framework/app-domains/how-to-unload-an-application-domain.md)。</span><span class="sxs-lookup"><span data-stu-id="a5df7-108">For more information, see [How to: Unload an Application Domain](../../../../framework/app-domains/how-to-unload-an-application-domain.md).</span></span>  
  
### <a name="to-load-an-assembly-into-an-application-domain"></a><span data-ttu-id="a5df7-109">將組件載入應用程式定義域</span><span class="sxs-lookup"><span data-stu-id="a5df7-109">To load an assembly into an application domain</span></span>  
  
1.  <span data-ttu-id="a5df7-110">使用 <xref:System.AppDomain> 和 <xref:System.Reflection> 類別中所含之數種載入方法的其中一種。</span><span class="sxs-lookup"><span data-stu-id="a5df7-110">Use one of the several load methods contained in the classes <xref:System.AppDomain> and <xref:System.Reflection>.</span></span> <span data-ttu-id="a5df7-111">如需詳細資訊，請參閱[如何：將組件載入應用程式定義域](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)。</span><span class="sxs-lookup"><span data-stu-id="a5df7-111">For more information, see [How to: Load Assemblies into an Application Domain](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).</span></span>  
  
### <a name="to-unload-an-application-domain"></a><span data-ttu-id="a5df7-112">卸載應用程式定義域</span><span class="sxs-lookup"><span data-stu-id="a5df7-112">To unload an application domain</span></span>  
  
1.  <span data-ttu-id="a5df7-113">若要卸載個別組件，您必須先卸載所有包含該組件的應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="a5df7-113">There is no way to unload an individual assembly without unloading all of the application domains that contain it.</span></span> <span data-ttu-id="a5df7-114">使用 <xref:System.AppDomain> 中的 `Unload` 方法來卸載應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="a5df7-114">Use the `Unload` method from <xref:System.AppDomain> to unload the application domains.</span></span> <span data-ttu-id="a5df7-115">如需詳細資訊，請參閱[如何：卸載應用程式定義域](../../../../framework/app-domains/how-to-unload-an-application-domain.md)。</span><span class="sxs-lookup"><span data-stu-id="a5df7-115">For more information, see [How to: Unload an Application Domain](../../../../framework/app-domains/how-to-unload-an-application-domain.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5df7-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="a5df7-116">See Also</span></span>  
 [<span data-ttu-id="a5df7-117">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="a5df7-117">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a5df7-118">組件和全域組件快取 (C#)</span><span class="sxs-lookup"><span data-stu-id="a5df7-118">Assemblies and the Global Assembly Cache (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="a5df7-119">如何：將組件載入應用程式定義域</span><span class="sxs-lookup"><span data-stu-id="a5df7-119">How to: Load Assemblies into an Application Domain</span></span>](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)
