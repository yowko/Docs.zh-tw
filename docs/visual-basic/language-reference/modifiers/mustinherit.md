---
title: MustInherit
ms.date: 07/20/2015
f1_keywords:
- MustInherit
- vb.MustInherit
helpviewer_keywords:
- classes [Visual Basic], abstract
- MustInherit classes [Visual Basic], MustInherit keyword
- abstract classes [Visual Basic], MustInherit class
- MustInherit keyword [Visual Basic]
ms.assetid: b8f05185-90e3-4dd7-adc2-90d852fab5b4
ms.openlocfilehash: 30befaaf194d78d26a57f29c59bf0a603e9f07a3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351502"
---
# <a name="mustinherit-visual-basic"></a><span data-ttu-id="81510-102">MustInherit (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="81510-102">MustInherit (Visual Basic)</span></span>
<span data-ttu-id="81510-103">指定類別只能當做基類使用，而且您無法直接從它建立物件。</span><span class="sxs-lookup"><span data-stu-id="81510-103">Specifies that a class can be used only as a base class and that you cannot create an object directly from it.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="81510-104">備註</span><span class="sxs-lookup"><span data-stu-id="81510-104">Remarks</span></span>  
 <span data-ttu-id="81510-105">*基類*（也稱為*抽象類別*）的目的，是要定義所有衍生自它的類別通用的功能。</span><span class="sxs-lookup"><span data-stu-id="81510-105">The purpose of a *base class* (also known as an *abstract class*) is to define functionality that is common to all the classes derived from it.</span></span> <span data-ttu-id="81510-106">如此一來，衍生的類別就必須重新定義通用元素。</span><span class="sxs-lookup"><span data-stu-id="81510-106">This saves the derived classes from having to redefine the common elements.</span></span> <span data-ttu-id="81510-107">在某些情況下，這個常見的功能並不足以建立可用的物件，而每個衍生的類別會定義遺漏的功能。</span><span class="sxs-lookup"><span data-stu-id="81510-107">In some cases, this common functionality is not complete enough to make a usable object, and each derived class defines the missing functionality.</span></span> <span data-ttu-id="81510-108">在這種情況下，您會想要使用的程式碼只從衍生類別建立物件。</span><span class="sxs-lookup"><span data-stu-id="81510-108">In such a case, you want the consuming code to create objects only from the derived classes.</span></span> <span data-ttu-id="81510-109">您會在基類上使用 `MustInherit` 來強制執行此操作。</span><span class="sxs-lookup"><span data-stu-id="81510-109">You use `MustInherit` on the base class to enforce this.</span></span>  
  
 <span data-ttu-id="81510-110">`MustInherit` 類別的另一個用法是將變數限制為一組相關的類別。</span><span class="sxs-lookup"><span data-stu-id="81510-110">Another use of a `MustInherit` class is to restrict a variable to a set of related classes.</span></span> <span data-ttu-id="81510-111">您可以定義基類，並從該類別衍生所有相關的類別。</span><span class="sxs-lookup"><span data-stu-id="81510-111">You can define a base class and derive all these related classes from it.</span></span> <span data-ttu-id="81510-112">基類不需要提供所有衍生類別通用的任何功能，但它可以做為將值指派給變數的篩選準則。</span><span class="sxs-lookup"><span data-stu-id="81510-112">The base class does not need to provide any functionality common to all the derived classes, but it can serve as a filter for assigning values to variables.</span></span> <span data-ttu-id="81510-113">如果您的取用程式碼將變數宣告為基類，Visual Basic 可讓您只將一個衍生類別中的物件指派給該變數。</span><span class="sxs-lookup"><span data-stu-id="81510-113">If your consuming code declares a variable as the base class, Visual Basic allows you to assign only an object from one of the derived classes to that variable.</span></span>  
  
 <span data-ttu-id="81510-114">.NET Framework 會定義數個 `MustInherit` 類別，其中 <xref:System.Array>、<xref:System.Enum>和 <xref:System.ValueType>。</span><span class="sxs-lookup"><span data-stu-id="81510-114">The .NET Framework defines several `MustInherit` classes, among them <xref:System.Array>, <xref:System.Enum>, and <xref:System.ValueType>.</span></span> <span data-ttu-id="81510-115"><xref:System.ValueType> 是限制變數之基類的範例。</span><span class="sxs-lookup"><span data-stu-id="81510-115"><xref:System.ValueType> is an example of a base class that restricts a variable.</span></span> <span data-ttu-id="81510-116">所有實值型別都是衍生自 <xref:System.ValueType>。</span><span class="sxs-lookup"><span data-stu-id="81510-116">All value types derive from <xref:System.ValueType>.</span></span> <span data-ttu-id="81510-117">如果您將變數宣告為 <xref:System.ValueType>，就只能將實數值型別指派給該變數。</span><span class="sxs-lookup"><span data-stu-id="81510-117">If you declare a variable as <xref:System.ValueType>, you can assign only value types to that variable.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="81510-118">規則</span><span class="sxs-lookup"><span data-stu-id="81510-118">Rules</span></span>  
  
