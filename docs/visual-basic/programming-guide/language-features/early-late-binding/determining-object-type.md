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
ms.openlocfilehash: a77cc0603a0b61f58a4aa703c4b1e6ef4c26729c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345192"
---
# <a name="determining-object-type-visual-basic"></a><span data-ttu-id="76c22-102">決定物件類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="76c22-102">Determining Object Type (Visual Basic)</span></span>
<span data-ttu-id="76c22-103">泛型物件變數（也就是您宣告為 `Object`的變數）可以保存任何類別中的物件。</span><span class="sxs-lookup"><span data-stu-id="76c22-103">Generic object variables (that is, variables you declare as `Object`) can hold objects from any class.</span></span> <span data-ttu-id="76c22-104">當您使用 `Object`類型的變數時，您可能需要根據物件的類別來採取不同的動作;例如，某些物件可能不支援特定的屬性或方法。</span><span class="sxs-lookup"><span data-stu-id="76c22-104">When using variables of type `Object`, you may need to take different actions based on the class of the object; for example, some objects might not support a particular property or method.</span></span> <span data-ttu-id="76c22-105">Visual Basic 提供兩個方法來決定要將哪一種類型的物件儲存在物件變數中： `TypeName` 函數和 `TypeOf...Is` 運算子。</span><span class="sxs-lookup"><span data-stu-id="76c22-105">Visual Basic provides two means of determining which type of object is stored in an object variable: the `TypeName` function and the `TypeOf...Is` operator.</span></span>  
  
