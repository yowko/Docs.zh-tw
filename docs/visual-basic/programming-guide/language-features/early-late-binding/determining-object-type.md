---
title: "決定物件類型 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- classes [Visual Basic], discovering which an object belongs to
- types [Visual Basic], determining Visual Basic object types
- object variables, testing values
- TypeOf...Is expression, object type at run time
- TypeName function
- objects [Visual Basic], type determining
ms.assetid: d95e7ad1-cd63-41d6-9a28-d7a1380d49c1
caps.latest.revision: 13
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
ms.openlocfilehash: fec7a275029dde469425b651d5b1220cb21ddbf6
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="determining-object-type-visual-basic"></a><span data-ttu-id="cc32a-102">決定物件類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cc32a-102">Determining Object Type (Visual Basic)</span></span>
<span data-ttu-id="cc32a-103">泛型物件變數 (也就是變數宣告為`Object`) 可以保存任何類別的物件。</span><span class="sxs-lookup"><span data-stu-id="cc32a-103">Generic object variables (that is, variables you declare as `Object`) can hold objects from any class.</span></span> <span data-ttu-id="cc32a-104">使用型別的變數時`Object`，您可能需要採取不同的物件類別為基礎的動作; 例如，有些物件可能不支援特定的屬性或方法。</span><span class="sxs-lookup"><span data-stu-id="cc32a-104">When using variables of type `Object`, you may need to take different actions based on the class of the object; for example, some objects might not support a particular property or method.</span></span> [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="cc32a-105">提供兩種方法可判斷哪一種物件會儲存在物件變數︰`TypeName`函式和`TypeOf...Is`運算子。</span><span class="sxs-lookup"><span data-stu-id="cc32a-105"> provides two means of determining which type of object is stored in an object variable: the `TypeName` function and the `TypeOf...Is` operator.</span></span>  
  
## <a name="typename-and-typeofis"></a><span data-ttu-id="cc32a-106">TypeName 和 TypeOf...是</span><span class="sxs-lookup"><span data-stu-id="cc32a-106">TypeName and TypeOf…Is</span></span>  
 <span data-ttu-id="cc32a-107">`TypeName`函式會傳回 string，而是最佳選擇，當您需要儲存或顯示類別物件的名稱，如下列程式碼片段所示︰</span><span class="sxs-lookup"><span data-stu-id="cc32a-107">The `TypeName` function returns a string and is the best choice when you need to store or display the class name of an object, as shown in the following code fragment:</span></span>  
  
 <span data-ttu-id="cc32a-108">[!code-vb[VbVbalrOOP #&92;](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="cc32a-108">[!code-vb[VbVbalrOOP#92](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_1.vb)]</span></span>  
  
 <span data-ttu-id="cc32a-109">`TypeOf...Is`運算子是測試的物件類型的最佳選擇，因為它是速度比對等的字串比較使用`TypeName`。</span><span class="sxs-lookup"><span data-stu-id="cc32a-109">The `TypeOf...Is` operator is the best choice for testing an object's type, because it is much faster than an equivalent string comparison using `TypeName`.</span></span> <span data-ttu-id="cc32a-110">下列程式碼片段使用`TypeOf...Is`內`If...Then...Else`陳述式︰</span><span class="sxs-lookup"><span data-stu-id="cc32a-110">The following code fragment uses `TypeOf...Is` within an `If...Then...Else` statement:</span></span>  
  
 <span data-ttu-id="cc32a-111">[!code-vb[VbVbalrOOP #&93;](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="cc32a-111">[!code-vb[VbVbalrOOP#93](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_2.vb)]</span></span>  
  
 <span data-ttu-id="cc32a-112">注意在此到期。</span><span class="sxs-lookup"><span data-stu-id="cc32a-112">A word of caution is due here.</span></span> <span data-ttu-id="cc32a-113">`TypeOf...Is`運算子會傳回`True`如果物件是特定型別，或衍生自特定型別。</span><span class="sxs-lookup"><span data-stu-id="cc32a-113">The `TypeOf...Is` operator returns `True` if an object is of a specific type, or is derived from a specific type.</span></span> <span data-ttu-id="cc32a-114">幾乎所有項目中所做的[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]牽涉到物件，包括一些通常不會被視為物件，例如字串和整數的項目。</span><span class="sxs-lookup"><span data-stu-id="cc32a-114">Almost everything you do with [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] involves objects, which include some elements not normally thought of as objects, such as strings and integers.</span></span> <span data-ttu-id="cc32a-115">這些物件衍生自與繼承來自<xref:System.Object>.</xref:System.Object>方法</span><span class="sxs-lookup"><span data-stu-id="cc32a-115">These objects are derived from and inherit methods from <xref:System.Object>.</span></span> <span data-ttu-id="cc32a-116">當傳遞`Integer`和評估與`Object`、`TypeOf...Is`運算子會傳回`True`。</span><span class="sxs-lookup"><span data-stu-id="cc32a-116">When passed an `Integer` and evaluated with `Object`, the `TypeOf...Is` operator returns `True`.</span></span> <span data-ttu-id="cc32a-117">下列範例會報告參數`InParam`同時為`Object`和`Integer`:</span><span class="sxs-lookup"><span data-stu-id="cc32a-117">The following example reports that the parameter `InParam` is both an `Object` and an `Integer`:</span></span>  
  
 <span data-ttu-id="cc32a-118">[!code-vb[VbVbalrOOP #&94;](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="cc32a-118">[!code-vb[VbVbalrOOP#94](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_3.vb)]</span></span>  
  
 <span data-ttu-id="cc32a-119">下列範例使用`TypeOf...Is`和`TypeName`判斷傳遞給它的物件型別`Ctrl`引數。</span><span class="sxs-lookup"><span data-stu-id="cc32a-119">The following example uses both `TypeOf...Is` and `TypeName` to determine the type of object passed to it in the `Ctrl` argument.</span></span> <span data-ttu-id="cc32a-120">`TestObject`程序呼叫`ShowType`有三種不同的控制項。</span><span class="sxs-lookup"><span data-stu-id="cc32a-120">The `TestObject` procedure calls `ShowType` with three different kinds of controls.</span></span>  
  
#### <a name="to-run-the-example"></a><span data-ttu-id="cc32a-121">執行範例</span><span class="sxs-lookup"><span data-stu-id="cc32a-121">To run the example</span></span>  
  
1.  <span data-ttu-id="cc32a-122">建立新的 Windows 應用程式專案並加入<xref:System.Windows.Forms.Button>控制項，<xref:System.Windows.Forms.CheckBox>控制項，以及<xref:System.Windows.Forms.RadioButton>控制項加入表單。</xref:System.Windows.Forms.RadioButton> </xref:System.Windows.Forms.CheckBox> </xref:System.Windows.Forms.Button></span><span class="sxs-lookup"><span data-stu-id="cc32a-122">Create a new Windows Application project and add a <xref:System.Windows.Forms.Button> control, a <xref:System.Windows.Forms.CheckBox> control, and a <xref:System.Windows.Forms.RadioButton> control to the form.</span></span>  
  
2.  <span data-ttu-id="cc32a-123">在表單上按鈕中，呼叫`TestObject`程序。</span><span class="sxs-lookup"><span data-stu-id="cc32a-123">From the button on your form, call the `TestObject` procedure.</span></span>  
  
3.  <span data-ttu-id="cc32a-124">將下列程式碼加入至表單︰</span><span class="sxs-lookup"><span data-stu-id="cc32a-124">Add the following code to your form:</span></span>  
  
     <span data-ttu-id="cc32a-125">[!code-vb[VbVbalrOOP #&95;](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="cc32a-125">[!code-vb[VbVbalrOOP#95](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_4.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc32a-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cc32a-126">See Also</span></span>  
 <span data-ttu-id="cc32a-127"><xref:Microsoft.VisualBasic.Information.TypeName%2A></xref:Microsoft.VisualBasic.Information.TypeName%2A></span><span class="sxs-lookup"><span data-stu-id="cc32a-127"><xref:Microsoft.VisualBasic.Information.TypeName%2A></span></span>   
<span data-ttu-id="cc32a-128"> [使用字串名稱呼叫屬性或方法](../../../../visual-basic/programming-guide/language-features/early-late-binding/calling-a-property-or-method-using-a-string-name.md) </span><span class="sxs-lookup"><span data-stu-id="cc32a-128"> [Calling a Property or Method Using a String Name](../../../../visual-basic/programming-guide/language-features/early-late-binding/calling-a-property-or-method-using-a-string-name.md) </span></span>  
<span data-ttu-id="cc32a-129"> [Object 資料型別](../../../../visual-basic/language-reference/data-types/object-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="cc32a-129"> [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) </span></span>  
<span data-ttu-id="cc32a-130"> [如果...然後...Else 陳述式](../../../../visual-basic/language-reference/statements/if-then-else-statement.md) </span><span class="sxs-lookup"><span data-stu-id="cc32a-130"> [If...Then...Else Statement](../../../../visual-basic/language-reference/statements/if-then-else-statement.md) </span></span>  
<span data-ttu-id="cc32a-131"> [字串資料類型](../../../../visual-basic/language-reference/data-types/string-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="cc32a-131"> [String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md) </span></span>  
<span data-ttu-id="cc32a-132"> [Integer 資料類型](../../../../visual-basic/language-reference/data-types/integer-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="cc32a-132"> [Integer Data Type](../../../../visual-basic/language-reference/data-types/integer-data-type.md)</span></span>
