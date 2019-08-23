---
title: 程式碼中以關鍵字做為項目名稱 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, naming conventions
- keywords [Visual Basic], in code
- name conflicts [Visual Basic]
- element names [Visual Basic], in code
ms.assetid: 2e4e8e02-23f7-49b9-a1c8-2b0402b6b525
ms.openlocfilehash: 2e3613bd4a74da51cf7dbb63e52eddca811ca8e1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947668"
---
# <a name="keywords-as-element-names-in-code-visual-basic"></a><span data-ttu-id="703b1-102">程式碼中以關鍵字做為項目名稱 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="703b1-102">Keywords as Element Names in Code (Visual Basic)</span></span>
<span data-ttu-id="703b1-103">任何程式元素 (例如變數、類別或成員) 的名稱都可以與受限關鍵字相同。</span><span class="sxs-lookup"><span data-stu-id="703b1-103">Any program element — such as a variable, class, or member — can have the same name as a restricted keyword.</span></span> <span data-ttu-id="703b1-104">例如, 您可以建立名為`Loop`的變數。</span><span class="sxs-lookup"><span data-stu-id="703b1-104">For example, you can create a variable named `Loop`.</span></span> <span data-ttu-id="703b1-105">不過, 若要參考您的版本 (其名稱與受限制`Loop`的關鍵字相同), 您必須在其前面加上完整限定字串, 或將其括在方括弧 (`[ ]`) 中, 如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="703b1-105">However, to refer to your version of it — which has the same name as the restricted `Loop` keyword — you must either precede it with a full qualification string or enclose it in square brackets (`[ ]`), as the following example shows.</span></span>  
  
 [!code-vb[VbVbcnConventions#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#8)]  
  
 <span data-ttu-id="703b1-106">如果您未執行上述任一項, 則 Visual Basic 會假設使用內`Loop`建關鍵字並產生錯誤, 如下列範例所示:</span><span class="sxs-lookup"><span data-stu-id="703b1-106">If you do not do either of these, then Visual Basic assumes use of the intrinsic `Loop` keyword and produces an error, as in the following example:</span></span>  
  
 `' The following statement causes a compiler error.`  
  
 `Loop.Visible = True`  
  
 <span data-ttu-id="703b1-107">您可以在參考表單和控制項時, 以及在宣告變數或使用與受限制關鍵字相同的名稱來定義程式時, 使用方括弧。</span><span class="sxs-lookup"><span data-stu-id="703b1-107">You can use square brackets when referring to forms and controls, and when declaring a variable or defining a procedure with the same name as a restricted keyword.</span></span> <span data-ttu-id="703b1-108">您可能很容易忘記限定名稱或包含方括弧, 因此在您的程式碼中引進錯誤, 使其更難以閱讀。</span><span class="sxs-lookup"><span data-stu-id="703b1-108">It can be easy to forget to qualify names or include square brackets, and thus introduce errors into your code and make it harder to read.</span></span> <span data-ttu-id="703b1-109">基於這個理由, 我們建議您不要使用受限制的關鍵字做為程式元素的名稱。</span><span class="sxs-lookup"><span data-stu-id="703b1-109">For this reason, we recommend that you not use restricted keywords as the names of program elements.</span></span> <span data-ttu-id="703b1-110">不過, 如果 Visual Basic 的未來版本定義了與現有表單或控制項名稱衝突的新關鍵字, 則在更新程式碼以使用新版本時, 您可以使用這項技術。</span><span class="sxs-lookup"><span data-stu-id="703b1-110">However, if a future version of Visual Basic defines a new keyword that conflicts with an existing form or control name, then you can use this technique when updating your code to work with the new version.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="703b1-111">您的程式也可能包含其他參考元件所提供的元素名稱。</span><span class="sxs-lookup"><span data-stu-id="703b1-111">Your program also might include element names provided by other referenced assemblies.</span></span> <span data-ttu-id="703b1-112">如果這些名稱與受限制的關鍵字衝突, 則在其周圍加上方括弧會導致 Visual Basic 將它們解讀為您定義的元素。</span><span class="sxs-lookup"><span data-stu-id="703b1-112">If these names conflict with restricted keywords, then placing square brackets around them causes Visual Basic to interpret them as your defined elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="703b1-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="703b1-113">See also</span></span>

- [<span data-ttu-id="703b1-114">Visual Basic 命名慣例</span><span class="sxs-lookup"><span data-stu-id="703b1-114">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
- [<span data-ttu-id="703b1-115">程式結構和程式碼慣例</span><span class="sxs-lookup"><span data-stu-id="703b1-115">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [<span data-ttu-id="703b1-116">關鍵字</span><span class="sxs-lookup"><span data-stu-id="703b1-116">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
