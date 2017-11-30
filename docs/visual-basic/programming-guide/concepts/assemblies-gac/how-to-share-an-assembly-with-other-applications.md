---
title: "如何： 共用組件與其他應用程式 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5388aedc-cb42-4622-8b70-8e701eee057a
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 491791ba9b6f0cf6da86a160eddf8e78109b11c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-share-an-assembly-with-other-applications-visual-basic"></a><span data-ttu-id="9f59f-102">如何： 共用組件與其他應用程式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9f59f-102">How to: Share an Assembly with Other Applications (Visual Basic)</span></span>
<span data-ttu-id="9f59f-103">組件可以是私用或共用的︰根據預設，大多數簡單的程式由於不會供其他應用程式使用，因此只會包含一個私用組件。</span><span class="sxs-lookup"><span data-stu-id="9f59f-103">Assemblies can be private or shared: by default, most simple programs consist of a private assembly because they are not intended to be used by other applications.</span></span>  
  
 <span data-ttu-id="9f59f-104">為了與其他應用程式共用組件，必須將該組件放在[全域組件快取](../../../../framework/app-domains/gac.md) (GAC) 中。</span><span class="sxs-lookup"><span data-stu-id="9f59f-104">In order to share an assembly with other applications, it must be placed in the [Global Assembly Cache](../../../../framework/app-domains/gac.md) (GAC).</span></span>  
  
### <a name="sharing-an-assembly"></a><span data-ttu-id="9f59f-105">共用組件</span><span class="sxs-lookup"><span data-stu-id="9f59f-105">Sharing an assembly</span></span>  
  
1.  <span data-ttu-id="9f59f-106">建立您的組件。</span><span class="sxs-lookup"><span data-stu-id="9f59f-106">Create your assembly.</span></span> <span data-ttu-id="9f59f-107">如需詳細資訊，請參閱[建立組件](../../../../framework/app-domains/create-assemblies.md)。</span><span class="sxs-lookup"><span data-stu-id="9f59f-107">For more information, see [Creating Assemblies](../../../../framework/app-domains/create-assemblies.md).</span></span>  
  
2.  <span data-ttu-id="9f59f-108">為您的組件指派強式名稱。</span><span class="sxs-lookup"><span data-stu-id="9f59f-108">Assign a strong name to your assembly.</span></span> <span data-ttu-id="9f59f-109">如需詳細資訊，請參閱[如何：使用強式名稱簽署組件](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)。</span><span class="sxs-lookup"><span data-stu-id="9f59f-109">For more information, see [How to: Sign an Assembly with a Strong Name](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>  
  
3.  <span data-ttu-id="9f59f-110">將版本資訊指派給您的組件。</span><span class="sxs-lookup"><span data-stu-id="9f59f-110">Assign version information to your assembly.</span></span> <span data-ttu-id="9f59f-111">如需詳細資訊，請參閱[組件版本控制](https://msdn.microsoft.com/library/51ket42z)。</span><span class="sxs-lookup"><span data-stu-id="9f59f-111">For more information, see [Assembly Versioning](https://msdn.microsoft.com/library/51ket42z).</span></span>  
  
4.  <span data-ttu-id="9f59f-112">將您的組件新增至全域組件快取。</span><span class="sxs-lookup"><span data-stu-id="9f59f-112">Add your assembly to the Global Assembly Cache.</span></span> <span data-ttu-id="9f59f-113">如需詳細資訊，請參閱[如何：將組件安裝到全域組件快取](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md)。</span><span class="sxs-lookup"><span data-stu-id="9f59f-113">For more information, see [How to: Install an Assembly into the Global Assembly Cache](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).</span></span>  
  
5.  <span data-ttu-id="9f59f-114">從其他應用程式存取組件內含的類型。</span><span class="sxs-lookup"><span data-stu-id="9f59f-114">Access the types contained in the assembly from the other applications.</span></span> <span data-ttu-id="9f59f-115">如需詳細資訊，請參閱[如何：參考以強式名稱命名的組件](http://msdn.microsoft.com/library/4c6a406a-b5eb-44fa-b4ed-4e95bb95a813)。</span><span class="sxs-lookup"><span data-stu-id="9f59f-115">For more information, see [How to: Reference a Strong-Named Assembly](http://msdn.microsoft.com/library/4c6a406a-b5eb-44fa-b4ed-4e95bb95a813).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f59f-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9f59f-116">See Also</span></span>  
 <span data-ttu-id="9f59f-117">[程式設計概念](../../../../visual-basic/programming-guide/concepts/index.md)[組件和全域組件快取 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)</span><span class="sxs-lookup"><span data-stu-id="9f59f-117">[Programming Concepts](../../../../visual-basic/programming-guide/concepts/index.md) [Assemblies and the Global Assembly Cache (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)</span></span>  
 [<span data-ttu-id="9f59f-118">使用組件設計程式</span><span class="sxs-lookup"><span data-stu-id="9f59f-118">Programming with Assemblies</span></span>](../../../../framework/app-domains/programming-with-assemblies.md)
