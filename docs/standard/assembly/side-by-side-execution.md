---
title: 組件和並存執行
description: 深入瞭解並存執行，這是在同一部電腦上儲存和執行多個版本之應用程式或元件的能力。
ms.date: 08/20/2019
helpviewer_keywords:
- side-by-side execution [.NET]
- assemblies [.NET], side-by-side execution
ms.assetid: e42036ee-7590-47d1-b884-cc856e39bd5d
ms.openlocfilehash: 7bedd5a384ceace014412eb894adad5c92c00b05
ms.sourcegitcommit: 279fb6e8d515df51676528a7424a1df2f0917116
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92687980"
---
# <a name="assemblies-and-side-by-side-execution"></a><span data-ttu-id="8f037-103">組件和並存執行</span><span class="sxs-lookup"><span data-stu-id="8f037-103">Assemblies and side-by-side execution</span></span>

<span data-ttu-id="8f037-104">並存執行是可以在同一台電腦上儲存和執行多版應用程式或元件的能力。</span><span class="sxs-lookup"><span data-stu-id="8f037-104">Side-by-side execution is the ability to store and execute multiple versions of an application or component on the same computer.</span></span> <span data-ttu-id="8f037-105">這表示您可以同時在同一台電腦上擁有多版執行階段、多版應用程式和多個使用一個執行階段版本的元件。</span><span class="sxs-lookup"><span data-stu-id="8f037-105">This means that you can have multiple versions of the runtime, and multiple versions of applications and components that use a version of the runtime, on the same computer at the same time.</span></span> <span data-ttu-id="8f037-106">並存執行讓您可以進一步控制應用程式繫結到的元件版本，也能進一步控制應用程式所使用的執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="8f037-106">Side-by-side execution gives you more control over what versions of a component an application binds to, and more control over what version of the runtime an application uses.</span></span>  
  
<span data-ttu-id="8f037-107">支援並存儲存和執行同一組件的不同版本，是強式命名所不可或缺的部分，而且已內建至執行階段的基礎結構中。</span><span class="sxs-lookup"><span data-stu-id="8f037-107">Support for side-by-side storage and execution of different versions of the same assembly is an integral part of strong naming and is built into the infrastructure of the runtime.</span></span> <span data-ttu-id="8f037-108">由於強式名稱組件的版本號碼是其識別的一部分，所以執行階段可以在全域組件快取中存放相同組件的多個版本，並且在 Run Time 載入這些組件。</span><span class="sxs-lookup"><span data-stu-id="8f037-108">Because the strong-named assembly's version number is part of its identity, the runtime can store multiple versions of the same assembly in the global assembly cache and load those assemblies at run time.</span></span>  
  
<span data-ttu-id="8f037-109">雖然執行階段為您提供建立並存應用程式的能力，但是並存執行並非自動的。</span><span class="sxs-lookup"><span data-stu-id="8f037-109">Although the runtime provides you with the ability to create side-by-side applications, side-by-side execution is not automatic.</span></span> <span data-ttu-id="8f037-110">如需有關建立並存執行之應用程式的詳細資訊，請參閱 [建立並存執行元件的指導方針](../../framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md)。</span><span class="sxs-lookup"><span data-stu-id="8f037-110">For more information on creating applications for side-by-side execution, see [Guidelines for creating components for side-by-side execution](../../framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f037-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="8f037-111">See also</span></span>

- [<span data-ttu-id="8f037-112">執行時間如何找出元件</span><span class="sxs-lookup"><span data-stu-id="8f037-112">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="8f037-113">.NET 中的組件</span><span class="sxs-lookup"><span data-stu-id="8f037-113">Assemblies in .NET</span></span>](index.md)
