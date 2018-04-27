---
title: 決定物件類型 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- classes [Visual Basic], discovering which an object belongs to
- types [Visual Basic], determining Visual Basic object types
- object variables [Visual Basic], testing values
- TypeOf...Is expression, object type at run time
- TypeName function
- objects [Visual Basic], type determining
ms.assetid: d95e7ad1-cd63-41d6-9a28-d7a1380d49c1
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a6d24be68ea4a9872f8f4fe89c1aabb943fbcb91
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="determining-object-type-visual-basic"></a><span data-ttu-id="c2e23-102">決定物件類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c2e23-102">Determining Object Type (Visual Basic)</span></span>
<span data-ttu-id="c2e23-103">泛型物件變數 (也就是變數宣告為`Object`) 可以保存任何類別的物件。</span><span class="sxs-lookup"><span data-stu-id="c2e23-103">Generic object variables (that is, variables you declare as `Object`) can hold objects from any class.</span></span> <span data-ttu-id="c2e23-104">使用類型的變數時`Object`，您可能需要不同依據採取動作的物件類別; 例如，有些物件可能不支援的特定屬性或方法。</span><span class="sxs-lookup"><span data-stu-id="c2e23-104">When using variables of type `Object`, you may need to take different actions based on the class of the object; for example, some objects might not support a particular property or method.</span></span> <span data-ttu-id="c2e23-105">Visual Basic 提供決定物件變數中儲存的物件類型的兩種：`TypeName`函式和`TypeOf...Is`運算子。</span><span class="sxs-lookup"><span data-stu-id="c2e23-105">Visual Basic provides two means of determining which type of object is stored in an object variable: the `TypeName` function and the `TypeOf...Is` operator.</span></span>  
  
