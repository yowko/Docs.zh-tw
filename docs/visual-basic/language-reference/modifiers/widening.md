---
title: Widening (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.widening
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Widening keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: 646ae263-94d3-40a2-b0cc-64f619292f56
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 034099397c1d296a42712b8c202e2ac99a0fb43b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="widening-visual-basic"></a><span data-ttu-id="6f6fa-102">Widening (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6f6fa-102">Widening (Visual Basic)</span></span>
<span data-ttu-id="6f6fa-103">表示轉換運算子 (`CType`) 將類別或結構轉換成可容納原始類別或結構的所有可能值的類型。</span><span class="sxs-lookup"><span data-stu-id="6f6fa-103">Indicates that a conversion operator (`CType`) converts a class or structure to a type that can hold all possible values of the original class or structure.</span></span>  
  
## <a name="converting-with-the-widening-keyword"></a><span data-ttu-id="6f6fa-104">轉換以擴展關鍵字</span><span class="sxs-lookup"><span data-stu-id="6f6fa-104">Converting with the Widening Keyword</span></span>  
 <span data-ttu-id="6f6fa-105">轉換程序必須指定`Public Shared`除了`Widening`。</span><span class="sxs-lookup"><span data-stu-id="6f6fa-105">The conversion procedure must specify `Public Shared` in addition to `Widening`.</span></span>  
  
 <span data-ttu-id="6f6fa-106">擴展轉換，一定要成功執行階段，並永遠不會造成資料遺失。</span><span class="sxs-lookup"><span data-stu-id="6f6fa-106">Widening conversions always succeed at run time and never incur data loss.</span></span> <span data-ttu-id="6f6fa-107">範例包括`Single`至`Double`，`Char`至`String`，和其基底類型的衍生型別。</span><span class="sxs-lookup"><span data-stu-id="6f6fa-107">Examples are `Single` to `Double`, `Char` to `String`, and a derived type to its base type.</span></span> <span data-ttu-id="6f6fa-108">因為衍生的類型包含基底型別的所有成員，因此基底類型的執行個體，就會擴展這個最後一個轉換。</span><span class="sxs-lookup"><span data-stu-id="6f6fa-108">This last conversion is widening because the derived type contains all the members of the base type and thus is an instance of the base type.</span></span>  
  
 <span data-ttu-id="6f6fa-109">使用的程式碼不需要使用`CType`的擴展轉換，即使`Option Strict`是`On`。</span><span class="sxs-lookup"><span data-stu-id="6f6fa-109">The consuming code does not have to use `CType` for widening conversions, even if `Option Strict` is `On`.</span></span>  
  
 <span data-ttu-id="6f6fa-110">`Widening`關鍵字可用於此內容：</span><span class="sxs-lookup"><span data-stu-id="6f6fa-110">The `Widening` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="6f6fa-111">Operator 陳述式</span><span class="sxs-lookup"><span data-stu-id="6f6fa-111">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 <span data-ttu-id="6f6fa-112">定義擴展和縮小轉換的運算子，例如看到[如何： 定義轉換運算子](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="6f6fa-112">For example definitions of widening and narrowing conversion operators, see [How to: Define a Conversion Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f6fa-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6f6fa-113">See Also</span></span>  
 [<span data-ttu-id="6f6fa-114">Operator 陳述式</span><span class="sxs-lookup"><span data-stu-id="6f6fa-114">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="6f6fa-115">Narrowing</span><span class="sxs-lookup"><span data-stu-id="6f6fa-115">Narrowing</span></span>](../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [<span data-ttu-id="6f6fa-116">擴展和縮小轉換</span><span class="sxs-lookup"><span data-stu-id="6f6fa-116">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [<span data-ttu-id="6f6fa-117">如何：定義運算子</span><span class="sxs-lookup"><span data-stu-id="6f6fa-117">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [<span data-ttu-id="6f6fa-118">CType 函式</span><span class="sxs-lookup"><span data-stu-id="6f6fa-118">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)  
 [<span data-ttu-id="6f6fa-119">Option Strict 陳述式</span><span class="sxs-lookup"><span data-stu-id="6f6fa-119">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="6f6fa-120">如何：定義轉換運算子</span><span class="sxs-lookup"><span data-stu-id="6f6fa-120">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
