---
title: Generic Procedures in Visual Basic
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
ms.openlocfilehash: 9a88a979a6b46f897e5f04f4481d4a23e245b165
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2018
ms.locfileid: "45618814"
---
# <a name="generic-procedures-in-visual-basic"></a><span data-ttu-id="ccb81-102">Generic Procedures in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ccb81-102">Generic Procedures in Visual Basic</span></span>
<span data-ttu-id="ccb81-103">A*泛型程序*，也稱為*泛型方法*，是以至少一個型別參數所定義的程序。</span><span class="sxs-lookup"><span data-stu-id="ccb81-103">A *generic procedure*, also called a *generic method*, is a procedure defined with at least one type parameter.</span></span> <span data-ttu-id="ccb81-104">這可讓呼叫的程式碼，來調整使其符合需求的資料類型每次呼叫此程序。</span><span class="sxs-lookup"><span data-stu-id="ccb81-104">This allows the calling code to tailor the data types to its requirements each time it calls the procedure.</span></span>  
  
 <span data-ttu-id="ccb81-105">找不到一般只要透過泛型類別或泛型結構內所定義的程序。</span><span class="sxs-lookup"><span data-stu-id="ccb81-105">A procedure is not generic simply by virtue of being defined inside a generic class or a generic structure.</span></span> <span data-ttu-id="ccb81-106">若要成為泛型，程序必須採取至少一個型別參數，除了任何可能需要的一般參數。</span><span class="sxs-lookup"><span data-stu-id="ccb81-106">To be generic, the procedure must take at least one type parameter, in addition to any normal parameters it might take.</span></span> <span data-ttu-id="ccb81-107">泛型類別或結構可以包含非泛型程序和非泛型類別、 結構或模組可以包含一般的程序。</span><span class="sxs-lookup"><span data-stu-id="ccb81-107">A generic class or structure can contain nongeneric procedures, and a nongeneric class, structure, or module can contain generic procedures.</span></span>  
  
 <span data-ttu-id="ccb81-108">泛型程序可以在其一般的參數清單中，其傳回類型，如果有的話，和其程序程式碼中使用其型別參數。</span><span class="sxs-lookup"><span data-stu-id="ccb81-108">A generic procedure can use its type parameters in its normal parameter list, in its return type if it has one, and in its procedure code.</span></span>  
  
## <a name="type-inference"></a><span data-ttu-id="ccb81-109">類型推斷</span><span class="sxs-lookup"><span data-stu-id="ccb81-109">Type Inference</span></span>  
 <span data-ttu-id="ccb81-110">您可以呼叫泛型程序，而不需要完全提供任何類型引數。</span><span class="sxs-lookup"><span data-stu-id="ccb81-110">You can call a generic procedure without supplying any type arguments at all.</span></span> <span data-ttu-id="ccb81-111">如果您呼叫它如此一來，編譯器會嘗試判斷要傳遞至程序的類型引數的適當資料類型。</span><span class="sxs-lookup"><span data-stu-id="ccb81-111">If you call it this way, the compiler attempts to determine the appropriate data types to pass to the procedure's type arguments.</span></span> <span data-ttu-id="ccb81-112">這就叫做*型別推斷*。</span><span class="sxs-lookup"><span data-stu-id="ccb81-112">This is called *type inference*.</span></span> <span data-ttu-id="ccb81-113">下列程式碼顯示的呼叫中的編譯器會推斷它應該傳遞型別`String`的型別參數`t`。</span><span class="sxs-lookup"><span data-stu-id="ccb81-113">The following code shows a call in which the compiler infers that it should pass type `String` to the type parameter `t`.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#15](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_1.vb)]  
  
 <span data-ttu-id="ccb81-114">如果編譯器無法推斷類型引數，從呼叫的內容，則會回報錯誤。</span><span class="sxs-lookup"><span data-stu-id="ccb81-114">If the compiler cannot infer the type arguments from the context of your call, it reports an error.</span></span> <span data-ttu-id="ccb81-115">這類錯誤的其中一個可能的原因是陣列的陣序不符。</span><span class="sxs-lookup"><span data-stu-id="ccb81-115">One possible cause of such an error is an array rank mismatch.</span></span> <span data-ttu-id="ccb81-116">比方說，假設您定義一般參數的型別參數的陣列。</span><span class="sxs-lookup"><span data-stu-id="ccb81-116">For example, suppose you define a normal parameter as an array of a type parameter.</span></span> <span data-ttu-id="ccb81-117">如果您呼叫泛型程序提供為不同陣序 （維度數目），陣列不相符會導致失敗的型別推斷。</span><span class="sxs-lookup"><span data-stu-id="ccb81-117">If you call the generic procedure supplying an array of a different rank (number of dimensions), the mismatch causes type inference to fail.</span></span> <span data-ttu-id="ccb81-118">下列程式碼顯示的呼叫中的二維陣列傳遞至預期的一維陣列的程序。</span><span class="sxs-lookup"><span data-stu-id="ccb81-118">The following code shows a call in which a two-dimensional array is passed to a procedure that expects a one-dimensional array.</span></span>  
  
