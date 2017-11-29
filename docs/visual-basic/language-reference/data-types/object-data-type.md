---
title: Object Data Type
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Object
- vb.Variant
helpviewer_keywords:
- object variables [Visual Basic], Object type
- data types [Visual Basic], assigning
- Object data type
- Object data type [Visual Basic], reference
ms.assetid: 61ea4a7c-3b3d-48d4-adc4-eacfa91779b2
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 847f2b50296ad1a1ba6f0009d1d6afced27f9abe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="object-data-type"></a><span data-ttu-id="f830a-102">Object Data Type</span><span class="sxs-lookup"><span data-stu-id="f830a-102">Object Data Type</span></span>
<span data-ttu-id="f830a-103">參考物件的保留位址。</span><span class="sxs-lookup"><span data-stu-id="f830a-103">Holds addresses that refer to objects.</span></span> <span data-ttu-id="f830a-104">您可以將任何參考類型 （字串、 陣列、 類別或介面） 指派給`Object`變數。</span><span class="sxs-lookup"><span data-stu-id="f830a-104">You can assign any reference type (string, array, class, or interface) to an `Object` variable.</span></span> <span data-ttu-id="f830a-105">`Object`變數也可以指任何實值類型的資料 (數值， `Boolean`， `Char`， `Date`、 結構或列舉型別)。</span><span class="sxs-lookup"><span data-stu-id="f830a-105">An `Object` variable can also refer to data of any value type (numeric, `Boolean`, `Char`, `Date`, structure, or enumeration).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f830a-106">備註</span><span class="sxs-lookup"><span data-stu-id="f830a-106">Remarks</span></span>  
 <span data-ttu-id="f830a-107">`Object`資料型別可以指向任何資料類型，包括您的應用程式可辨識的任何物件執行個體的資料。</span><span class="sxs-lookup"><span data-stu-id="f830a-107">The `Object` data type can point to data of any data type, including any object instance your application recognizes.</span></span> <span data-ttu-id="f830a-108">使用`Object`時您不知道在編譯時期何種資料類型的變數可能指向。</span><span class="sxs-lookup"><span data-stu-id="f830a-108">Use `Object` when you do not know at compile time what data type the variable might point to.</span></span>  
  
 <span data-ttu-id="f830a-109">預設值`Object`是`Nothing`（null 參考）。</span><span class="sxs-lookup"><span data-stu-id="f830a-109">The default value of `Object` is `Nothing` (a null reference).</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="f830a-110">資料類型</span><span class="sxs-lookup"><span data-stu-id="f830a-110">Data Types</span></span>  
 <span data-ttu-id="f830a-111">您可以指派變數、 常數或運算式的任何資料型別`Object`變數。</span><span class="sxs-lookup"><span data-stu-id="f830a-111">You can assign a variable, constant, or expression of any data type to an `Object` variable.</span></span> <span data-ttu-id="f830a-112">若要判斷資料型別`Object`目前參考變數，您可以使用<xref:System.Type.GetTypeCode%2A>方法<xref:System.Type?displayProperty=nameWithType>類別。</span><span class="sxs-lookup"><span data-stu-id="f830a-112">To determine the data type an `Object` variable currently refers to, you can use the <xref:System.Type.GetTypeCode%2A> method of the <xref:System.Type?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="f830a-113">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="f830a-113">The following example illustrates this.</span></span>  
  
```  
Dim myObject As Object  
' Suppose myObject has now had something assigned to it.  
Dim datTyp As Integer  
datTyp = Type.GetTypeCode(myObject.GetType())  
```  
  
 <span data-ttu-id="f830a-114">`Object`資料類型是參考類型。</span><span class="sxs-lookup"><span data-stu-id="f830a-114">The `Object` data type is a reference type.</span></span> <span data-ttu-id="f830a-115">不過，Visual Basic 會將`Object`變數作為時參考的是實值類型的實值類型。</span><span class="sxs-lookup"><span data-stu-id="f830a-115">However, Visual Basic treats an `Object` variable as a value type when it refers to data of a value type.</span></span>  
  
