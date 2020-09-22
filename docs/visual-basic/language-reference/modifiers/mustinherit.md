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
ms.openlocfilehash: 6502da947ae331a26e66d8ce2dbcda46e4172a6e
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867961"
---
# <a name="mustinherit-visual-basic"></a><span data-ttu-id="323cf-102">MustInherit (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="323cf-102">MustInherit (Visual Basic)</span></span>

<span data-ttu-id="323cf-103">指定類別只能當做基類使用，而且您無法直接從它建立物件。</span><span class="sxs-lookup"><span data-stu-id="323cf-103">Specifies that a class can be used only as a base class and that you cannot create an object directly from it.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="323cf-104">備註</span><span class="sxs-lookup"><span data-stu-id="323cf-104">Remarks</span></span>  

 <span data-ttu-id="323cf-105">*基類*的用途 (也稱為*抽象類別*) 是用來定義所有衍生自該類別之類別的通用功能。</span><span class="sxs-lookup"><span data-stu-id="323cf-105">The purpose of a *base class* (also known as an *abstract class*) is to define functionality that is common to all the classes derived from it.</span></span> <span data-ttu-id="323cf-106">這會儲存衍生類別，使其不需要重新定義通用元素。</span><span class="sxs-lookup"><span data-stu-id="323cf-106">This saves the derived classes from having to redefine the common elements.</span></span> <span data-ttu-id="323cf-107">在某些情況下，這種常見的功能不夠完整，無法建立可用的物件，而且每個衍生類別都會定義遺漏的功能。</span><span class="sxs-lookup"><span data-stu-id="323cf-107">In some cases, this common functionality is not complete enough to make a usable object, and each derived class defines the missing functionality.</span></span> <span data-ttu-id="323cf-108">在這種情況下，您只想要使用程式碼從衍生類別建立物件。</span><span class="sxs-lookup"><span data-stu-id="323cf-108">In such a case, you want the consuming code to create objects only from the derived classes.</span></span> <span data-ttu-id="323cf-109">您會 `MustInherit` 在基類上使用來強制執行此操作。</span><span class="sxs-lookup"><span data-stu-id="323cf-109">You use `MustInherit` on the base class to enforce this.</span></span>  
  
 <span data-ttu-id="323cf-110">類別的另一種用法 `MustInherit` 是將變數限制為一組相關的類別。</span><span class="sxs-lookup"><span data-stu-id="323cf-110">Another use of a `MustInherit` class is to restrict a variable to a set of related classes.</span></span> <span data-ttu-id="323cf-111">您可以定義基類，並從中衍生所有相關的類別。</span><span class="sxs-lookup"><span data-stu-id="323cf-111">You can define a base class and derive all these related classes from it.</span></span> <span data-ttu-id="323cf-112">基類不需要提供所有衍生類別通用的功能，但它可以做為將值指派給變數的篩選準則。</span><span class="sxs-lookup"><span data-stu-id="323cf-112">The base class does not need to provide any functionality common to all the derived classes, but it can serve as a filter for assigning values to variables.</span></span> <span data-ttu-id="323cf-113">如果您的使用程式碼將變數宣告為基類，Visual Basic 可讓您只將一個衍生類別中的物件指派給該變數。</span><span class="sxs-lookup"><span data-stu-id="323cf-113">If your consuming code declares a variable as the base class, Visual Basic allows you to assign only an object from one of the derived classes to that variable.</span></span>  
  
 <span data-ttu-id="323cf-114">.NET Framework 定義數個類別，其中包括、 `MustInherit` <xref:System.Array> <xref:System.Enum> 和 <xref:System.ValueType> 。</span><span class="sxs-lookup"><span data-stu-id="323cf-114">The .NET Framework defines several `MustInherit` classes, among them <xref:System.Array>, <xref:System.Enum>, and <xref:System.ValueType>.</span></span> <span data-ttu-id="323cf-115"><xref:System.ValueType> 是限制變數的基類範例。</span><span class="sxs-lookup"><span data-stu-id="323cf-115"><xref:System.ValueType> is an example of a base class that restricts a variable.</span></span> <span data-ttu-id="323cf-116">所有實數值型別都是衍生自 <xref:System.ValueType> 。</span><span class="sxs-lookup"><span data-stu-id="323cf-116">All value types derive from <xref:System.ValueType>.</span></span> <span data-ttu-id="323cf-117">如果您將變數宣告為 <xref:System.ValueType> ，則只能將實數值型別指派給該變數。</span><span class="sxs-lookup"><span data-stu-id="323cf-117">If you declare a variable as <xref:System.ValueType>, you can assign only value types to that variable.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="323cf-118">規則</span><span class="sxs-lookup"><span data-stu-id="323cf-118">Rules</span></span>  
  
