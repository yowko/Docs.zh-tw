---
title: 如何：在 Visual Basic 中宣告及呼叫預設屬性
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
ms.openlocfilehash: 7805ee4dcd4bad0d0624c97ccc25232e9bc31ba4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-declare-and-call-a-default-property-in-visual-basic"></a><span data-ttu-id="6ad38-102">如何：在 Visual Basic 中宣告及呼叫預設屬性</span><span class="sxs-lookup"><span data-stu-id="6ad38-102">How to: Declare and Call a Default Property in Visual Basic</span></span>
<span data-ttu-id="6ad38-103">A*預設屬性*是類別或結構的屬性，可以存取您的程式碼，而不指定它。</span><span class="sxs-lookup"><span data-stu-id="6ad38-103">A *default property* is a class or structure property that your code can access without specifying it.</span></span> <span data-ttu-id="6ad38-104">在呼叫程式碼命名類別或結構，但不是屬性，與內容允許存取屬性時，Visual Basic 會解析成該類別或結構的預設屬性存取如果有的話。</span><span class="sxs-lookup"><span data-stu-id="6ad38-104">When calling code names a class or structure but not a property, and the context allows access to a property, Visual Basic resolves the access to that class or structure's default property if one exists.</span></span>  
  
 <span data-ttu-id="6ad38-105">類別或結構最多可以有一個預設屬性。</span><span class="sxs-lookup"><span data-stu-id="6ad38-105">A class or structure can have at most one default property.</span></span> <span data-ttu-id="6ad38-106">不過，您可以多載預設屬性，並擁有多個版本。</span><span class="sxs-lookup"><span data-stu-id="6ad38-106">However, you can overload a default property and have more than one version of it.</span></span>  
  
 <span data-ttu-id="6ad38-107">如需詳細資訊，請參閱[預設](../../../../visual-basic/language-reference/modifiers/default.md)。</span><span class="sxs-lookup"><span data-stu-id="6ad38-107">For more information, see [Default](../../../../visual-basic/language-reference/modifiers/default.md).</span></span>  
  
### <a name="to-declare-a-default-property"></a><span data-ttu-id="6ad38-108">若要宣告預設屬性</span><span class="sxs-lookup"><span data-stu-id="6ad38-108">To declare a default property</span></span>  
  
1.  <span data-ttu-id="6ad38-109">以一般方式宣告屬性。</span><span class="sxs-lookup"><span data-stu-id="6ad38-109">Declare the property in the normal way.</span></span> <span data-ttu-id="6ad38-110">未指定`Shared`或`Private`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="6ad38-110">Do not specify the `Shared` or `Private` keyword.</span></span>  
  
2.  <span data-ttu-id="6ad38-111">包含`Default`屬性宣告中的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="6ad38-111">Include the `Default` keyword in the property declaration.</span></span>  
  