- <span data-ttu-id="81510-119">**宣告內容。**</span><span class="sxs-lookup"><span data-stu-id="81510-119">**Declaration Context.**</span></span> <span data-ttu-id="81510-120">您只能在 `Class` 語句中使用 `MustInherit`。</span><span class="sxs-lookup"><span data-stu-id="81510-120">You can use `MustInherit` only in a `Class` statement.</span></span>  
  
- <span data-ttu-id="81510-121">**合併的修飾詞。**</span><span class="sxs-lookup"><span data-stu-id="81510-121">**Combined Modifiers.**</span></span> <span data-ttu-id="81510-122">您不能在相同的宣告中同時指定與 `NotInheritable` `MustInherit`。</span><span class="sxs-lookup"><span data-stu-id="81510-122">You cannot specify `MustInherit` together with `NotInheritable` in the same declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="81510-123">範例</span><span class="sxs-lookup"><span data-stu-id="81510-123">Example</span></span>  
 <span data-ttu-id="81510-124">下列範例說明強制繼承和強制覆寫。</span><span class="sxs-lookup"><span data-stu-id="81510-124">The following example illustrates both forced inheritance and forced overriding.</span></span> <span data-ttu-id="81510-125">基底類別 `shape` 定義變數 `acrossLine`。</span><span class="sxs-lookup"><span data-stu-id="81510-125">The base class `shape` defines a variable `acrossLine`.</span></span> <span data-ttu-id="81510-126">`circle` 和 `square` 衍生自 `shape`的類別。</span><span class="sxs-lookup"><span data-stu-id="81510-126">The classes `circle` and `square` derive from `shape`.</span></span> <span data-ttu-id="81510-127">它們會繼承 `acrossLine`的定義，但是必須定義函式 `area`，因為每一種形狀的計算都不同。</span><span class="sxs-lookup"><span data-stu-id="81510-127">They inherit the definition of `acrossLine`, but they must define the function `area` because that calculation is different for each kind of shape.</span></span>  
  
 [!code-vb[VbVbalrKeywords#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#2)]  
  
 <span data-ttu-id="81510-128">您可以宣告 `shape1`，並 `shape2` `shape`的類型。</span><span class="sxs-lookup"><span data-stu-id="81510-128">You can declare `shape1` and `shape2` to be of type `shape`.</span></span> <span data-ttu-id="81510-129">不過，您無法從 `shape` 建立物件，因為它缺少函式 `area` 的功能，而且已標記為 `MustInherit`。</span><span class="sxs-lookup"><span data-stu-id="81510-129">However, you cannot create an object from `shape` because it lacks the functionality of the function `area` and is marked `MustInherit`.</span></span>  
  
 <span data-ttu-id="81510-130">因為它們宣告為 `shape`，`shape1` 和 `shape2` 的變數會限制為衍生類別 `circle` 和 `square`中的物件。</span><span class="sxs-lookup"><span data-stu-id="81510-130">Because they are declared as `shape`, the variables `shape1` and `shape2` are restricted to objects from the derived classes `circle` and `square`.</span></span> <span data-ttu-id="81510-131">Visual Basic 不允許您將任何其他物件指派給這些變數，這會提供高階的型別安全。</span><span class="sxs-lookup"><span data-stu-id="81510-131">Visual Basic does not allow you to assign any other object to these variables, which gives you a high level of type safety.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="81510-132">使用方式</span><span class="sxs-lookup"><span data-stu-id="81510-132">Usage</span></span>  
 <span data-ttu-id="81510-133">`MustInherit` 修飾詞可以在此內容中使用：</span><span class="sxs-lookup"><span data-stu-id="81510-133">The `MustInherit` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="81510-134">Class 陳述式</span><span class="sxs-lookup"><span data-stu-id="81510-134">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="81510-135">請參閱</span><span class="sxs-lookup"><span data-stu-id="81510-135">See also</span></span>

- [<span data-ttu-id="81510-136">Inherits 陳述式</span><span class="sxs-lookup"><span data-stu-id="81510-136">Inherits Statement</span></span>](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="81510-137">NotInheritable</span><span class="sxs-lookup"><span data-stu-id="81510-137">NotInheritable</span></span>](../../../visual-basic/language-reference/modifiers/notinheritable.md)
- [<span data-ttu-id="81510-138">關鍵字</span><span class="sxs-lookup"><span data-stu-id="81510-138">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="81510-139">繼承的基本概念</span><span class="sxs-lookup"><span data-stu-id="81510-139">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
