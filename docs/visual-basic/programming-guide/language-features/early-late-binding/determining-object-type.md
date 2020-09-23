---
title: 決定物件類型
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic], discovering which an object belongs to
- types [Visual Basic], determining Visual Basic object types
- object variables [Visual Basic], testing values
- TypeOf...Is expression, object type at run time
- TypeName function
- objects [Visual Basic], type determining
ms.assetid: d95e7ad1-cd63-41d6-9a28-d7a1380d49c1
ms.openlocfilehash: ae338bc9bad9646abc045a652d4ef33a8863354b
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91086058"
---
# <a name="determining-object-type-visual-basic"></a><span data-ttu-id="65021-102">決定物件類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="65021-102">Determining Object Type (Visual Basic)</span></span>

<span data-ttu-id="65021-103">泛型物件變數 (也就是說，您宣告為) 的變數 `Object` 可以保存任何類別的物件。</span><span class="sxs-lookup"><span data-stu-id="65021-103">Generic object variables (that is, variables you declare as `Object`) can hold objects from any class.</span></span> <span data-ttu-id="65021-104">使用類型的變數時 `Object` ，您可能需要根據物件的類別來採取不同的動作; 例如，某些物件可能不支援特定的屬性或方法。</span><span class="sxs-lookup"><span data-stu-id="65021-104">When using variables of type `Object`, you may need to take different actions based on the class of the object; for example, some objects might not support a particular property or method.</span></span> <span data-ttu-id="65021-105">Visual Basic 提供兩種方式來決定要在物件變數中儲存哪種類型的物件： `TypeName` 函數和 `TypeOf...Is` 運算子。</span><span class="sxs-lookup"><span data-stu-id="65021-105">Visual Basic provides two means of determining which type of object is stored in an object variable: the `TypeName` function and the `TypeOf...Is` operator.</span></span>  
  
