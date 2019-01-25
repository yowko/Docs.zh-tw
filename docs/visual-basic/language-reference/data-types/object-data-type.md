---
title: Object 資料型別 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Object
- vb.Variant
helpviewer_keywords:
- object variables [Visual Basic], Object type
- data types [Visual Basic], assigning
- Object data type
- Object data type [Visual Basic], reference
ms.assetid: 61ea4a7c-3b3d-48d4-adc4-eacfa91779b2
ms.openlocfilehash: 5a37b571e0600927e0e50fdb1a63bcf8ef194d72
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54617534"
---
# <a name="object-data-type"></a><span data-ttu-id="7230c-102">Object Data Type</span><span class="sxs-lookup"><span data-stu-id="7230c-102">Object Data Type</span></span>
<span data-ttu-id="7230c-103">包含參考物件的位址。</span><span class="sxs-lookup"><span data-stu-id="7230c-103">Holds addresses that refer to objects.</span></span> <span data-ttu-id="7230c-104">您可以將任何參考型別 （字串、 陣列、 類別或介面） 指派給`Object`變數。</span><span class="sxs-lookup"><span data-stu-id="7230c-104">You can assign any reference type (string, array, class, or interface) to an `Object` variable.</span></span> <span data-ttu-id="7230c-105">`Object`變數也可以參考資料的任何實值類型 (數字`Boolean`， `Char`， `Date`、 結構或列舉)。</span><span class="sxs-lookup"><span data-stu-id="7230c-105">An `Object` variable can also refer to data of any value type (numeric, `Boolean`, `Char`, `Date`, structure, or enumeration).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7230c-106">備註</span><span class="sxs-lookup"><span data-stu-id="7230c-106">Remarks</span></span>  
 <span data-ttu-id="7230c-107">`Object`資料型別可以指向任何資料類型，包括您的應用程式可辨識的任何物件執行個體的資料。</span><span class="sxs-lookup"><span data-stu-id="7230c-107">The `Object` data type can point to data of any data type, including any object instance your application recognizes.</span></span> <span data-ttu-id="7230c-108">使用`Object`當您在編譯時期不知道何種資料類型的變數可能指向。</span><span class="sxs-lookup"><span data-stu-id="7230c-108">Use `Object` when you do not know at compile time what data type the variable might point to.</span></span>  
  
 <span data-ttu-id="7230c-109">預設值`Object`是`Nothing`（null 參考）。</span><span class="sxs-lookup"><span data-stu-id="7230c-109">The default value of `Object` is `Nothing` (a null reference).</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="7230c-110">資料類型</span><span class="sxs-lookup"><span data-stu-id="7230c-110">Data Types</span></span>  
 <span data-ttu-id="7230c-111">您可以指派變數、 常數或運算式的任何資料型別`Object`變數。</span><span class="sxs-lookup"><span data-stu-id="7230c-111">You can assign a variable, constant, or expression of any data type to an `Object` variable.</span></span> <span data-ttu-id="7230c-112">若要判斷資料型別`Object`目前參考變數，您可以使用<xref:System.Type.GetTypeCode%2A>方法<xref:System.Type?displayProperty=nameWithType>類別。</span><span class="sxs-lookup"><span data-stu-id="7230c-112">To determine the data type an `Object` variable currently refers to, you can use the <xref:System.Type.GetTypeCode%2A> method of the <xref:System.Type?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="7230c-113">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="7230c-113">The following example illustrates this.</span></span>  
  
```  
Dim myObject As Object  
' Suppose myObject has now had something assigned to it.  
Dim datTyp As Integer  
datTyp = Type.GetTypeCode(myObject.GetType())  
```  
  
 <span data-ttu-id="7230c-114">`Object`資料型別是參考類型。</span><span class="sxs-lookup"><span data-stu-id="7230c-114">The `Object` data type is a reference type.</span></span> <span data-ttu-id="7230c-115">不過，Visual Basic 會將`Object`變數設定為當它是指資料的實值類型的實值型別。</span><span class="sxs-lookup"><span data-stu-id="7230c-115">However, Visual Basic treats an `Object` variable as a value type when it refers to data of a value type.</span></span>  
  
