---
title: "在 Visual Basic 中的串連運算子 |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- '& operator [Visual Basic], concatenation'
- concatenation operators
- operators [Visual Basic], concatenation
- Visual Basic code, operators
- + operator [Visual Basic], concatenation
- concatenation operators, Visual Basic strings
ms.assetid: e59908c3-89e0-41ae-933d-3e8826c16a04
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: f255e168b9eb794ef846e0cc18dbbdba5941bec5
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="concatenation-operators-in-visual-basic"></a><span data-ttu-id="fa9a3-102">Visual Basic 中的串連運算子</span><span class="sxs-lookup"><span data-stu-id="fa9a3-102">Concatenation Operators in Visual Basic</span></span>
<span data-ttu-id="fa9a3-103">串連運算子會將多個字串連成單一字串。</span><span class="sxs-lookup"><span data-stu-id="fa9a3-103">Concatenation operators join multiple strings into a single string.</span></span> <span data-ttu-id="fa9a3-104">串連運算子有兩種：`+` 和 `&`。</span><span class="sxs-lookup"><span data-stu-id="fa9a3-104">There are two concatenation operators, `+` and `&`.</span></span> <span data-ttu-id="fa9a3-105">兩者都會進行基本的串連作業，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="fa9a3-105">Both carry out the basic concatenation operation, as the following example shows.</span></span>  
  
```vb
Dim x As String = "Mic" & "ro" & "soft" 
Dim y As String = "Mic" + "ro" + "soft" 
' The preceding statements set both x and y to "Microsoft".
```  
  
 <span data-ttu-id="fa9a3-106">這些運算子也可以串連 `String` 變數，如下列所示。</span><span class="sxs-lookup"><span data-stu-id="fa9a3-106">These operators can also concatenate `String` variables, as the following example shows.</span></span>  
  
 <span data-ttu-id="fa9a3-107">[!code-vb[VbVbalrOperators #&76;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/concatenation-operators_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="fa9a3-107">[!code-vb[VbVbalrOperators#76](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/concatenation-operators_1.vb)]</span></span>  
  
## <a name="differences-between-the-two-concatenation-operators"></a><span data-ttu-id="fa9a3-108">兩種串連運算子之間的差異</span><span class="sxs-lookup"><span data-stu-id="fa9a3-108">Differences Between the Two Concatenation Operators</span></span>  
 <span data-ttu-id="fa9a3-109">[+ 運算子](../../../../visual-basic/language-reference/operators/addition-operator.md)新增兩個數字的主要目的。</span><span class="sxs-lookup"><span data-stu-id="fa9a3-109">The [+ Operator](../../../../visual-basic/language-reference/operators/addition-operator.md) has the primary purpose of adding two numbers.</span></span> <span data-ttu-id="fa9a3-110">不過，它也可以串連數值運算元與字串運算元。</span><span class="sxs-lookup"><span data-stu-id="fa9a3-110">However, it can also concatenate numeric operands with string operands.</span></span> <span data-ttu-id="fa9a3-111">`+`運算子有一組複雜的規則，以決定是否要加入、 串連、 通知編譯器錯誤，或擲回執行階段<xref:System.InvalidCastException>例外狀況。</xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="fa9a3-111">The `+` operator has a complex set of rules that determine whether to add, concatenate, signal a compiler error, or throw a run-time <xref:System.InvalidCastException> exception.</span></span>  
  
 <span data-ttu-id="fa9a3-112">[i 運算子](../../../../visual-basic/language-reference/operators/concatenation-operator.md)定義僅適用於`String`運算元和它一律會將運算元擴展到`String`，不論設定`Option Strict`。</span><span class="sxs-lookup"><span data-stu-id="fa9a3-112">The [& Operator](../../../../visual-basic/language-reference/operators/concatenation-operator.md) is defined only for `String` operands, and it always widens its operands to `String`, regardless of the setting of `Option Strict`.</span></span> <span data-ttu-id="fa9a3-113">建議使用 `&` 運算元進行字串串連，因為它的定義為專門針對字串，且能減少您產生意外轉換的機會。</span><span class="sxs-lookup"><span data-stu-id="fa9a3-113">The `&` operator is recommended for string concatenation because it is defined exclusively for strings and reduces your chances of generating an unintended conversion.</span></span>  
  
## <a name="performance-string-and-stringbuilder"></a><span data-ttu-id="fa9a3-114">效能：String 和 StringBuilder</span><span class="sxs-lookup"><span data-stu-id="fa9a3-114">Performance: String and StringBuilder</span></span>  
 <span data-ttu-id="fa9a3-115">如果您有大量的字串，例如串連、 刪除和取代，操作您的效能可能可以藉由<xref:System.Text.StringBuilder>類別<xref:System.Text>命名空間。</xref:System.Text> </xref:System.Text.StringBuilder></span><span class="sxs-lookup"><span data-stu-id="fa9a3-115">If you do a significant number of manipulations on a string, such as concatenations, deletions, and replacements, your performance might profit from the <xref:System.Text.StringBuilder> class in the <xref:System.Text> namespace.</span></span> <span data-ttu-id="fa9a3-116">它會採用額外的指令，來建立和初始化<xref:System.Text.StringBuilder>物件，並將其最終值轉換成另一個指令`String`，但您可以彌補這個時間，因為<xref:System.Text.StringBuilder>執行地更快速。</xref:System.Text.StringBuilder> </xref:System.Text.StringBuilder></span><span class="sxs-lookup"><span data-stu-id="fa9a3-116">It takes an extra instruction to create and initialize a <xref:System.Text.StringBuilder> object, and another instruction to convert its final value to a `String`, but you might recover this time because <xref:System.Text.StringBuilder> can perform faster.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa9a3-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa9a3-117">See Also</span></span>  
 <span data-ttu-id="fa9a3-118">[Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md) </span><span class="sxs-lookup"><span data-stu-id="fa9a3-118">[Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) </span></span>  
<span data-ttu-id="fa9a3-119"> [在 Visual Basic 中字串管理方法的類型](../../../../visual-basic/programming-guide/language-features/strings/types-of-string-manipulation-methods.md) </span><span class="sxs-lookup"><span data-stu-id="fa9a3-119"> [Types of String Manipulation Methods in Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/types-of-string-manipulation-methods.md) </span></span>  
<span data-ttu-id="fa9a3-120"> [在 Visual Basic 中的算術運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md) </span><span class="sxs-lookup"><span data-stu-id="fa9a3-120"> [Arithmetic Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md) </span></span>  
<span data-ttu-id="fa9a3-121"> [在 Visual Basic 中的比較運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) </span><span class="sxs-lookup"><span data-stu-id="fa9a3-121"> [Comparison Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) </span></span>  
<span data-ttu-id="fa9a3-122"> [在 Visual Basic 中的邏輯和位元運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)</span><span class="sxs-lookup"><span data-stu-id="fa9a3-122"> [Logical and Bitwise Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)</span></span>
