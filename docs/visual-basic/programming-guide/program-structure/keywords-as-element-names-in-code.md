---
title: 程式碼中以關鍵字做為項目名稱 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, naming conventions
- keywords [Visual Basic], in code
- name conflicts [Visual Basic]
- element names [Visual Basic], in code
ms.assetid: 2e4e8e02-23f7-49b9-a1c8-2b0402b6b525
ms.openlocfilehash: c247ada67f6554362f287cf252dd49856c4995da
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58841143"
---
# <a name="keywords-as-element-names-in-code-visual-basic"></a><span data-ttu-id="be6e4-102">程式碼中以關鍵字做為項目名稱 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="be6e4-102">Keywords as Element Names in Code (Visual Basic)</span></span>
<span data-ttu-id="be6e4-103">任何程式項目，例如變數、 類別或成員，可以有相同名稱做為受限制的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="be6e4-103">Any program element — such as a variable, class, or member — can have the same name as a restricted keyword.</span></span> <span data-ttu-id="be6e4-104">例如，您可以建立名為的變數`Loop`。</span><span class="sxs-lookup"><span data-stu-id="be6e4-104">For example, you can create a variable named `Loop`.</span></span> <span data-ttu-id="be6e4-105">不過，來參考它的版本，具有相同名稱的限制`Loop`關鍵字，您必須前面使用完整限定性條件字串，或將它括在方括號 (`[ ]`)，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="be6e4-105">However, to refer to your version of it — which has the same name as the restricted `Loop` keyword — you must either precede it with a full qualification string or enclose it in square brackets (`[ ]`), as the following example shows.</span></span>  
  
 [!code-vb[VbVbcnConventions#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#8)]  
  
 <span data-ttu-id="be6e4-106">如果你未執行任一種，則 Visual Basic 會假設使用內建函式`Loop`關鍵字，並產生錯誤，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="be6e4-106">If you do not do either of these, then Visual Basic assumes use of the intrinsic `Loop` keyword and produces an error, as in the following example:</span></span>  
  
 `' The following statement causes a compiler error.`  
  
 `Loop.Visible = True`  
  
 <span data-ttu-id="be6e4-107">您可以使用方括號，當參考表單和控制項，以及當宣告的變數，或做為限制關鍵字定義具有相同名稱的程序。</span><span class="sxs-lookup"><span data-stu-id="be6e4-107">You can use square brackets when referring to forms and controls, and when declaring a variable or defining a procedure with the same name as a restricted keyword.</span></span> <span data-ttu-id="be6e4-108">它可以很容易忘記來限定名稱，或包含方括號，因此引入您的程式碼中的錯誤並讓它更難讀取。</span><span class="sxs-lookup"><span data-stu-id="be6e4-108">It can be easy to forget to qualify names or include square brackets, and thus introduce errors into your code and make it harder to read.</span></span> <span data-ttu-id="be6e4-109">基於這個理由，我們建議您不要使用限制的關鍵字做為程式項目的名稱。</span><span class="sxs-lookup"><span data-stu-id="be6e4-109">For this reason, we recommend that you not use restricted keywords as the names of program elements.</span></span> <span data-ttu-id="be6e4-110">不過，如果未來的 Visual Basic 版本定義新的關鍵字，與現有的表單或控制項名稱的衝突，然後您可以使用這項技術更新您的程式碼時才能使用新的版本。</span><span class="sxs-lookup"><span data-stu-id="be6e4-110">However, if a future version of Visual Basic defines a new keyword that conflicts with an existing form or control name, then you can use this technique when updating your code to work with the new version.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="be6e4-111">您的程式也可能包含其他參考的組件所提供的項目名稱。</span><span class="sxs-lookup"><span data-stu-id="be6e4-111">Your program also might include element names provided by other referenced assemblies.</span></span> <span data-ttu-id="be6e4-112">如果與限制關鍵字，這些名稱衝突，然後將其周圍的方括號會使 Visual Basic，以將它們解譯為您定義的項目。</span><span class="sxs-lookup"><span data-stu-id="be6e4-112">If these names conflict with restricted keywords, then placing square brackets around them causes Visual Basic to interpret them as your defined elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be6e4-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be6e4-113">See also</span></span>

- [<span data-ttu-id="be6e4-114">Visual Basic 命名慣例</span><span class="sxs-lookup"><span data-stu-id="be6e4-114">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
- [<span data-ttu-id="be6e4-115">程式結構和程式碼慣例</span><span class="sxs-lookup"><span data-stu-id="be6e4-115">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [<span data-ttu-id="be6e4-116">關鍵字</span><span class="sxs-lookup"><span data-stu-id="be6e4-116">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
