---
title: HOW TO：推斷屬性名稱和型別在匿名類型宣告 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- inferring property names [Visual Basic]
- anonymous types [Visual Basic], inferring property names and types
- inferring property types [Visual Basic]
ms.assetid: 7c748b22-913f-4d9d-b747-6b7bf296a0bc
ms.openlocfilehash: aba8c37059cfc58fdffda55bcf1c485b61c3d249
ms.sourcegitcommit: 4a3c95e91289d16c38979575a245a4f76b0da147
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/05/2019
ms.locfileid: "67569490"
---
# <a name="how-to-infer-property-names-and-types-in-anonymous-type-declarations-visual-basic"></a><span data-ttu-id="5aaa5-102">作法：推斷屬性名稱和型別在匿名類型宣告 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5aaa5-102">How to: Infer Property Names and Types in Anonymous Type Declarations (Visual Basic)</span></span>
<span data-ttu-id="5aaa5-103">匿名類型未提供任何機制來直接指定屬性的資料類型。</span><span class="sxs-lookup"><span data-stu-id="5aaa5-103">Anonymous types provide no mechanism for directly specifying the data types of properties.</span></span> <span data-ttu-id="5aaa5-104">所有屬性的類型都是推斷而來。</span><span class="sxs-lookup"><span data-stu-id="5aaa5-104">Types of all properties are inferred.</span></span> <span data-ttu-id="5aaa5-105">在下列範例中，透過用來初始化 `Name` 和 `Price` 類型的值，直接推斷這些類型。</span><span class="sxs-lookup"><span data-stu-id="5aaa5-105">In the following example, the types of `Name` and `Price` are inferred directly from the values that are used to initialize them.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#1)]  
  
 <span data-ttu-id="5aaa5-106">匿名類型也可以推斷其他來源的屬性名稱和類型。</span><span class="sxs-lookup"><span data-stu-id="5aaa5-106">Anonymous types can also infer property names and types from other sources.</span></span> <span data-ttu-id="5aaa5-107">以下章節提供可進行推斷的情況清單，以及不可進行推斷的狀況範例。</span><span class="sxs-lookup"><span data-stu-id="5aaa5-107">The sections that follow provide a list of the circumstances where inference is possible, and examples of situations where it is not.</span></span>  
  
## <a name="successful-inference"></a><span data-ttu-id="5aaa5-108">成功推斷</span><span class="sxs-lookup"><span data-stu-id="5aaa5-108">Successful Inference</span></span>  
  
#### <a name="anonymous-types-can-infer-property-names-and-types-from-the-following-sources"></a><span data-ttu-id="5aaa5-109">匿名類型可以推斷下列來源的屬性名稱和類型：</span><span class="sxs-lookup"><span data-stu-id="5aaa5-109">Anonymous types can infer property names and types from the following sources:</span></span>  
  
- <span data-ttu-id="5aaa5-110">透過變數名稱。</span><span class="sxs-lookup"><span data-stu-id="5aaa5-110">From variable names.</span></span> <span data-ttu-id="5aaa5-111">匿名類型 `anonProduct` 會有兩個屬性： `productName` 和 `productPrice`。</span><span class="sxs-lookup"><span data-stu-id="5aaa5-111">Anonymous type `anonProduct` will have two properties, `productName` and `productPrice`.</span></span> <span data-ttu-id="5aaa5-112">其資料類型分別是下列原始變數： `String` 和 `Double`。</span><span class="sxs-lookup"><span data-stu-id="5aaa5-112">Their data types will be those of the original variables, `String` and `Double`, respectively.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#11)]  
  
- <span data-ttu-id="5aaa5-113">透過其他物件的屬性或欄位名稱。</span><span class="sxs-lookup"><span data-stu-id="5aaa5-113">From property or field names of other objects.</span></span> <span data-ttu-id="5aaa5-114">例如，考慮使用類型為 `car` 且包含 `CarClass` 和 `Name` 屬性的 `ID` 物件。</span><span class="sxs-lookup"><span data-stu-id="5aaa5-114">For example, consider a `car` object of a `CarClass` type that includes `Name` and `ID` properties.</span></span> <span data-ttu-id="5aaa5-115">若要利用使用 `car1`物件值初始化的 `Name` 和 `ID` 屬性來建立新的匿名類型執行個體 ( `car` )，您可以撰寫下列項目：</span><span class="sxs-lookup"><span data-stu-id="5aaa5-115">To create a new anonymous type instance, `car1`, with `Name` and `ID` properties that are initialized with the values from the `car` object, you can write the following:</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#34)]  
  
     <span data-ttu-id="5aaa5-116">先前的宣告等同於定義匿名類型 `car2`的較長程式碼行。</span><span class="sxs-lookup"><span data-stu-id="5aaa5-116">The previous declaration is equivalent to the longer line of code that defines anonymous type `car2`.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#35)]  
  
