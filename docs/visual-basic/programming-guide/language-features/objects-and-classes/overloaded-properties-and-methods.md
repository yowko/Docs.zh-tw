---
title: 多載屬性和方法
ms.date: 07/20/2015
helpviewer_keywords:
- properties [Visual Basic], overloading
- methods [Visual Basic], overloading
- shadowing
- names [Visual Basic], multiple procedures with same
- procedures [Visual Basic], multiples with same name
- classes [Visual Basic], properties
- classes [Visual Basic], methods
- method overloading
- Overloads keyword [Visual Basic], overloaded members
ms.assetid: b686fb97-e7d7-4001-afaa-6650cba08f0d
ms.openlocfilehash: a5017d371f8a01436020443b2e3466c78fc35d21
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346094"
---
# <a name="overloaded-properties-and-methods-visual-basic"></a><span data-ttu-id="4588b-102">多載屬性和方法（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="4588b-102">Overloaded properties and methods (Visual Basic)</span></span>

<span data-ttu-id="4588b-103">多載是在具有相同名稱但不同引數類型的類別中，建立一個以上的程式、實例函數或屬性。</span><span class="sxs-lookup"><span data-stu-id="4588b-103">Overloading is the creation of more than one procedure, instance constructor, or property in a class with the same name but different argument types.</span></span>

## <a name="overloading-usage"></a><span data-ttu-id="4588b-104">多載使用</span><span class="sxs-lookup"><span data-stu-id="4588b-104">Overloading usage</span></span>

<span data-ttu-id="4588b-105">當您的物件模型指示您針對在不同資料類型上運作的程式使用相同的名稱時，多載特別有用。</span><span class="sxs-lookup"><span data-stu-id="4588b-105">Overloading is especially useful when your object model dictates that you employ identical names for procedures that operate on different data types.</span></span> <span data-ttu-id="4588b-106">例如，可以顯示數個不同資料類型的類別可能會有如下所示的 `Display` 程式：</span><span class="sxs-lookup"><span data-stu-id="4588b-106">For example, a class that can display several different data types could have `Display` procedures that look like this:</span></span>