## <a name="typename-and-typeofis"></a><span data-ttu-id="65021-106">TypeName 和 TypeOf .。。是</span><span class="sxs-lookup"><span data-stu-id="65021-106">TypeName and TypeOf…Is</span></span>  

 <span data-ttu-id="65021-107">`TypeName`當您需要儲存或顯示物件的類別名稱時，函式會傳回字串，而這是最好的選擇，如下列程式碼片段所示：</span><span class="sxs-lookup"><span data-stu-id="65021-107">The `TypeName` function returns a string and is the best choice when you need to store or display the class name of an object, as shown in the following code fragment:</span></span>  
  
 [!code-vb[VbVbalrOOP#92](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#92)]  
  
 <span data-ttu-id="65021-108">`TypeOf...Is`運算子是測試物件類型的最佳選擇，因為它的速度比使用的對等字串比較快許多 `TypeName` 。</span><span class="sxs-lookup"><span data-stu-id="65021-108">The `TypeOf...Is` operator is the best choice for testing an object's type, because it is much faster than an equivalent string comparison using `TypeName`.</span></span> <span data-ttu-id="65021-109">下列程式碼片段會 `TypeOf...Is` 在語句中使用 `If...Then...Else` ：</span><span class="sxs-lookup"><span data-stu-id="65021-109">The following code fragment uses `TypeOf...Is` within an `If...Then...Else` statement:</span></span>  
  
 [!code-vb[VbVbalrOOP#93](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#93)]  
  
 <span data-ttu-id="65021-110">有一點要特別注意。</span><span class="sxs-lookup"><span data-stu-id="65021-110">A word of caution is due here.</span></span> <span data-ttu-id="65021-111">`TypeOf...Is` `True` 如果物件是特定型別，或衍生自特定型別，則運算子會傳回。</span><span class="sxs-lookup"><span data-stu-id="65021-111">The `TypeOf...Is` operator returns `True` if an object is of a specific type, or is derived from a specific type.</span></span> <span data-ttu-id="65021-112">幾乎您使用 Visual Basic 所做的一切都牽涉到物件，包括通常不視為物件的一些元素，例如字串和整數。</span><span class="sxs-lookup"><span data-stu-id="65021-112">Almost everything you do with Visual Basic involves objects, which include some elements not normally thought of as objects, such as strings and integers.</span></span> <span data-ttu-id="65021-113">這些物件是衍生自，而且會繼承方法 <xref:System.Object> 。</span><span class="sxs-lookup"><span data-stu-id="65021-113">These objects are derived from and inherit methods from <xref:System.Object>.</span></span> <span data-ttu-id="65021-114">當傳遞 `Integer` 和評估時 `Object` ，運算子會傳回 `TypeOf...Is` `True` 。</span><span class="sxs-lookup"><span data-stu-id="65021-114">When passed an `Integer` and evaluated with `Object`, the `TypeOf...Is` operator returns `True`.</span></span> <span data-ttu-id="65021-115">下列範例會報告參數 `InParam` 同時是 `Object` 和 `Integer` ：</span><span class="sxs-lookup"><span data-stu-id="65021-115">The following example reports that the parameter `InParam` is both an `Object` and an `Integer`:</span></span>  
  
 [!code-vb[VbVbalrOOP#94](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#94)]  
  
 <span data-ttu-id="65021-116">下列範例會使用 `TypeOf...Is` 和 `TypeName` 來判斷在引數中傳遞給它的物件類型 `Ctrl` 。</span><span class="sxs-lookup"><span data-stu-id="65021-116">The following example uses both `TypeOf...Is` and `TypeName` to determine the type of object passed to it in the `Ctrl` argument.</span></span> <span data-ttu-id="65021-117">程式會 `TestObject` `ShowType` 使用三種不同的控制項來呼叫。</span><span class="sxs-lookup"><span data-stu-id="65021-117">The `TestObject` procedure calls `ShowType` with three different kinds of controls.</span></span>  
  
#### <a name="to-run-the-example"></a><span data-ttu-id="65021-118">執行範例</span><span class="sxs-lookup"><span data-stu-id="65021-118">To run the example</span></span>  
  
1. <span data-ttu-id="65021-119">建立新的 Windows 應用程式專案，並將控制項 <xref:System.Windows.Forms.Button> 、 <xref:System.Windows.Forms.CheckBox> 控制項和控制項加入 <xref:System.Windows.Forms.RadioButton> 表單中。</span><span class="sxs-lookup"><span data-stu-id="65021-119">Create a new Windows Application project and add a <xref:System.Windows.Forms.Button> control, a <xref:System.Windows.Forms.CheckBox> control, and a <xref:System.Windows.Forms.RadioButton> control to the form.</span></span>  
  
2. <span data-ttu-id="65021-120">從表單上的按鈕，呼叫程式 `TestObject` 。</span><span class="sxs-lookup"><span data-stu-id="65021-120">From the button on your form, call the `TestObject` procedure.</span></span>  
  
3. <span data-ttu-id="65021-121">將下列程式碼新增至您的表單：</span><span class="sxs-lookup"><span data-stu-id="65021-121">Add the following code to your form:</span></span>  
  
     [!code-vb[VbVbalrOOP#95](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#95)]  
  
## <a name="see-also"></a><span data-ttu-id="65021-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="65021-122">See also</span></span>

- <xref:Microsoft.VisualBasic.Information.TypeName%2A>
- [<span data-ttu-id="65021-123">使用字串名稱呼叫屬性或方法</span><span class="sxs-lookup"><span data-stu-id="65021-123">Calling a Property or Method Using a String Name</span></span>](calling-a-property-or-method-using-a-string-name.md)
- [<span data-ttu-id="65021-124">Object Data Type</span><span class="sxs-lookup"><span data-stu-id="65021-124">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="65021-125">If...Then...Else 陳述式</span><span class="sxs-lookup"><span data-stu-id="65021-125">If...Then...Else Statement</span></span>](../../../language-reference/statements/if-then-else-statement.md)
- [<span data-ttu-id="65021-126">String 資料類型</span><span class="sxs-lookup"><span data-stu-id="65021-126">String Data Type</span></span>](../../../language-reference/data-types/string-data-type.md)
- [<span data-ttu-id="65021-127">整數資料類型</span><span class="sxs-lookup"><span data-stu-id="65021-127">Integer Data Type</span></span>](../../../language-reference/data-types/integer-data-type.md)