## <a name="storage"></a><span data-ttu-id="7230c-116">存放裝置</span><span class="sxs-lookup"><span data-stu-id="7230c-116">Storage</span></span>  
 <span data-ttu-id="7230c-117">它是指，任何資料型別`Object`變數本身，但而不是值的指標不包含資料值。</span><span class="sxs-lookup"><span data-stu-id="7230c-117">Whatever data type it refers to, an `Object` variable does not contain the data value itself, but rather a pointer to the value.</span></span> <span data-ttu-id="7230c-118">它會在電腦記憶體中，一律使用四個位元組，但這不包括表示變數值的資料的儲存體。</span><span class="sxs-lookup"><span data-stu-id="7230c-118">It always uses four bytes in computer memory, but this does not include the storage for the data representing the value of the variable.</span></span> <span data-ttu-id="7230c-119">因為找到的資料，使用滑鼠指標的程式碼`Object`含有實值型別變數會稍微慢一點，來存取比明確具類型的變數。</span><span class="sxs-lookup"><span data-stu-id="7230c-119">Because of the code that uses the pointer to locate the data, `Object` variables holding value types are slightly slower to access than explicitly typed variables.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="7230c-120">程式設計提示</span><span class="sxs-lookup"><span data-stu-id="7230c-120">Programming Tips</span></span>  
  
-   <span data-ttu-id="7230c-121">**Interop 考量。**</span><span class="sxs-lookup"><span data-stu-id="7230c-121">**Interop Considerations.**</span></span> <span data-ttu-id="7230c-122">如果您要使用的元件不是撰寫.NET framework，例如 Automation 或 COM 物件，請記住，在其他環境中的指標類型不相容於 Visual Basic`Object`型別。</span><span class="sxs-lookup"><span data-stu-id="7230c-122">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that pointer types in other environments are not compatible with the Visual Basic `Object` type.</span></span>  
  
-   <span data-ttu-id="7230c-123">**效能。**</span><span class="sxs-lookup"><span data-stu-id="7230c-123">**Performance.**</span></span> <span data-ttu-id="7230c-124">您使用宣告的變數`Object`型別是有足夠的彈性，以包含任何物件的參考。</span><span class="sxs-lookup"><span data-stu-id="7230c-124">A variable you declare with the `Object` type is flexible enough to contain a reference to any object.</span></span> <span data-ttu-id="7230c-125">不過，當您叫用方法或屬性，這類的變數上，您一定會產生*晚期繫結*（在執行階段）。</span><span class="sxs-lookup"><span data-stu-id="7230c-125">However, when you invoke a method or property on such a variable, you always incur *late binding* (at run time).</span></span> <span data-ttu-id="7230c-126">若要強制*早期繫結*（在編譯時期） 和較佳的效能、 宣告的變數，以特定的類別名稱，或將它轉換成特定資料類型。</span><span class="sxs-lookup"><span data-stu-id="7230c-126">To force *early binding* (at compile time) and better performance, declare the variable with a specific class name, or cast it to the specific data type.</span></span>  
  
     <span data-ttu-id="7230c-127">當您宣告物件變數時，嘗試使用特定類別類型，例如<xref:System.OperatingSystem>，而不是 一般化`Object`型別。</span><span class="sxs-lookup"><span data-stu-id="7230c-127">When you declare an object variable, try to use a specific class type, for example <xref:System.OperatingSystem>, instead of the generalized `Object` type.</span></span> <span data-ttu-id="7230c-128">您也應該使用最特定的類別使用，例如<xref:System.Windows.Forms.TextBox>而不是<xref:System.Windows.Forms.Control>，如此一來，您可以存取其屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="7230c-128">You should also use the most specific class available, such as <xref:System.Windows.Forms.TextBox> instead of <xref:System.Windows.Forms.Control>, so that you can access its properties and methods.</span></span> <span data-ttu-id="7230c-129">您通常可以使用**類別**列入**物件瀏覽器**來尋找可用的類別名稱。</span><span class="sxs-lookup"><span data-stu-id="7230c-129">You can usually use the **Classes** list in the **Object Browser** to find available class names.</span></span>  
  