[!code-vb[VbVbalrOOP#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#64)]

<span data-ttu-id="4588b-107">如果沒有多載，您就必須為每個程式建立不同的名稱，即使它們執行相同的動作，如下所示：</span><span class="sxs-lookup"><span data-stu-id="4588b-107">Without overloading, you would need to create distinct names for each procedure, even though they do the same thing, as shown next:</span></span>

[!code-vb[VbVbalrOOP#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#65)]

<span data-ttu-id="4588b-108">多載可讓您更輕鬆地使用屬性或方法，因為它會提供可供使用的資料類型選擇。</span><span class="sxs-lookup"><span data-stu-id="4588b-108">Overloading makes it easier to use properties or methods because it provides a choice of data types that can be used.</span></span> <span data-ttu-id="4588b-109">例如，您可以使用下列任何一行程式碼呼叫先前所討論的多載 `Display` 方法：</span><span class="sxs-lookup"><span data-stu-id="4588b-109">For example, the overloaded `Display` method discussed previously can be called with any of the following lines of code:</span></span>

[!code-vb[VbVbalrOOP#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#66)]

<span data-ttu-id="4588b-110">在執行時間，Visual Basic 會根據您指定之參數的資料類型，呼叫正確的程式。</span><span class="sxs-lookup"><span data-stu-id="4588b-110">At run time, Visual Basic calls the correct procedure based on the data types of the parameters you specify.</span></span>

## <a name="overloading-rules"></a><span data-ttu-id="4588b-111">多載規則</span><span class="sxs-lookup"><span data-stu-id="4588b-111">Overloading rules</span></span>

 <span data-ttu-id="4588b-112">您可以藉由加入兩個或多個具有相同名稱的屬性或方法，來建立類別的多載成員。</span><span class="sxs-lookup"><span data-stu-id="4588b-112">You create an overloaded member for a class by adding two or more properties or methods with the same name.</span></span> <span data-ttu-id="4588b-113">除了多載的衍生成員之外，每個多載成員都必須有不同的參數清單，而且當多載屬性或程式時，無法使用下列專案做為區分功能：</span><span class="sxs-lookup"><span data-stu-id="4588b-113">Except for overloaded derived members, each overloaded member must have different parameter lists, and the following items cannot be used as a differentiating feature when overloading a property or procedure:</span></span>

- <span data-ttu-id="4588b-114">套用至成員的修飾詞，例如 `ByVal` 或 `ByRef`，或成員的參數。</span><span class="sxs-lookup"><span data-stu-id="4588b-114">Modifiers, such as `ByVal` or `ByRef`, that apply to a member, or parameters of the member.</span></span>

- <span data-ttu-id="4588b-115">參數的名稱</span><span class="sxs-lookup"><span data-stu-id="4588b-115">Names of parameters</span></span>

- <span data-ttu-id="4588b-116">傳回程序的類型</span><span class="sxs-lookup"><span data-stu-id="4588b-116">Return types of procedures</span></span>

<span data-ttu-id="4588b-117">當多載時，`Overloads` 關鍵字是選擇性的，但如果有任何多載成員使用 `Overloads` 關鍵字，則所有具有相同名稱的其他多載成員也都必須指定此關鍵字。</span><span class="sxs-lookup"><span data-stu-id="4588b-117">The `Overloads` keyword is optional when overloading, but if any overloaded member uses the `Overloads` keyword, then all other overloaded members with the same name must also specify this keyword.</span></span>

<span data-ttu-id="4588b-118">衍生的類別可以多載繼承的成員，這些成員具有相同的參數和參數類型，這種*程式稱為依名稱和*簽章的遮蔽。</span><span class="sxs-lookup"><span data-stu-id="4588b-118">Derived classes can overload inherited members with members that have identical parameters and parameter types, a process known as *shadowing by name and signature*.</span></span> <span data-ttu-id="4588b-119">如果在依名稱和簽章進行遮蔽時使用 `Overloads` 關鍵字，則會使用衍生類別的成員執行，而不是基類中的實作為，而且該成員的所有其他多載都可供衍生類別的實例使用。</span><span class="sxs-lookup"><span data-stu-id="4588b-119">If the `Overloads` keyword is used when shadowing by name and signature, the derived class's implementation of the member will be used instead of the implementation in the base class, and all other overloads for that member will be available to instances of the derived class.</span></span>

<span data-ttu-id="4588b-120">如果在使用具有相同參數和參數類型的成員多載繼承的成員時，會省略 `Overloads` 關鍵字，則會*依名稱*將多載稱為「遮蔽」。</span><span class="sxs-lookup"><span data-stu-id="4588b-120">If the `Overloads` keyword is omitted when overloading an inherited member with a member that has identical parameters and parameter types, then the overloading is called *shadowing by name*.</span></span> <span data-ttu-id="4588b-121">依名稱遮蔽會取代成員的繼承實作為，並讓衍生類別的實例和其 decedents 無法使用所有其他多載。</span><span class="sxs-lookup"><span data-stu-id="4588b-121">Shadowing by name replaces the inherited implementation of a member, and it makes all other overloads unavailable to instances of the derived class and its decedents.</span></span>

<span data-ttu-id="4588b-122">`Overloads` 和 `Shadows` 修飾詞不能同時用於相同的屬性或方法。</span><span class="sxs-lookup"><span data-stu-id="4588b-122">The `Overloads` and `Shadows` modifiers cannot both be used with the same property or method.</span></span>

### <a name="example"></a><span data-ttu-id="4588b-123">範例</span><span class="sxs-lookup"><span data-stu-id="4588b-123">Example</span></span>

<span data-ttu-id="4588b-124">下列範例會建立多載的方法，以接受貨幣金額的 `String` 或 `Decimal` 標記法，並傳回包含銷售稅額的字串。</span><span class="sxs-lookup"><span data-stu-id="4588b-124">The following example creates overloaded methods that accept either a `String` or `Decimal` representation of a dollar amount and return a string containing the sales tax.</span></span>

#### <a name="to-use-this-example-to-create-an-overloaded-method"></a><span data-ttu-id="4588b-125">若要使用此範例來建立多載方法</span><span class="sxs-lookup"><span data-stu-id="4588b-125">To use this example to create an overloaded method</span></span>

1. <span data-ttu-id="4588b-126">開啟新的專案，並新增名為 `TaxClass`的類別。</span><span class="sxs-lookup"><span data-stu-id="4588b-126">Open a new project and add a class named `TaxClass`.</span></span>

2. <span data-ttu-id="4588b-127">將下列程式碼加入 `TaxClass` 類別。</span><span class="sxs-lookup"><span data-stu-id="4588b-127">Add the following code to the `TaxClass` class.</span></span>

    [!code-vb[VbVbalrOOP#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#67)]

3. <span data-ttu-id="4588b-128">將下列程式新增至您的表單。</span><span class="sxs-lookup"><span data-stu-id="4588b-128">Add the following procedure to your form.</span></span>

    [!code-vb[VbVbalrOOP#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#68)]

4. <span data-ttu-id="4588b-129">將按鈕新增至表單，並從按鈕的 [`Button1_Click`] 事件呼叫 `ShowTax` 程式。</span><span class="sxs-lookup"><span data-stu-id="4588b-129">Add a button to your form and call the `ShowTax` procedure from the `Button1_Click` event of the button.</span></span>

5. <span data-ttu-id="4588b-130">執行專案，然後按一下表單上的按鈕，以測試多載的 `ShowTax` 程式。</span><span class="sxs-lookup"><span data-stu-id="4588b-130">Run the project and click the button on the form to test the overloaded `ShowTax` procedure.</span></span>

<span data-ttu-id="4588b-131">在執行時間，編譯器會選擇符合所使用之參數的適當多載函式。</span><span class="sxs-lookup"><span data-stu-id="4588b-131">At run time, the compiler chooses the appropriate overloaded function that matches the parameters being used.</span></span> <span data-ttu-id="4588b-132">當您按一下此按鈕時，會先呼叫多載的方法，並以 `Price` 參數為字串，而訊息為「價格為字串。</span><span class="sxs-lookup"><span data-stu-id="4588b-132">When you click the button, the overloaded method is called first with a `Price` parameter that is a string and the message, "Price is a String.</span></span> <span data-ttu-id="4588b-133">稅金為 $5.12」隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="4588b-133">Tax is $5.12" is displayed.</span></span> <span data-ttu-id="4588b-134">第二次使用 `Decimal` 值來呼叫 `TaxAmount`，而「價格」是十進位。</span><span class="sxs-lookup"><span data-stu-id="4588b-134">`TaxAmount` is called with a `Decimal` value the second time and the message, "Price is a Decimal.</span></span> <span data-ttu-id="4588b-135">稅金為 $5.12」隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="4588b-135">Tax is $5.12" is displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="4588b-136">請參閱</span><span class="sxs-lookup"><span data-stu-id="4588b-136">See also</span></span>

- [<span data-ttu-id="4588b-137">物件和類別</span><span class="sxs-lookup"><span data-stu-id="4588b-137">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="4588b-138">Visual Basic 中的陰影</span><span class="sxs-lookup"><span data-stu-id="4588b-138">Shadowing in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [<span data-ttu-id="4588b-139">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="4588b-139">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="4588b-140">繼承的基本概念</span><span class="sxs-lookup"><span data-stu-id="4588b-140">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="4588b-141">Shadows</span><span class="sxs-lookup"><span data-stu-id="4588b-141">Shadows</span></span>](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="4588b-142">ParamArray</span><span class="sxs-lookup"><span data-stu-id="4588b-142">ByVal</span></span>](../../../../visual-basic/language-reference/modifiers/byval.md)
- [<span data-ttu-id="4588b-143">ByRef</span><span class="sxs-lookup"><span data-stu-id="4588b-143">ByRef</span></span>](../../../../visual-basic/language-reference/modifiers/byref.md)
- [<span data-ttu-id="4588b-144">多載</span><span class="sxs-lookup"><span data-stu-id="4588b-144">Overloads</span></span>](../../../../visual-basic/language-reference/modifiers/overloads.md)
- [<span data-ttu-id="4588b-145">Shadows</span><span class="sxs-lookup"><span data-stu-id="4588b-145">Shadows</span></span>](../../../../visual-basic/language-reference/modifiers/shadows.md)
