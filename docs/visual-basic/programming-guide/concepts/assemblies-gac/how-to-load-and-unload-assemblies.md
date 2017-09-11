---
title: "如何︰ 載入和卸載組件 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: bbc84236-04b6-4c1b-9672-52773f65a5dc
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 2e38be72bb58573b532fa42a569563df0be8301d
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-load-and-unload-assemblies-visual-basic"></a><span data-ttu-id="a5479-102">如何︰ 載入和卸載組件 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a5479-102">How to: Load and Unload Assemblies (Visual Basic)</span></span>
<span data-ttu-id="a5479-103">您的程式所參考的組件會自動載入在建置階段，但是也可以在特定的組件載入目前應用程式定義域在執行階段。</span><span class="sxs-lookup"><span data-stu-id="a5479-103">The assemblies referenced by your program will automatically be loaded at build time, but it is also possible to load specific assemblies into the current application domain at runtime.</span></span> <span data-ttu-id="a5479-104">如需詳細資訊，請參閱[How to︰ 載入組件的應用程式定義域](http://msdn.microsoft.com/library/1432aa2d-bd83-4346-bf3b-a1b7920e2aa9)。</span><span class="sxs-lookup"><span data-stu-id="a5479-104">For more information, see [How to: Load Assemblies into an Application Domain](http://msdn.microsoft.com/library/1432aa2d-bd83-4346-bf3b-a1b7920e2aa9).</span></span>  
  
 <span data-ttu-id="a5479-105">沒有任何方法，而不需卸載所有包含它之應用程式定義域卸載個別組件。</span><span class="sxs-lookup"><span data-stu-id="a5479-105">There is no way to unload an individual assembly without unloading all of the application domains that contain it.</span></span> <span data-ttu-id="a5479-106">即使組件超出範圍時，實際的組件檔會保持載入，直到包含它的所有應用程式定義域，就會卸載。</span><span class="sxs-lookup"><span data-stu-id="a5479-106">Even if the assembly goes out of scope, the actual assembly file will remain loaded until all application domains that contain it are unloaded.</span></span>  
  
 <span data-ttu-id="a5479-107">如果您想要卸載某些組件而非其他電腦，請考慮建立新的應用程式定義域執行該網域內的程式碼，然後卸載該應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="a5479-107">If you want to unload some assemblies but not others, consider creating a new application domain, executing the code inside that domain, and then unloading that application domain.</span></span> <span data-ttu-id="a5479-108">如需詳細資訊，請參閱[如何︰ 卸載應用程式定義域](http://msdn.microsoft.com/library/f356116d-e415-4f7c-a332-6e6a60227192)。</span><span class="sxs-lookup"><span data-stu-id="a5479-108">For more information, see [How to: Unload an Application Domain](http://msdn.microsoft.com/library/f356116d-e415-4f7c-a332-6e6a60227192).</span></span>  
  
### <a name="to-load-an-assembly-into-an-application-domain"></a><span data-ttu-id="a5479-109">應用程式定義域載入組件</span><span class="sxs-lookup"><span data-stu-id="a5479-109">To load an assembly into an application domain</span></span>  
  
1.  <span data-ttu-id="a5479-110">使用其中一種類別<xref:System.AppDomain>和<xref:System.Reflection>.</xref:System.Reflection></xref:System.AppDomain>中所包含的載入方法</span><span class="sxs-lookup"><span data-stu-id="a5479-110">Use one of the several load methods contained in the classes <xref:System.AppDomain> and <xref:System.Reflection>.</span></span> <span data-ttu-id="a5479-111">如需詳細資訊，請參閱[How to︰ 載入組件的應用程式定義域](http://msdn.microsoft.com/library/1432aa2d-bd83-4346-bf3b-a1b7920e2aa9)。</span><span class="sxs-lookup"><span data-stu-id="a5479-111">For more information, see [How to: Load Assemblies into an Application Domain](http://msdn.microsoft.com/library/1432aa2d-bd83-4346-bf3b-a1b7920e2aa9).</span></span>  
  
### <a name="to-unload-an-application-domain"></a><span data-ttu-id="a5479-112">卸載應用程式定義域</span><span class="sxs-lookup"><span data-stu-id="a5479-112">To unload an application domain</span></span>  
  
1.  <span data-ttu-id="a5479-113">沒有任何方法，而不需卸載所有包含它之應用程式定義域卸載個別組件。</span><span class="sxs-lookup"><span data-stu-id="a5479-113">There is no way to unload an individual assembly without unloading all of the application domains that contain it.</span></span> <span data-ttu-id="a5479-114">使用`Unload`方法從<xref:System.AppDomain>卸載應用程式定義域。</xref:System.AppDomain></span><span class="sxs-lookup"><span data-stu-id="a5479-114">Use the `Unload` method from <xref:System.AppDomain> to unload the application domains.</span></span> <span data-ttu-id="a5479-115">如需詳細資訊，請參閱[如何︰ 卸載應用程式定義域](http://msdn.microsoft.com/library/f356116d-e415-4f7c-a332-6e6a60227192)。</span><span class="sxs-lookup"><span data-stu-id="a5479-115">For more information, see [How to: Unload an Application Domain](http://msdn.microsoft.com/library/f356116d-e415-4f7c-a332-6e6a60227192).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5479-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a5479-116">See Also</span></span>  
 <span data-ttu-id="a5479-117">[程式設計概念](../../../../visual-basic/programming-guide/concepts/index.md) </span><span class="sxs-lookup"><span data-stu-id="a5479-117">[Programming Concepts](../../../../visual-basic/programming-guide/concepts/index.md) </span></span>  
<span data-ttu-id="a5479-118"> [組件和全域組件快取 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span><span class="sxs-lookup"><span data-stu-id="a5479-118"> [Assemblies and the Global Assembly Cache (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span></span>  
<span data-ttu-id="a5479-119"> [如何︰ 將應用程式定義域載入組件](http://msdn.microsoft.com/library/1432aa2d-bd83-4346-bf3b-a1b7920e2aa9)</span><span class="sxs-lookup"><span data-stu-id="a5479-119"> [How to: Load Assemblies into an Application Domain](http://msdn.microsoft.com/library/1432aa2d-bd83-4346-bf3b-a1b7920e2aa9)</span></span>
