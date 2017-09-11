---
title: "物件變數值 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- object variables, values
- values, of object variables
- data types [Visual Basic], object variable
- variables [Visual Basic], object
ms.assetid: 31555704-58a3-49f1-9a0a-6421f605664f
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 5f42706a79212ae523b08ee336fdcacb3f761af6
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="object-variable-values-visual-basic"></a><span data-ttu-id="22fe8-102">物件變數值 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="22fe8-102">Object Variable Values (Visual Basic)</span></span>
<span data-ttu-id="22fe8-103">變數的[Object 資料型別](../../../../visual-basic/language-reference/data-types/object-data-type.md)可指向任何類型的資料。</span><span class="sxs-lookup"><span data-stu-id="22fe8-103">A variable of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) can refer to data of any type.</span></span> <span data-ttu-id="22fe8-104">您將存放的值`Object`變數保存在其他地方在記憶體中，同時在本身的變數存放資料的指標。</span><span class="sxs-lookup"><span data-stu-id="22fe8-104">The value you store in an `Object` variable is kept elsewhere in memory, while the variable itself holds a pointer to the data.</span></span>  
  
## <a name="object-classifier-functions"></a><span data-ttu-id="22fe8-105">物件分類函數</span><span class="sxs-lookup"><span data-stu-id="22fe8-105">Object Classifier Functions</span></span>  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="22fe8-106">提供函式會傳回什麼資訊`Object`變數參考到下, 表所示。</span><span class="sxs-lookup"><span data-stu-id="22fe8-106"> supplies functions that return information about what an `Object` variable refers to, as shown in the following table.</span></span>  
  
|<span data-ttu-id="22fe8-107">函式</span><span class="sxs-lookup"><span data-stu-id="22fe8-107">Function</span></span>|<span data-ttu-id="22fe8-108">如果物件變數參考，則傳回 True</span><span class="sxs-lookup"><span data-stu-id="22fe8-108">Returns True if the Object variable refers to</span></span>|  
|--------------|---------------------------------------------------|  
|<span data-ttu-id="22fe8-109"><xref:Microsoft.VisualBasic.Information.IsArray%2A></xref:Microsoft.VisualBasic.Information.IsArray%2A></span><span class="sxs-lookup"><span data-stu-id="22fe8-109"><xref:Microsoft.VisualBasic.Information.IsArray%2A></span></span>|<span data-ttu-id="22fe8-110">值，而不是單一值的陣列</span><span class="sxs-lookup"><span data-stu-id="22fe8-110">An array of values, rather than a single value</span></span>|  
|<span data-ttu-id="22fe8-111"><xref:Microsoft.VisualBasic.Information.IsDate%2A></xref:Microsoft.VisualBasic.Information.IsDate%2A></span><span class="sxs-lookup"><span data-stu-id="22fe8-111"><xref:Microsoft.VisualBasic.Information.IsDate%2A></span></span>|<span data-ttu-id="22fe8-112">A[日期資料型別](../../../../visual-basic/language-reference/data-types/date-data-type.md)值或可以解譯為日期和時間值的字串</span><span class="sxs-lookup"><span data-stu-id="22fe8-112">A [Date Data Type](../../../../visual-basic/language-reference/data-types/date-data-type.md) value, or a string that can be interpreted as a date and time value</span></span>|  
|<span data-ttu-id="22fe8-113"><xref:Microsoft.VisualBasic.Information.IsDBNull%2A></xref:Microsoft.VisualBasic.Information.IsDBNull%2A></span><span class="sxs-lookup"><span data-stu-id="22fe8-113"><xref:Microsoft.VisualBasic.Information.IsDBNull%2A></span></span>|<span data-ttu-id="22fe8-114">物件的型別<xref:System.DBNull>，用來表示資料遺失或不存在</xref:System.DBNull></span><span class="sxs-lookup"><span data-stu-id="22fe8-114">An object of type <xref:System.DBNull>, which represents missing or nonexistent data</span></span>|  
|<span data-ttu-id="22fe8-115"><xref:Microsoft.VisualBasic.Information.IsError%2A></xref:Microsoft.VisualBasic.Information.IsError%2A></span><span class="sxs-lookup"><span data-stu-id="22fe8-115"><xref:Microsoft.VisualBasic.Information.IsError%2A></span></span>|<span data-ttu-id="22fe8-116">例外狀況物件，它是衍生自<xref:System.Exception></xref:System.Exception></span><span class="sxs-lookup"><span data-stu-id="22fe8-116">An exception object, which derives from <xref:System.Exception></span></span>|  
|<span data-ttu-id="22fe8-117"><xref:Microsoft.VisualBasic.Information.IsNothing%2A></xref:Microsoft.VisualBasic.Information.IsNothing%2A></span><span class="sxs-lookup"><span data-stu-id="22fe8-117"><xref:Microsoft.VisualBasic.Information.IsNothing%2A></span></span>|<span data-ttu-id="22fe8-118">[Nothing](../../../../visual-basic/language-reference/nothing.md)，也就是沒有物件目前指派給變數</span><span class="sxs-lookup"><span data-stu-id="22fe8-118">[Nothing](../../../../visual-basic/language-reference/nothing.md), that is, no object is currently assigned to the variable</span></span>|  
|<span data-ttu-id="22fe8-119"><xref:Microsoft.VisualBasic.Information.IsNumeric%2A></xref:Microsoft.VisualBasic.Information.IsNumeric%2A></span><span class="sxs-lookup"><span data-stu-id="22fe8-119"><xref:Microsoft.VisualBasic.Information.IsNumeric%2A></span></span>|<span data-ttu-id="22fe8-120">數字或可以解譯為數字的字串</span><span class="sxs-lookup"><span data-stu-id="22fe8-120">A number, or a string that can be interpreted as a number</span></span>|  
|<span data-ttu-id="22fe8-121"><xref:Microsoft.VisualBasic.Information.IsReference%2A></xref:Microsoft.VisualBasic.Information.IsReference%2A></span><span class="sxs-lookup"><span data-stu-id="22fe8-121"><xref:Microsoft.VisualBasic.Information.IsReference%2A></span></span>|<span data-ttu-id="22fe8-122">參考型別 （例如字串、 陣列、 委派或類別類型）</span><span class="sxs-lookup"><span data-stu-id="22fe8-122">A reference type (such as a string, array, delegate, or class type)</span></span>|  
  
 <span data-ttu-id="22fe8-123">您可以使用這些函式，以避免送出至操作或程序無效的值。</span><span class="sxs-lookup"><span data-stu-id="22fe8-123">You can use these functions to avoid submitting an invalid value to an operation or a procedure.</span></span>  
  
