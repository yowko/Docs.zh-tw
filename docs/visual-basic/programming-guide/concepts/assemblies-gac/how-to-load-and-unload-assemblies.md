---
title: HOW TO：載入和卸載組件 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: bbc84236-04b6-4c1b-9672-52773f65a5dc
ms.openlocfilehash: adfe23c2c70b1f49e23fb7c3866c8dac5c9c09ef
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54549700"
---
# <a name="how-to-load-and-unload-assemblies-visual-basic"></a><span data-ttu-id="46936-102">HOW TO：載入和卸載組件 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="46936-102">How to: Load and Unload Assemblies (Visual Basic)</span></span>
<span data-ttu-id="46936-103">您的程式所參考的組件會在建置時自動載入，不過您也可以在執行階段，將特定組件載入目前的應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="46936-103">The assemblies referenced by your program will automatically be loaded at build time, but it is also possible to load specific assemblies into the current application domain at runtime.</span></span> <span data-ttu-id="46936-104">如需詳細資訊，請參閱[＜How to：將組件載入應用程式定義域](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)。</span><span class="sxs-lookup"><span data-stu-id="46936-104">For more information, see [How to: Load Assemblies into an Application Domain](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).</span></span>  
  
 <span data-ttu-id="46936-105">若要卸載個別組件，您必須先卸載所有包含該組件的應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="46936-105">There is no way to unload an individual assembly without unloading all of the application domains that contain it.</span></span> <span data-ttu-id="46936-106">即使組件超出範圍，實際組件檔仍會保持載入狀態，直到卸載所有包含該組件的應用程式定義域為止。</span><span class="sxs-lookup"><span data-stu-id="46936-106">Even if the assembly goes out of scope, the actual assembly file will remain loaded until all application domains that contain it are unloaded.</span></span>  
  
 <span data-ttu-id="46936-107">如果您只想要卸載其中一部分組件，請考慮建立新的應用程式定義域、在該定義域內執行程式碼，然後卸載該應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="46936-107">If you want to unload some assemblies but not others, consider creating a new application domain, executing the code inside that domain, and then unloading that application domain.</span></span> <span data-ttu-id="46936-108">如需詳細資訊，請參閱[＜How to：卸載應用程式定義域](../../../../framework/app-domains/how-to-unload-an-application-domain.md)。</span><span class="sxs-lookup"><span data-stu-id="46936-108">For more information, see [How to: Unload an Application Domain](../../../../framework/app-domains/how-to-unload-an-application-domain.md).</span></span>  
  
### <a name="to-load-an-assembly-into-an-application-domain"></a><span data-ttu-id="46936-109">將組件載入應用程式定義域</span><span class="sxs-lookup"><span data-stu-id="46936-109">To load an assembly into an application domain</span></span>  
  
1.  <span data-ttu-id="46936-110">使用 <xref:System.AppDomain> 和 <xref:System.Reflection> 類別中所含之數種載入方法的其中一種。</span><span class="sxs-lookup"><span data-stu-id="46936-110">Use one of the several load methods contained in the classes <xref:System.AppDomain> and <xref:System.Reflection>.</span></span> <span data-ttu-id="46936-111">如需詳細資訊，請參閱[＜How to：將組件載入應用程式定義域](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)。</span><span class="sxs-lookup"><span data-stu-id="46936-111">For more information, see [How to: Load Assemblies into an Application Domain](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).</span></span>  
  
### <a name="to-unload-an-application-domain"></a><span data-ttu-id="46936-112">卸載應用程式定義域</span><span class="sxs-lookup"><span data-stu-id="46936-112">To unload an application domain</span></span>  
  
1.  <span data-ttu-id="46936-113">若要卸載個別組件，您必須先卸載所有包含該組件的應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="46936-113">There is no way to unload an individual assembly without unloading all of the application domains that contain it.</span></span> <span data-ttu-id="46936-114">使用 <xref:System.AppDomain> 中的 `Unload` 方法來卸載應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="46936-114">Use the `Unload` method from <xref:System.AppDomain> to unload the application domains.</span></span> <span data-ttu-id="46936-115">如需詳細資訊，請參閱[＜How to：卸載應用程式定義域](../../../../framework/app-domains/how-to-unload-an-application-domain.md)。</span><span class="sxs-lookup"><span data-stu-id="46936-115">For more information, see [How to: Unload an Application Domain](../../../../framework/app-domains/how-to-unload-an-application-domain.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46936-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="46936-116">See also</span></span>
- [<span data-ttu-id="46936-117">程式設計概念</span><span class="sxs-lookup"><span data-stu-id="46936-117">Programming Concepts</span></span>](../../../../visual-basic/programming-guide/concepts/index.md)
- [<span data-ttu-id="46936-118">組件和全域組件快取 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="46936-118">Assemblies and the Global Assembly Cache (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)
- [<span data-ttu-id="46936-119">如何：將組件載入應用程式定義域</span><span class="sxs-lookup"><span data-stu-id="46936-119">How to: Load Assemblies into an Application Domain</span></span>](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)
