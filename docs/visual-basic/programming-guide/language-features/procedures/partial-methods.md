---
title: 部分方法
ms.date: 07/20/2015
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
ms.openlocfilehash: 61a1398ba7de8dab005fa1e9efa13dc2ba18cc3c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84364119"
---
# <a name="partial-methods-visual-basic"></a><span data-ttu-id="9c35e-102">部分方法 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9c35e-102">Partial Methods (Visual Basic)</span></span>
<span data-ttu-id="9c35e-103">部分方法可讓開發人員在程式碼中插入自訂邏輯。</span><span class="sxs-lookup"><span data-stu-id="9c35e-103">Partial methods enable developers to insert custom logic into code.</span></span> <span data-ttu-id="9c35e-104">一般來說，程式碼是設計工具產生之類別的一部分。</span><span class="sxs-lookup"><span data-stu-id="9c35e-104">Typically, the code is part of a designer-generated class.</span></span> <span data-ttu-id="9c35e-105">部分方法定義于程式碼產生器所建立的部分類別中，而且通常用來提供已變更專案的通知。</span><span class="sxs-lookup"><span data-stu-id="9c35e-105">Partial methods are defined in a partial class that is created by a code generator, and they are commonly used to provide notification that something has been changed.</span></span> <span data-ttu-id="9c35e-106">它們可讓開發人員指定自訂行為，以回應變更。</span><span class="sxs-lookup"><span data-stu-id="9c35e-106">They enable the developer to specify custom behavior in response to the change.</span></span>  
  
 <span data-ttu-id="9c35e-107">程式碼產生器的設計工具只會定義方法簽章，以及一或多個對方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="9c35e-107">The designer of the code generator defines only the method signature and one or more calls to the method.</span></span> <span data-ttu-id="9c35e-108">如果開發人員想要自訂所產生程式碼的行為，則可以提供方法的實作為方式。</span><span class="sxs-lookup"><span data-stu-id="9c35e-108">Developers can then provide implementations for the method if they want to customize the behavior of the generated code.</span></span> <span data-ttu-id="9c35e-109">當未提供任何執行時，編譯器會移除對方法的呼叫，而不會產生額外的效能負擔。</span><span class="sxs-lookup"><span data-stu-id="9c35e-109">When no implementation is provided, calls to the method are removed by the compiler, resulting in no additional performance overhead.</span></span>  
  
## <a name="declaration"></a><span data-ttu-id="9c35e-110">宣告</span><span class="sxs-lookup"><span data-stu-id="9c35e-110">Declaration</span></span>  
 <span data-ttu-id="9c35e-111">產生的程式碼會將關鍵字放在簽章行開頭，以標記部分方法的定義 `Partial` 。</span><span class="sxs-lookup"><span data-stu-id="9c35e-111">The generated code marks the definition of a partial method by placing the keyword `Partial` at the start of the signature line.</span></span>  
  
```vb  
Partial Private Sub QuantityChanged()  
End Sub  
```  
  
 <span data-ttu-id="9c35e-112">定義必須符合下列條件：</span><span class="sxs-lookup"><span data-stu-id="9c35e-112">The definition must meet the following conditions:</span></span>  
  
- <span data-ttu-id="9c35e-113">方法必須是 `Sub` ，而不是 `Function` 。</span><span class="sxs-lookup"><span data-stu-id="9c35e-113">The method must be a `Sub`, not a `Function`.</span></span>  
  
- <span data-ttu-id="9c35e-114">方法的主體必須保留空白。</span><span class="sxs-lookup"><span data-stu-id="9c35e-114">The body of the method must be left empty.</span></span>  
  
- <span data-ttu-id="9c35e-115">存取修飾詞必須是 `Private` 。</span><span class="sxs-lookup"><span data-stu-id="9c35e-115">The access modifier must be `Private`.</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="9c35e-116">實作</span><span class="sxs-lookup"><span data-stu-id="9c35e-116">Implementation</span></span>  
 <span data-ttu-id="9c35e-117">此實作為主要的部分方法。</span><span class="sxs-lookup"><span data-stu-id="9c35e-117">The implementation consists primarily of filling in the body of the partial method.</span></span> <span data-ttu-id="9c35e-118">此實作為定義的一部分，通常是在不同的部分類別中，而且是由想要擴充所產生程式碼的開發人員所撰寫。</span><span class="sxs-lookup"><span data-stu-id="9c35e-118">The implementation is typically in a separate partial class from the definition, and is written by a developer who wants to extend the generated code.</span></span>  
  