- <span data-ttu-id="323cf-119">**宣告內容。**</span><span class="sxs-lookup"><span data-stu-id="323cf-119">**Declaration Context.**</span></span> <span data-ttu-id="323cf-120">您 `MustInherit` 只能在語句中使用 `Class` 。</span><span class="sxs-lookup"><span data-stu-id="323cf-120">You can use `MustInherit` only in a `Class` statement.</span></span>  
  
- <span data-ttu-id="323cf-121">**結合的修飾詞。**</span><span class="sxs-lookup"><span data-stu-id="323cf-121">**Combined Modifiers.**</span></span> <span data-ttu-id="323cf-122">您無法 `MustInherit` `NotInheritable` 在相同的宣告中同時指定。</span><span class="sxs-lookup"><span data-stu-id="323cf-122">You cannot specify `MustInherit` together with `NotInheritable` in the same declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="323cf-123">範例</span><span class="sxs-lookup"><span data-stu-id="323cf-123">Example</span></span>  

 <span data-ttu-id="323cf-124">下列範例說明強制繼承和強制覆寫。</span><span class="sxs-lookup"><span data-stu-id="323cf-124">The following example illustrates both forced inheritance and forced overriding.</span></span> <span data-ttu-id="323cf-125">基底類別會 `shape` 定義變數 `acrossLine` 。</span><span class="sxs-lookup"><span data-stu-id="323cf-125">The base class `shape` defines a variable `acrossLine`.</span></span> <span data-ttu-id="323cf-126">類別 `circle` 和 `square` 衍生自 `shape` 。</span><span class="sxs-lookup"><span data-stu-id="323cf-126">The classes `circle` and `square` derive from `shape`.</span></span> <span data-ttu-id="323cf-127">它們會繼承的定義 `acrossLine` ，但必須定義函數， `area` 因為每種形狀的計算都不同。</span><span class="sxs-lookup"><span data-stu-id="323cf-127">They inherit the definition of `acrossLine`, but they must define the function `area` because that calculation is different for each kind of shape.</span></span>  
  
 [!code-vb[VbVbalrKeywords#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#2)]  
  
 <span data-ttu-id="323cf-128">您可以 `shape1` 將和宣告為 `shape2` 類型 `shape` 。</span><span class="sxs-lookup"><span data-stu-id="323cf-128">You can declare `shape1` and `shape2` to be of type `shape`.</span></span> <span data-ttu-id="323cf-129">不過，您無法從建立物件， `shape` 因為它缺少函式的功能 `area` 且已標示 `MustInherit` 。</span><span class="sxs-lookup"><span data-stu-id="323cf-129">However, you cannot create an object from `shape` because it lacks the functionality of the function `area` and is marked `MustInherit`.</span></span>  
  
 <span data-ttu-id="323cf-130">因為它們是宣告為 `shape` ，所以變數 `shape1` 和 `shape2` 會限制為衍生類別和的物件 `circle` `square` 。</span><span class="sxs-lookup"><span data-stu-id="323cf-130">Because they are declared as `shape`, the variables `shape1` and `shape2` are restricted to objects from the derived classes `circle` and `square`.</span></span> <span data-ttu-id="323cf-131">Visual Basic 不允許您將任何其他物件指派給這些變數，以提供高層級的安全性。</span><span class="sxs-lookup"><span data-stu-id="323cf-131">Visual Basic does not allow you to assign any other object to these variables, which gives you a high level of type safety.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="323cf-132">使用方式</span><span class="sxs-lookup"><span data-stu-id="323cf-132">Usage</span></span>  

 <span data-ttu-id="323cf-133">`MustInherit`修飾詞可用於此內容中：</span><span class="sxs-lookup"><span data-stu-id="323cf-133">The `MustInherit` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="323cf-134">Class 陳述式</span><span class="sxs-lookup"><span data-stu-id="323cf-134">Class Statement</span></span>](../statements/class-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="323cf-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="323cf-135">See also</span></span>

- [<span data-ttu-id="323cf-136">Inherits Statement</span><span class="sxs-lookup"><span data-stu-id="323cf-136">Inherits Statement</span></span>](../statements/inherits-statement.md)
- [<span data-ttu-id="323cf-137">NotInheritable</span><span class="sxs-lookup"><span data-stu-id="323cf-137">NotInheritable</span></span>](notinheritable.md)
- [<span data-ttu-id="323cf-138">關鍵字</span><span class="sxs-lookup"><span data-stu-id="323cf-138">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="323cf-139">繼承基本概念</span><span class="sxs-lookup"><span data-stu-id="323cf-139">Inheritance Basics</span></span>](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
