---
title: "部分方法 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.PartialMethod
- PartialMethod
helpviewer_keywords:
- custom logic into code [Visual Basic]
- partial methods [Visual Basic]
- partial [Visual Basic], methods [Visual Basic]
- methods [Visual Basic], partial methods
- inserting custom logic into code
ms.assetid: 74b3368b-b348-44a0-a326-7d7dc646f4e9
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8ebedd6f8173e3c349240d24ddaf16e4841f67a4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="partial-methods-visual-basic"></a><span data-ttu-id="a96ab-102">部分方法 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a96ab-102">Partial Methods (Visual Basic)</span></span>
<span data-ttu-id="a96ab-103">部分方法可讓開發人員程式碼中插入自訂邏輯。</span><span class="sxs-lookup"><span data-stu-id="a96ab-103">Partial methods enable developers to insert custom logic into code.</span></span> <span data-ttu-id="a96ab-104">通常，程式碼是類別的設計工具產生的一部分。</span><span class="sxs-lookup"><span data-stu-id="a96ab-104">Typically, the code is part of a designer-generated class.</span></span> <span data-ttu-id="a96ab-105">部分方法中所建立的程式碼產生器中，部分類別定義，它們通常用來提供到的項目已變更的通知。</span><span class="sxs-lookup"><span data-stu-id="a96ab-105">Partial methods are defined in a partial class that is created by a code generator, and they are commonly used to provide notification that something has been changed.</span></span> <span data-ttu-id="a96ab-106">它們可讓開發人員指定自訂的行為變更的回應。</span><span class="sxs-lookup"><span data-stu-id="a96ab-106">They enable the developer to specify custom behavior in response to the change.</span></span>  
  
 <span data-ttu-id="a96ab-107">程式碼產生器的設計工具定義方法簽章和一或多個方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="a96ab-107">The designer of the code generator defines only the method signature and one or more calls to the method.</span></span> <span data-ttu-id="a96ab-108">如果他們想要自訂產生程式碼的行為，開發人員隨後即可提供方法的實作。</span><span class="sxs-lookup"><span data-stu-id="a96ab-108">Developers can then provide implementations for the method if they want to customize the behavior of the generated code.</span></span> <span data-ttu-id="a96ab-109">提供沒有實作時，編譯器，導致沒有產生額外效能負荷會移除對方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="a96ab-109">When no implementation is provided, calls to the method are removed by the compiler, resulting in no additional performance overhead.</span></span>  
  
## <a name="declaration"></a><span data-ttu-id="a96ab-110">宣告</span><span class="sxs-lookup"><span data-stu-id="a96ab-110">Declaration</span></span>  
 <span data-ttu-id="a96ab-111">產生的程式碼將放入關鍵字標記的部分方法定義`Partial`簽章一行的開頭。</span><span class="sxs-lookup"><span data-stu-id="a96ab-111">The generated code marks the definition of a partial method by placing the keyword `Partial` at the start of the signature line.</span></span>  
  
```vb  
Partial Private Sub QuantityChanged()  
End Sub  
```  
  
 <span data-ttu-id="a96ab-112">定義必須符合下列條件：</span><span class="sxs-lookup"><span data-stu-id="a96ab-112">The definition must meet the following conditions:</span></span>  
  
-   <span data-ttu-id="a96ab-113">方法必須為`Sub`，而非`Function`。</span><span class="sxs-lookup"><span data-stu-id="a96ab-113">The method must be a `Sub`, not a `Function`.</span></span>  
  
-   <span data-ttu-id="a96ab-114">方法的主體必須是空白。</span><span class="sxs-lookup"><span data-stu-id="a96ab-114">The body of the method must be left empty.</span></span>  
  
-   <span data-ttu-id="a96ab-115">存取修飾詞必須`Private`。</span><span class="sxs-lookup"><span data-stu-id="a96ab-115">The access modifier must be `Private`.</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="a96ab-116">實作</span><span class="sxs-lookup"><span data-stu-id="a96ab-116">Implementation</span></span>  
 <span data-ttu-id="a96ab-117">實作包含主要填滿的部分方法主體中。</span><span class="sxs-lookup"><span data-stu-id="a96ab-117">The implementation consists primarily of filling in the body of the partial method.</span></span> <span data-ttu-id="a96ab-118">通常是在不同的部分類別定義中，從與想要將產生的程式碼擴充的開發人員撰寫的實作。</span><span class="sxs-lookup"><span data-stu-id="a96ab-118">The implementation is typically in a separate partial class from the definition, and is written by a developer who wants to extend the generated code.</span></span>  
  