```vb  
Private Sub QuantityChanged()  
'    Code for executing the desired action.  
End Sub  
```  
  
 <span data-ttu-id="9c35e-119">上一個範例會完全複製宣告中的簽章，但可能會有變化。</span><span class="sxs-lookup"><span data-stu-id="9c35e-119">The previous example duplicates the signature in the declaration exactly, but variations are possible.</span></span> <span data-ttu-id="9c35e-120">特別是，可以加入其他修飾詞，例如 `Overloads` 或 `Overrides` 。</span><span class="sxs-lookup"><span data-stu-id="9c35e-120">In particular, other modifiers can be added, such as `Overloads` or `Overrides`.</span></span> <span data-ttu-id="9c35e-121">只 `Overrides` 允許一個修飾詞。</span><span class="sxs-lookup"><span data-stu-id="9c35e-121">Only one `Overrides` modifier is permitted.</span></span> <span data-ttu-id="9c35e-122">如需方法修飾詞的詳細資訊，請參閱[Sub 語句](../../../language-reference/statements/sub-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="9c35e-122">For more information about method modifiers, see [Sub Statement](../../../language-reference/statements/sub-statement.md).</span></span>  
  
## <a name="use"></a><span data-ttu-id="9c35e-123">使用</span><span class="sxs-lookup"><span data-stu-id="9c35e-123">Use</span></span>  
 <span data-ttu-id="9c35e-124">您可以呼叫部分方法，就像呼叫任何其他程式一樣 `Sub` 。</span><span class="sxs-lookup"><span data-stu-id="9c35e-124">You call a partial method as you would call any other `Sub` procedure.</span></span> <span data-ttu-id="9c35e-125">如果已執行方法，則會評估引數，並執行方法的主體。</span><span class="sxs-lookup"><span data-stu-id="9c35e-125">If the method has been implemented, the arguments are evaluated and the body of the method is executed.</span></span> <span data-ttu-id="9c35e-126">不過，請記住，執行部分方法是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="9c35e-126">However, remember that implementing a partial method is optional.</span></span> <span data-ttu-id="9c35e-127">如果未執行方法，則呼叫它不會有任何作用，而且不會評估當做引數傳遞至方法的運算式。</span><span class="sxs-lookup"><span data-stu-id="9c35e-127">If the method is not implemented, a call to it has no effect, and expressions passed as arguments to the method are not evaluated.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c35e-128">範例</span><span class="sxs-lookup"><span data-stu-id="9c35e-128">Example</span></span>  
 <span data-ttu-id="9c35e-129">在名為 .vb 的檔案中，定義 `Product` 具有屬性的類別 `Quantity` 。</span><span class="sxs-lookup"><span data-stu-id="9c35e-129">In a file named Product.Designer.vb, define a `Product` class that has a `Quantity` property.</span></span>  
  
 [!code-vb[VbVbalrPartialMeths#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#4)]  
  
 <span data-ttu-id="9c35e-130">在名為 .vb 的檔案中，提供的執行 `QuantityChanged` 。</span><span class="sxs-lookup"><span data-stu-id="9c35e-130">In a file named Product.vb, provide an implementation for `QuantityChanged`.</span></span>  
  
 [!code-vb[VbVbalrPartialMeths#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#5)]  
  
 <span data-ttu-id="9c35e-131">最後，在專案的 Main 方法中，宣告實例， `Product` 並提供其屬性的初始值 `Quantity` 。</span><span class="sxs-lookup"><span data-stu-id="9c35e-131">Finally, in the Main method of a project, declare a `Product` instance and provide an initial value for its `Quantity` property.</span></span>  
  
 [!code-vb[VbVbalrPartialMeths#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#6)]  
  
 <span data-ttu-id="9c35e-132">此時應該會出現訊息方塊，顯示此訊息：</span><span class="sxs-lookup"><span data-stu-id="9c35e-132">A message box should appear that displays this message:</span></span>  
  
 `Quantity was changed to 100`  
  
## <a name="see-also"></a><span data-ttu-id="9c35e-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9c35e-133">See also</span></span>

- [<span data-ttu-id="9c35e-134">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="9c35e-134">Sub Statement</span></span>](../../../language-reference/statements/sub-statement.md)
- [<span data-ttu-id="9c35e-135">Sub 程序</span><span class="sxs-lookup"><span data-stu-id="9c35e-135">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="9c35e-136">選擇性參數</span><span class="sxs-lookup"><span data-stu-id="9c35e-136">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="9c35e-137">Partial</span><span class="sxs-lookup"><span data-stu-id="9c35e-137">Partial</span></span>](../../../language-reference/modifiers/partial.md)
- [<span data-ttu-id="9c35e-138">LINQ to SQL 中的程式碼產生</span><span class="sxs-lookup"><span data-stu-id="9c35e-138">Code Generation in LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [<span data-ttu-id="9c35e-139">使用部分方法新增商務邏輯</span><span class="sxs-lookup"><span data-stu-id="9c35e-139">Adding Business Logic By Using Partial Methods</span></span>](../../../../framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md)
