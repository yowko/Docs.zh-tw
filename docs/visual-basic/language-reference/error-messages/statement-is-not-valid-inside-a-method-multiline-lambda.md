---
title: 方法多行 lambda 內的陳述式無效
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30024
- bc30024
helpviewer_keywords:
- BC30024
ms.assetid: 758e7a8f-429b-42c1-9a78-778e5b480e04
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 80673fc7a1497b4148a6505d29581c6403115558
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="statement-is-not-valid-inside-a-methodmultiline-lambda"></a><span data-ttu-id="133d1-102">陳述式在方法/多行 Lambda 內無效</span><span class="sxs-lookup"><span data-stu-id="133d1-102">Statement is not valid inside a method/multiline lambda</span></span>
<span data-ttu-id="133d1-103">陳述式內無效`Sub`， `Function`，屬性`Get`，或屬性`Set`程序。</span><span class="sxs-lookup"><span data-stu-id="133d1-103">The statement is not valid within a `Sub`, `Function`, property `Get`, or property `Set` procedure.</span></span> <span data-ttu-id="133d1-104">某些陳述式可以放在模組或類別層級。</span><span class="sxs-lookup"><span data-stu-id="133d1-104">Some statements can be placed at the module or class level.</span></span> <span data-ttu-id="133d1-105">其他項目，例如`Option Strict`，必須是在命名空間層級，而且在所有其他宣告之前。</span><span class="sxs-lookup"><span data-stu-id="133d1-105">Others, such as `Option Strict`, must be at namespace level and precede all other declarations.</span></span>  
  
 <span data-ttu-id="133d1-106">**錯誤 ID:** BC30024</span><span class="sxs-lookup"><span data-stu-id="133d1-106">**Error ID:** BC30024</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="133d1-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="133d1-107">To correct this error</span></span>  
  
-   <span data-ttu-id="133d1-108">移除程序中的陳述式。</span><span class="sxs-lookup"><span data-stu-id="133d1-108">Remove the statement from the procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="133d1-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="133d1-109">See Also</span></span>  
 [<span data-ttu-id="133d1-110">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="133d1-110">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="133d1-111">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="133d1-111">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="133d1-112">Get 陳述式</span><span class="sxs-lookup"><span data-stu-id="133d1-112">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)  
 [<span data-ttu-id="133d1-113">Set 陳述式</span><span class="sxs-lookup"><span data-stu-id="133d1-113">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)
