---
title: 程式碼中的項目名稱關鍵字
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, naming conventions
- keywords [Visual Basic], in code
- name conflicts [Visual Basic]
- element names [Visual Basic], in code
ms.assetid: 2e4e8e02-23f7-49b9-a1c8-2b0402b6b525
ms.openlocfilehash: e895db180dbb44cd4cfe4053d4be429f13324fe8
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91065745"
---
# <a name="keywords-as-element-names-in-code-visual-basic"></a><span data-ttu-id="ea087-102">程式碼中以關鍵字做為項目名稱 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ea087-102">Keywords as Element Names in Code (Visual Basic)</span></span>

<span data-ttu-id="ea087-103">任何程式元素（例如變數、類別或成員）的名稱都可以與限制關鍵字相同。</span><span class="sxs-lookup"><span data-stu-id="ea087-103">Any program element — such as a variable, class, or member — can have the same name as a restricted keyword.</span></span> <span data-ttu-id="ea087-104">例如，您可以建立名為的變數 `Loop` 。</span><span class="sxs-lookup"><span data-stu-id="ea087-104">For example, you can create a variable named `Loop`.</span></span> <span data-ttu-id="ea087-105">不過，若要參考您的版本（名稱與限制 `Loop` 關鍵字相同），您必須在其前面加上完整的限定性字串，或將它放在以方括弧括住的 (`[ ]`) ，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="ea087-105">However, to refer to your version of it — which has the same name as the restricted `Loop` keyword — you must either precede it with a full qualification string or enclose it in square brackets (`[ ]`), as the following example shows.</span></span>  
  
 [!code-vb[VbVbcnConventions#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#8)]  
  
 <span data-ttu-id="ea087-106">如果您沒有執行這其中一項，則 Visual Basic 會假設使用內建 `Loop` 關鍵字並產生錯誤，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="ea087-106">If you do not do either of these, then Visual Basic assumes use of the intrinsic `Loop` keyword and produces an error, as in the following example:</span></span>  
  
 `' The following statement causes a compiler error.`  
  
 `Loop.Visible = True`  
  
 <span data-ttu-id="ea087-107">當您參考表單和控制項時，以及宣告變數或定義與限制關鍵字同名的程式時，可以使用方括弧。</span><span class="sxs-lookup"><span data-stu-id="ea087-107">You can use square brackets when referring to forms and controls, and when declaring a variable or defining a procedure with the same name as a restricted keyword.</span></span> <span data-ttu-id="ea087-108">您可以很容易忘記限定名稱或包含方括弧，進而將錯誤導入程式碼，使其更難以閱讀。</span><span class="sxs-lookup"><span data-stu-id="ea087-108">It can be easy to forget to qualify names or include square brackets, and thus introduce errors into your code and make it harder to read.</span></span> <span data-ttu-id="ea087-109">基於這個理由，我們建議您不要使用受限制的關鍵字做為程式元素的名稱。</span><span class="sxs-lookup"><span data-stu-id="ea087-109">For this reason, we recommend that you not use restricted keywords as the names of program elements.</span></span> <span data-ttu-id="ea087-110">但是，如果 Visual Basic 的未來版本定義了與現有表單或控制項名稱衝突的新關鍵字，則在更新程式碼以使用新版本時，您可以使用這項技術。</span><span class="sxs-lookup"><span data-stu-id="ea087-110">However, if a future version of Visual Basic defines a new keyword that conflicts with an existing form or control name, then you can use this technique when updating your code to work with the new version.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ea087-111">您的程式也可能包含其他參考元件所提供的元素名稱。</span><span class="sxs-lookup"><span data-stu-id="ea087-111">Your program also might include element names provided by other referenced assemblies.</span></span> <span data-ttu-id="ea087-112">如果這些名稱與受限制的關鍵字衝突，則在其周圍加上方括弧會導致 Visual Basic 將它們解讀為您定義的元素。</span><span class="sxs-lookup"><span data-stu-id="ea087-112">If these names conflict with restricted keywords, then placing square brackets around them causes Visual Basic to interpret them as your defined elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea087-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ea087-113">See also</span></span>

- [<span data-ttu-id="ea087-114">Visual Basic 命名慣例</span><span class="sxs-lookup"><span data-stu-id="ea087-114">Visual Basic Naming Conventions</span></span>](naming-conventions.md)
- [<span data-ttu-id="ea087-115">程式結構和程式碼慣例</span><span class="sxs-lookup"><span data-stu-id="ea087-115">Program Structure and Code Conventions</span></span>](program-structure-and-code-conventions.md)
- [<span data-ttu-id="ea087-116">關鍵字</span><span class="sxs-lookup"><span data-stu-id="ea087-116">Keywords</span></span>](../../language-reference/keywords/index.md)
