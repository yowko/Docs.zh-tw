---
title: Narrowing (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.narrowing
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Narrowing keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: a207ee91-aca4-4771-b4e2-713f029bf2bb
ms.openlocfilehash: eb5f021371291483b8eb2a13727a9fda94540638
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58838842"
---
# <a name="narrowing-visual-basic"></a><span data-ttu-id="6be5e-102">Narrowing (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6be5e-102">Narrowing (Visual Basic)</span></span>
<span data-ttu-id="6be5e-103">表示轉換運算子 (`CType`) 將類別或結構轉換成可能無法保留一些可能的值，原始的類別或結構的類型。</span><span class="sxs-lookup"><span data-stu-id="6be5e-103">Indicates that a conversion operator (`CType`) converts a class or structure to a type that might not be able to hold some of the possible values of the original class or structure.</span></span>  
  
## <a name="converting-with-the-narrowing-keyword"></a><span data-ttu-id="6be5e-104">轉換以縮小關鍵字</span><span class="sxs-lookup"><span data-stu-id="6be5e-104">Converting with the Narrowing Keyword</span></span>  
 <span data-ttu-id="6be5e-105">轉換程序必須指定`Public Shared`除了`Narrowing`。</span><span class="sxs-lookup"><span data-stu-id="6be5e-105">The conversion procedure must specify `Public Shared` in addition to `Narrowing`.</span></span>  
  
 <span data-ttu-id="6be5e-106">縮小轉換執行不一定成功在執行階段，並可能會失敗或者會造成資料遺失。</span><span class="sxs-lookup"><span data-stu-id="6be5e-106">Narrowing conversions do not always succeed at run time, and can fail or incur data loss.</span></span> <span data-ttu-id="6be5e-107">範例包括`Long`來`Integer`，`String`到`Date`，並為衍生類型的基底型別。</span><span class="sxs-lookup"><span data-stu-id="6be5e-107">Examples are `Long` to `Integer`, `String` to `Date`, and a base type to a derived type.</span></span> <span data-ttu-id="6be5e-108">這個最後一個轉換縮小，因為基底型別可能不會包含衍生型別的所有成員，而且不是衍生型別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="6be5e-108">This last conversion is narrowing because the base type might not contain all the members of the derived type and thus is not an instance of the derived type.</span></span>  
  
 <span data-ttu-id="6be5e-109">如果`Option Strict`已`On`，使用程式碼必須使用`CType`所有的縮小轉換。</span><span class="sxs-lookup"><span data-stu-id="6be5e-109">If `Option Strict` is `On`, the consuming code must use `CType` for all narrowing conversions.</span></span>  
  
 <span data-ttu-id="6be5e-110">`Narrowing`關鍵字可以用在此內容中：</span><span class="sxs-lookup"><span data-stu-id="6be5e-110">The `Narrowing` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="6be5e-111">Operator 陳述式</span><span class="sxs-lookup"><span data-stu-id="6be5e-111">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="6be5e-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6be5e-112">See also</span></span>

- [<span data-ttu-id="6be5e-113">Operator 陳述式</span><span class="sxs-lookup"><span data-stu-id="6be5e-113">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="6be5e-114">Widening</span><span class="sxs-lookup"><span data-stu-id="6be5e-114">Widening</span></span>](../../../visual-basic/language-reference/modifiers/widening.md)
- [<span data-ttu-id="6be5e-115">擴展和縮小轉換</span><span class="sxs-lookup"><span data-stu-id="6be5e-115">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="6be5e-116">如何：定義運算子</span><span class="sxs-lookup"><span data-stu-id="6be5e-116">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="6be5e-117">CType 函式</span><span class="sxs-lookup"><span data-stu-id="6be5e-117">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)
- [<span data-ttu-id="6be5e-118">Option Strict 陳述式</span><span class="sxs-lookup"><span data-stu-id="6be5e-118">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
