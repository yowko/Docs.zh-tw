---
title: 如何：宣告及呼叫預設屬性
ms.date: 07/20/2015
helpviewer_keywords:
- defaults [Visual Basic], properties
- properties [Visual Basic], default
- procedures [Visual Basic], defining
- default properties [Visual Basic], in Visual Basic
- Visual Basic code, procedures
- Visual Basic code, properties
- default properties
ms.assetid: 68b4026e-09ef-4613-808e-f6287494ff63
ms.openlocfilehash: 21aa6e6a9bba23d767b9d1fac610eaac3265550d
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91087449"
---
# <a name="how-to-declare-and-call-a-default-property-in-visual-basic"></a><span data-ttu-id="97608-102">如何：在 Visual Basic 中宣告及呼叫預設屬性</span><span class="sxs-lookup"><span data-stu-id="97608-102">How to: Declare and Call a Default Property in Visual Basic</span></span>

<span data-ttu-id="97608-103">*預設屬性*為類別或結構屬性，您的程式碼可以存取，而不需要指定它。</span><span class="sxs-lookup"><span data-stu-id="97608-103">A *default property* is a class or structure property that your code can access without specifying it.</span></span> <span data-ttu-id="97608-104">當呼叫程式碼命名類別或結構，但不允許存取屬性時，Visual Basic 會解析該類別或結構的預設屬性（如果有的話）的存取權。</span><span class="sxs-lookup"><span data-stu-id="97608-104">When calling code names a class or structure but not a property, and the context allows access to a property, Visual Basic resolves the access to that class or structure's default property if one exists.</span></span>  
  
 <span data-ttu-id="97608-105">類別或結構最多隻能有一個預設屬性。</span><span class="sxs-lookup"><span data-stu-id="97608-105">A class or structure can have at most one default property.</span></span> <span data-ttu-id="97608-106">不過，您可以多載預設屬性，並擁有一個以上的版本。</span><span class="sxs-lookup"><span data-stu-id="97608-106">However, you can overload a default property and have more than one version of it.</span></span>  
  
 <span data-ttu-id="97608-107">如需詳細資訊，請參閱 [Default](../../../language-reference/modifiers/default.md)。</span><span class="sxs-lookup"><span data-stu-id="97608-107">For more information, see [Default](../../../language-reference/modifiers/default.md).</span></span>  
  
### <a name="to-declare-a-default-property"></a><span data-ttu-id="97608-108">宣告預設屬性</span><span class="sxs-lookup"><span data-stu-id="97608-108">To declare a default property</span></span>  
  
1. <span data-ttu-id="97608-109">以正常方式宣告屬性。</span><span class="sxs-lookup"><span data-stu-id="97608-109">Declare the property in the normal way.</span></span> <span data-ttu-id="97608-110">請勿指定 `Shared` 或 `Private` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="97608-110">Do not specify the `Shared` or `Private` keyword.</span></span>  
  
2. <span data-ttu-id="97608-111">`Default`在屬性宣告中包含關鍵字。</span><span class="sxs-lookup"><span data-stu-id="97608-111">Include the `Default` keyword in the property declaration.</span></span>  
  
