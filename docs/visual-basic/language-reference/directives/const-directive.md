---
title: '#Const 指示詞 (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.#Const
- '#vb.Const'
- '#Const'
helpviewer_keywords:
- '#Const directive'
- conditional compilation [Visual Basic], directives
- Const directive (#Const)
- Visual Basic compiler, compiler directives
- constants [Visual Basic], Const directive
- constants [Visual Basic], declaring
- Const statement [Visual Basic], directive (#Const)
- 'declaring constants [Visual Basic], #const directive'
ms.assetid: 707669e5-23f9-4f17-8622-a0d534429386
ms.openlocfilehash: 58d786c5e16b1e667f7c7c78b0f7857cd9711239
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43541610"
---
# <a name="const-directive"></a><span data-ttu-id="899c7-102">#Const 指示詞</span><span class="sxs-lookup"><span data-stu-id="899c7-102">#Const Directive</span></span>
<span data-ttu-id="899c7-103">適用於 Visual Basic 中定義條件式編譯器常數。</span><span class="sxs-lookup"><span data-stu-id="899c7-103">Defines conditional compiler constants for Visual Basic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="899c7-104">語法</span><span class="sxs-lookup"><span data-stu-id="899c7-104">Syntax</span></span>  
  
```  
#Const constname = expression  
```  
  
## <a name="parts"></a><span data-ttu-id="899c7-105">組件</span><span class="sxs-lookup"><span data-stu-id="899c7-105">Parts</span></span>  
 `constname`  
 <span data-ttu-id="899c7-106">必要。</span><span class="sxs-lookup"><span data-stu-id="899c7-106">Required.</span></span> <span data-ttu-id="899c7-107">所定義的常數名稱。</span><span class="sxs-lookup"><span data-stu-id="899c7-107">Name of the constant being defined.</span></span>  
  
 `expression`  
 <span data-ttu-id="899c7-108">必要。</span><span class="sxs-lookup"><span data-stu-id="899c7-108">Required.</span></span> <span data-ttu-id="899c7-109">常值、 條件式編譯器常數或任何組合，包括任何或所有算術或邏輯運算子，除了`Is`。</span><span class="sxs-lookup"><span data-stu-id="899c7-109">Literal, other conditional compiler constant, or any combination that includes any or all arithmetic or logical operators except `Is`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="899c7-110">備註</span><span class="sxs-lookup"><span data-stu-id="899c7-110">Remarks</span></span>  
 <span data-ttu-id="899c7-111">條件式編譯器常數一律是以其出現的檔案公開的。</span><span class="sxs-lookup"><span data-stu-id="899c7-111">Conditional compiler constants are always private to the file in which they appear.</span></span> <span data-ttu-id="899c7-112">您無法建立使用的公用編譯器常數`#Const`指示詞; 您可以只在使用者介面，或與建立它們`/define`編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="899c7-112">You cannot create public compiler constants using the `#Const` directive; you can create them only in the user interface or with the `/define` compiler option.</span></span>  
  
 <span data-ttu-id="899c7-113">您只能使用條件式編譯器常數和常值中的`expression`。</span><span class="sxs-lookup"><span data-stu-id="899c7-113">You can use only conditional compiler constants and literals in `expression`.</span></span> <span data-ttu-id="899c7-114">使用標準的常數，以定義`Const`會造成錯誤。</span><span class="sxs-lookup"><span data-stu-id="899c7-114">Using a standard constant defined with `Const` causes an error.</span></span> <span data-ttu-id="899c7-115">相反地，您可以使用常數定義`#Const`條件式編譯的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="899c7-115">Conversely, you can use constants defined with the `#Const` keyword only for conditional compilation.</span></span> <span data-ttu-id="899c7-116">常數也可以定義，在此情況下，它們的值為`Nothing`。</span><span class="sxs-lookup"><span data-stu-id="899c7-116">Constants can also be undefined, in which case they have a value of `Nothing`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="899c7-117">範例</span><span class="sxs-lookup"><span data-stu-id="899c7-117">Example</span></span>  
 <span data-ttu-id="899c7-118">此範例使用 `#Const` 指示詞。</span><span class="sxs-lookup"><span data-stu-id="899c7-118">This example uses the `#Const` directive.</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#3](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/const-directive_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="899c7-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="899c7-119">See Also</span></span>  
 [<span data-ttu-id="899c7-120">/define (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="899c7-120">/define (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/define.md)  
 [<span data-ttu-id="899c7-121">#If...Then...#Else 指示詞</span><span class="sxs-lookup"><span data-stu-id="899c7-121">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [<span data-ttu-id="899c7-122">Const 陳述式</span><span class="sxs-lookup"><span data-stu-id="899c7-122">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
 [<span data-ttu-id="899c7-123">條件式編譯</span><span class="sxs-lookup"><span data-stu-id="899c7-123">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 [<span data-ttu-id="899c7-124">If...Then...Else 陳述式</span><span class="sxs-lookup"><span data-stu-id="899c7-124">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