## <a name="typename-and-typeofis"></a><span data-ttu-id="c2e23-106">TypeName 和 TypeOf...是</span><span class="sxs-lookup"><span data-stu-id="c2e23-106">TypeName and TypeOf…Is</span></span>  
 <span data-ttu-id="c2e23-107">`TypeName`函式傳回的字串，是最佳選擇，當您需要儲存或顯示類別物件的名稱，如下列程式碼片段所示：</span><span class="sxs-lookup"><span data-stu-id="c2e23-107">The `TypeName` function returns a string and is the best choice when you need to store or display the class name of an object, as shown in the following code fragment:</span></span>  
  
 [!code-vb[VbVbalrOOP#92](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_1.vb)]  
  
 <span data-ttu-id="c2e23-108">`TypeOf...Is`運算子會測試的物件類型的最佳選擇，因為它的速度比對等字串比較使用`TypeName`。</span><span class="sxs-lookup"><span data-stu-id="c2e23-108">The `TypeOf...Is` operator is the best choice for testing an object's type, because it is much faster than an equivalent string comparison using `TypeName`.</span></span> <span data-ttu-id="c2e23-109">下列程式碼片段使用`TypeOf...Is`內`If...Then...Else`陳述式：</span><span class="sxs-lookup"><span data-stu-id="c2e23-109">The following code fragment uses `TypeOf...Is` within an `If...Then...Else` statement:</span></span>  
  
 [!code-vb[VbVbalrOOP#93](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_2.vb)]  
  
 <span data-ttu-id="c2e23-110">注意這裡會到期。</span><span class="sxs-lookup"><span data-stu-id="c2e23-110">A word of caution is due here.</span></span> <span data-ttu-id="c2e23-111">`TypeOf...Is`運算子會傳回`True`如果物件是特定型別，或衍生自特定型別。</span><span class="sxs-lookup"><span data-stu-id="c2e23-111">The `TypeOf...Is` operator returns `True` if an object is of a specific type, or is derived from a specific type.</span></span> <span data-ttu-id="c2e23-112">幾乎所有項目中所做的 Visual Basic 牽涉到物件，其中包含通常不會視為物件，例如字串和整數的某些項目。</span><span class="sxs-lookup"><span data-stu-id="c2e23-112">Almost everything you do with Visual Basic involves objects, which include some elements not normally thought of as objects, such as strings and integers.</span></span> <span data-ttu-id="c2e23-113">這些物件衍生自和繼承方法從<xref:System.Object>。</span><span class="sxs-lookup"><span data-stu-id="c2e23-113">These objects are derived from and inherit methods from <xref:System.Object>.</span></span> <span data-ttu-id="c2e23-114">當傳遞`Integer`和評估與`Object`、`TypeOf...Is`運算子會傳回`True`。</span><span class="sxs-lookup"><span data-stu-id="c2e23-114">When passed an `Integer` and evaluated with `Object`, the `TypeOf...Is` operator returns `True`.</span></span> <span data-ttu-id="c2e23-115">下列範例會報告參數`InParam`同時為`Object`和`Integer`:</span><span class="sxs-lookup"><span data-stu-id="c2e23-115">The following example reports that the parameter `InParam` is both an `Object` and an `Integer`:</span></span>  
  
 [!code-vb[VbVbalrOOP#94](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_3.vb)]  
  
 <span data-ttu-id="c2e23-116">下列範例會使用這兩者`TypeOf...Is`和`TypeName`判斷物件傳遞給該型別`Ctrl`引數。</span><span class="sxs-lookup"><span data-stu-id="c2e23-116">The following example uses both `TypeOf...Is` and `TypeName` to determine the type of object passed to it in the `Ctrl` argument.</span></span> <span data-ttu-id="c2e23-117">`TestObject`程序呼叫`ShowType`含有三種不同的控制項。</span><span class="sxs-lookup"><span data-stu-id="c2e23-117">The `TestObject` procedure calls `ShowType` with three different kinds of controls.</span></span>  
  
#### <a name="to-run-the-example"></a><span data-ttu-id="c2e23-118">執行範例</span><span class="sxs-lookup"><span data-stu-id="c2e23-118">To run the example</span></span>  
  
1.  <span data-ttu-id="c2e23-119">建立新的 Windows 應用程式專案，加入<xref:System.Windows.Forms.Button>控制項，<xref:System.Windows.Forms.CheckBox>控制項和<xref:System.Windows.Forms.RadioButton>控制項加入表單。</span><span class="sxs-lookup"><span data-stu-id="c2e23-119">Create a new Windows Application project and add a <xref:System.Windows.Forms.Button> control, a <xref:System.Windows.Forms.CheckBox> control, and a <xref:System.Windows.Forms.RadioButton> control to the form.</span></span>  
  
2.  <span data-ttu-id="c2e23-120">您的表單上的按鈕，從呼叫`TestObject`程序。</span><span class="sxs-lookup"><span data-stu-id="c2e23-120">From the button on your form, call the `TestObject` procedure.</span></span>  
  
3.  <span data-ttu-id="c2e23-121">將下列程式碼加入至表單：</span><span class="sxs-lookup"><span data-stu-id="c2e23-121">Add the following code to your form:</span></span>  
  
     [!code-vb[VbVbalrOOP#95](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="c2e23-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c2e23-122">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Information.TypeName%2A>  
 [<span data-ttu-id="c2e23-123">使用字串名稱呼叫屬性或方法</span><span class="sxs-lookup"><span data-stu-id="c2e23-123">Calling a Property or Method Using a String Name</span></span>](../../../../visual-basic/programming-guide/language-features/early-late-binding/calling-a-property-or-method-using-a-string-name.md)  
 [<span data-ttu-id="c2e23-124">Object 資料類型</span><span class="sxs-lookup"><span data-stu-id="c2e23-124">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [<span data-ttu-id="c2e23-125">If...Then...Else 陳述式</span><span class="sxs-lookup"><span data-stu-id="c2e23-125">If...Then...Else Statement</span></span>](../../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [<span data-ttu-id="c2e23-126">String 資料類型</span><span class="sxs-lookup"><span data-stu-id="c2e23-126">String Data Type</span></span>](../../../../visual-basic/language-reference/data-types/string-data-type.md)  
 [<span data-ttu-id="c2e23-127">Integer 資料類型</span><span class="sxs-lookup"><span data-stu-id="c2e23-127">Integer Data Type</span></span>](../../../../visual-basic/language-reference/data-types/integer-data-type.md)