```vb  
Public Sub demoSub(Of t)(ByVal arg() As t)
End Sub

Public Sub callDemoSub()
    Dim twoDimensions(,) As Integer
    demoSub(twoDimensions)
End Sub
```
  
 <span data-ttu-id="ccb81-119">您可以只藉由略過所有型別引數來叫用型別推斷。</span><span class="sxs-lookup"><span data-stu-id="ccb81-119">You can invoke type inference only by omitting all the type arguments.</span></span> <span data-ttu-id="ccb81-120">如果您提供一個類型引數時，您必須將它們全部提供。</span><span class="sxs-lookup"><span data-stu-id="ccb81-120">If you supply one type argument, you must supply them all.</span></span>  
  
 <span data-ttu-id="ccb81-121">僅針對泛型程序支援的類型推斷。</span><span class="sxs-lookup"><span data-stu-id="ccb81-121">Type inference is supported only for generic procedures.</span></span> <span data-ttu-id="ccb81-122">您無法叫用在泛型類別、 結構、 介面或委派的型別推斷。</span><span class="sxs-lookup"><span data-stu-id="ccb81-122">You cannot invoke type inference on generic classes, structures, interfaces, or delegates.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ccb81-123">範例</span><span class="sxs-lookup"><span data-stu-id="ccb81-123">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="ccb81-124">描述</span><span class="sxs-lookup"><span data-stu-id="ccb81-124">Description</span></span>  
 <span data-ttu-id="ccb81-125">下列範例會定義泛型`Function`尋找特定的項目陣列中的程序。</span><span class="sxs-lookup"><span data-stu-id="ccb81-125">The following example defines a generic `Function` procedure to find a particular element in an array.</span></span> <span data-ttu-id="ccb81-126">它會定義一個型別參數，並使用它來建構參數清單中的兩個參數。</span><span class="sxs-lookup"><span data-stu-id="ccb81-126">It defines one type parameter and uses it to construct the two parameters in the parameter list.</span></span>  
  
### <a name="code"></a><span data-ttu-id="ccb81-127">程式碼</span><span class="sxs-lookup"><span data-stu-id="ccb81-127">Code</span></span>  
 [!code-vb[VbVbalrDataTypes#14](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_2.vb)]  
  
### <a name="comments"></a><span data-ttu-id="ccb81-128">註解</span><span class="sxs-lookup"><span data-stu-id="ccb81-128">Comments</span></span>  
 <span data-ttu-id="ccb81-129">上述範例要求可讓您比較`searchValue`針對每個元素的`searchArray`。</span><span class="sxs-lookup"><span data-stu-id="ccb81-129">The preceding example requires the ability to compare `searchValue` against each element of `searchArray`.</span></span> <span data-ttu-id="ccb81-130">若要確保這項功能，它會限制型別參數`T`實作<xref:System.IComparable%601>介面。</span><span class="sxs-lookup"><span data-stu-id="ccb81-130">To guarantee this ability, it constrains the type parameter `T` to implement the <xref:System.IComparable%601> interface.</span></span> <span data-ttu-id="ccb81-131">程式碼會使用<xref:System.IComparable%601.CompareTo%2A>方法，而非`=`運算子，因為型別引數提供給不保證`T`支援`=`運算子。</span><span class="sxs-lookup"><span data-stu-id="ccb81-131">The code uses the <xref:System.IComparable%601.CompareTo%2A> method instead of the `=` operator, because there is no guarantee that a type argument supplied for `T` supports the `=` operator.</span></span>  
  
 <span data-ttu-id="ccb81-132">您可以測試`findElement`為下列程式碼的程序。</span><span class="sxs-lookup"><span data-stu-id="ccb81-132">You can test the `findElement` procedure with the following code.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#13](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_3.vb)]  
  
 <span data-ttu-id="ccb81-133">上述呼叫`MsgBox`分別顯示"0"、"1"和"-1"。</span><span class="sxs-lookup"><span data-stu-id="ccb81-133">The preceding calls to `MsgBox` display "0", "1", and "-1" respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccb81-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ccb81-134">See Also</span></span>  
 [<span data-ttu-id="ccb81-135">Visual Basic 中的泛型型別</span><span class="sxs-lookup"><span data-stu-id="ccb81-135">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="ccb81-136">如何：定義可以在不同資料類型上提供完全相同功能的類別</span><span class="sxs-lookup"><span data-stu-id="ccb81-136">How to: Define a Class That Can Provide Identical Functionality on Different Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)  
 [<span data-ttu-id="ccb81-137">如何：使用泛型類別</span><span class="sxs-lookup"><span data-stu-id="ccb81-137">How to: Use a Generic Class</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [<span data-ttu-id="ccb81-138">程序</span><span class="sxs-lookup"><span data-stu-id="ccb81-138">Procedures</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="ccb81-139">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="ccb81-139">Procedure Parameters and Arguments</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="ccb81-140">類型清單</span><span class="sxs-lookup"><span data-stu-id="ccb81-140">Type List</span></span>](../../../../visual-basic/language-reference/statements/type-list.md)  
 [<span data-ttu-id="ccb81-141">參數清單</span><span class="sxs-lookup"><span data-stu-id="ccb81-141">Parameter List</span></span>](../../../../visual-basic/language-reference/statements/parameter-list.md)