```vb  
Private Sub QuantityChanged()  
'    Code for executing the desired action.  
End Sub  
```  
  
 <span data-ttu-id="a96ab-119">上述範例重複項目中宣告的簽章，但可能會有變化。</span><span class="sxs-lookup"><span data-stu-id="a96ab-119">The previous example duplicates the signature in the declaration exactly, but variations are possible.</span></span> <span data-ttu-id="a96ab-120">特別是，其他修飾詞可增加，例如`Overloads`或`Overrides`。</span><span class="sxs-lookup"><span data-stu-id="a96ab-120">In particular, other modifiers can be added, such as `Overloads` or `Overrides`.</span></span> <span data-ttu-id="a96ab-121">只有一個`Overrides`允許修飾詞。</span><span class="sxs-lookup"><span data-stu-id="a96ab-121">Only one `Overrides` modifier is permitted.</span></span> <span data-ttu-id="a96ab-122">如需有關方法的修飾詞的詳細資訊，請參閱[Sub 陳述式](../../../../visual-basic/language-reference/statements/sub-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="a96ab-122">For more information about method modifiers, see [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
## <a name="use"></a><span data-ttu-id="a96ab-123">用法</span><span class="sxs-lookup"><span data-stu-id="a96ab-123">Use</span></span>  
 <span data-ttu-id="a96ab-124">您呼叫的部分方法時，就會呼叫任何其他`Sub`程序。</span><span class="sxs-lookup"><span data-stu-id="a96ab-124">You call a partial method as you would call any other `Sub` procedure.</span></span> <span data-ttu-id="a96ab-125">如果已實作的方法，評估引數，並執行之方法主體。</span><span class="sxs-lookup"><span data-stu-id="a96ab-125">If the method has been implemented, the arguments are evaluated and the body of the method is executed.</span></span> <span data-ttu-id="a96ab-126">不過請記住，實作部分方法是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="a96ab-126">However, remember that implementing a partial method is optional.</span></span> <span data-ttu-id="a96ab-127">如果未實作方法，它的呼叫沒有任何作用，並不會評估運算式做為引數傳遞給方法。</span><span class="sxs-lookup"><span data-stu-id="a96ab-127">If the method is not implemented, a call to it has no effect, and expressions passed as arguments to the method are not evaluated.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a96ab-128">範例</span><span class="sxs-lookup"><span data-stu-id="a96ab-128">Example</span></span>  
 <span data-ttu-id="a96ab-129">在檔案中名為 Product.Designer.vb，定義`Product`類別具有`Quantity`屬性。</span><span class="sxs-lookup"><span data-stu-id="a96ab-129">In a file named Product.Designer.vb, define a `Product` class that has a `Quantity` property.</span></span>  
  
 [!code-vb[VbVbalrPartialMeths#4](./codesnippet/VisualBasic/partial-methods_1.vb)]  
  
 <span data-ttu-id="a96ab-130">在檔案中名為 Product.vb，提供實作`QuantityChanged`。</span><span class="sxs-lookup"><span data-stu-id="a96ab-130">In a file named Product.vb, provide an implementation for `QuantityChanged`.</span></span>  
  
 [!code-vb[VbVbalrPartialMeths#5](./codesnippet/VisualBasic/partial-methods_2.vb)]  
  
 <span data-ttu-id="a96ab-131">最後，在專案的 Main 方法中，宣告`Product`執行個體並提供的初始值其`Quantity`屬性。</span><span class="sxs-lookup"><span data-stu-id="a96ab-131">Finally, in the Main method of a project, declare a `Product` instance and provide an initial value for its `Quantity` property.</span></span>  
  
 [!code-vb[VbVbalrPartialMeths#6](./codesnippet/VisualBasic/partial-methods_3.vb)]  
  
 <span data-ttu-id="a96ab-132">應該會出現訊息方塊會顯示此訊息：</span><span class="sxs-lookup"><span data-stu-id="a96ab-132">A message box should appear that displays this message:</span></span>  
  
 `Quantity was changed to 100`  
  
## <a name="see-also"></a><span data-ttu-id="a96ab-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a96ab-133">See Also</span></span>  
 [<span data-ttu-id="a96ab-134">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="a96ab-134">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="a96ab-135">Sub 程序</span><span class="sxs-lookup"><span data-stu-id="a96ab-135">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="a96ab-136">選擇性參數</span><span class="sxs-lookup"><span data-stu-id="a96ab-136">Optional Parameters</span></span>](./optional-parameters.md)  
 [<span data-ttu-id="a96ab-137">Partial</span><span class="sxs-lookup"><span data-stu-id="a96ab-137">Partial</span></span>](../../../../visual-basic/language-reference/modifiers/partial.md)  
 [<span data-ttu-id="a96ab-138">LINQ to SQL 中的程式碼產生</span><span class="sxs-lookup"><span data-stu-id="a96ab-138">Code Generation in LINQ to SQL</span></span>](https://msdn.microsoft.com/library/bb399400)  
 [<span data-ttu-id="a96ab-139">使用部分方法加入商務邏輯</span><span class="sxs-lookup"><span data-stu-id="a96ab-139">Adding Business Logic By Using Partial Methods</span></span>](https://msdn.microsoft.com/library/bb546176)