## <a name="typeof-operator"></a><span data-ttu-id="22fe8-124">TypeOf 運算子</span><span class="sxs-lookup"><span data-stu-id="22fe8-124">TypeOf Operator</span></span>  
 <span data-ttu-id="22fe8-125">您也可以使用[TypeOf 運算子](../../../../visual-basic/language-reference/operators/typeof-operator.md)來決定物件變數是否目前參考特定資料型別。</span><span class="sxs-lookup"><span data-stu-id="22fe8-125">You can also use the [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md) to determine whether an object variable currently refers to a specific data type.</span></span> <span data-ttu-id="22fe8-126">The `TypeOf`...`Is`運算式評估為`True`如果運算元的執行階段型別衍生自或實作指定的型別。</span><span class="sxs-lookup"><span data-stu-id="22fe8-126">The `TypeOf`...`Is` expression evaluates to `True` if the run-time type of the operand is derived from or implements the specified type.</span></span>  
  
 <span data-ttu-id="22fe8-127">下列範例會使用`TypeOf`上物件變數值和參考型別參考。</span><span class="sxs-lookup"><span data-stu-id="22fe8-127">The following example uses `TypeOf` on object variables referring to value and reference types.</span></span>  
  
```  
' The following statement puts a value type (Integer) in an Object variable.  
Dim num As Object = 10  
' The following statement puts a reference type (Form) in an Object variable.  
Dim frm As Object = New Form()  
If TypeOf num Is Long Then Debug.WriteLine("num is Long")  
If TypeOf num Is Integer Then Debug.WriteLine("num is Integer")  
If TypeOf num Is Short Then Debug.WriteLine("num is Short")  
If TypeOf num Is Object Then Debug.WriteLine("num is Object")  
If TypeOf frm Is Form Then Debug.WriteLine("frm is Form")  
If TypeOf frm Is Label Then Debug.WriteLine("frm is Label")  
If TypeOf frm Is Object Then Debug.WriteLine("frm is Object")  
```  
  
 <span data-ttu-id="22fe8-128">上述範例會將下列幾行以**偵錯**視窗︰</span><span class="sxs-lookup"><span data-stu-id="22fe8-128">The preceding example writes the following lines to the **Debug** window:</span></span>  
  
 `num is Integer`  
  
 `num is Object`  
  
 `frm is Form`  
  
 `frm is Object`  
  
 <span data-ttu-id="22fe8-129">物件變數`num`指的是資料型別的`Integer`，和`frm` <xref:System.Windows.Forms.Form>.</xref:System.Windows.Forms.Form>類別的物件參考</span><span class="sxs-lookup"><span data-stu-id="22fe8-129">The object variable `num` refers to data of type `Integer`, and `frm` refers to an object of class <xref:System.Windows.Forms.Form>.</span></span>  
  
