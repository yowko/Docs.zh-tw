---
title: 多載的屬性和方法 (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- properties [Visual Basic], overloading
- methods [Visual Basic], overloading
- shadowing
- names [Visual Basic], multiple procedures with same
- procedures [Visual Basic], mulltiples with same name
- classes [Visual Basic], properties
- classes [Visual Basic], methods
- method overloading
- Overloads keyword [Visual Basic], overloaded members
ms.assetid: b686fb97-e7d7-4001-afaa-6650cba08f0d
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 96d5ef2462f5312baa5269865977596035a254d5
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="overloaded-properties-and-methods-visual-basic"></a><span data-ttu-id="48a98-102">多載的屬性和方法 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="48a98-102">Overloaded properties and methods (Visual Basic)</span></span>

<span data-ttu-id="48a98-103">多載，就是建立多個程序、 執行個體建構函式或具有相同名稱但不同的引數類型的類別中的屬性。</span><span class="sxs-lookup"><span data-stu-id="48a98-103">Overloading is the creation of more than one procedure, instance constructor, or property in a class with the same name but different argument types.</span></span>  
  
## <a name="overloading-usage"></a><span data-ttu-id="48a98-104">多載使用方式</span><span class="sxs-lookup"><span data-stu-id="48a98-104">Overloading usage</span></span>

 <span data-ttu-id="48a98-105">當您採用不同的資料類型上作業的程序的相同名稱的物件模型規定，多載會特別有用。</span><span class="sxs-lookup"><span data-stu-id="48a98-105">Overloading is especially useful when your object model dictates that you employ identical names for procedures that operate on different data types.</span></span> <span data-ttu-id="48a98-106">例如，可以顯示數種不同的資料類型的類別可以有`Display`看起來像這樣的程序：</span><span class="sxs-lookup"><span data-stu-id="48a98-106">For example, a class that can display several different data types could have `Display` procedures that look like this:</span></span>  
  
 [!code-vb[VbVbalrOOP#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#64)]
  
 <span data-ttu-id="48a98-107">沒有多載中，您必須建立不同的名稱，每個程序，即使它們沒有相同的作業，如下所示：</span><span class="sxs-lookup"><span data-stu-id="48a98-107">Without overloading, you would need to create distinct names for each procedure, even though they do the same thing, as shown next:</span></span>  
  
 [!code-vb[VbVbalrOOP#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#65)]
  
 <span data-ttu-id="48a98-108">多載可讓您更輕鬆地使用屬性或方法，因為它提供了可用的資料類型的選擇。</span><span class="sxs-lookup"><span data-stu-id="48a98-108">Overloading makes it easier to use properties or methods because it provides a choice of data types that can be used.</span></span> <span data-ttu-id="48a98-109">例如，多載`Display`方法討論之前可以呼叫任何下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="48a98-109">For example, the overloaded `Display` method discussed previously can be called with any of the following lines of code:</span></span>  
  
 [!code-vb[VbVbalrOOP#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#66)]
  
 <span data-ttu-id="48a98-110">在執行階段，Visual Basic 呼叫正確的程序，根據您指定的參數資料類型。</span><span class="sxs-lookup"><span data-stu-id="48a98-110">At run time, Visual Basic calls the correct procedure based on the data types of the parameters you specify.</span></span>  
  
## <a name="overloading-rules"></a><span data-ttu-id="48a98-111">多載規則</span><span class="sxs-lookup"><span data-stu-id="48a98-111">Overloading rules</span></span>

 <span data-ttu-id="48a98-112">您可以新增兩個或多個屬性具有相同名稱的方法，以建立多載的成員的類別。</span><span class="sxs-lookup"><span data-stu-id="48a98-112">You create an overloaded member for a class by adding two or more properties or methods with the same name.</span></span> <span data-ttu-id="48a98-113">除了多載衍生的成員，每個多載的成員必須具有不同的參數清單，並多載屬性或程序時，無法做為區別的功能使用下列項目：</span><span class="sxs-lookup"><span data-stu-id="48a98-113">Except for overloaded derived members, each overloaded member must have different parameter lists, and the following items cannot be used as a differentiating feature when overloading a property or procedure:</span></span>  
  
-   <span data-ttu-id="48a98-114">修飾詞，例如`ByVal`或`ByRef`，套用至成員或成員的參數。</span><span class="sxs-lookup"><span data-stu-id="48a98-114">Modifiers, such as `ByVal` or `ByRef`, that apply to a member, or parameters of the member.</span></span>  
  
-   <span data-ttu-id="48a98-115">參數的名稱</span><span class="sxs-lookup"><span data-stu-id="48a98-115">Names of parameters</span></span>  
  
-   <span data-ttu-id="48a98-116">程序的傳回型別</span><span class="sxs-lookup"><span data-stu-id="48a98-116">Return types of procedures</span></span>  
  
 <span data-ttu-id="48a98-117">`Overloads`關鍵字是選擇性的多載時，但是，如果任何多載成員會使用`Overloads`關鍵字，則所有其他多載的成員具有相同名稱也必須指定此關鍵字。</span><span class="sxs-lookup"><span data-stu-id="48a98-117">The `Overloads` keyword is optional when overloading, but if any overloaded member uses the `Overloads` keyword, then all other overloaded members with the same name must also specify this keyword.</span></span>  
  
 <span data-ttu-id="48a98-118">在衍生的類別可以多載繼承的成員與具有相同參數和參數類型，這道程序的成員*的名稱和簽章，以遮蔽*。</span><span class="sxs-lookup"><span data-stu-id="48a98-118">Derived classes can overload inherited members with members that have identical parameters and parameter types, a process known as *shadowing by name and signature*.</span></span> <span data-ttu-id="48a98-119">如果`Overloads`的名稱和簽章，以遮蔽，成員的衍生的類別的實作將會使用而不是基底類別中實作，而且該成員的所有多載可用的執行個體時，會使用關鍵字在衍生的類別。</span><span class="sxs-lookup"><span data-stu-id="48a98-119">If the `Overloads` keyword is used when shadowing by name and signature, the derived class's implementation of the member will be used instead of the implementation in the base class, and all other overloads for that member will be available to instances of the derived class.</span></span>  
  
 <span data-ttu-id="48a98-120">如果`Overloads`多載繼承的成員具有相同參數和參數類型的成員時，省略關鍵字，則稱為多載*的名稱，以遮蔽*。</span><span class="sxs-lookup"><span data-stu-id="48a98-120">If the `Overloads` keyword is omitted when overloading an inherited member with a member that has identical parameters and parameter types, then the overloading is called *shadowing by name*.</span></span> <span data-ttu-id="48a98-121">名稱，以遮蔽取代繼承的成員，實作，而它會使得所有其他多載衍生的類別和及其子系的執行個體無法使用。</span><span class="sxs-lookup"><span data-stu-id="48a98-121">Shadowing by name replaces the inherited implementation of a member, and it makes all other overloads unavailable to instances of the derived class and its decedents.</span></span>  
  
 <span data-ttu-id="48a98-122">`Overloads`和`Shadows`修飾詞不能同時用於相同的屬性或方法。</span><span class="sxs-lookup"><span data-stu-id="48a98-122">The `Overloads` and `Shadows` modifiers cannot both be used with the same property or method.</span></span>  
  
### <a name="example"></a><span data-ttu-id="48a98-123">範例</span><span class="sxs-lookup"><span data-stu-id="48a98-123">Example</span></span>

 <span data-ttu-id="48a98-124">下列範例會建立多載的方法都接受`String`或`Decimal`金額和傳回包含營業稅的字串表示。</span><span class="sxs-lookup"><span data-stu-id="48a98-124">The following example creates overloaded methods that accept either a `String` or `Decimal` representation of a dollar amount and return a string containing the sales tax.</span></span>  
  
#### <a name="to-use-this-example-to-create-an-overloaded-method"></a><span data-ttu-id="48a98-125">使用此範例來建立多載的方法</span><span class="sxs-lookup"><span data-stu-id="48a98-125">To use this example to create an overloaded method</span></span>
  
1.  <span data-ttu-id="48a98-126">開啟新的專案，然後加入類別，名為`TaxClass`。</span><span class="sxs-lookup"><span data-stu-id="48a98-126">Open a new project and add a class named `TaxClass`.</span></span>  
  
2.  <span data-ttu-id="48a98-127">將下列程式碼加入 `TaxClass` 類別。</span><span class="sxs-lookup"><span data-stu-id="48a98-127">Add the following code to the `TaxClass` class.</span></span>  
  
     [!code-vb[VbVbalrOOP#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#67)]
  
3.  <span data-ttu-id="48a98-128">將下列程序加入至表單。</span><span class="sxs-lookup"><span data-stu-id="48a98-128">Add the following procedure to your form.</span></span>  
  
     [!code-vb[VbVbalrOOP#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#68)]
  
4.  <span data-ttu-id="48a98-129">將按鈕加入到您的表單並呼叫`ShowTax`程序從`Button1_Click`按鈕的事件。</span><span class="sxs-lookup"><span data-stu-id="48a98-129">Add a button to your form and call the `ShowTax` procedure from the `Button1_Click` event of the button.</span></span>  
  
5.  <span data-ttu-id="48a98-130">執行專案，然後按一下 若要測試的多載表單上的按鈕`ShowTax`程序。</span><span class="sxs-lookup"><span data-stu-id="48a98-130">Run the project and click the button on the form to test the overloaded `ShowTax` procedure.</span></span>  
  
 <span data-ttu-id="48a98-131">在執行階段，編譯器會選擇適當的多載函式所使用的參數相符。</span><span class="sxs-lookup"><span data-stu-id="48a98-131">At run time, the compiler chooses the appropriate overloaded function that matches the parameters being used.</span></span> <span data-ttu-id="48a98-132">當您按一下按鈕時，使用第一次呼叫多載的方法`Price`參數是字串和訊息，「 價格會是一個字串。</span><span class="sxs-lookup"><span data-stu-id="48a98-132">When you click the button, the overloaded method is called first with a `Price` parameter that is a string and the message, "Price is a String.</span></span> <span data-ttu-id="48a98-133">稅是 $5.12 「 顯示。</span><span class="sxs-lookup"><span data-stu-id="48a98-133">Tax is $5.12" is displayed.</span></span> <span data-ttu-id="48a98-134">`TaxAmount` 使用呼叫`Decimal`值的第二個時間和訊息，「 價格是十進位數。</span><span class="sxs-lookup"><span data-stu-id="48a98-134">`TaxAmount` is called with a `Decimal` value the second time and the message, "Price is a Decimal.</span></span> <span data-ttu-id="48a98-135">稅是 $5.12 「 顯示。</span><span class="sxs-lookup"><span data-stu-id="48a98-135">Tax is $5.12" is displayed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48a98-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="48a98-136">See also</span></span>

 [<span data-ttu-id="48a98-137">物件和類別</span><span class="sxs-lookup"><span data-stu-id="48a98-137">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [<span data-ttu-id="48a98-138">Visual Basic 中的遮蔽功能</span><span class="sxs-lookup"><span data-stu-id="48a98-138">Shadowing in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)  
 [<span data-ttu-id="48a98-139">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="48a98-139">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="48a98-140">繼承的基本概念</span><span class="sxs-lookup"><span data-stu-id="48a98-140">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [<span data-ttu-id="48a98-141">Shadows</span><span class="sxs-lookup"><span data-stu-id="48a98-141">Shadows</span></span>](../../../../visual-basic/language-reference/modifiers/shadows.md)  
 [<span data-ttu-id="48a98-142">ByVal</span><span class="sxs-lookup"><span data-stu-id="48a98-142">ByVal</span></span>](../../../../visual-basic/language-reference/modifiers/byval.md)  
 [<span data-ttu-id="48a98-143">ByRef</span><span class="sxs-lookup"><span data-stu-id="48a98-143">ByRef</span></span>](../../../../visual-basic/language-reference/modifiers/byref.md)  
 [<span data-ttu-id="48a98-144">多載</span><span class="sxs-lookup"><span data-stu-id="48a98-144">Overloads</span></span>](../../../../visual-basic/language-reference/modifiers/overloads.md)  
 [<span data-ttu-id="48a98-145">Shadows</span><span class="sxs-lookup"><span data-stu-id="48a98-145">Shadows</span></span>](../../../../visual-basic/language-reference/modifiers/shadows.md)
