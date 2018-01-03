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
ms.openlocfilehash: e6a2d66c860b72bd3ef59c02f548ac563fab6b8c
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="no-accessible-39main39-method-with-an-appropriate-signature-was-found-in-39ltnamegt39"></a><span data-ttu-id="b9d59-102">沒有可存取 &#39;Main &#39;中找不到具有適當簽章的方法 &#39;&lt;名稱&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="b9d59-102">No accessible &#39;Main&#39; method with an appropriate signature was found in &#39;&lt;name&gt;&#39;</span></span>
<span data-ttu-id="b9d59-103">命令列應用程式必須具備`Sub Main`定義。</span><span class="sxs-lookup"><span data-stu-id="b9d59-103">Command-line applications must have a `Sub Main` defined.</span></span> <span data-ttu-id="b9d59-104">`Main`必須宣告為`Public Shared`如果已定義在類別中，或做為`Public`如果的模組中定義。</span><span class="sxs-lookup"><span data-stu-id="b9d59-104">`Main` must be declared as `Public Shared` if it is defined in a class, or as `Public` if defined in a module.</span></span>  
  
 <span data-ttu-id="b9d59-105">**錯誤 ID:** BC30737</span><span class="sxs-lookup"><span data-stu-id="b9d59-105">**Error ID:** BC30737</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b9d59-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="b9d59-106">To correct this error</span></span>  
  
-   <span data-ttu-id="b9d59-107">定義`Public Sub Main`程序，為您的專案。</span><span class="sxs-lookup"><span data-stu-id="b9d59-107">Define a `Public Sub Main` procedure for your project.</span></span> <span data-ttu-id="b9d59-108">將它宣告為`Shared`如果且只有在類別內定義它。</span><span class="sxs-lookup"><span data-stu-id="b9d59-108">Declare it as `Shared` if and only if you define it inside a class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9d59-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="b9d59-109">See Also</span></span>  
 [<span data-ttu-id="b9d59-110">Visual Basic 程式的結構</span><span class="sxs-lookup"><span data-stu-id="b9d59-110">Structure of a Visual Basic Program</span></span>](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)  
 [<span data-ttu-id="b9d59-111">程序</span><span class="sxs-lookup"><span data-stu-id="b9d59-111">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
