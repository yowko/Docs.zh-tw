---
title: 泛型程序
ms.date: 07/20/2015
helpviewer_keywords:
- generic methods [Visual Basic], type inference
- generics [Visual Basic], type inference
- procedures [Visual Basic], generic
- generic procedures
- type inference, generics
- generic methods [Visual Basic]
- type inference
- generics [Visual Basic], procedures
- generic procedures [Visual Basic], type inference
ms.assetid: 95577b28-137f-4d5c-a149-919c828600e5
ms.openlocfilehash: 558601f038fccdcb9b94acb7c796e2b49fb6e6f4
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91059193"
---
# <a name="generic-procedures-in-visual-basic"></a><span data-ttu-id="c839a-102">Generic Procedures in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c839a-102">Generic Procedures in Visual Basic</span></span>

<span data-ttu-id="c839a-103">*泛型*程式（也稱為*泛型方法*）是至少以一個類型參數定義的程式。</span><span class="sxs-lookup"><span data-stu-id="c839a-103">A *generic procedure*, also called a *generic method*, is a procedure defined with at least one type parameter.</span></span> <span data-ttu-id="c839a-104">這可讓呼叫程式碼在每次呼叫程式時，將資料類型自訂為其需求。</span><span class="sxs-lookup"><span data-stu-id="c839a-104">This allows the calling code to tailor the data types to its requirements each time it calls the procedure.</span></span>  
  
 <span data-ttu-id="c839a-105">程式並非泛型，只要是在泛型類別或泛型結構內定義。</span><span class="sxs-lookup"><span data-stu-id="c839a-105">A procedure is not generic simply by virtue of being defined inside a generic class or a generic structure.</span></span> <span data-ttu-id="c839a-106">若為泛型，除了可能採用的任何一般參數之外，此程式必須至少要有一個型別參數。</span><span class="sxs-lookup"><span data-stu-id="c839a-106">To be generic, the procedure must take at least one type parameter, in addition to any normal parameters it might take.</span></span> <span data-ttu-id="c839a-107">泛型類別或結構可以包含非泛型程式，而非泛型類別、結構或模組可以包含泛型程式。</span><span class="sxs-lookup"><span data-stu-id="c839a-107">A generic class or structure can contain nongeneric procedures, and a nongeneric class, structure, or module can contain generic procedures.</span></span>  
  
 <span data-ttu-id="c839a-108">泛型程式可以在其一般參數清單中使用其型別參數（如果有的話），並在其程式碼中使用它的傳回型別。</span><span class="sxs-lookup"><span data-stu-id="c839a-108">A generic procedure can use its type parameters in its normal parameter list, in its return type if it has one, and in its procedure code.</span></span>  
  
## <a name="type-inference"></a><span data-ttu-id="c839a-109">類型推斷</span><span class="sxs-lookup"><span data-stu-id="c839a-109">Type Inference</span></span>  

 <span data-ttu-id="c839a-110">您可以呼叫泛型程式，完全不提供任何類型引數。</span><span class="sxs-lookup"><span data-stu-id="c839a-110">You can call a generic procedure without supplying any type arguments at all.</span></span> <span data-ttu-id="c839a-111">如果您以這種方式呼叫它，則編譯器會嘗試判斷要傳遞給程式型別引數的適當資料類型。</span><span class="sxs-lookup"><span data-stu-id="c839a-111">If you call it this way, the compiler attempts to determine the appropriate data types to pass to the procedure's type arguments.</span></span> <span data-ttu-id="c839a-112">這稱為「 *型別推斷*」。</span><span class="sxs-lookup"><span data-stu-id="c839a-112">This is called *type inference*.</span></span> <span data-ttu-id="c839a-113">下列程式碼示範編譯器推斷應將型別傳遞 `String` 至型別參數的呼叫 `t` 。</span><span class="sxs-lookup"><span data-stu-id="c839a-113">The following code shows a call in which the compiler infers that it should pass type `String` to the type parameter `t`.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#15)]  
  
 <span data-ttu-id="c839a-114">如果編譯器無法從呼叫內容推斷類型引數，則會報告錯誤。</span><span class="sxs-lookup"><span data-stu-id="c839a-114">If the compiler cannot infer the type arguments from the context of your call, it reports an error.</span></span> <span data-ttu-id="c839a-115">這類錯誤的其中一個可能原因是陣列排名不相符。</span><span class="sxs-lookup"><span data-stu-id="c839a-115">One possible cause of such an error is an array rank mismatch.</span></span> <span data-ttu-id="c839a-116">例如，假設您將一般參數定義為型別參數的陣列。</span><span class="sxs-lookup"><span data-stu-id="c839a-116">For example, suppose you define a normal parameter as an array of a type parameter.</span></span> <span data-ttu-id="c839a-117">如果您呼叫泛型程式來提供不同排名的陣列 () 的維度數目，則不相符會導致型別推斷失敗。</span><span class="sxs-lookup"><span data-stu-id="c839a-117">If you call the generic procedure supplying an array of a different rank (number of dimensions), the mismatch causes type inference to fail.</span></span> <span data-ttu-id="c839a-118">下列程式碼示範將二維陣列傳遞至需要一維陣列的程式的呼叫。</span><span class="sxs-lookup"><span data-stu-id="c839a-118">The following code shows a call in which a two-dimensional array is passed to a procedure that expects a one-dimensional array.</span></span>  
  
