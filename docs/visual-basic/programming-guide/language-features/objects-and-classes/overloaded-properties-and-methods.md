---
title: "多載屬性和方法 (Visual Basic) |Microsoft 文件"
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
- properties [Visual Basic], overloading
- methods [Visual Basic], overloading
- shadowing
- names, multiple procedures with same
- procedures, mulltiples with same name
- classes [Visual Basic], properties
- classes [Visual Basic], methods
- method overloading
- Overloads keyword, overloaded members
ms.assetid: b686fb97-e7d7-4001-afaa-6650cba08f0d
caps.latest.revision: 12
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
ms.openlocfilehash: 0b0040f78fd8e091027e32efae3a0f26c2a08622
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="overloaded-properties-and-methods-visual-basic"></a><span data-ttu-id="03f19-102">多載屬性和方法 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="03f19-102">Overloaded Properties and Methods (Visual Basic)</span></span>
<span data-ttu-id="03f19-103">多載會建立多個程序、 執行個體建構函式或具有相同名稱但不同引數型別類別中的屬性。</span><span class="sxs-lookup"><span data-stu-id="03f19-103">Overloading is the creation of more than one procedure, instance constructor, or property in a class with the same name but different argument types.</span></span>  
  
## <a name="overloading-usage"></a><span data-ttu-id="03f19-104">使用多載化</span><span class="sxs-lookup"><span data-stu-id="03f19-104">Overloading Usage</span></span>  
 <span data-ttu-id="03f19-105">當您採用不同的資料型別上作業的程序的相同名稱的物件模型規定時，多載會特別有用。</span><span class="sxs-lookup"><span data-stu-id="03f19-105">Overloading is especially useful when your object model dictates that you employ identical names for procedures that operate on different data types.</span></span> <span data-ttu-id="03f19-106">比方說，可以顯示數個不同的資料類型的類別可能會有`Display`看起來像這樣的程序︰</span><span class="sxs-lookup"><span data-stu-id="03f19-106">For example, a class that can display several different data types could have `Display` procedures that look like this:</span></span>  
  
 <span data-ttu-id="03f19-107">[!code-vb[VbVbalrOOP #&64;](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="03f19-107">[!code-vb[VbVbalrOOP#64](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_1.vb)]</span></span>  
  
 <span data-ttu-id="03f19-108">沒有多載化，您必須建立不同的名稱，每個程序，即使它們是一樣，一步所示︰</span><span class="sxs-lookup"><span data-stu-id="03f19-108">Without overloading, you would need to create distinct names for each procedure, even though they do the same thing, as shown next:</span></span>  
  
 <span data-ttu-id="03f19-109">[!code-vb[VbVbalrOOP #&65;](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="03f19-109">[!code-vb[VbVbalrOOP#65](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_2.vb)]</span></span>  
  
 <span data-ttu-id="03f19-110">多載可讓您更輕鬆地使用屬性或方法，因為它提供了可用的資料類型的選擇。</span><span class="sxs-lookup"><span data-stu-id="03f19-110">Overloading makes it easier to use properties or methods because it provides a choice of data types that can be used.</span></span> <span data-ttu-id="03f19-111">例如，多載`Display`所討論的方法之前可以呼叫任何下列程式碼行︰</span><span class="sxs-lookup"><span data-stu-id="03f19-111">For example, the overloaded `Display` method discussed previously can be called with any of the following lines of code:</span></span>  
  
 <span data-ttu-id="03f19-112">[!code-vb[VbVbalrOOP #&66;](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="03f19-112">[!code-vb[VbVbalrOOP#66](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_3.vb)]</span></span>  
  
 <span data-ttu-id="03f19-113">在執行階段，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]呼叫正確的程序根據資料型別參數的您所指定。</span><span class="sxs-lookup"><span data-stu-id="03f19-113">At run time, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] calls the correct procedure based on the data types of the parameters you specify.</span></span>  
  
## <a name="overloading-rules"></a><span data-ttu-id="03f19-114">多載規則</span><span class="sxs-lookup"><span data-stu-id="03f19-114">Overloading Rules</span></span>  
 <span data-ttu-id="03f19-115">您可以新增兩個或多個屬性或方法具有相同名稱建立多載類別成員。</span><span class="sxs-lookup"><span data-stu-id="03f19-115">You create an overloaded member for a class by adding two or more properties or methods with the same name.</span></span> <span data-ttu-id="03f19-116">除了多載衍生的成員，每個多載的成員必須具有不同的參數清單和多載屬性或程序時，不做為區別功能使用下列項目︰</span><span class="sxs-lookup"><span data-stu-id="03f19-116">Except for overloaded derived members, each overloaded member must have different parameter lists, and the following items cannot be used as a differentiating feature when overloading a property or procedure:</span></span>  
  
-   <span data-ttu-id="03f19-117">修飾詞，例如`ByVal`或`ByRef`，套用到成員或成員的參數。</span><span class="sxs-lookup"><span data-stu-id="03f19-117">Modifiers, such as `ByVal` or `ByRef`, that apply to a member, or parameters of the member.</span></span>  
  
-   <span data-ttu-id="03f19-118">參數的名稱</span><span class="sxs-lookup"><span data-stu-id="03f19-118">Names of parameters</span></span>  
  
-   <span data-ttu-id="03f19-119">程序的傳回型別</span><span class="sxs-lookup"><span data-stu-id="03f19-119">Return types of procedures</span></span>  
  
 <span data-ttu-id="03f19-120">`Overloads`多載時，關鍵字是選擇性，但如果有多載成員會使用`Overloads`關鍵字，則其他所有多載的成員具有相同名稱也必須指定這個關鍵字。</span><span class="sxs-lookup"><span data-stu-id="03f19-120">The `Overloads` keyword is optional when overloading, but if any overloaded member uses the `Overloads` keyword, then all other overloaded members with the same name must also specify this keyword.</span></span>  
  
 <span data-ttu-id="03f19-121">在衍生的類別可以多載具有相同參數和參數型別，這道程序的繼承的成員*名稱和簽章，以遮蔽*。</span><span class="sxs-lookup"><span data-stu-id="03f19-121">Derived classes can overload inherited members with members that have identical parameters and parameter types, a process known as *shadowing by name and signature*.</span></span> <span data-ttu-id="03f19-122">如果`Overloads`關鍵字，以遮蔽名稱和簽章，衍生的類別實作的成員將用於而不是基底類別中實作及使用該成員的所有多載可供衍生類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="03f19-122">If the `Overloads` keyword is used when shadowing by name and signature, the derived class's implementation of the member will be used instead of the implementation in the base class, and all other overloads for that member will be available to instances of the derived class.</span></span>  
  
 <span data-ttu-id="03f19-123">如果`Overloads`多載化繼承的成員具有相同參數和參數類型的成員時省略關鍵字，則多載會呼叫*以名稱遮蔽*。</span><span class="sxs-lookup"><span data-stu-id="03f19-123">If the `Overloads` keyword is omitted when overloading an inherited member with a member that has identical parameters and parameter types, then the overloading is called *shadowing by name*.</span></span> <span data-ttu-id="03f19-124">以名稱遮蔽取代繼承的成員，實作，它會使其他所有多載無法在衍生的類別和及其子系的執行個體。</span><span class="sxs-lookup"><span data-stu-id="03f19-124">Shadowing by name replaces the inherited implementation of a member, and it makes all other overloads unavailable to instances of the derived class and its decedents.</span></span>  
  
 <span data-ttu-id="03f19-125">`Overloads`和`Shadows`修飾詞都不可與相同的屬性或方法。</span><span class="sxs-lookup"><span data-stu-id="03f19-125">The `Overloads` and `Shadows` modifiers cannot both be used with the same property or method.</span></span>  
  
### <a name="example"></a><span data-ttu-id="03f19-126">範例</span><span class="sxs-lookup"><span data-stu-id="03f19-126">Example</span></span>  
 <span data-ttu-id="03f19-127">下列範例會建立多載的方法可接受 `String`或`Decimal`金額和傳回包含營業稅的字串表示。</span><span class="sxs-lookup"><span data-stu-id="03f19-127">The following example creates overloaded methods that accept either a `String` or `Decimal` representation of a dollar amount and return a string containing the sales tax.</span></span>  
  
##### <a name="to-use-this-example-to-create-an-overloaded-method"></a><span data-ttu-id="03f19-128">若要使用此範例建立一個多載的方法</span><span class="sxs-lookup"><span data-stu-id="03f19-128">To use this example to create an overloaded method</span></span>  
  
1.  <span data-ttu-id="03f19-129">開啟新專案，並新增名為`TaxClass`。</span><span class="sxs-lookup"><span data-stu-id="03f19-129">Open a new project and add a class named `TaxClass`.</span></span>  
  
2.  <span data-ttu-id="03f19-130">將下列程式碼加入 `TaxClass` 類別。</span><span class="sxs-lookup"><span data-stu-id="03f19-130">Add the following code to the `TaxClass` class.</span></span>  
  
     <span data-ttu-id="03f19-131">[!code-vb[VbVbalrOOP #&67;](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="03f19-131">[!code-vb[VbVbalrOOP#67](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_4.vb)]</span></span>  
  
3.  <span data-ttu-id="03f19-132">將下列程序加入至表單。</span><span class="sxs-lookup"><span data-stu-id="03f19-132">Add the following procedure to your form.</span></span>  
  
     <span data-ttu-id="03f19-133">[!code-vb[VbVbalrOOP #&68;](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="03f19-133">[!code-vb[VbVbalrOOP#68](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_5.vb)]</span></span>  
  
4.  <span data-ttu-id="03f19-134">將按鈕加入至您的表單，並呼叫`ShowTax`程序從`Button1_Click`按鈕的事件。</span><span class="sxs-lookup"><span data-stu-id="03f19-134">Add a button to your form and call the `ShowTax` procedure from the `Button1_Click` event of the button.</span></span>  
  
5.  <span data-ttu-id="03f19-135">執行專案，然後按一下 若要測試的多載表單上的按鈕`ShowTax`程序。</span><span class="sxs-lookup"><span data-stu-id="03f19-135">Run the project and click the button on the form to test the overloaded `ShowTax` procedure.</span></span>  
  
 <span data-ttu-id="03f19-136">在執行階段，編譯器會選擇適當的多載函式所使用的參數相符。</span><span class="sxs-lookup"><span data-stu-id="03f19-136">At run time, the compiler chooses the appropriate overloaded function that matches the parameters being used.</span></span> <span data-ttu-id="03f19-137">當您按一下按鈕時，使用第一次呼叫多載的方法`Price`參數是字串和訊息，「 價格會是一個字串。</span><span class="sxs-lookup"><span data-stu-id="03f19-137">When you click the button, the overloaded method is called first with a `Price` parameter that is a string and the message, "Price is a String.</span></span> <span data-ttu-id="03f19-138">稅率為 $5.12 」 顯示。</span><span class="sxs-lookup"><span data-stu-id="03f19-138">Tax is $5.12" is displayed.</span></span> <span data-ttu-id="03f19-139">`TaxAmount`使用呼叫`Decimal`值第二次和訊息，「 價格是十進位。</span><span class="sxs-lookup"><span data-stu-id="03f19-139">`TaxAmount` is called with a `Decimal` value the second time and the message, "Price is a Decimal.</span></span> <span data-ttu-id="03f19-140">稅率為 $5.12 」 顯示。</span><span class="sxs-lookup"><span data-stu-id="03f19-140">Tax is $5.12" is displayed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03f19-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03f19-141">See Also</span></span>  
 <span data-ttu-id="03f19-142">[物件和類別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) </span><span class="sxs-lookup"><span data-stu-id="03f19-142">[Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) </span></span>  
<span data-ttu-id="03f19-143"> [在 Visual Basic 中，以遮蔽](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md) </span><span class="sxs-lookup"><span data-stu-id="03f19-143"> [Shadowing in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md) </span></span>  
<span data-ttu-id="03f19-144"> [Sub 陳述式](../../../../visual-basic/language-reference/statements/sub-statement.md) </span><span class="sxs-lookup"><span data-stu-id="03f19-144"> [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md) </span></span>  
<span data-ttu-id="03f19-145"> [繼承基本概念](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md) </span><span class="sxs-lookup"><span data-stu-id="03f19-145"> [Inheritance Basics](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md) </span></span>  
<span data-ttu-id="03f19-146"> [陰影](../../../../visual-basic/language-reference/modifiers/shadows.md) </span><span class="sxs-lookup"><span data-stu-id="03f19-146"> [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) </span></span>  
<span data-ttu-id="03f19-147"> [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) </span><span class="sxs-lookup"><span data-stu-id="03f19-147"> [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) </span></span>  
<span data-ttu-id="03f19-148"> [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) </span><span class="sxs-lookup"><span data-stu-id="03f19-148"> [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) </span></span>  
<span data-ttu-id="03f19-149"> [多載](../../../../visual-basic/language-reference/modifiers/overloads.md) </span><span class="sxs-lookup"><span data-stu-id="03f19-149"> [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) </span></span>  
<span data-ttu-id="03f19-150"> [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)</span><span class="sxs-lookup"><span data-stu-id="03f19-150"> [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)</span></span>
