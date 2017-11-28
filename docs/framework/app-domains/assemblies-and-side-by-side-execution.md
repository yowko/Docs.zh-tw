---
title: "組件和並存執行"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- side-by-side execution [.NET Framework]
- assemblies [.NET Framework], side-by-side execution
ms.assetid: e42036ee-7590-47d1-b884-cc856e39bd5d
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d0f5e5d0e9a2385d3ebf1c2f1dc7838de79b27e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="assemblies-and-side-by-side-execution"></a><span data-ttu-id="dc902-102">組件和並存執行</span><span class="sxs-lookup"><span data-stu-id="dc902-102">Assemblies and Side-by-Side Execution</span></span>
<span data-ttu-id="dc902-103">並存執行是可以在同一台電腦上儲存和執行多版應用程式或元件的能力。</span><span class="sxs-lookup"><span data-stu-id="dc902-103">Side-by-side execution is the ability to store and execute multiple versions of an application or component on the same computer.</span></span> <span data-ttu-id="dc902-104">這表示您可以同時在同一台電腦上擁有多版執行階段、多版應用程式和多個使用一個執行階段版本的元件。</span><span class="sxs-lookup"><span data-stu-id="dc902-104">This means that you can have multiple versions of the runtime, and multiple versions of applications and components that use a version of the runtime, on the same computer at the same time.</span></span> <span data-ttu-id="dc902-105">並存執行讓您可以進一步控制應用程式繫結到的元件版本，也能進一步控制應用程式所使用的執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="dc902-105">Side-by-side execution gives you more control over what versions of a component an application binds to, and more control over what version of the runtime an application uses.</span></span>  
  
 <span data-ttu-id="dc902-106">支援並存儲存和執行同一組件的不同版本，是強式命名所不可或缺的部分，而且已內建至執行階段的基礎結構中。</span><span class="sxs-lookup"><span data-stu-id="dc902-106">Support for side-by-side storage and execution of different versions of the same assembly is an integral part of strong naming and is built into the infrastructure of the runtime.</span></span> <span data-ttu-id="dc902-107">由於強式名稱組件的版本號碼是其識別的一部分，所以執行階段可以在全域組件快取中存放相同組件的多個版本，並且在 Run Time 載入這些組件。</span><span class="sxs-lookup"><span data-stu-id="dc902-107">Because the strong-named assembly's version number is part of its identity, the runtime can store multiple versions of the same assembly in the global assembly cache and load those assemblies at run time.</span></span>  
  
 <span data-ttu-id="dc902-108">雖然執行階段為您提供建立並存應用程式的能力，但是並存執行並非自動的。</span><span class="sxs-lookup"><span data-stu-id="dc902-108">Although the runtime provides you with the ability to create side-by-side applications, side-by-side execution is not automatic.</span></span> <span data-ttu-id="dc902-109">如需建立並存執行應用程式的詳細資訊，請參閱[建立並存執行元件的方針](../../../docs/framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md)。</span><span class="sxs-lookup"><span data-stu-id="dc902-109">For more information on creating applications for side-by-side execution, see [Guidelines for Creating Components for Side-by-Side Execution](../../../docs/framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc902-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc902-110">See Also</span></span>  
 [<span data-ttu-id="dc902-111">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="dc902-111">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="dc902-112">Common Language Runtime 中的組件</span><span class="sxs-lookup"><span data-stu-id="dc902-112">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
