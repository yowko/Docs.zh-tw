---
title: 部分方法 (Visual Basic)
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
ms.openlocfilehash: 765a667f18340c53909c3ff1e9fcc5f2ffc0f9bc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791933"
---
# <a name="partial-methods-visual-basic"></a><span data-ttu-id="e7300-102">部分方法 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e7300-102">Partial Methods (Visual Basic)</span></span>
<span data-ttu-id="e7300-103">部分方法可讓開發人員程式碼中插入自訂邏輯。</span><span class="sxs-lookup"><span data-stu-id="e7300-103">Partial methods enable developers to insert custom logic into code.</span></span> <span data-ttu-id="e7300-104">一般而言，程式碼會是類別的一部分的設計工具所產生。</span><span class="sxs-lookup"><span data-stu-id="e7300-104">Typically, the code is part of a designer-generated class.</span></span> <span data-ttu-id="e7300-105">部分方法中所建立的程式碼產生器中，部分類別定義，它們通常用來提供的項目已變更的通知。</span><span class="sxs-lookup"><span data-stu-id="e7300-105">Partial methods are defined in a partial class that is created by a code generator, and they are commonly used to provide notification that something has been changed.</span></span> <span data-ttu-id="e7300-106">它們可讓開發人員指定自訂的行為變更的回應。</span><span class="sxs-lookup"><span data-stu-id="e7300-106">They enable the developer to specify custom behavior in response to the change.</span></span>  
  
 <span data-ttu-id="e7300-107">程式碼產生器的設計工具定義方法簽章和方法的一個或多個呼叫。</span><span class="sxs-lookup"><span data-stu-id="e7300-107">The designer of the code generator defines only the method signature and one or more calls to the method.</span></span> <span data-ttu-id="e7300-108">如果他們想要自訂產生的程式碼的行為，開發人員可以接著會提供方法的實作。</span><span class="sxs-lookup"><span data-stu-id="e7300-108">Developers can then provide implementations for the method if they want to customize the behavior of the generated code.</span></span> <span data-ttu-id="e7300-109">提供任何實作時，對方法的呼叫會移除的編譯器，產生任何額外的效能負擔。</span><span class="sxs-lookup"><span data-stu-id="e7300-109">When no implementation is provided, calls to the method are removed by the compiler, resulting in no additional performance overhead.</span></span>  
  
## <a name="declaration"></a><span data-ttu-id="e7300-110">宣告</span><span class="sxs-lookup"><span data-stu-id="e7300-110">Declaration</span></span>  
 <span data-ttu-id="e7300-111">產生的程式碼會加上關鍵字標記的部分方法定義`Partial`簽名行開頭。</span><span class="sxs-lookup"><span data-stu-id="e7300-111">The generated code marks the definition of a partial method by placing the keyword `Partial` at the start of the signature line.</span></span>  
  
```vb  
Partial Private Sub QuantityChanged()  
End Sub  
```  
  
 <span data-ttu-id="e7300-112">定義必須符合下列條件：</span><span class="sxs-lookup"><span data-stu-id="e7300-112">The definition must meet the following conditions:</span></span>  
  
- <span data-ttu-id="e7300-113">這個方法必須是`Sub`，而非`Function`。</span><span class="sxs-lookup"><span data-stu-id="e7300-113">The method must be a `Sub`, not a `Function`.</span></span>  
  
- <span data-ttu-id="e7300-114">方法的主體必須是空白。</span><span class="sxs-lookup"><span data-stu-id="e7300-114">The body of the method must be left empty.</span></span>  
  
- <span data-ttu-id="e7300-115">存取修飾詞必須是`Private`。</span><span class="sxs-lookup"><span data-stu-id="e7300-115">The access modifier must be `Private`.</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="e7300-116">實作</span><span class="sxs-lookup"><span data-stu-id="e7300-116">Implementation</span></span>  
 <span data-ttu-id="e7300-117">實作主要包含填入部分方法的主體。</span><span class="sxs-lookup"><span data-stu-id="e7300-117">The implementation consists primarily of filling in the body of the partial method.</span></span> <span data-ttu-id="e7300-118">實作通常是在不同的部分類別定義，並寫入由開發人員想要擴充產生的程式碼。</span><span class="sxs-lookup"><span data-stu-id="e7300-118">The implementation is typically in a separate partial class from the definition, and is written by a developer who wants to extend the generated code.</span></span>  
  