```vb  
Public Sub demoSub(Of t)(ByVal arg() As t)
End Sub

Public Sub callDemoSub()
    Dim twoDimensions(,) As Integer
    demoSub(twoDimensions)
End Sub
```
  
 <span data-ttu-id="c839a-119">您只能藉由省略所有型別引數來叫用型別推斷。</span><span class="sxs-lookup"><span data-stu-id="c839a-119">You can invoke type inference only by omitting all the type arguments.</span></span> <span data-ttu-id="c839a-120">如果您提供一個類型引數，則必須提供這些引數。</span><span class="sxs-lookup"><span data-stu-id="c839a-120">If you supply one type argument, you must supply them all.</span></span>  
  
 <span data-ttu-id="c839a-121">只有泛型程式才支援型別推斷。</span><span class="sxs-lookup"><span data-stu-id="c839a-121">Type inference is supported only for generic procedures.</span></span> <span data-ttu-id="c839a-122">您無法在泛型類別、結構、介面或委派上叫用型別推斷。</span><span class="sxs-lookup"><span data-stu-id="c839a-122">You cannot invoke type inference on generic classes, structures, interfaces, or delegates.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c839a-123">範例</span><span class="sxs-lookup"><span data-stu-id="c839a-123">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="c839a-124">描述</span><span class="sxs-lookup"><span data-stu-id="c839a-124">Description</span></span>  

 <span data-ttu-id="c839a-125">下列範例會定義泛型 `Function` 程式，以尋找陣列中的特定元素。</span><span class="sxs-lookup"><span data-stu-id="c839a-125">The following example defines a generic `Function` procedure to find a particular element in an array.</span></span> <span data-ttu-id="c839a-126">它會定義一個型別參數，並使用它來在參數清單中建立兩個參數。</span><span class="sxs-lookup"><span data-stu-id="c839a-126">It defines one type parameter and uses it to construct the two parameters in the parameter list.</span></span>  
  
### <a name="code"></a><span data-ttu-id="c839a-127">程式碼</span><span class="sxs-lookup"><span data-stu-id="c839a-127">Code</span></span>  

 [!code-vb[VbVbalrDataTypes#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#14)]  
  
### <a name="comments"></a><span data-ttu-id="c839a-128">註解</span><span class="sxs-lookup"><span data-stu-id="c839a-128">Comments</span></span>  

 <span data-ttu-id="c839a-129">上述範例需要能夠與 `searchValue` 的每個專案進行比較 `searchArray` 。</span><span class="sxs-lookup"><span data-stu-id="c839a-129">The preceding example requires the ability to compare `searchValue` against each element of `searchArray`.</span></span> <span data-ttu-id="c839a-130">為保證這種功能，它會限制型別參數 `T` 來執行 <xref:System.IComparable%601> 介面。</span><span class="sxs-lookup"><span data-stu-id="c839a-130">To guarantee this ability, it constrains the type parameter `T` to implement the <xref:System.IComparable%601> interface.</span></span> <span data-ttu-id="c839a-131">程式碼會使用 <xref:System.IComparable%601.CompareTo%2A> 方法，而不是 `=` 運算子，因為不保證提供的型別引數可 `T` 支援 `=` 運算子。</span><span class="sxs-lookup"><span data-stu-id="c839a-131">The code uses the <xref:System.IComparable%601.CompareTo%2A> method instead of the `=` operator, because there is no guarantee that a type argument supplied for `T` supports the `=` operator.</span></span>  
  
 <span data-ttu-id="c839a-132">您可以使用下列程式碼來測試程式 `findElement` 。</span><span class="sxs-lookup"><span data-stu-id="c839a-132">You can test the `findElement` procedure with the following code.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#13)]  
  
 <span data-ttu-id="c839a-133">上述呼叫會 `MsgBox` 分別顯示 "0"、"1" 和 "-1"。</span><span class="sxs-lookup"><span data-stu-id="c839a-133">The preceding calls to `MsgBox` display "0", "1", and "-1" respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c839a-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c839a-134">See also</span></span>

- [<span data-ttu-id="c839a-135">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c839a-135">Generic Types in Visual Basic</span></span>](generic-types.md)
- [<span data-ttu-id="c839a-136">作法：定義可以為不同資料類型提供相同功能的類別</span><span class="sxs-lookup"><span data-stu-id="c839a-136">How to: Define a Class That Can Provide Identical Functionality on Different Data Types</span></span>](how-to-define-a-class-that-can-provide-identical-functionality.md)
- [<span data-ttu-id="c839a-137">作法：使用泛型類別</span><span class="sxs-lookup"><span data-stu-id="c839a-137">How to: Use a Generic Class</span></span>](how-to-use-a-generic-class.md)
- [<span data-ttu-id="c839a-138">程序</span><span class="sxs-lookup"><span data-stu-id="c839a-138">Procedures</span></span>](../procedures/index.md)
- [<span data-ttu-id="c839a-139">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="c839a-139">Procedure Parameters and Arguments</span></span>](../procedures/procedure-parameters-and-arguments.md)
- [<span data-ttu-id="c839a-140">Type List</span><span class="sxs-lookup"><span data-stu-id="c839a-140">Type List</span></span>](../../../language-reference/statements/type-list.md)
- [<span data-ttu-id="c839a-141">參數清單</span><span class="sxs-lookup"><span data-stu-id="c839a-141">Parameter List</span></span>](../../../language-reference/statements/parameter-list.md)
