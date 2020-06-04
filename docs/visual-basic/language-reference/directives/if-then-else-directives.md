---
title: '#If...Then...#Else 指示詞'
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
ms.openlocfilehash: 7054a6ada4583c5d89e020437eb622a59d3eb17a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410006"
---
# <a name="ifthenelse-directives"></a><span data-ttu-id="b9980-102">#If...Then...#Else 指示詞</span><span class="sxs-lookup"><span data-stu-id="b9980-102">#If...Then...#Else Directives</span></span>

<span data-ttu-id="b9980-103">有條件地編譯選取的 Visual Basic 程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="b9980-103">Conditionally compiles selected blocks of Visual Basic code.</span></span>

## <a name="syntax"></a><span data-ttu-id="b9980-104">語法</span><span class="sxs-lookup"><span data-stu-id="b9980-104">Syntax</span></span>

```vb
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

## <a name="parts"></a><span data-ttu-id="b9980-105">組件</span><span class="sxs-lookup"><span data-stu-id="b9980-105">Parts</span></span>

`expression`  
<span data-ttu-id="b9980-106">`#If`和語句的必要 `#ElseIf` ，其他地方則為選擇性。</span><span class="sxs-lookup"><span data-stu-id="b9980-106">Required for `#If` and `#ElseIf` statements, optional elsewhere.</span></span> <span data-ttu-id="b9980-107">由評估為或的一個或多個條件式編譯器常數、常值和運算子所組成的任何運算式 `True` `False` 。</span><span class="sxs-lookup"><span data-stu-id="b9980-107">Any expression, consisting exclusively of one or more conditional compiler constants, literals, and operators, that evaluates to `True` or `False`.</span></span>

`statements`  
<span data-ttu-id="b9980-108">`#If`語句區塊的必要參數，其他地方則為選擇性。</span><span class="sxs-lookup"><span data-stu-id="b9980-108">Required for `#If` statement block, optional elsewhere.</span></span> <span data-ttu-id="b9980-109">當相關聯的運算式評估為時，Visual Basic 編譯的程式列或編譯器指示詞 `True` 。</span><span class="sxs-lookup"><span data-stu-id="b9980-109">Visual Basic program lines or compiler directives that are compiled if the associated expression evaluates to `True`.</span></span>

`#End If`  
<span data-ttu-id="b9980-110">終止 `#If` 語句區塊。</span><span class="sxs-lookup"><span data-stu-id="b9980-110">Terminates the `#If` statement block.</span></span>

## <a name="remarks"></a><span data-ttu-id="b9980-111">備註</span><span class="sxs-lookup"><span data-stu-id="b9980-111">Remarks</span></span>

<span data-ttu-id="b9980-112">在介面上，指示詞的行為 `#If...Then...#Else` 會與 `If...Then...Else` 語句相同。</span><span class="sxs-lookup"><span data-stu-id="b9980-112">On the surface, the behavior of the `#If...Then...#Else` directives appears the same as that of the `If...Then...Else` statements.</span></span> <span data-ttu-id="b9980-113">不過，指示詞 `#If...Then...#Else` 會評估編譯器所編譯的內容，而 `If...Then...Else` 語句會在執行時間評估條件。</span><span class="sxs-lookup"><span data-stu-id="b9980-113">However, the `#If...Then...#Else` directives evaluate what is compiled by the compiler, whereas the `If...Then...Else` statements evaluate conditions at run time.</span></span>

<span data-ttu-id="b9980-114">條件式編譯通常用來針對不同的平臺編譯相同的程式。</span><span class="sxs-lookup"><span data-stu-id="b9980-114">Conditional compilation is typically used to compile the same program for different platforms.</span></span> <span data-ttu-id="b9980-115">它也可用來防止程式碼在可執行檔中出現。</span><span class="sxs-lookup"><span data-stu-id="b9980-115">It is also used to prevent debugging code from appearing in an executable file.</span></span> <span data-ttu-id="b9980-116">在條件式編譯期間排除的程式碼會完全從最終可執行檔中省略，因此它不會影響大小或效能。</span><span class="sxs-lookup"><span data-stu-id="b9980-116">Code excluded during conditional compilation is completely omitted from the final executable file, so it has no effect on size or performance.</span></span>

<span data-ttu-id="b9980-117">不論任何評估的結果為何，都會使用來評估所有運算式 `Option Compare Binary` 。</span><span class="sxs-lookup"><span data-stu-id="b9980-117">Regardless of the outcome of any evaluation, all expressions are evaluated using `Option Compare Binary`.</span></span> <span data-ttu-id="b9980-118">`Option Compare`語句不會影響和語句中的運算式 `#If` `#ElseIf` 。</span><span class="sxs-lookup"><span data-stu-id="b9980-118">The `Option Compare` statement does not affect expressions in `#If` and `#ElseIf` statements.</span></span>

> [!NOTE]
> <span data-ttu-id="b9980-119">沒有、、和指示詞的單行形式 `#If` `#Else` `#ElseIf` `#End If` 存在。</span><span class="sxs-lookup"><span data-stu-id="b9980-119">No single-line form of the `#If`, `#Else`, `#ElseIf`, and `#End If` directives exists.</span></span> <span data-ttu-id="b9980-120">任何其他程式碼都無法出現在與任何指示詞相同的行上。</span><span class="sxs-lookup"><span data-stu-id="b9980-120">No other code can appear on the same line as any of the directives.</span></span>

<span data-ttu-id="b9980-121">條件式編譯區塊內的語句必須是完整的邏輯語句。</span><span class="sxs-lookup"><span data-stu-id="b9980-121">The statements within a conditional compilation block must be complete logical statements.</span></span> <span data-ttu-id="b9980-122">例如，您不能有條件地只編譯函式的屬性，但您可以有條件地宣告函式及其屬性：</span><span class="sxs-lookup"><span data-stu-id="b9980-122">For example, you cannot conditionally compile only the attributes of a function, but you can conditionally declare the function along with its attributes:</span></span>

```vb
#If DEBUG Then
<WebMethod()>
Public Function SomeFunction() As String
#Else
<WebMethod(CacheDuration:=86400)>
Public Function SomeFunction() As String
#End If
```

## <a name="example"></a><span data-ttu-id="b9980-123">範例</span><span class="sxs-lookup"><span data-stu-id="b9980-123">Example</span></span>

<span data-ttu-id="b9980-124">這個範例會使用 `#If...Then...#Else` 結構來判斷是否要編譯特定語句。</span><span class="sxs-lookup"><span data-stu-id="b9980-124">This example uses the `#If...Then...#Else` construct to determine whether to compile certain statements.</span></span>

[!code-vb[VbVbalrConditionalComp#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#1)]

## <a name="see-also"></a><span data-ttu-id="b9980-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9980-125">See also</span></span>

- [<span data-ttu-id="b9980-126">#Const 指示詞</span><span class="sxs-lookup"><span data-stu-id="b9980-126">#Const Directive</span></span>](const-directive.md)
- [<span data-ttu-id="b9980-127">If...Then...Else 陳述式</span><span class="sxs-lookup"><span data-stu-id="b9980-127">If...Then...Else Statement</span></span>](../statements/if-then-else-statement.md)
- [<span data-ttu-id="b9980-128">條件式編譯</span><span class="sxs-lookup"><span data-stu-id="b9980-128">Conditional Compilation</span></span>](../../programming-guide/program-structure/conditional-compilation.md)
- <xref:System.Diagnostics.ConditionalAttribute?displayProperty=nameWithType>