- <span data-ttu-id="5aaa5-117">透過 XML 成員名稱。</span><span class="sxs-lookup"><span data-stu-id="5aaa5-117">From XML member names.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#12)]  
  
     <span data-ttu-id="5aaa5-118">針對 `anon` 產生的屬性會有一個類型 `Book`(Of XElement) 的屬性 <xref:System.Collections.IEnumerable>。</span><span class="sxs-lookup"><span data-stu-id="5aaa5-118">The resulting type for `anon` would have one property, `Book`, of type <xref:System.Collections.IEnumerable>(Of XElement).</span></span>  
  
- <span data-ttu-id="5aaa5-119">透過沒有參數的函式 (如下列範例中的 `SomeFunction` )。</span><span class="sxs-lookup"><span data-stu-id="5aaa5-119">From a function that has no parameters, such as `SomeFunction` in the following example.</span></span>  

  ```vb
     Dim sc As New SomeClass
     Dim anon1 = New With {Key sc.SomeFunction()}
  ```
  
     <span data-ttu-id="5aaa5-120">下列程式碼中的變數 `anon2` 是具有一個屬性 (名稱為 `First`的字元) 的匿名類型。</span><span class="sxs-lookup"><span data-stu-id="5aaa5-120">The variable `anon2` in the following code is an anonymous type that has one property, a character named `First`.</span></span> <span data-ttu-id="5aaa5-121">此程式碼會顯示字母 "E" (即函式 <xref:System.Linq.Enumerable.First%2A>所傳回的字母)。</span><span class="sxs-lookup"><span data-stu-id="5aaa5-121">This code will display a letter "E," the letter that is returned by function <xref:System.Linq.Enumerable.First%2A>.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#13)]  
  
## <a name="inference-failures"></a><span data-ttu-id="5aaa5-122">推斷失敗</span><span class="sxs-lookup"><span data-stu-id="5aaa5-122">Inference Failures</span></span>  
  
#### <a name="name-inference-will-fail-in-many-circumstances-including-the-following"></a><span data-ttu-id="5aaa5-123">在許多情況下，名稱推斷都會失敗，包括下列情況：</span><span class="sxs-lookup"><span data-stu-id="5aaa5-123">Name inference will fail in many circumstances, including the following:</span></span>  
  
- <span data-ttu-id="5aaa5-124">推斷衍生自叫用方法、建構函式或需要引數的參數化屬性。</span><span class="sxs-lookup"><span data-stu-id="5aaa5-124">The inference derives from the invocation of a method, a constructor, or a parameterized property that requires arguments.</span></span> <span data-ttu-id="5aaa5-125">如果 `anon1` 有一個或多個引數，則 `someFunction` 的先前宣告會失敗。</span><span class="sxs-lookup"><span data-stu-id="5aaa5-125">The previous declaration of `anon1` fails if `someFunction` has one or more arguments.</span></span>  

    ```vb
    ' Not valid.
    ' Dim anon3 = New With {Key sc.someFunction(someArg)}
    ```
    
     <span data-ttu-id="5aaa5-126">指派給新的屬性名稱可解決問題。</span><span class="sxs-lookup"><span data-stu-id="5aaa5-126">Assignment to a new property name solves the problem.</span></span>  

    ```vb
    ' Valid.
    Dim anon4 = New With {Key .FunResult = sc.someFunction(someArg)}
    ```

- <span data-ttu-id="5aaa5-127">推斷衍生自複雜運算式。</span><span class="sxs-lookup"><span data-stu-id="5aaa5-127">The inference derives from a complex expression.</span></span>  
  
    ```vb  
    Dim aString As String = "Act "  
    ' Not valid.  
    ' Dim label = New With {Key aString & "IV"}  
    ```  
  
     <span data-ttu-id="5aaa5-128">將運算式的結果指派給屬性名稱，即可解決錯誤。</span><span class="sxs-lookup"><span data-stu-id="5aaa5-128">The error can be resolved by assigning the result of the expression to a property name.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#14)]  
  