## <a name="storage"></a><span data-ttu-id="f830a-116">儲存區</span><span class="sxs-lookup"><span data-stu-id="f830a-116">Storage</span></span>  
 <span data-ttu-id="f830a-117">任何資料類型，則是指，`Object`本身，但而不是值的指標變數不包含資料值。</span><span class="sxs-lookup"><span data-stu-id="f830a-117">Whatever data type it refers to, an `Object` variable does not contain the data value itself, but rather a pointer to the value.</span></span> <span data-ttu-id="f830a-118">在電腦記憶體中，永遠使用四個位元組，但這不包括代表變數的值資料的儲存體。</span><span class="sxs-lookup"><span data-stu-id="f830a-118">It always uses four bytes in computer memory, but this does not include the storage for the data representing the value of the variable.</span></span> <span data-ttu-id="f830a-119">由於使用找到的資料指標的程式碼`Object`持有實值類型的變數會稍微慢一點比明確存取具類型的變數。</span><span class="sxs-lookup"><span data-stu-id="f830a-119">Because of the code that uses the pointer to locate the data, `Object` variables holding value types are slightly slower to access than explicitly typed variables.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="f830a-120">程式設計提示</span><span class="sxs-lookup"><span data-stu-id="f830a-120">Programming Tips</span></span>  
  
-   <span data-ttu-id="f830a-121">**Interop 考量。**</span><span class="sxs-lookup"><span data-stu-id="f830a-121">**Interop Considerations.**</span></span> <span data-ttu-id="f830a-122">如果您要使用的元件不是撰寫.NET framework，例如 Automation 或 COM 物件，請記住在其他環境中的指標類型不相容，使用 Visual Basic`Object`型別。</span><span class="sxs-lookup"><span data-stu-id="f830a-122">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that pointer types in other environments are not compatible with the Visual Basic `Object` type.</span></span>  
  
-   <span data-ttu-id="f830a-123">**效能。**</span><span class="sxs-lookup"><span data-stu-id="f830a-123">**Performance.**</span></span> <span data-ttu-id="f830a-124">以宣告的變數`Object`型別是有足夠的彈性，以包含任何物件的參考。</span><span class="sxs-lookup"><span data-stu-id="f830a-124">A variable you declare with the `Object` type is flexible enough to contain a reference to any object.</span></span> <span data-ttu-id="f830a-125">不過，當您叫用方法或屬性，這類變數上的，您一定會造成*晚期繫結*（在執行階段）。</span><span class="sxs-lookup"><span data-stu-id="f830a-125">However, when you invoke a method or property on such a variable, you always incur *late binding* (at run time).</span></span> <span data-ttu-id="f830a-126">若要強制*早期繫結*（在編譯時期） 和較佳的效能、 宣告變數的特定類別名稱，或將它轉換成特定資料類型。</span><span class="sxs-lookup"><span data-stu-id="f830a-126">To force *early binding* (at compile time) and better performance, declare the variable with a specific class name, or cast it to the specific data type.</span></span>  
  
     <span data-ttu-id="f830a-127">當您宣告物件變數時，再試一次使用特定類別類型，例如<xref:System.OperatingSystem>，而非一般化`Object`型別。</span><span class="sxs-lookup"><span data-stu-id="f830a-127">When you declare an object variable, try to use a specific class type, for example <xref:System.OperatingSystem>, instead of the generalized `Object` type.</span></span> <span data-ttu-id="f830a-128">您也應該使用最適合的類別使用，例如<xref:System.Windows.Forms.TextBox>而不是<xref:System.Windows.Forms.Control>，如此一來，您可以存取其屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="f830a-128">You should also use the most specific class available, such as <xref:System.Windows.Forms.TextBox> instead of <xref:System.Windows.Forms.Control>, so that you can access its properties and methods.</span></span> <span data-ttu-id="f830a-129">您通常可以使用**類別**清單中**物件瀏覽器**來尋找可用的類別名稱。</span><span class="sxs-lookup"><span data-stu-id="f830a-129">You can usually use the **Classes** list in the **Object Browser** to find available class names.</span></span>  
  
