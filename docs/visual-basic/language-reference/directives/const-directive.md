---
title: '#Const 指示詞'
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
ms.openlocfilehash: 91152771a4ef5ec74a7408511ccc2afe28dd442e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415462"
---
# <a name="const-directive"></a><span data-ttu-id="37d32-102">#Const 指示詞</span><span class="sxs-lookup"><span data-stu-id="37d32-102">#Const Directive</span></span>

<span data-ttu-id="37d32-103">定義 Visual Basic 的條件式編譯器常數。</span><span class="sxs-lookup"><span data-stu-id="37d32-103">Defines conditional compiler constants for Visual Basic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37d32-104">語法</span><span class="sxs-lookup"><span data-stu-id="37d32-104">Syntax</span></span>  
  
```vb  
#Const constname = expression  
```  
  
## <a name="parts"></a><span data-ttu-id="37d32-105">組件</span><span class="sxs-lookup"><span data-stu-id="37d32-105">Parts</span></span>  

 `constname`  
 <span data-ttu-id="37d32-106">必要。</span><span class="sxs-lookup"><span data-stu-id="37d32-106">Required.</span></span> <span data-ttu-id="37d32-107">所定義之常數的名稱。</span><span class="sxs-lookup"><span data-stu-id="37d32-107">Name of the constant being defined.</span></span>  
  
 `expression`  
 <span data-ttu-id="37d32-108">必要。</span><span class="sxs-lookup"><span data-stu-id="37d32-108">Required.</span></span> <span data-ttu-id="37d32-109">常值、其他條件式編譯器常數，或包含除了以外的任何或所有算術或邏輯運算子的任何組合 `Is` 。</span><span class="sxs-lookup"><span data-stu-id="37d32-109">Literal, other conditional compiler constant, or any combination that includes any or all arithmetic or logical operators except `Is`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="37d32-110">備註</span><span class="sxs-lookup"><span data-stu-id="37d32-110">Remarks</span></span>  

 <span data-ttu-id="37d32-111">條件式編譯器常數一律為其出現所在檔案的私用。</span><span class="sxs-lookup"><span data-stu-id="37d32-111">Conditional compiler constants are always private to the file in which they appear.</span></span> <span data-ttu-id="37d32-112">您無法使用指示詞來建立公用編譯器常數 `#Const` ; 您只能在使用者介面或使用編譯器選項來建立它們 `/define` 。</span><span class="sxs-lookup"><span data-stu-id="37d32-112">You cannot create public compiler constants using the `#Const` directive; you can create them only in the user interface or with the `/define` compiler option.</span></span>  
  
 <span data-ttu-id="37d32-113">您只能在中使用條件式編譯器常數和常值 `expression` 。</span><span class="sxs-lookup"><span data-stu-id="37d32-113">You can use only conditional compiler constants and literals in `expression`.</span></span> <span data-ttu-id="37d32-114">使用定義的標準常數 `Const` 會造成錯誤。</span><span class="sxs-lookup"><span data-stu-id="37d32-114">Using a standard constant defined with `Const` causes an error.</span></span> <span data-ttu-id="37d32-115">相反地，您可以使用以關鍵字定義的常數 `#Const` 來進行條件式編譯。</span><span class="sxs-lookup"><span data-stu-id="37d32-115">Conversely, you can use constants defined with the `#Const` keyword only for conditional compilation.</span></span> <span data-ttu-id="37d32-116">常數也可以是未定義的，在此情況下，它們的值為 `Nothing` 。</span><span class="sxs-lookup"><span data-stu-id="37d32-116">Constants can also be undefined, in which case they have a value of `Nothing`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="37d32-117">範例</span><span class="sxs-lookup"><span data-stu-id="37d32-117">Example</span></span>  

 <span data-ttu-id="37d32-118">此範例使用 `#Const` 指示詞。</span><span class="sxs-lookup"><span data-stu-id="37d32-118">This example uses the `#Const` directive.</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="37d32-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="37d32-119">See also</span></span>

- [<span data-ttu-id="37d32-120">-define （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="37d32-120">-define (Visual Basic)</span></span>](../../reference/command-line-compiler/define.md)
- [<span data-ttu-id="37d32-121">#If .。。Then ... #Else 指示詞</span><span class="sxs-lookup"><span data-stu-id="37d32-121">#If...Then...#Else Directives</span></span>](if-then-else-directives.md)
- [<span data-ttu-id="37d32-122">Const 陳述式</span><span class="sxs-lookup"><span data-stu-id="37d32-122">Const Statement</span></span>](../statements/const-statement.md)
- [<span data-ttu-id="37d32-123">條件式編譯</span><span class="sxs-lookup"><span data-stu-id="37d32-123">Conditional Compilation</span></span>](../../programming-guide/program-structure/conditional-compilation.md)
- [<span data-ttu-id="37d32-124">If...Then...Else 陳述式</span><span class="sxs-lookup"><span data-stu-id="37d32-124">If...Then...Else Statement</span></span>](../statements/if-then-else-statement.md)