- <span data-ttu-id="5aaa5-129">多個屬性的推斷會產生兩個或多個同名的屬性。</span><span class="sxs-lookup"><span data-stu-id="5aaa5-129">Inference for multiple properties produces two or more properties that have the same name.</span></span> <span data-ttu-id="5aaa5-130">推斷回先前範例中的宣告，無法將 `product.Name` 和 `car1.Name` 列為相同匿名類型的屬性。</span><span class="sxs-lookup"><span data-stu-id="5aaa5-130">Referring back to declarations in earlier examples, you cannot list both `product.Name` and `car1.Name` as properties of the same anonymous type.</span></span> <span data-ttu-id="5aaa5-131">原因是所有的推斷識別項都是 `Name`。</span><span class="sxs-lookup"><span data-stu-id="5aaa5-131">This is because the inferred identifier for each of these would be `Name`.</span></span>  

     ```vb
     ' Not valid.
     ' Dim anon5 = New With {Key product.Name, Key car1.Name}
     ```
     
     <span data-ttu-id="5aaa5-132">將值指派給不同的屬性名稱，即可解決問題。</span><span class="sxs-lookup"><span data-stu-id="5aaa5-132">The problem can be solved by assigning the values to distinct property names.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#36)]  
  
     <span data-ttu-id="5aaa5-133">請注意，大小寫的變更 (大寫與小寫字母之間的變更) 並不會讓這兩個名稱不同。</span><span class="sxs-lookup"><span data-stu-id="5aaa5-133">Note that changes in case (changes between uppercase and lowercase letters) do not make two names distinct.</span></span>  

     ```vb
     Dim price = 0
     ' Not valid, because Price and price are the same name.
     ' Dim anon7 = New With {Key product.Price, Key price}
     ```
  
- <span data-ttu-id="5aaa5-134">一個屬性的初始類型和值取決於尚未建立的另一個屬性。</span><span class="sxs-lookup"><span data-stu-id="5aaa5-134">The initial type and value of one property depends on another property that is not yet established.</span></span> <span data-ttu-id="5aaa5-135">例如，除非已初始化 `.IDName = .LastName` ，否則 `.LastName` 在匿名類型宣告中無效。</span><span class="sxs-lookup"><span data-stu-id="5aaa5-135">For example, `.IDName = .LastName` is not valid in an anonymous type declaration unless `.LastName` is already initialized.</span></span>  

     ```vb
     ' Not valid.
     ' Dim anon8 = New With {Key .IDName = .LastName, Key .LastName = "Jones"}
     ```
     
     <span data-ttu-id="5aaa5-136">在此範例中，您可以反轉屬性的宣告順序來修正問題。</span><span class="sxs-lookup"><span data-stu-id="5aaa5-136">In this example, you can fix the problem by reversing the order in which the properties are declared.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#15)]  
  
- <span data-ttu-id="5aaa5-137">匿名類型的屬性名稱與 <xref:System.Object>成員的名稱相同。</span><span class="sxs-lookup"><span data-stu-id="5aaa5-137">A property name of the anonymous type is the same as the name of a member of <xref:System.Object>.</span></span> <span data-ttu-id="5aaa5-138">例如，因為 `Equals` 是 <xref:System.Object>的方法，所以下列宣告會失敗。</span><span class="sxs-lookup"><span data-stu-id="5aaa5-138">For example, the following declaration fails because `Equals` is a method of <xref:System.Object>.</span></span>  
  
     ```vb
     ' Not valid.
     ' Dim relationsLabels1 = New With {Key .Equals = "equals", Key .Greater = _
     '                       "greater than", Key .Less = "less than"}
     ```
     
     <span data-ttu-id="5aaa5-139">變更屬性名稱，即可修正問題：</span><span class="sxs-lookup"><span data-stu-id="5aaa5-139">You can fix the problem by changing the property name:</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#16)]  
  
## <a name="see-also"></a><span data-ttu-id="5aaa5-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5aaa5-140">See also</span></span>

- [<span data-ttu-id="5aaa5-141">物件初始設定式：具名和匿名類型</span><span class="sxs-lookup"><span data-stu-id="5aaa5-141">Object Initializers: Named and Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="5aaa5-142">區域類型推斷</span><span class="sxs-lookup"><span data-stu-id="5aaa5-142">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="5aaa5-143">匿名類型</span><span class="sxs-lookup"><span data-stu-id="5aaa5-143">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="5aaa5-144">Key</span><span class="sxs-lookup"><span data-stu-id="5aaa5-144">Key</span></span>](../../../../visual-basic/language-reference/modifiers/key.md)