-   <span data-ttu-id="f830a-130">**擴展。**</span><span class="sxs-lookup"><span data-stu-id="f830a-130">**Widening.**</span></span> <span data-ttu-id="f830a-131">所有的資料型別和所有參考型別擴展為`Object`資料型別。</span><span class="sxs-lookup"><span data-stu-id="f830a-131">All data types and all reference types widen to the `Object` data type.</span></span> <span data-ttu-id="f830a-132">這表示您可以將任何型別轉換`Object`而不會發生<xref:System.OverflowException?displayProperty=nameWithType>錯誤。</span><span class="sxs-lookup"><span data-stu-id="f830a-132">This means you can convert any type to `Object` without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
     <span data-ttu-id="f830a-133">不過，如果您實值類型之間進行轉換和`Object`，Visual Basic 會在執行作業呼叫*boxing*和*unboxing*，剩下的執行速度變慢。</span><span class="sxs-lookup"><span data-stu-id="f830a-133">However, if you convert between value types and `Object`, Visual Basic performs operations called *boxing* and *unboxing*, which make execution slower.</span></span>  
  
-   <span data-ttu-id="f830a-134">**類型字元。**</span><span class="sxs-lookup"><span data-stu-id="f830a-134">**Type Characters.**</span></span> <span data-ttu-id="f830a-135">`Object`沒有任何常值類型字元或識別項類型字元。</span><span class="sxs-lookup"><span data-stu-id="f830a-135">`Object` has no literal type character or identifier type character.</span></span>  
  
-   <span data-ttu-id="f830a-136">**架構類型。**</span><span class="sxs-lookup"><span data-stu-id="f830a-136">**Framework Type.**</span></span> <span data-ttu-id="f830a-137">.NET Framework 中對應的類型是<xref:System.Object?displayProperty=nameWithType>類別。</span><span class="sxs-lookup"><span data-stu-id="f830a-137">The corresponding type in the .NET Framework is the <xref:System.Object?displayProperty=nameWithType> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f830a-138">範例</span><span class="sxs-lookup"><span data-stu-id="f830a-138">Example</span></span>  
 <span data-ttu-id="f830a-139">下列範例說明`Object`變數指向的物件執行個體。</span><span class="sxs-lookup"><span data-stu-id="f830a-139">The following example illustrates an `Object` variable pointing to an object instance.</span></span>  
  
```  
Dim objDb As Object  
Dim myCollection As New Collection()  
' Suppose myCollection has now been populated.  
objDb = myCollection.Item(1)  
```  
  
## <a name="see-also"></a><span data-ttu-id="f830a-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f830a-140">See Also</span></span>  
 <xref:System.Object>  
 [<span data-ttu-id="f830a-141">資料類型</span><span class="sxs-lookup"><span data-stu-id="f830a-141">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="f830a-142">類型轉換函式</span><span class="sxs-lookup"><span data-stu-id="f830a-142">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="f830a-143">轉換摘要</span><span class="sxs-lookup"><span data-stu-id="f830a-143">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="f830a-144">有效率地使用資料類型</span><span class="sxs-lookup"><span data-stu-id="f830a-144">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)  
 [<span data-ttu-id="f830a-145">如何：判斷兩個物件是否關聯</span><span class="sxs-lookup"><span data-stu-id="f830a-145">How to: Determine Whether Two Objects Are Related</span></span>](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)  
 [<span data-ttu-id="f830a-146">如何：判斷兩個物件是否相同</span><span class="sxs-lookup"><span data-stu-id="f830a-146">How to: Determine Whether Two Objects Are Identical</span></span>](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
