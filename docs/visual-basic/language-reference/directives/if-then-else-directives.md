---
title: '#如果......#Else 指示詞'
ms.date: 04/11/2018
f1_keywords:
- vb.#EndIf
- '#End If'
- '#Then'
- '#ElseIf'
- vb.#ElseIf
- vb.#Else
- vb.#If
helpviewer_keywords:
- Visual Basic code, compiling
- '#If directive [Visual Basic]'
- conditional compilation [Visual Basic], directives
- '#End if directive [Visual Basic]'
- selective compiling
- else directive (#else)
- '#Else directive [Visual Basic]'
ms.assetid: 10bba104-e3fd-451b-b672-faa472530502
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 69ce56d770de5f004f204b1764fd51d948ba92c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591077"
---
# <a name="ifthenelse-directives"></a><span data-ttu-id="8b3f1-102">#If...Then...#Else 指示詞</span><span class="sxs-lookup"><span data-stu-id="8b3f1-102">#If...Then...#Else Directives</span></span>
<span data-ttu-id="8b3f1-103">有條件地編譯選取的 Visual Basic 程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="8b3f1-103">Conditionally compiles selected blocks of Visual Basic code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b3f1-104">語法</span><span class="sxs-lookup"><span data-stu-id="8b3f1-104">Syntax</span></span>  
  
```  
#If expression Then  
   statements  
[ #ElseIf expression Then  
   [ statements ]  
...  
#ElseIf expression Then  
   [ statements ] ]  
[ #Else  
   [ statements ] ]  
#End If  
```  
  
## <a name="parts"></a><span data-ttu-id="8b3f1-105">組件</span><span class="sxs-lookup"><span data-stu-id="8b3f1-105">Parts</span></span>  
 `expression`  
 <span data-ttu-id="8b3f1-106">所需的`#If`和`#ElseIf`陳述式，指定其他位置。</span><span class="sxs-lookup"><span data-stu-id="8b3f1-106">Required for `#If` and `#ElseIf` statements, optional elsewhere.</span></span> <span data-ttu-id="8b3f1-107">任何運算式，以獨佔方式組成一或多個條件式編譯器常數、 常值和運算子，評估為`True`或`False`。</span><span class="sxs-lookup"><span data-stu-id="8b3f1-107">Any expression, consisting exclusively of one or more conditional compiler constants, literals, and operators, that evaluates to `True` or `False`.</span></span>  
  
 `statements`  
 <span data-ttu-id="8b3f1-108">所需的`#If`陳述式區塊，選擇性其他位置。</span><span class="sxs-lookup"><span data-stu-id="8b3f1-108">Required for `#If` statement block, optional elsewhere.</span></span> <span data-ttu-id="8b3f1-109">Visual Basic 程式行或如果相關聯的運算式評估為編譯的編譯器指示詞`True`。</span><span class="sxs-lookup"><span data-stu-id="8b3f1-109">Visual Basic program lines or compiler directives that are compiled if the associated expression evaluates to `True`.</span></span>  
  
 `#End If`  
 <span data-ttu-id="8b3f1-110">終止`#If`陳述式區塊。</span><span class="sxs-lookup"><span data-stu-id="8b3f1-110">Terminates the `#If` statement block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8b3f1-111">備註</span><span class="sxs-lookup"><span data-stu-id="8b3f1-111">Remarks</span></span>  
 <span data-ttu-id="8b3f1-112">在介面中，行為`#If...Then...#Else`指示詞會出現相同的`If...Then...Else`陳述式。</span><span class="sxs-lookup"><span data-stu-id="8b3f1-112">On the surface, the behavior of the `#If...Then...#Else` directives appears the same as that of the `If...Then...Else` statements.</span></span> <span data-ttu-id="8b3f1-113">不過，`#If...Then...#Else`指示詞評估由編譯器所編譯的功能而`If...Then...Else`陳述式在執行階段評估的條件。</span><span class="sxs-lookup"><span data-stu-id="8b3f1-113">However, the `#If...Then...#Else` directives evaluate what is compiled by the compiler, whereas the `If...Then...Else` statements evaluate conditions at run time.</span></span>  
  
 <span data-ttu-id="8b3f1-114">條件式編譯通常用來編譯為不同平台相同的程式。</span><span class="sxs-lookup"><span data-stu-id="8b3f1-114">Conditional compilation is typically used to compile the same program for different platforms.</span></span> <span data-ttu-id="8b3f1-115">它也會用來防止偵錯的可執行檔中出現的程式碼。</span><span class="sxs-lookup"><span data-stu-id="8b3f1-115">It is also used to prevent debugging code from appearing in an executable file.</span></span> <span data-ttu-id="8b3f1-116">條件式編譯期間排除的程式碼完全中會省略最後的可執行檔，所以其大小或效能上的沒有作用。</span><span class="sxs-lookup"><span data-stu-id="8b3f1-116">Code excluded during conditional compilation is completely omitted from the final executable file, so it has no effect on size or performance.</span></span>  
  
 <span data-ttu-id="8b3f1-117">不論任何評估結果，評估所有運算式都使用`Option Compare Binary`。</span><span class="sxs-lookup"><span data-stu-id="8b3f1-117">Regardless of the outcome of any evaluation, all expressions are evaluated using `Option Compare Binary`.</span></span> <span data-ttu-id="8b3f1-118">`Option Compare`陳述式不會影響運算式中的`#If`和`#ElseIf`陳述式。</span><span class="sxs-lookup"><span data-stu-id="8b3f1-118">The `Option Compare` statement does not affect expressions in `#If` and `#ElseIf` statements.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8b3f1-119">任何單一線條形式的`#If`， `#Else`， `#ElseIf`，和`#End If`存在指示詞。</span><span class="sxs-lookup"><span data-stu-id="8b3f1-119">No single-line form of the `#If`, `#Else`, `#ElseIf`, and `#End If` directives exists.</span></span> <span data-ttu-id="8b3f1-120">沒有其他程式碼可以出現在任何指示詞的同一行。</span><span class="sxs-lookup"><span data-stu-id="8b3f1-120">No other code can appear on the same line as any of the directives.</span></span> 

<span data-ttu-id="8b3f1-121">條件式編譯區塊內的陳述式必須是完整的邏輯陳述式。</span><span class="sxs-lookup"><span data-stu-id="8b3f1-121">The statements within a conditional compilation block must be complete logical statements.</span></span> <span data-ttu-id="8b3f1-122">例如，您不能有條件地編譯函式的屬性，但您可以有條件地宣告的函式，以及它的屬性：</span><span class="sxs-lookup"><span data-stu-id="8b3f1-122">For example, you cannot conditionally compile only the attributes of a function, but you can conditionally declare the function along with its attributes:</span></span>

```vb
   #If DEBUG Then
   <WebMethod()>
   Public Function SomeFunction() As String
   #Else
   <WebMethod(CacheDuration:=86400)>
   Public Function SomeFunction() As String
   #End If
```

## <a name="example"></a><span data-ttu-id="8b3f1-123">範例</span><span class="sxs-lookup"><span data-stu-id="8b3f1-123">Example</span></span>
 <span data-ttu-id="8b3f1-124">這個範例會使用`#If...Then...#Else`建構函式來判斷是否要編譯某些陳述式。</span><span class="sxs-lookup"><span data-stu-id="8b3f1-124">This example uses the `#If...Then...#Else` construct to determine whether to compile certain statements.</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#1](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/if-then-else-directives_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="8b3f1-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8b3f1-125">See Also</span></span>  
[<span data-ttu-id="8b3f1-126">#Const 指示詞</span><span class="sxs-lookup"><span data-stu-id="8b3f1-126">#Const Directive</span></span>](../../../visual-basic/language-reference/directives/const-directive.md)  
[<span data-ttu-id="8b3f1-127">If...Then...Else 陳述式</span><span class="sxs-lookup"><span data-stu-id="8b3f1-127">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
<span data-ttu-id="8b3f1-128">[條件式編譯](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md) </span><span class="sxs-lookup"><span data-stu-id="8b3f1-128">[Conditional Compilation](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md) </span></span>  
<xref:System.Diagnostics.ConditionalAttribute?displayProperty=nameWithType>   