3.  <span data-ttu-id="6ad38-112">指定至少一個參數的屬性。</span><span class="sxs-lookup"><span data-stu-id="6ad38-112">Specify at least one parameter for the property.</span></span> <span data-ttu-id="6ad38-113">您無法定義預設屬性不需要使用至少一個引數。</span><span class="sxs-lookup"><span data-stu-id="6ad38-113">You cannot define a default property that does not take at least one argument.</span></span>  
  
     [!code-vb[VbVbcnProcedures#17](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_1.vb)]  
  
### <a name="to-call-a-default-property"></a><span data-ttu-id="6ad38-114">若要呼叫預設屬性</span><span class="sxs-lookup"><span data-stu-id="6ad38-114">To call a default property</span></span>  
  
1.  <span data-ttu-id="6ad38-115">宣告包含的類別或結構類型的變數。</span><span class="sxs-lookup"><span data-stu-id="6ad38-115">Declare a variable of the containing class or structure type.</span></span>  
  
     [!code-vb[VbVbcnProcedures#16](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_2.vb)]  
  
2.  <span data-ttu-id="6ad38-116">使用只在運算式中的變數名稱，您通常會包含屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="6ad38-116">Use the variable name alone in an expression where you would normally include the property name.</span></span>  
  
     [!code-vb[VbVbcnProcedures#21](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_3.vb)]  
  
3.  <span data-ttu-id="6ad38-117">在變數名稱後面的括號括住的引數清單。</span><span class="sxs-lookup"><span data-stu-id="6ad38-117">Follow the variable name with an argument list in parentheses.</span></span> <span data-ttu-id="6ad38-118">預設屬性必須接受一個引數。</span><span class="sxs-lookup"><span data-stu-id="6ad38-118">A default property must take at least one argument.</span></span>  
  
     [!code-vb[VbVbcnProcedures#20](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_4.vb)]  
  
4.  <span data-ttu-id="6ad38-119">若要擷取預設屬性值，使用變數名稱，在運算式中，或等號之後的引數清單 (`=`) 登入指派陳述式。</span><span class="sxs-lookup"><span data-stu-id="6ad38-119">To retrieve the default property value, use the variable name, with an argument list, in an expression or following the equal (`=`) sign in an assignment statement.</span></span>  
  
     [!code-vb[VbVbcnProcedures#15](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_5.vb)]  
  
5.  <span data-ttu-id="6ad38-120">若要設定預設屬性值，使用的引數清單，在指派陳述式左邊的變數名稱。</span><span class="sxs-lookup"><span data-stu-id="6ad38-120">To set the default property value, use the variable name, with an argument list, on the left side of an assignment statement.</span></span>  
  
     [!code-vb[VbVbcnProcedures#14](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_6.vb)]  
  
6.  <span data-ttu-id="6ad38-121">您一律可以指定預設屬性名稱以及變數名稱，就像您一樣存取任何其他屬性。</span><span class="sxs-lookup"><span data-stu-id="6ad38-121">You can always specify the default property name together with the variable name, just as you would do to access any other property.</span></span>  
  
     [!code-vb[VbVbcnProcedures#19](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_7.vb)]  
  
## <a name="example"></a><span data-ttu-id="6ad38-122">範例</span><span class="sxs-lookup"><span data-stu-id="6ad38-122">Example</span></span>  
 <span data-ttu-id="6ad38-123">下列範例會宣告預設屬性類別上。</span><span class="sxs-lookup"><span data-stu-id="6ad38-123">The following example declares a default property on a class.</span></span>  
  
 [!code-vb[VbVbcnProcedures#12](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_8.vb)]  
  
## <a name="example"></a><span data-ttu-id="6ad38-124">範例</span><span class="sxs-lookup"><span data-stu-id="6ad38-124">Example</span></span>  
 <span data-ttu-id="6ad38-125">下列範例示範如何呼叫預設屬性`myProperty`類別上`class1`。</span><span class="sxs-lookup"><span data-stu-id="6ad38-125">The following example demonstrates how to call the default property `myProperty` on class `class1`.</span></span> <span data-ttu-id="6ad38-126">三個指派陳述式數值儲存在`myProperty`，而<xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>呼叫讀取值。</span><span class="sxs-lookup"><span data-stu-id="6ad38-126">The three assignment statements store values in `myProperty`, and the <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> call reads the values.</span></span>  
  
 [!code-vb[VbVbcnProcedures#13](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_9.vb)]  
  
 <span data-ttu-id="6ad38-127">預設屬性的最常見的用法是<xref:Microsoft.VisualBasic.Collection.Item%2A>上各種不同的集合類別的屬性。</span><span class="sxs-lookup"><span data-stu-id="6ad38-127">The most common use of a default property is the <xref:Microsoft.VisualBasic.Collection.Item%2A> property on various collection classes.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="6ad38-128">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="6ad38-128">Robust Programming</span></span>  
 <span data-ttu-id="6ad38-129">預設屬性可能會導致小型減少原始程式碼字元，但它們可讓您的程式碼更難閱讀。</span><span class="sxs-lookup"><span data-stu-id="6ad38-129">Default properties can result in a small reduction in source code-characters, but they can make your code more difficult to read.</span></span> <span data-ttu-id="6ad38-130">如果類別或結構名稱的參考時呼叫的程式碼不熟悉您自己的類別或結構，它無法確定該參考存取類別或結構本身或預設屬性。</span><span class="sxs-lookup"><span data-stu-id="6ad38-130">If the calling code is not familiar with your class or structure, when it makes a reference to the class or structure name it cannot be certain whether that reference accesses the class or structure itself, or a default property.</span></span> <span data-ttu-id="6ad38-131">這可能會導致編譯器錯誤或難以察覺的執行階段邏輯錯誤。</span><span class="sxs-lookup"><span data-stu-id="6ad38-131">This can lead to compiler errors or subtle run-time logic errors.</span></span>  
  
 <span data-ttu-id="6ad38-132">您可以稍微降低預設屬性錯誤的機率都使用[Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)設定要檢查的編譯器型別`On`。</span><span class="sxs-lookup"><span data-stu-id="6ad38-132">You can somewhat reduce the chance of default property errors by always using the [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) to set compiler type checking to `On`.</span></span>  
  
 <span data-ttu-id="6ad38-133">如果您打算使用預先定義的類別或結構中程式碼，您必須判斷是否具有預設屬性，而且如果是，它的名稱為何。</span><span class="sxs-lookup"><span data-stu-id="6ad38-133">If you are planning to use a predefined class or structure in your code, you must determine whether it has a default property, and if so, what its name is.</span></span>  
  
 <span data-ttu-id="6ad38-134">由於這些缺點，您應該考慮不要定義預設屬性。</span><span class="sxs-lookup"><span data-stu-id="6ad38-134">Because of these disadvantages, you should consider not defining default properties.</span></span> <span data-ttu-id="6ad38-135">程式碼的可讀性，您應該也會考慮一律明確地參考所有屬性，甚至是預設屬性。</span><span class="sxs-lookup"><span data-stu-id="6ad38-135">For code readability, you should also consider always referring to all properties explicitly, even default properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ad38-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6ad38-136">See Also</span></span>  
 [<span data-ttu-id="6ad38-137">屬性程序</span><span class="sxs-lookup"><span data-stu-id="6ad38-137">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="6ad38-138">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="6ad38-138">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="6ad38-139">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="6ad38-139">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="6ad38-140">Default</span><span class="sxs-lookup"><span data-stu-id="6ad38-140">Default</span></span>](../../../../visual-basic/language-reference/modifiers/default.md)  
 [<span data-ttu-id="6ad38-141">在 Visual Basic 中屬性和變數之間的差異</span><span class="sxs-lookup"><span data-stu-id="6ad38-141">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)  
 [<span data-ttu-id="6ad38-142">如何：建立屬性</span><span class="sxs-lookup"><span data-stu-id="6ad38-142">How to: Create a Property</span></span>](./how-to-create-a-property.md)  
 [<span data-ttu-id="6ad38-143">如何：宣告混合存取層級的屬性</span><span class="sxs-lookup"><span data-stu-id="6ad38-143">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [<span data-ttu-id="6ad38-144">如何：呼叫屬性程序</span><span class="sxs-lookup"><span data-stu-id="6ad38-144">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)  
 [<span data-ttu-id="6ad38-145">如何：將值置入屬性</span><span class="sxs-lookup"><span data-stu-id="6ad38-145">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)  
 [<span data-ttu-id="6ad38-146">如何：取得屬性值</span><span class="sxs-lookup"><span data-stu-id="6ad38-146">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