3. <span data-ttu-id="97608-112">至少為屬性指定一個參數。</span><span class="sxs-lookup"><span data-stu-id="97608-112">Specify at least one parameter for the property.</span></span> <span data-ttu-id="97608-113">您無法定義未採用至少一個引數的預設屬性。</span><span class="sxs-lookup"><span data-stu-id="97608-113">You cannot define a default property that does not take at least one argument.</span></span>  
  
     [!code-vb[VbVbcnProcedures#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#17)]  
  
### <a name="to-call-a-default-property"></a><span data-ttu-id="97608-114">若要呼叫預設屬性</span><span class="sxs-lookup"><span data-stu-id="97608-114">To call a default property</span></span>  
  
1. <span data-ttu-id="97608-115">宣告包含類別或結構類型的變數。</span><span class="sxs-lookup"><span data-stu-id="97608-115">Declare a variable of the containing class or structure type.</span></span>  
  
     [!code-vb[VbVbcnProcedures#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#16)]  
  
2. <span data-ttu-id="97608-116">在您通常會包含屬性名稱的運算式中單獨使用變數名稱。</span><span class="sxs-lookup"><span data-stu-id="97608-116">Use the variable name alone in an expression where you would normally include the property name.</span></span>  
  
     [!code-vb[VbVbcnProcedures#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#21)]  
  
3. <span data-ttu-id="97608-117">在變數名稱後面加上括弧中的引數清單。</span><span class="sxs-lookup"><span data-stu-id="97608-117">Follow the variable name with an argument list in parentheses.</span></span> <span data-ttu-id="97608-118">預設屬性必須採用至少一個引數。</span><span class="sxs-lookup"><span data-stu-id="97608-118">A default property must take at least one argument.</span></span>  
  
     [!code-vb[VbVbcnProcedures#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#20)]  
  
4. <span data-ttu-id="97608-119">若要取出預設屬性值，請在運算式中使用變數名稱，並使用引數清單，或遵循相等的 (`=`) 登入指派語句。</span><span class="sxs-lookup"><span data-stu-id="97608-119">To retrieve the default property value, use the variable name, with an argument list, in an expression or following the equal (`=`) sign in an assignment statement.</span></span>  
  
     [!code-vb[VbVbcnProcedures#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#15)]  
  
5. <span data-ttu-id="97608-120">若要設定預設屬性值，請在指派語句的左側使用變數名稱和引數清單。</span><span class="sxs-lookup"><span data-stu-id="97608-120">To set the default property value, use the variable name, with an argument list, on the left side of an assignment statement.</span></span>  
  
     [!code-vb[VbVbcnProcedures#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#14)]  
  
6. <span data-ttu-id="97608-121">您一律可以使用變數名稱來指定預設的屬性名稱，就像存取任何其他屬性一樣。</span><span class="sxs-lookup"><span data-stu-id="97608-121">You can always specify the default property name together with the variable name, just as you would do to access any other property.</span></span>  
  
     [!code-vb[VbVbcnProcedures#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#19)]  
  
## <a name="example"></a><span data-ttu-id="97608-122">範例</span><span class="sxs-lookup"><span data-stu-id="97608-122">Example</span></span>  

 <span data-ttu-id="97608-123">下列範例會宣告類別的預設屬性。</span><span class="sxs-lookup"><span data-stu-id="97608-123">The following example declares a default property on a class.</span></span>  
  
 [!code-vb[VbVbcnProcedures#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="97608-124">範例</span><span class="sxs-lookup"><span data-stu-id="97608-124">Example</span></span>  

 <span data-ttu-id="97608-125">下列範例示範如何呼叫類別上的預設屬性 `myProperty` `class1` 。</span><span class="sxs-lookup"><span data-stu-id="97608-125">The following example demonstrates how to call the default property `myProperty` on class `class1`.</span></span> <span data-ttu-id="97608-126">這三個指派語句會在中儲存值 `myProperty` ，而 <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> 呼叫會讀取這些值。</span><span class="sxs-lookup"><span data-stu-id="97608-126">The three assignment statements store values in `myProperty`, and the <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> call reads the values.</span></span>  
  
 [!code-vb[VbVbcnProcedures#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#13)]  
  
 <span data-ttu-id="97608-127">預設屬性最常見的用法是 <xref:Microsoft.VisualBasic.Collection.Item%2A> 各種集合類別上的屬性。</span><span class="sxs-lookup"><span data-stu-id="97608-127">The most common use of a default property is the <xref:Microsoft.VisualBasic.Collection.Item%2A> property on various collection classes.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="97608-128">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="97608-128">Robust Programming</span></span>  

 <span data-ttu-id="97608-129">預設屬性可能會減少原始程式碼字元，但可以讓您的程式碼更難以讀取。</span><span class="sxs-lookup"><span data-stu-id="97608-129">Default properties can result in a small reduction in source code-characters, but they can make your code more difficult to read.</span></span> <span data-ttu-id="97608-130">如果呼叫程式碼不熟悉您的類別或結構，則在參考類別或結構名稱時，如果該參考存取類別或結構本身或預設屬性，則無法確定。</span><span class="sxs-lookup"><span data-stu-id="97608-130">If the calling code is not familiar with your class or structure, when it makes a reference to the class or structure name it cannot be certain whether that reference accesses the class or structure itself, or a default property.</span></span> <span data-ttu-id="97608-131">這可能會導致編譯器錯誤或微妙的執行時間邏輯錯誤。</span><span class="sxs-lookup"><span data-stu-id="97608-131">This can lead to compiler errors or subtle run-time logic errors.</span></span>  
  
 <span data-ttu-id="97608-132">您可以使用 [Option Strict 語句](../../../language-reference/statements/option-strict-statement.md) 將編譯器類型檢查設定為，以稍微減少預設屬性錯誤的機率 `On` 。</span><span class="sxs-lookup"><span data-stu-id="97608-132">You can somewhat reduce the chance of default property errors by always using the [Option Strict Statement](../../../language-reference/statements/option-strict-statement.md) to set compiler type checking to `On`.</span></span>  
  
 <span data-ttu-id="97608-133">如果您打算在程式碼中使用預先定義的類別或結構，就必須判斷它是否有預設屬性，如果是，它的名稱就是。</span><span class="sxs-lookup"><span data-stu-id="97608-133">If you are planning to use a predefined class or structure in your code, you must determine whether it has a default property, and if so, what its name is.</span></span>  
  
 <span data-ttu-id="97608-134">因為這些缺點，您應該考慮不要定義預設屬性。</span><span class="sxs-lookup"><span data-stu-id="97608-134">Because of these disadvantages, you should consider not defining default properties.</span></span> <span data-ttu-id="97608-135">為了讓程式碼更容易閱讀，您也應該考慮一律明確參考所有屬性，甚至是預設屬性。</span><span class="sxs-lookup"><span data-stu-id="97608-135">For code readability, you should also consider always referring to all properties explicitly, even default properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97608-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="97608-136">See also</span></span>

- [<span data-ttu-id="97608-137">屬性程序</span><span class="sxs-lookup"><span data-stu-id="97608-137">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="97608-138">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="97608-138">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="97608-139">Property Statement</span><span class="sxs-lookup"><span data-stu-id="97608-139">Property Statement</span></span>](../../../language-reference/statements/property-statement.md)
- [<span data-ttu-id="97608-140">預設值</span><span class="sxs-lookup"><span data-stu-id="97608-140">Default</span></span>](../../../language-reference/modifiers/default.md)
- [<span data-ttu-id="97608-141">Visual Basic 中屬性和變數的差異</span><span class="sxs-lookup"><span data-stu-id="97608-141">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="97608-142">如何：建立屬性</span><span class="sxs-lookup"><span data-stu-id="97608-142">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="97608-143">如何：宣告混合存取層級的屬性</span><span class="sxs-lookup"><span data-stu-id="97608-143">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="97608-144">如何：呼叫屬性程序</span><span class="sxs-lookup"><span data-stu-id="97608-144">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="97608-145">如何：將值置入屬性</span><span class="sxs-lookup"><span data-stu-id="97608-145">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="97608-146">如何：取得屬性值</span><span class="sxs-lookup"><span data-stu-id="97608-146">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