-   <span data-ttu-id="7230c-130">**擴展。**</span><span class="sxs-lookup"><span data-stu-id="7230c-130">**Widening.**</span></span> <span data-ttu-id="7230c-131">所有的資料類型和所有參考型別會擴展為`Object`資料型別。</span><span class="sxs-lookup"><span data-stu-id="7230c-131">All data types and all reference types widen to the `Object` data type.</span></span> <span data-ttu-id="7230c-132">這表示您可以將任何類型轉換`Object`而不會發生<xref:System.OverflowException?displayProperty=nameWithType>時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="7230c-132">This means you can convert any type to `Object` without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
     <span data-ttu-id="7230c-133">不過，如果您實值型別之間進行轉換並`Object`，Visual Basic 執行呼叫的作業*boxing*並*unboxing*，如此一來讓執行速度變慢。</span><span class="sxs-lookup"><span data-stu-id="7230c-133">However, if you convert between value types and `Object`, Visual Basic performs operations called *boxing* and *unboxing*, which make execution slower.</span></span>  
  
-   <span data-ttu-id="7230c-134">**類型字元。**</span><span class="sxs-lookup"><span data-stu-id="7230c-134">**Type Characters.**</span></span> <span data-ttu-id="7230c-135">`Object` 沒有任何常值類型字元或識別項類型字元。</span><span class="sxs-lookup"><span data-stu-id="7230c-135">`Object` has no literal type character or identifier type character.</span></span>  
  
-   <span data-ttu-id="7230c-136">**Framework 型別。**</span><span class="sxs-lookup"><span data-stu-id="7230c-136">**Framework Type.**</span></span> <span data-ttu-id="7230c-137">.NET Framework 中對應的型別是<xref:System.Object?displayProperty=nameWithType>類別。</span><span class="sxs-lookup"><span data-stu-id="7230c-137">The corresponding type in the .NET Framework is the <xref:System.Object?displayProperty=nameWithType> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7230c-138">範例</span><span class="sxs-lookup"><span data-stu-id="7230c-138">Example</span></span>  
 <span data-ttu-id="7230c-139">下列範例說明`Object`變數指向的物件執行個體。</span><span class="sxs-lookup"><span data-stu-id="7230c-139">The following example illustrates an `Object` variable pointing to an object instance.</span></span>  
  
```  
Dim objDb As Object  
Dim myCollection As New Collection()  
' Suppose myCollection has now been populated.  
objDb = myCollection.Item(1)  
```  
  
## <a name="see-also"></a><span data-ttu-id="7230c-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7230c-140">See also</span></span>
- <xref:System.Object>
- [<span data-ttu-id="7230c-141">資料類型</span><span class="sxs-lookup"><span data-stu-id="7230c-141">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="7230c-142">類型轉換函式</span><span class="sxs-lookup"><span data-stu-id="7230c-142">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="7230c-143">轉換摘要</span><span class="sxs-lookup"><span data-stu-id="7230c-143">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="7230c-144">有效率地使用資料類型</span><span class="sxs-lookup"><span data-stu-id="7230c-144">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="7230c-145">如何：判斷兩個物件是否關聯</span><span class="sxs-lookup"><span data-stu-id="7230c-145">How to: Determine Whether Two Objects Are Related</span></span>](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [<span data-ttu-id="7230c-146">如何：判斷兩個物件是否相同</span><span class="sxs-lookup"><span data-stu-id="7230c-146">How to: Determine Whether Two Objects Are Identical</span></span>](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
