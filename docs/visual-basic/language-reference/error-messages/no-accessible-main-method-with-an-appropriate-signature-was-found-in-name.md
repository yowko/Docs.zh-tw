---
title: "沒有可存取 &#39;Main &#39;中找不到具有適當簽章的方法 &#39;&lt;名稱&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30737
- vbc30737
helpviewer_keywords: BC30737
ms.assetid: 3f40bacd-3fac-4741-b204-852f693d4340
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3f45dc17304c3c9d62b65760f2c1b5d461812a66
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="no-accessible-39main39-method-with-an-appropriate-signature-was-found-in-39ltnamegt39"></a><span data-ttu-id="dc3c6-102">沒有可存取 &#39;Main &#39;中找不到具有適當簽章的方法 &#39;&lt;名稱&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="dc3c6-102">No accessible &#39;Main&#39; method with an appropriate signature was found in &#39;&lt;name&gt;&#39;</span></span>
<span data-ttu-id="dc3c6-103">命令列應用程式必須具備`Sub Main`定義。</span><span class="sxs-lookup"><span data-stu-id="dc3c6-103">Command-line applications must have a `Sub Main` defined.</span></span> <span data-ttu-id="dc3c6-104">`Main`必須宣告為`Public Shared`如果已定義在類別中，或做為`Public`如果的模組中定義。</span><span class="sxs-lookup"><span data-stu-id="dc3c6-104">`Main` must be declared as `Public Shared` if it is defined in a class, or as `Public` if defined in a module.</span></span>  
  
 <span data-ttu-id="dc3c6-105">如需有關`Main`，請參閱[NIB: Visual Basic 版本的 Hello，World](http://msdn.microsoft.com/en-us/9d030b60-e148-4366-a462-69532f02294c)。</span><span class="sxs-lookup"><span data-stu-id="dc3c6-105">For more information on `Main`, see [NIB: Visual Basic Version of Hello, World](http://msdn.microsoft.com/en-us/9d030b60-e148-4366-a462-69532f02294c).</span></span>  
  
 <span data-ttu-id="dc3c6-106">**錯誤 ID:** BC30737</span><span class="sxs-lookup"><span data-stu-id="dc3c6-106">**Error ID:** BC30737</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="dc3c6-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="dc3c6-107">To correct this error</span></span>  
  
-   <span data-ttu-id="dc3c6-108">定義`Public Sub Main`程序，為您的專案。</span><span class="sxs-lookup"><span data-stu-id="dc3c6-108">Define a `Public Sub Main` procedure for your project.</span></span> <span data-ttu-id="dc3c6-109">將它宣告為`Shared`如果且只有在類別內定義它。</span><span class="sxs-lookup"><span data-stu-id="dc3c6-109">Declare it as `Shared` if and only if you define it inside a class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc3c6-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc3c6-110">See Also</span></span>  
 [<span data-ttu-id="dc3c6-111">NIB: Visual Basic 版本的 Hello，World</span><span class="sxs-lookup"><span data-stu-id="dc3c6-111">NIB: Visual Basic Version of Hello, World</span></span>](http://msdn.microsoft.com/en-us/9d030b60-e148-4366-a462-69532f02294c)  
 [<span data-ttu-id="dc3c6-112">Visual Basic 程式的結構</span><span class="sxs-lookup"><span data-stu-id="dc3c6-112">Structure of a Visual Basic Program</span></span>](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)  
 [<span data-ttu-id="dc3c6-113">程序</span><span class="sxs-lookup"><span data-stu-id="dc3c6-113">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