## <a name="typename-and-typeofis"></a><span data-ttu-id="76c22-106">TypeName 和 TypeOf 。均</span><span class="sxs-lookup"><span data-stu-id="76c22-106">TypeName and TypeOf…Is</span></span>  
 <span data-ttu-id="76c22-107">當您需要儲存或顯示物件的類別名稱時，`TypeName` 函式會傳回字串，而且是最佳的選擇，如下列程式碼片段所示：</span><span class="sxs-lookup"><span data-stu-id="76c22-107">The `TypeName` function returns a string and is the best choice when you need to store or display the class name of an object, as shown in the following code fragment:</span></span>  
  
 [!code-vb[VbVbalrOOP#92](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#92)]  
  
 <span data-ttu-id="76c22-108">`TypeOf...Is` 運算子是測試物件類型的最佳選擇，因為它的速度比使用 `TypeName`的對等字串比較快很多。</span><span class="sxs-lookup"><span data-stu-id="76c22-108">The `TypeOf...Is` operator is the best choice for testing an object's type, because it is much faster than an equivalent string comparison using `TypeName`.</span></span> <span data-ttu-id="76c22-109">下列程式碼片段會在 `If...Then...Else` 語句中使用 `TypeOf...Is`：</span><span class="sxs-lookup"><span data-stu-id="76c22-109">The following code fragment uses `TypeOf...Is` within an `If...Then...Else` statement:</span></span>  
  
 [!code-vb[VbVbalrOOP#93](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#93)]  
  
 <span data-ttu-id="76c22-110">請注意，這裡有一個注意事項。</span><span class="sxs-lookup"><span data-stu-id="76c22-110">A word of caution is due here.</span></span> <span data-ttu-id="76c22-111">如果物件屬於特定型別，或衍生自特定型別，則 `TypeOf...Is` 運算子會傳回 `True`。</span><span class="sxs-lookup"><span data-stu-id="76c22-111">The `TypeOf...Is` operator returns `True` if an object is of a specific type, or is derived from a specific type.</span></span> <span data-ttu-id="76c22-112">幾乎所有您使用 Visual Basic 執行的工作都牽涉到物件，其中包括一些通常不會被視為物件的元素，例如字串和整數。</span><span class="sxs-lookup"><span data-stu-id="76c22-112">Almost everything you do with Visual Basic involves objects, which include some elements not normally thought of as objects, such as strings and integers.</span></span> <span data-ttu-id="76c22-113">這些物件衍生自，並繼承自 <xref:System.Object>的方法。</span><span class="sxs-lookup"><span data-stu-id="76c22-113">These objects are derived from and inherit methods from <xref:System.Object>.</span></span> <span data-ttu-id="76c22-114">當傳遞 `Integer` 並使用 `Object`進行評估時，`TypeOf...Is` 運算子會傳回 `True`。</span><span class="sxs-lookup"><span data-stu-id="76c22-114">When passed an `Integer` and evaluated with `Object`, the `TypeOf...Is` operator returns `True`.</span></span> <span data-ttu-id="76c22-115">下列範例會報告參數 `InParam` 同時為 `Object` 和 `Integer`：</span><span class="sxs-lookup"><span data-stu-id="76c22-115">The following example reports that the parameter `InParam` is both an `Object` and an `Integer`:</span></span>  
  
 [!code-vb[VbVbalrOOP#94](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#94)]  
  
 <span data-ttu-id="76c22-116">下列範例會使用 `TypeOf...Is` 和 `TypeName`，來判斷在 `Ctrl` 引數中傳遞給它的物件類型。</span><span class="sxs-lookup"><span data-stu-id="76c22-116">The following example uses both `TypeOf...Is` and `TypeName` to determine the type of object passed to it in the `Ctrl` argument.</span></span> <span data-ttu-id="76c22-117">`TestObject` 程式會使用三種不同的控制項來呼叫 `ShowType`。</span><span class="sxs-lookup"><span data-stu-id="76c22-117">The `TestObject` procedure calls `ShowType` with three different kinds of controls.</span></span>  
  
#### <a name="to-run-the-example"></a><span data-ttu-id="76c22-118">執行範例</span><span class="sxs-lookup"><span data-stu-id="76c22-118">To run the example</span></span>  
  
1. <span data-ttu-id="76c22-119">建立新的 Windows 應用程式專案，並將 <xref:System.Windows.Forms.Button> 控制項、<xref:System.Windows.Forms.CheckBox> 控制項和 <xref:System.Windows.Forms.RadioButton> 控制項加入至表單。</span><span class="sxs-lookup"><span data-stu-id="76c22-119">Create a new Windows Application project and add a <xref:System.Windows.Forms.Button> control, a <xref:System.Windows.Forms.CheckBox> control, and a <xref:System.Windows.Forms.RadioButton> control to the form.</span></span>  
  
2. <span data-ttu-id="76c22-120">從表單上的按鈕，呼叫 `TestObject` 程式。</span><span class="sxs-lookup"><span data-stu-id="76c22-120">From the button on your form, call the `TestObject` procedure.</span></span>  
  
3. <span data-ttu-id="76c22-121">將下列程式碼新增至您的表單：</span><span class="sxs-lookup"><span data-stu-id="76c22-121">Add the following code to your form:</span></span>  
  
     [!code-vb[VbVbalrOOP#95](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#95)]  
  
## <a name="see-also"></a><span data-ttu-id="76c22-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="76c22-122">See also</span></span>

- <xref:Microsoft.VisualBasic.Information.TypeName%2A>
- [<span data-ttu-id="76c22-123">使用字串名稱呼叫屬性或方法</span><span class="sxs-lookup"><span data-stu-id="76c22-123">Calling a Property or Method Using a String Name</span></span>](../../../../visual-basic/programming-guide/language-features/early-late-binding/calling-a-property-or-method-using-a-string-name.md)
- [<span data-ttu-id="76c22-124">Object Data Type</span><span class="sxs-lookup"><span data-stu-id="76c22-124">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="76c22-125">If...Then...Else 陳述式</span><span class="sxs-lookup"><span data-stu-id="76c22-125">If...Then...Else Statement</span></span>](../../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [<span data-ttu-id="76c22-126">String 資料類型</span><span class="sxs-lookup"><span data-stu-id="76c22-126">String Data Type</span></span>](../../../../visual-basic/language-reference/data-types/string-data-type.md)
- [<span data-ttu-id="76c22-127">Integer 資料類型</span><span class="sxs-lookup"><span data-stu-id="76c22-127">Integer Data Type</span></span>](../../../../visual-basic/language-reference/data-types/integer-data-type.md)
