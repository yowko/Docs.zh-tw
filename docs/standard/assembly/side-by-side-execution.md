---
title: 組件和並存執行
ms.date: 08/20/2019
helpviewer_keywords:
- side-by-side execution [.NET Framework]
- assemblies [.NET Framework], side-by-side execution
ms.assetid: e42036ee-7590-47d1-b884-cc856e39bd5d
ms.openlocfilehash: 234efba66d87b520b54d6d113afcc4bba0bfe06a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138635"
---
# <a name="assemblies-and-side-by-side-execution"></a><span data-ttu-id="cf271-102">組件和並存執行</span><span class="sxs-lookup"><span data-stu-id="cf271-102">Assemblies and side-by-side execution</span></span>

<span data-ttu-id="cf271-103">並存執行是可以在同一台電腦上儲存和執行多版應用程式或元件的能力。</span><span class="sxs-lookup"><span data-stu-id="cf271-103">Side-by-side execution is the ability to store and execute multiple versions of an application or component on the same computer.</span></span> <span data-ttu-id="cf271-104">這表示您可以同時在同一台電腦上擁有多版執行階段、多版應用程式和多個使用一個執行階段版本的元件。</span><span class="sxs-lookup"><span data-stu-id="cf271-104">This means that you can have multiple versions of the runtime, and multiple versions of applications and components that use a version of the runtime, on the same computer at the same time.</span></span> <span data-ttu-id="cf271-105">並存執行讓您可以進一步控制應用程式繫結到的元件版本，也能進一步控制應用程式所使用的執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="cf271-105">Side-by-side execution gives you more control over what versions of a component an application binds to, and more control over what version of the runtime an application uses.</span></span>  
  
<span data-ttu-id="cf271-106">支援並存儲存和執行同一組件的不同版本，是強式命名所不可或缺的部分，而且已內建至執行階段的基礎結構中。</span><span class="sxs-lookup"><span data-stu-id="cf271-106">Support for side-by-side storage and execution of different versions of the same assembly is an integral part of strong naming and is built into the infrastructure of the runtime.</span></span> <span data-ttu-id="cf271-107">由於強式名稱組件的版本號碼是其識別的一部分，所以執行階段可以在全域組件快取中存放相同組件的多個版本，並且在 Run Time 載入這些組件。</span><span class="sxs-lookup"><span data-stu-id="cf271-107">Because the strong-named assembly's version number is part of its identity, the runtime can store multiple versions of the same assembly in the global assembly cache and load those assemblies at run time.</span></span>  
  
<span data-ttu-id="cf271-108">雖然執行階段為您提供建立並存應用程式的能力，但是並存執行並非自動的。</span><span class="sxs-lookup"><span data-stu-id="cf271-108">Although the runtime provides you with the ability to create side-by-side applications, side-by-side execution is not automatic.</span></span> <span data-ttu-id="cf271-109">有關創建應用程式以進行並存執行的詳細資訊，請參閱[創建元件以進行並存執行的指南](../../framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md)。</span><span class="sxs-lookup"><span data-stu-id="cf271-109">For more information on creating applications for side-by-side execution, see [Guidelines for creating components for side-by-side execution](../../framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf271-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cf271-110">See also</span></span>

- [<span data-ttu-id="cf271-111">運行時如何定位程式集</span><span class="sxs-lookup"><span data-stu-id="cf271-111">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="cf271-112">.NET 中的組件</span><span class="sxs-lookup"><span data-stu-id="cf271-112">Assemblies in .NET</span></span>](index.md)
