---
title: 物件變數值 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- object variables [Visual Basic], values
- values [Visual Basic], of object variables
- data types [Visual Basic], object variable
- variables [Visual Basic], object
ms.assetid: 31555704-58a3-49f1-9a0a-6421f605664f
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 28307cc477f661c3046e125f297c1519485ad797
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="object-variable-values-visual-basic"></a><span data-ttu-id="367fd-102">物件變數值 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="367fd-102">Object Variable Values (Visual Basic)</span></span>
<span data-ttu-id="367fd-103">變數的[物件資料類型](../../../../visual-basic/language-reference/data-types/object-data-type.md)可以指向任何類型的資料。</span><span class="sxs-lookup"><span data-stu-id="367fd-103">A variable of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) can refer to data of any type.</span></span> <span data-ttu-id="367fd-104">您將儲存的值`Object`變數保留其他地方在記憶體中，而變數本身會保留資料指標。</span><span class="sxs-lookup"><span data-stu-id="367fd-104">The value you store in an `Object` variable is kept elsewhere in memory, while the variable itself holds a pointer to the data.</span></span>  
  
## <a name="object-classifier-functions"></a><span data-ttu-id="367fd-105">物件的分類函數</span><span class="sxs-lookup"><span data-stu-id="367fd-105">Object Classifier Functions</span></span>  
 <span data-ttu-id="367fd-106">Visual Basic 提供傳回什麼的相關資訊的函式`Object`變數參考至下, 表所示。</span><span class="sxs-lookup"><span data-stu-id="367fd-106">Visual Basic supplies functions that return information about what an `Object` variable refers to, as shown in the following table.</span></span>  
  
|<span data-ttu-id="367fd-107">功能</span><span class="sxs-lookup"><span data-stu-id="367fd-107">Function</span></span>|<span data-ttu-id="367fd-108">如果物件變數參考，則傳回 True</span><span class="sxs-lookup"><span data-stu-id="367fd-108">Returns True if the Object variable refers to</span></span>|  
|--------------|---------------------------------------------------|  
|<xref:Microsoft.VisualBasic.Information.IsArray%2A>|<span data-ttu-id="367fd-109">值，而非單一值的陣列</span><span class="sxs-lookup"><span data-stu-id="367fd-109">An array of values, rather than a single value</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsDate%2A>|<span data-ttu-id="367fd-110">A[日期資料型別](../../../../visual-basic/language-reference/data-types/date-data-type.md)值或可以解譯為日期和時間值的字串</span><span class="sxs-lookup"><span data-stu-id="367fd-110">A [Date Data Type](../../../../visual-basic/language-reference/data-types/date-data-type.md) value, or a string that can be interpreted as a date and time value</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsDBNull%2A>|<span data-ttu-id="367fd-111">型別的物件<xref:System.DBNull>，用來表示資料遺漏或不存在</span><span class="sxs-lookup"><span data-stu-id="367fd-111">An object of type <xref:System.DBNull>, which represents missing or nonexistent data</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsError%2A>|<span data-ttu-id="367fd-112">例外狀況物件，衍生自 <xref:System.Exception></span><span class="sxs-lookup"><span data-stu-id="367fd-112">An exception object, which derives from <xref:System.Exception></span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsNothing%2A>|<span data-ttu-id="367fd-113">[執行任何動作](../../../../visual-basic/language-reference/nothing.md)，也就是沒有物件目前指派給變數</span><span class="sxs-lookup"><span data-stu-id="367fd-113">[Nothing](../../../../visual-basic/language-reference/nothing.md), that is, no object is currently assigned to the variable</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsNumeric%2A>|<span data-ttu-id="367fd-114">數字或可以解譯為數字的字串</span><span class="sxs-lookup"><span data-stu-id="367fd-114">A number, or a string that can be interpreted as a number</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsReference%2A>|<span data-ttu-id="367fd-115">參考類型 （例如字串、 陣列、 委派或類別類型）</span><span class="sxs-lookup"><span data-stu-id="367fd-115">A reference type (such as a string, array, delegate, or class type)</span></span>|  
  
 <span data-ttu-id="367fd-116">您可以使用這些函式，以避免送出至作業或程序無效的值。</span><span class="sxs-lookup"><span data-stu-id="367fd-116">You can use these functions to avoid submitting an invalid value to an operation or a procedure.</span></span>  
  
