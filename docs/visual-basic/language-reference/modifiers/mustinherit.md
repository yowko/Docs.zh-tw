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
ms.openlocfilehash: 84df7a5cfdad3b5bc6764675725a5d0cb402b0b7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396203"
---
# <a name="mustinherit-visual-basic"></a><span data-ttu-id="76caa-102">MustInherit (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="76caa-102">MustInherit (Visual Basic)</span></span>
<span data-ttu-id="76caa-103">指定類別只能當做基類使用，而且您無法直接從它建立物件。</span><span class="sxs-lookup"><span data-stu-id="76caa-103">Specifies that a class can be used only as a base class and that you cannot create an object directly from it.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="76caa-104">備註</span><span class="sxs-lookup"><span data-stu-id="76caa-104">Remarks</span></span>  
 <span data-ttu-id="76caa-105">*基類*（也稱為*抽象類別*）的目的，是要定義所有衍生自它的類別通用的功能。</span><span class="sxs-lookup"><span data-stu-id="76caa-105">The purpose of a *base class* (also known as an *abstract class*) is to define functionality that is common to all the classes derived from it.</span></span> <span data-ttu-id="76caa-106">如此一來，衍生的類別就必須重新定義通用元素。</span><span class="sxs-lookup"><span data-stu-id="76caa-106">This saves the derived classes from having to redefine the common elements.</span></span> <span data-ttu-id="76caa-107">在某些情況下，這個常見的功能並不足以建立可用的物件，而每個衍生的類別會定義遺漏的功能。</span><span class="sxs-lookup"><span data-stu-id="76caa-107">In some cases, this common functionality is not complete enough to make a usable object, and each derived class defines the missing functionality.</span></span> <span data-ttu-id="76caa-108">在這種情況下，您會想要使用的程式碼只從衍生類別建立物件。</span><span class="sxs-lookup"><span data-stu-id="76caa-108">In such a case, you want the consuming code to create objects only from the derived classes.</span></span> <span data-ttu-id="76caa-109">您會 `MustInherit` 在基類上使用來強制執行此操作。</span><span class="sxs-lookup"><span data-stu-id="76caa-109">You use `MustInherit` on the base class to enforce this.</span></span>  
  
 <span data-ttu-id="76caa-110">類別的另一個用法 `MustInherit` 是將變數限制為一組相關的類別。</span><span class="sxs-lookup"><span data-stu-id="76caa-110">Another use of a `MustInherit` class is to restrict a variable to a set of related classes.</span></span> <span data-ttu-id="76caa-111">您可以定義基類，並從該類別衍生所有相關的類別。</span><span class="sxs-lookup"><span data-stu-id="76caa-111">You can define a base class and derive all these related classes from it.</span></span> <span data-ttu-id="76caa-112">基類不需要提供所有衍生類別通用的任何功能，但它可以做為將值指派給變數的篩選準則。</span><span class="sxs-lookup"><span data-stu-id="76caa-112">The base class does not need to provide any functionality common to all the derived classes, but it can serve as a filter for assigning values to variables.</span></span> <span data-ttu-id="76caa-113">如果您的取用程式碼將變數宣告為基類，Visual Basic 可讓您只將一個衍生類別中的物件指派給該變數。</span><span class="sxs-lookup"><span data-stu-id="76caa-113">If your consuming code declares a variable as the base class, Visual Basic allows you to assign only an object from one of the derived classes to that variable.</span></span>  
  
 <span data-ttu-id="76caa-114">.NET Framework 會定義數個 `MustInherit` 類別，其中包括 <xref:System.Array> 、 <xref:System.Enum> 和 <xref:System.ValueType> 。</span><span class="sxs-lookup"><span data-stu-id="76caa-114">The .NET Framework defines several `MustInherit` classes, among them <xref:System.Array>, <xref:System.Enum>, and <xref:System.ValueType>.</span></span> <span data-ttu-id="76caa-115"><xref:System.ValueType>是限制變數的基類範例。</span><span class="sxs-lookup"><span data-stu-id="76caa-115"><xref:System.ValueType> is an example of a base class that restricts a variable.</span></span> <span data-ttu-id="76caa-116">所有實值型別都是衍生自 <xref:System.ValueType> 。</span><span class="sxs-lookup"><span data-stu-id="76caa-116">All value types derive from <xref:System.ValueType>.</span></span> <span data-ttu-id="76caa-117">如果您將變數宣告為 <xref:System.ValueType> ，則只能將實數值型別指派給該變數。</span><span class="sxs-lookup"><span data-stu-id="76caa-117">If you declare a variable as <xref:System.ValueType>, you can assign only value types to that variable.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="76caa-118">規則</span><span class="sxs-lookup"><span data-stu-id="76caa-118">Rules</span></span>  
  
