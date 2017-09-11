---
title: "如何︰ 共用組件與其他應用程式 (Visual Basic) |Microsoft 文件"
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
ms.assetid: 5388aedc-cb42-4622-8b70-8e701eee057a
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
ms.openlocfilehash: ceebb3934c269284db18c9ca8e561417eaf5baa1
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-share-an-assembly-with-other-applications-visual-basic"></a><span data-ttu-id="68671-102">如何︰ 共用組件與其他應用程式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="68671-102">How to: Share an Assembly with Other Applications (Visual Basic)</span></span>
<span data-ttu-id="68671-103">組件可以是私人或共用︰ 根據預設，最簡單的程式中包含私用組件因為它們不能供其他應用程式。</span><span class="sxs-lookup"><span data-stu-id="68671-103">Assemblies can be private or shared: by default, most simple programs consist of a private assembly because they are not intended to be used by other applications.</span></span>  
  
 <span data-ttu-id="68671-104">為了與其他應用程式共用組件，它必須放在[全域組件快取](http://msdn.microsoft.com/library/cf5eacd0-d3ec-4879-b6da-5fd5e4372202)(GAC)。</span><span class="sxs-lookup"><span data-stu-id="68671-104">In order to share an assembly with other applications, it must be placed in the [Global Assembly Cache](http://msdn.microsoft.com/library/cf5eacd0-d3ec-4879-b6da-5fd5e4372202) (GAC).</span></span>  
  
### <a name="sharing-an-assembly"></a><span data-ttu-id="68671-105">共用組件</span><span class="sxs-lookup"><span data-stu-id="68671-105">Sharing an assembly</span></span>  
  
1.  <span data-ttu-id="68671-106">建立您的組件。</span><span class="sxs-lookup"><span data-stu-id="68671-106">Create your assembly.</span></span> <span data-ttu-id="68671-107">如需詳細資訊，請參閱[建立組件](http://msdn.microsoft.com/library/54832ee9-dca8-4c8b-913c-c0b9d265e9a4)。</span><span class="sxs-lookup"><span data-stu-id="68671-107">For more information, see [Creating Assemblies](http://msdn.microsoft.com/library/54832ee9-dca8-4c8b-913c-c0b9d265e9a4).</span></span>  
  
2.  <span data-ttu-id="68671-108">將強式名稱指派給您的組件。</span><span class="sxs-lookup"><span data-stu-id="68671-108">Assign a strong name to your assembly.</span></span> <span data-ttu-id="68671-109">如需詳細資訊，請參閱[How to︰ 使用強式名稱簽署組](http://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67)。</span><span class="sxs-lookup"><span data-stu-id="68671-109">For more information, see [How to: Sign an Assembly with a Strong Name](http://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67).</span></span>  
  
3.  <span data-ttu-id="68671-110">將版本資訊指派給您的組件。</span><span class="sxs-lookup"><span data-stu-id="68671-110">Assign version information to your assembly.</span></span> <span data-ttu-id="68671-111">如需詳細資訊，請參閱[組件版本控制](https://msdn.microsoft.com/library/51ket42z)。</span><span class="sxs-lookup"><span data-stu-id="68671-111">For more information, see [Assembly Versioning](https://msdn.microsoft.com/library/51ket42z).</span></span>  
  
4.  <span data-ttu-id="68671-112">將您的組件加入至全域組件快取。</span><span class="sxs-lookup"><span data-stu-id="68671-112">Add your assembly to the Global Assembly Cache.</span></span> <span data-ttu-id="68671-113">如需詳細資訊，請參閱[How to︰ 將組件安裝到全域組件快取](http://msdn.microsoft.com/library/a7e6f091-d02c-49ba-b736-7295cb0eb743)。</span><span class="sxs-lookup"><span data-stu-id="68671-113">For more information, see [How to: Install an Assembly into the Global Assembly Cache](http://msdn.microsoft.com/library/a7e6f091-d02c-49ba-b736-7295cb0eb743).</span></span>  
  
5.  <span data-ttu-id="68671-114">存取其他應用程式的組件中所包含的型別。</span><span class="sxs-lookup"><span data-stu-id="68671-114">Access the types contained in the assembly from the other applications.</span></span> <span data-ttu-id="68671-115">如需詳細資訊，請參閱[如何︰ 參考強式名稱組件](http://msdn.microsoft.com/library/4c6a406a-b5eb-44fa-b4ed-4e95bb95a813)。</span><span class="sxs-lookup"><span data-stu-id="68671-115">For more information, see [How to: Reference a Strong-Named Assembly](http://msdn.microsoft.com/library/4c6a406a-b5eb-44fa-b4ed-4e95bb95a813).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68671-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="68671-116">See Also</span></span>  
 <span data-ttu-id="68671-117">[程式設計概念](../../../../visual-basic/programming-guide/concepts/index.md)
 [組件和全域組件快取 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span><span class="sxs-lookup"><span data-stu-id="68671-117">[Programming Concepts](../../../../visual-basic/programming-guide/concepts/index.md)
 [Assemblies and the Global Assembly Cache (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span></span>  
<span data-ttu-id="68671-118"> [使用組件設計程式](http://msdn.microsoft.com/library/25918b15-701d-42c7-95fc-c290d08648d6)</span><span class="sxs-lookup"><span data-stu-id="68671-118"> [Programming with Assemblies](http://msdn.microsoft.com/library/25918b15-701d-42c7-95fc-c290d08648d6)</span></span>
