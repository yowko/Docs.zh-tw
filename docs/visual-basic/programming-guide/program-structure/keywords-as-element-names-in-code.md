---
title: "程式碼中以關鍵字做為項目名稱 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, naming conventions
- keywords [Visual Basic], in code
- name conflicts [Visual Basic]
- element names [Visual Basic], in code
ms.assetid: 2e4e8e02-23f7-49b9-a1c8-2b0402b6b525
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f410a0eaac0dcc034d406a89ed1d01a8f228a583
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="keywords-as-element-names-in-code-visual-basic"></a><span data-ttu-id="bdfc3-102">程式碼中以關鍵字做為項目名稱 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bdfc3-102">Keywords as Element Names in Code (Visual Basic)</span></span>
<span data-ttu-id="bdfc3-103">任何程式項目，例如變數、 類別或成員，可以有相同名稱做為限制關鍵字。</span><span class="sxs-lookup"><span data-stu-id="bdfc3-103">Any program element — such as a variable, class, or member — can have the same name as a restricted keyword.</span></span> <span data-ttu-id="bdfc3-104">例如，您可以建立名為的變數`Loop`。</span><span class="sxs-lookup"><span data-stu-id="bdfc3-104">For example, you can create a variable named `Loop`.</span></span> <span data-ttu-id="bdfc3-105">不過，來參考它的版本，具有相同的名稱限制`Loop`關鍵字 — 您必須在其前面加完整限定性條件字串，或將它括在方括號 (`[ ]`)，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="bdfc3-105">However, to refer to your version of it — which has the same name as the restricted `Loop` keyword — you must either precede it with a full qualification string or enclose it in square brackets (`[ ]`), as the following example shows.</span></span>  
  
 [!code-vb[VbVbcnConventions#8](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/keywords-as-element-names-in-code_1.vb)]  
  
 <span data-ttu-id="bdfc3-106">如果你未執行任一種，則 Visual Basic 會假設使用內建函式`Loop`關鍵字，並產生錯誤，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="bdfc3-106">If you do not do either of these, then Visual Basic assumes use of the intrinsic `Loop` keyword and produces an error, as in the following example:</span></span>  
  
 `' The following statement causes a compiler error.`  
  
 `Loop.Visible = True`  
  
 <span data-ttu-id="bdfc3-107">您可以使用方括號，當參考表單和控制項，以及當宣告的變數，或做為限制關鍵字定義具有相同名稱的程序。</span><span class="sxs-lookup"><span data-stu-id="bdfc3-107">You can use square brackets when referring to forms and controls, and when declaring a variable or defining a procedure with the same name as a restricted keyword.</span></span> <span data-ttu-id="bdfc3-108">可能很容易會忘記來限定名稱或包含方括號，因此會導致您的程式碼發生錯誤並讓它更難閱讀。</span><span class="sxs-lookup"><span data-stu-id="bdfc3-108">It can be easy to forget to qualify names or include square brackets, and thus introduce errors into your code and make it harder to read.</span></span> <span data-ttu-id="bdfc3-109">基於這個理由，我們建議您不要使用限制的關鍵字做為程式項目的名稱。</span><span class="sxs-lookup"><span data-stu-id="bdfc3-109">For this reason, we recommend that you not use restricted keywords as the names of program elements.</span></span> <span data-ttu-id="bdfc3-110">不過，如果未來的 Visual Basic 版本定義新的關鍵字與現有的表單或控制項名稱發生衝突，然後您可以使用這項技術更新您的程式碼時才能使用新的版本。</span><span class="sxs-lookup"><span data-stu-id="bdfc3-110">However, if a future version of Visual Basic defines a new keyword that conflicts with an existing form or control name, then you can use this technique when updating your code to work with the new version.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bdfc3-111">您的程式也可能包含其他參考組件所提供的項目名稱。</span><span class="sxs-lookup"><span data-stu-id="bdfc3-111">Your program also might include element names provided by other referenced assemblies.</span></span> <span data-ttu-id="bdfc3-112">如果這些名稱衝突與限制的關鍵字，然後將設周圍的方括號會造成 Visual Basic 將它們解譯為定義的項目。</span><span class="sxs-lookup"><span data-stu-id="bdfc3-112">If these names conflict with restricted keywords, then placing square brackets around them causes Visual Basic to interpret them as your defined elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdfc3-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bdfc3-113">See Also</span></span>  
 [<span data-ttu-id="bdfc3-114">Visual Basic 命名慣例</span><span class="sxs-lookup"><span data-stu-id="bdfc3-114">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 [<span data-ttu-id="bdfc3-115">程式結構和程式碼慣例</span><span class="sxs-lookup"><span data-stu-id="bdfc3-115">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [<span data-ttu-id="bdfc3-116">關鍵字</span><span class="sxs-lookup"><span data-stu-id="bdfc3-116">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