```vb  
Private Sub QuantityChanged()  
'    Code for executing the desired action.  
End Sub  
```  
  
 <span data-ttu-id="e7300-119">上述範例重複項目中宣告的簽章，但可能會有變化。</span><span class="sxs-lookup"><span data-stu-id="e7300-119">The previous example duplicates the signature in the declaration exactly, but variations are possible.</span></span> <span data-ttu-id="e7300-120">特別是，其他修飾詞，可以加入這類`Overloads`或`Overrides`。</span><span class="sxs-lookup"><span data-stu-id="e7300-120">In particular, other modifiers can be added, such as `Overloads` or `Overrides`.</span></span> <span data-ttu-id="e7300-121">只有一個`Overrides`允許修飾詞。</span><span class="sxs-lookup"><span data-stu-id="e7300-121">Only one `Overrides` modifier is permitted.</span></span> <span data-ttu-id="e7300-122">如需有關方法的修飾詞的詳細資訊，請參閱 < [Sub 陳述式](../../../../visual-basic/language-reference/statements/sub-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="e7300-122">For more information about method modifiers, see [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
## <a name="use"></a><span data-ttu-id="e7300-123">使用</span><span class="sxs-lookup"><span data-stu-id="e7300-123">Use</span></span>  
 <span data-ttu-id="e7300-124">您呼叫的部分方法時，就會呼叫任何其他`Sub`程序。</span><span class="sxs-lookup"><span data-stu-id="e7300-124">You call a partial method as you would call any other `Sub` procedure.</span></span> <span data-ttu-id="e7300-125">如果方法已實作，會評估引數，並執行方法的主體。</span><span class="sxs-lookup"><span data-stu-id="e7300-125">If the method has been implemented, the arguments are evaluated and the body of the method is executed.</span></span> <span data-ttu-id="e7300-126">不過請記住，實作部分方法是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="e7300-126">However, remember that implementing a partial method is optional.</span></span> <span data-ttu-id="e7300-127">如果未實作方法，呼叫它沒有任何作用，並不會評估運算式做為引數傳遞至方法。</span><span class="sxs-lookup"><span data-stu-id="e7300-127">If the method is not implemented, a call to it has no effect, and expressions passed as arguments to the method are not evaluated.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7300-128">範例</span><span class="sxs-lookup"><span data-stu-id="e7300-128">Example</span></span>  
 <span data-ttu-id="e7300-129">在檔案中名為 Product.Designer.vb，定義`Product`類別具有`Quantity`屬性。</span><span class="sxs-lookup"><span data-stu-id="e7300-129">In a file named Product.Designer.vb, define a `Product` class that has a `Quantity` property.</span></span>  
  
 [!code-vb[VbVbalrPartialMeths#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#4)]  
  
 <span data-ttu-id="e7300-130">在檔案中名為 Product.vb，提供實作`QuantityChanged`。</span><span class="sxs-lookup"><span data-stu-id="e7300-130">In a file named Product.vb, provide an implementation for `QuantityChanged`.</span></span>  
  
 [!code-vb[VbVbalrPartialMeths#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#5)]  
  
 <span data-ttu-id="e7300-131">最後，在專案的 Main 方法中，宣告`Product`執行個體，並提供初始值其`Quantity`屬性。</span><span class="sxs-lookup"><span data-stu-id="e7300-131">Finally, in the Main method of a project, declare a `Product` instance and provide an initial value for its `Quantity` property.</span></span>  
  
 [!code-vb[VbVbalrPartialMeths#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#6)]  
  
 <span data-ttu-id="e7300-132">應該會出現訊息方塊，會顯示下列訊息：</span><span class="sxs-lookup"><span data-stu-id="e7300-132">A message box should appear that displays this message:</span></span>  
  
 `Quantity was changed to 100`  
  
## <a name="see-also"></a><span data-ttu-id="e7300-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7300-133">See also</span></span>

- [<span data-ttu-id="e7300-134">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="e7300-134">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="e7300-135">Sub 程序</span><span class="sxs-lookup"><span data-stu-id="e7300-135">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="e7300-136">選擇性參數</span><span class="sxs-lookup"><span data-stu-id="e7300-136">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="e7300-137">Partial</span><span class="sxs-lookup"><span data-stu-id="e7300-137">Partial</span></span>](../../../../visual-basic/language-reference/modifiers/partial.md)
- [<span data-ttu-id="e7300-138">LINQ to SQL 中的程式碼產生</span><span class="sxs-lookup"><span data-stu-id="e7300-138">Code Generation in LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [<span data-ttu-id="e7300-139">使用部分方法新增商務邏輯</span><span class="sxs-lookup"><span data-stu-id="e7300-139">Adding Business Logic By Using Partial Methods</span></span>](../../../../framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md)