## <a name="object-arrays"></a><span data-ttu-id="22fe8-130">物件陣列</span><span class="sxs-lookup"><span data-stu-id="22fe8-130">Object Arrays</span></span>  
 <span data-ttu-id="22fe8-131">您可以宣告和使用的陣列`Object`變數。</span><span class="sxs-lookup"><span data-stu-id="22fe8-131">You can declare and use an array of `Object` variables.</span></span> <span data-ttu-id="22fe8-132">當您需要處理各種資料型別和物件類別時，這非常有用。</span><span class="sxs-lookup"><span data-stu-id="22fe8-132">This is useful when you need to handle a variety of data types and object classes.</span></span> <span data-ttu-id="22fe8-133">陣列中的所有項目必須具有相同的宣告的資料型別。</span><span class="sxs-lookup"><span data-stu-id="22fe8-133">All the elements in an array must have the same declared data type.</span></span> <span data-ttu-id="22fe8-134">宣告為此資料型別`Object`可讓您儲存物件和類別與陣列中其他資料類型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="22fe8-134">Declaring this data type as `Object` allows you to store objects and class instances alongside other data types in the array.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22fe8-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="22fe8-135">See Also</span></span>  
 <span data-ttu-id="22fe8-136">[物件變數](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md) </span><span class="sxs-lookup"><span data-stu-id="22fe8-136">[Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md) </span></span>  
<span data-ttu-id="22fe8-137"> [物件變數宣告](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md) </span><span class="sxs-lookup"><span data-stu-id="22fe8-137"> [Object Variable Declaration](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md) </span></span>  
<span data-ttu-id="22fe8-138"> [物件變數指派](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md) </span><span class="sxs-lookup"><span data-stu-id="22fe8-138"> [Object Variable Assignment](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md) </span></span>  
<span data-ttu-id="22fe8-139"> [如何︰ 參考物件的目前執行個體](../../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md) </span><span class="sxs-lookup"><span data-stu-id="22fe8-139"> [How to: Refer to the Current Instance of an Object](../../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md) </span></span>  
<span data-ttu-id="22fe8-140"> [如何︰ 決定物件變數參考的類型](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md) </span><span class="sxs-lookup"><span data-stu-id="22fe8-140"> [How to: Determine What Type an Object Variable Refers To](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md) </span></span>  
<span data-ttu-id="22fe8-141"> [如何︰ 判斷兩個物件是否關聯](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md) </span><span class="sxs-lookup"><span data-stu-id="22fe8-141"> [How to: Determine Whether Two Objects Are Related](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md) </span></span>  
<span data-ttu-id="22fe8-142"> [如何︰ 判斷兩個物件是否相同](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md) </span><span class="sxs-lookup"><span data-stu-id="22fe8-142"> [How to: Determine Whether Two Objects Are Identical](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md) </span></span>  
<span data-ttu-id="22fe8-143"> [資料類型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)</span><span class="sxs-lookup"><span data-stu-id="22fe8-143"> [Data Types](../../../../visual-basic/programming-guide/language-features/data-types/index.md)</span></span>