## <a name="typeof-operator"></a><span data-ttu-id="367fd-117">TypeOf 運算子</span><span class="sxs-lookup"><span data-stu-id="367fd-117">TypeOf Operator</span></span>  
 <span data-ttu-id="367fd-118">您也可以使用[TypeOf 運算子](../../../../visual-basic/language-reference/operators/typeof-operator.md)來判斷是否為特定的資料類型目前參考的物件變數。</span><span class="sxs-lookup"><span data-stu-id="367fd-118">You can also use the [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md) to determine whether an object variable currently refers to a specific data type.</span></span> <span data-ttu-id="367fd-119">`TypeOf`...`Is`運算式評估為`True`如果運算元的執行階段類型衍生自或實作指定的型別。</span><span class="sxs-lookup"><span data-stu-id="367fd-119">The `TypeOf`...`Is` expression evaluates to `True` if the run-time type of the operand is derived from or implements the specified type.</span></span>  
  
 <span data-ttu-id="367fd-120">下列範例會使用`TypeOf`物件變數參考值和參考型別。</span><span class="sxs-lookup"><span data-stu-id="367fd-120">The following example uses `TypeOf` on object variables referring to value and reference types.</span></span>  
  
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
  
 <span data-ttu-id="367fd-121">上述範例會將下列行以**偵錯**視窗：</span><span class="sxs-lookup"><span data-stu-id="367fd-121">The preceding example writes the following lines to the **Debug** window:</span></span>  
  
 `num is Integer`  
  
 `num is Object`  
  
 `frm is Form`  
  
 `frm is Object`  
  
 <span data-ttu-id="367fd-122">物件變數`num`類型的資料是指`Integer`，和`frm`類別的物件是指<xref:System.Windows.Forms.Form>。</span><span class="sxs-lookup"><span data-stu-id="367fd-122">The object variable `num` refers to data of type `Integer`, and `frm` refers to an object of class <xref:System.Windows.Forms.Form>.</span></span>  
  
## <a name="object-arrays"></a><span data-ttu-id="367fd-123">物件陣列</span><span class="sxs-lookup"><span data-stu-id="367fd-123">Object Arrays</span></span>  
 <span data-ttu-id="367fd-124">您可以宣告和使用的陣列`Object`變數。</span><span class="sxs-lookup"><span data-stu-id="367fd-124">You can declare and use an array of `Object` variables.</span></span> <span data-ttu-id="367fd-125">當您需要處理各種資料類型和物件的類別時，這非常有用。</span><span class="sxs-lookup"><span data-stu-id="367fd-125">This is useful when you need to handle a variety of data types and object classes.</span></span> <span data-ttu-id="367fd-126">陣列中的所有元素必須都有相同的宣告的資料類型。</span><span class="sxs-lookup"><span data-stu-id="367fd-126">All the elements in an array must have the same declared data type.</span></span> <span data-ttu-id="367fd-127">宣告為此資料型別`Object`可讓您儲存物件和類別以及陣列中其他資料類型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="367fd-127">Declaring this data type as `Object` allows you to store objects and class instances alongside other data types in the array.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="367fd-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="367fd-128">See Also</span></span>  
 [<span data-ttu-id="367fd-129">物件變數</span><span class="sxs-lookup"><span data-stu-id="367fd-129">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="367fd-130">物件變數宣告</span><span class="sxs-lookup"><span data-stu-id="367fd-130">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [<span data-ttu-id="367fd-131">物件變數指派</span><span class="sxs-lookup"><span data-stu-id="367fd-131">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [<span data-ttu-id="367fd-132">如何：參考物件目前的執行個體</span><span class="sxs-lookup"><span data-stu-id="367fd-132">How to: Refer to the Current Instance of an Object</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)  
 [<span data-ttu-id="367fd-133">如何：決定物件變數參考的型別</span><span class="sxs-lookup"><span data-stu-id="367fd-133">How to: Determine What Type an Object Variable Refers To</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md)  
 [<span data-ttu-id="367fd-134">如何：判斷兩個物件是否關聯</span><span class="sxs-lookup"><span data-stu-id="367fd-134">How to: Determine Whether Two Objects Are Related</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)  
 [<span data-ttu-id="367fd-135">如何：判斷兩個物件是否相同</span><span class="sxs-lookup"><span data-stu-id="367fd-135">How to: Determine Whether Two Objects Are Identical</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)  
 [<span data-ttu-id="367fd-136">資料類型</span><span class="sxs-lookup"><span data-stu-id="367fd-136">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
