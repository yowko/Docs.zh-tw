---
title: 決定物件類型 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic], discovering which an object belongs to
- types [Visual Basic], determining Visual Basic object types
- object variables [Visual Basic], testing values
- TypeOf...Is expression, object type at run time
- TypeName function
- objects [Visual Basic], type determining
ms.assetid: d95e7ad1-cd63-41d6-9a28-d7a1380d49c1
ms.openlocfilehash: becbbef008e8a474db198748d45f260fcb90c758
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56966767"
---
# <a name="determining-object-type-visual-basic"></a><span data-ttu-id="02ef2-102">決定物件類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="02ef2-102">Determining Object Type (Visual Basic)</span></span>
<span data-ttu-id="02ef2-103">泛型的物件變數 (也就是變數宣告為`Object`) 可以保留任何類別的物件。</span><span class="sxs-lookup"><span data-stu-id="02ef2-103">Generic object variables (that is, variables you declare as `Object`) can hold objects from any class.</span></span> <span data-ttu-id="02ef2-104">使用型別的變數時`Object`，您可能需要採取不同的物件類別為基礎的動作; 例如，某些物件可能不支援的特定屬性或方法。</span><span class="sxs-lookup"><span data-stu-id="02ef2-104">When using variables of type `Object`, you may need to take different actions based on the class of the object; for example, some objects might not support a particular property or method.</span></span> <span data-ttu-id="02ef2-105">Visual Basic 提供兩種決定物件變數中儲存的物件類型：`TypeName`函式和`TypeOf...Is`運算子。</span><span class="sxs-lookup"><span data-stu-id="02ef2-105">Visual Basic provides two means of determining which type of object is stored in an object variable: the `TypeName` function and the `TypeOf...Is` operator.</span></span>  
  