- <span data-ttu-id="76caa-119">**宣告內容。**</span><span class="sxs-lookup"><span data-stu-id="76caa-119">**Declaration Context.**</span></span> <span data-ttu-id="76caa-120">您 `MustInherit` 只能在語句中使用 `Class` 。</span><span class="sxs-lookup"><span data-stu-id="76caa-120">You can use `MustInherit` only in a `Class` statement.</span></span>  
  
- <span data-ttu-id="76caa-121">**結合的修飾詞。**</span><span class="sxs-lookup"><span data-stu-id="76caa-121">**Combined Modifiers.**</span></span> <span data-ttu-id="76caa-122">您不能 `MustInherit` 在相同的宣告中同時指定與 `NotInheritable` 。</span><span class="sxs-lookup"><span data-stu-id="76caa-122">You cannot specify `MustInherit` together with `NotInheritable` in the same declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76caa-123">範例</span><span class="sxs-lookup"><span data-stu-id="76caa-123">Example</span></span>  
 <span data-ttu-id="76caa-124">下列範例說明強制繼承和強制覆寫。</span><span class="sxs-lookup"><span data-stu-id="76caa-124">The following example illustrates both forced inheritance and forced overriding.</span></span> <span data-ttu-id="76caa-125">基類會 `shape` 定義一個變數 `acrossLine` 。</span><span class="sxs-lookup"><span data-stu-id="76caa-125">The base class `shape` defines a variable `acrossLine`.</span></span> <span data-ttu-id="76caa-126">`circle`和 `square` 衍生自的類別 `shape` 。</span><span class="sxs-lookup"><span data-stu-id="76caa-126">The classes `circle` and `square` derive from `shape`.</span></span> <span data-ttu-id="76caa-127">它們會繼承的定義 `acrossLine` ，但是它們必須定義函式， `area` 因為每一種形狀的計算都不同。</span><span class="sxs-lookup"><span data-stu-id="76caa-127">They inherit the definition of `acrossLine`, but they must define the function `area` because that calculation is different for each kind of shape.</span></span>  
  
 [!code-vb[VbVbalrKeywords#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#2)]  
  
 <span data-ttu-id="76caa-128">您可以 `shape1` 將和宣告為 `shape2` 類型 `shape` 。</span><span class="sxs-lookup"><span data-stu-id="76caa-128">You can declare `shape1` and `shape2` to be of type `shape`.</span></span> <span data-ttu-id="76caa-129">不過，您無法從建立物件， `shape` 因為它缺少函式的功能 `area` ，而且已標示為 `MustInherit` 。</span><span class="sxs-lookup"><span data-stu-id="76caa-129">However, you cannot create an object from `shape` because it lacks the functionality of the function `area` and is marked `MustInherit`.</span></span>  
  
 <span data-ttu-id="76caa-130">因為它們宣告為 `shape` ，所以變數 `shape1` 和僅 `shape2` 限於衍生類別和中的物件 `circle` `square` 。</span><span class="sxs-lookup"><span data-stu-id="76caa-130">Because they are declared as `shape`, the variables `shape1` and `shape2` are restricted to objects from the derived classes `circle` and `square`.</span></span> <span data-ttu-id="76caa-131">Visual Basic 不允許您將任何其他物件指派給這些變數，這會提供高階的型別安全。</span><span class="sxs-lookup"><span data-stu-id="76caa-131">Visual Basic does not allow you to assign any other object to these variables, which gives you a high level of type safety.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="76caa-132">使用方式</span><span class="sxs-lookup"><span data-stu-id="76caa-132">Usage</span></span>  
 <span data-ttu-id="76caa-133">`MustInherit`修飾詞可以在此內容中使用：</span><span class="sxs-lookup"><span data-stu-id="76caa-133">The `MustInherit` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="76caa-134">Class 陳述式</span><span class="sxs-lookup"><span data-stu-id="76caa-134">Class Statement</span></span>](../statements/class-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="76caa-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="76caa-135">See also</span></span>

- [<span data-ttu-id="76caa-136">Inherits Statement</span><span class="sxs-lookup"><span data-stu-id="76caa-136">Inherits Statement</span></span>](../statements/inherits-statement.md)
- [<span data-ttu-id="76caa-137">NotInheritable</span><span class="sxs-lookup"><span data-stu-id="76caa-137">NotInheritable</span></span>](notinheritable.md)
- [<span data-ttu-id="76caa-138">關鍵字</span><span class="sxs-lookup"><span data-stu-id="76caa-138">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="76caa-139">繼承基本概念</span><span class="sxs-lookup"><span data-stu-id="76caa-139">Inheritance Basics</span></span>](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