## <a name="typename-and-typeofis"></a><span data-ttu-id="02ef2-106">類型名稱，TypeOf...是</span><span class="sxs-lookup"><span data-stu-id="02ef2-106">TypeName and TypeOf…Is</span></span>  
 <span data-ttu-id="02ef2-107">`TypeName`函式傳回字串，是最佳選擇，當您需要儲存或顯示類別物件的名稱，如下列程式碼片段所示：</span><span class="sxs-lookup"><span data-stu-id="02ef2-107">The `TypeName` function returns a string and is the best choice when you need to store or display the class name of an object, as shown in the following code fragment:</span></span>  
  
 [!code-vb[VbVbalrOOP#92](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#92)]  
  
 <span data-ttu-id="02ef2-108">`TypeOf...Is`運算子會測試物件的類型的最佳選擇，因為它的速度比對等字串比較使用`TypeName`。</span><span class="sxs-lookup"><span data-stu-id="02ef2-108">The `TypeOf...Is` operator is the best choice for testing an object's type, because it is much faster than an equivalent string comparison using `TypeName`.</span></span> <span data-ttu-id="02ef2-109">下列程式碼片段會使用`TypeOf...Is`內`If...Then...Else`陳述式：</span><span class="sxs-lookup"><span data-stu-id="02ef2-109">The following code fragment uses `TypeOf...Is` within an `If...Then...Else` statement:</span></span>  
  
 [!code-vb[VbVbalrOOP#93](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#93)]  
  
 <span data-ttu-id="02ef2-110">注意這裡會到期。</span><span class="sxs-lookup"><span data-stu-id="02ef2-110">A word of caution is due here.</span></span> <span data-ttu-id="02ef2-111">`TypeOf...Is`運算子會傳回`True`如果物件是特定的類型，或衍生自特定的型別。</span><span class="sxs-lookup"><span data-stu-id="02ef2-111">The `TypeOf...Is` operator returns `True` if an object is of a specific type, or is derived from a specific type.</span></span> <span data-ttu-id="02ef2-112">幾乎所有項目中所做的 Visual Basic 牽涉到物件，其中包含一些通常不會視為物件，例如字串和整數的項目。</span><span class="sxs-lookup"><span data-stu-id="02ef2-112">Almost everything you do with Visual Basic involves objects, which include some elements not normally thought of as objects, such as strings and integers.</span></span> <span data-ttu-id="02ef2-113">這些物件衍生自和繼承方法<xref:System.Object>。</span><span class="sxs-lookup"><span data-stu-id="02ef2-113">These objects are derived from and inherit methods from <xref:System.Object>.</span></span> <span data-ttu-id="02ef2-114">當傳遞`Integer`和評估與`Object`，則`TypeOf...Is`運算子會傳回`True`。</span><span class="sxs-lookup"><span data-stu-id="02ef2-114">When passed an `Integer` and evaluated with `Object`, the `TypeOf...Is` operator returns `True`.</span></span> <span data-ttu-id="02ef2-115">下列範例會報告的參數`InParam`兼具`Object`和`Integer`:</span><span class="sxs-lookup"><span data-stu-id="02ef2-115">The following example reports that the parameter `InParam` is both an `Object` and an `Integer`:</span></span>  
  
 [!code-vb[VbVbalrOOP#94](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#94)]  
  
 <span data-ttu-id="02ef2-116">下列範例會使用這兩者`TypeOf...Is`並`TypeName`來判斷物件傳遞至該型別`Ctrl`引數。</span><span class="sxs-lookup"><span data-stu-id="02ef2-116">The following example uses both `TypeOf...Is` and `TypeName` to determine the type of object passed to it in the `Ctrl` argument.</span></span> <span data-ttu-id="02ef2-117">`TestObject`程序呼叫`ShowType`使用三種不同的控制項。</span><span class="sxs-lookup"><span data-stu-id="02ef2-117">The `TestObject` procedure calls `ShowType` with three different kinds of controls.</span></span>  
  
#### <a name="to-run-the-example"></a><span data-ttu-id="02ef2-118">執行範例</span><span class="sxs-lookup"><span data-stu-id="02ef2-118">To run the example</span></span>  
  
1.  <span data-ttu-id="02ef2-119">建立新的 Windows 應用程式專案並加入<xref:System.Windows.Forms.Button>控制<xref:System.Windows.Forms.CheckBox>控制項，和<xref:System.Windows.Forms.RadioButton>控制項加入表單。</span><span class="sxs-lookup"><span data-stu-id="02ef2-119">Create a new Windows Application project and add a <xref:System.Windows.Forms.Button> control, a <xref:System.Windows.Forms.CheckBox> control, and a <xref:System.Windows.Forms.RadioButton> control to the form.</span></span>  
  
2.  <span data-ttu-id="02ef2-120">從您的表單上的按鈕，呼叫`TestObject`程序。</span><span class="sxs-lookup"><span data-stu-id="02ef2-120">From the button on your form, call the `TestObject` procedure.</span></span>  
  
3.  <span data-ttu-id="02ef2-121">將下列程式碼新增至您的表單：</span><span class="sxs-lookup"><span data-stu-id="02ef2-121">Add the following code to your form:</span></span>  
  
     [!code-vb[VbVbalrOOP#95](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#95)]  
  
## <a name="see-also"></a><span data-ttu-id="02ef2-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02ef2-122">See also</span></span>
- <xref:Microsoft.VisualBasic.Information.TypeName%2A>
- [<span data-ttu-id="02ef2-123">使用字串名稱呼叫屬性或方法</span><span class="sxs-lookup"><span data-stu-id="02ef2-123">Calling a Property or Method Using a String Name</span></span>](../../../../visual-basic/programming-guide/language-features/early-late-binding/calling-a-property-or-method-using-a-string-name.md)
- [<span data-ttu-id="02ef2-124">Object 資料類型</span><span class="sxs-lookup"><span data-stu-id="02ef2-124">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="02ef2-125">If...Then...Else 陳述式</span><span class="sxs-lookup"><span data-stu-id="02ef2-125">If...Then...Else Statement</span></span>](../../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [<span data-ttu-id="02ef2-126">String 資料類型</span><span class="sxs-lookup"><span data-stu-id="02ef2-126">String Data Type</span></span>](../../../../visual-basic/language-reference/data-types/string-data-type.md)
- [<span data-ttu-id="02ef2-127">Integer 資料類型</span><span class="sxs-lookup"><span data-stu-id="02ef2-127">Integer Data Type</span></span>](../../../../visual-basic/language-reference/data-types/integer-data-type.md)
