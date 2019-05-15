---
title: 抽象類別
description: 深入了解F#抽象類別，讓所有或部分成員未提供，而且代表多樣化的物件類型的一般功能。
ms.date: 05/16/2016
ms.openlocfilehash: 8251d481c9056d40a0b13ae3c89353406986c116
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645554"
---
# <a name="abstract-classes"></a><span data-ttu-id="11b6e-103">抽象類別</span><span class="sxs-lookup"><span data-stu-id="11b6e-103">Abstract Classes</span></span>

<span data-ttu-id="11b6e-104">*抽象類別*會保留所有或部分成員未提供，以便可以提供實作，由衍生類別的類別。</span><span class="sxs-lookup"><span data-stu-id="11b6e-104">*Abstract classes* are classes that leave some or all members unimplemented, so that implementations can be provided by derived classes.</span></span>

## <a name="syntax"></a><span data-ttu-id="11b6e-105">語法</span><span class="sxs-lookup"><span data-stu-id="11b6e-105">Syntax</span></span>

```fsharp
// Abstract class syntax.
[<AbstractClass>]
type [ accessibility-modifier ] abstract-class-name =
[ inherit base-class-or-interface-name ]
[ abstract-member-declarations-and-member-definitions ]

// Abstract member syntax.
abstract member member-name : type-signature
```

## <a name="remarks"></a><span data-ttu-id="11b6e-106">備註</span><span class="sxs-lookup"><span data-stu-id="11b6e-106">Remarks</span></span>

<span data-ttu-id="11b6e-107">在物件導向程式設計中，抽象類別做為階層中，基底類別，並代表各種不同的一組物件類型的一般功能。</span><span class="sxs-lookup"><span data-stu-id="11b6e-107">In object-oriented programming, an abstract class is used as a base class of a hierarchy, and represents common functionality of a diverse set of object types.</span></span> <span data-ttu-id="11b6e-108">正如其名稱 「 抽象 」，抽象類別通常未對應到的問題領域中的具象實體直接。</span><span class="sxs-lookup"><span data-stu-id="11b6e-108">As the name "abstract" implies, abstract classes often do not correspond directly onto concrete entities in the problem domain.</span></span> <span data-ttu-id="11b6e-109">不過，它們並代表什麼許多不同的具象實體有共通。</span><span class="sxs-lookup"><span data-stu-id="11b6e-109">However, they do represent what many different concrete entities have in common.</span></span>

<span data-ttu-id="11b6e-110">抽象類別必須具有`AbstractClass`屬性。</span><span class="sxs-lookup"><span data-stu-id="11b6e-110">Abstract classes must have the `AbstractClass` attribute.</span></span> <span data-ttu-id="11b6e-111">它們可以實作而且未提供的成員。</span><span class="sxs-lookup"><span data-stu-id="11b6e-111">They can have implemented and unimplemented members.</span></span> <span data-ttu-id="11b6e-112">一詞的用法*抽象*套用至類別時，與其他.NET 語言; 相同不過，一詞的用法*抽象*時套用至方法 （和屬性） 會稍有不同的F#從其他.NET 語言中使用。</span><span class="sxs-lookup"><span data-stu-id="11b6e-112">The use of the term *abstract* when applied to a class is the same as in other .NET languages; however, the use of the term *abstract* when applied to methods (and properties) is a little different in F# from its use in other .NET languages.</span></span> <span data-ttu-id="11b6e-113">在F#，當方法會標示`abstract`關鍵字，這表示成員的項目，稱為*虛擬分派介面槽*，該類型的虛擬函式的內部資料表中。</span><span class="sxs-lookup"><span data-stu-id="11b6e-113">In F#, when a method is marked with the `abstract` keyword, this indicates that a member has an entry, known as a *virtual dispatch slot*, in the internal table of virtual functions for that type.</span></span> <span data-ttu-id="11b6e-114">換句話說，方法是虛擬的雖然`virtual`關鍵字不會在F#語言。</span><span class="sxs-lookup"><span data-stu-id="11b6e-114">In other words, the method is virtual, although the `virtual` keyword is not used in the F# language.</span></span> <span data-ttu-id="11b6e-115">關鍵字`abstract`虛擬方法，不論是否方法在實作上使用。</span><span class="sxs-lookup"><span data-stu-id="11b6e-115">The keyword `abstract` is used on virtual methods regardless of whether the method is implemented.</span></span> <span data-ttu-id="11b6e-116">虛擬分派位置的宣告，都是方法的獨立於該發送位置定義。</span><span class="sxs-lookup"><span data-stu-id="11b6e-116">The declaration of a virtual dispatch slot is separate from the definition of a method for that dispatch slot.</span></span> <span data-ttu-id="11b6e-117">因此，F#虛擬方法宣告和定義在另一種.NET 語言中的等同項目是抽象方法宣告和不同的定義，使用的組合`default`關鍵字或`override`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="11b6e-117">Therefore, the F# equivalent of a virtual method declaration and definition in another .NET language is a combination of both an abstract method declaration and a separate definition, with either the `default` keyword or the `override` keyword.</span></span> <span data-ttu-id="11b6e-118">如需詳細資訊和範例，請參閱 <<c0> [ 方法](members/methods.md)。</span><span class="sxs-lookup"><span data-stu-id="11b6e-118">For more information and examples, see [Methods](members/methods.md).</span></span>

<span data-ttu-id="11b6e-119">類別之所以被視為只有在已宣告但未定義的抽象方法的抽象的。</span><span class="sxs-lookup"><span data-stu-id="11b6e-119">A class is considered abstract only if there are abstract methods that are declared but not defined.</span></span> <span data-ttu-id="11b6e-120">因此，具有抽象方法的類別不一定是抽象類別。</span><span class="sxs-lookup"><span data-stu-id="11b6e-120">Therefore, classes that have abstract methods are not necessarily abstract classes.</span></span> <span data-ttu-id="11b6e-121">不使用類別中有未定義的抽象方法，除非**AbstractClass**屬性。</span><span class="sxs-lookup"><span data-stu-id="11b6e-121">Unless a class has undefined abstract methods, do not use the **AbstractClass** attribute.</span></span>

<span data-ttu-id="11b6e-122">在先前的語法*存取範圍修飾詞*可以是`public`，`private`或`internal`。</span><span class="sxs-lookup"><span data-stu-id="11b6e-122">In the previous syntax, *accessibility-modifier* can be `public`, `private` or `internal`.</span></span> <span data-ttu-id="11b6e-123">如需詳細資訊，請參閱[存取控制](access-control.md)。</span><span class="sxs-lookup"><span data-stu-id="11b6e-123">For more information, see [Access Control](access-control.md).</span></span>

<span data-ttu-id="11b6e-124">如同其他類型中，抽象類別可以有基底類別和一或多個基底介面。</span><span class="sxs-lookup"><span data-stu-id="11b6e-124">As with other types, abstract classes can have a base class and one or more base interfaces.</span></span> <span data-ttu-id="11b6e-125">每個基底類別或介面會出現在不同的行，並搭配`inherit`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="11b6e-125">Each base class or interface appears on a separate line together with the `inherit` keyword.</span></span>

<span data-ttu-id="11b6e-126">抽象類別的型別定義可以包含完整定義的成員，但它也可以包含抽象成員。</span><span class="sxs-lookup"><span data-stu-id="11b6e-126">The type definition of an abstract class can contain fully defined members, but it can also contain abstract members.</span></span> <span data-ttu-id="11b6e-127">抽象成員的語法分別顯示在先前的語法。</span><span class="sxs-lookup"><span data-stu-id="11b6e-127">The syntax for abstract members is shown separately in the previous syntax.</span></span> <span data-ttu-id="11b6e-128">在這個語法中，*型別簽章*成員的清單，其中包含參數和類型的順序傳回型別，以分隔`->`語彙基元和/或`*`權杖來作為適當的局部調用和 tuple參數。</span><span class="sxs-lookup"><span data-stu-id="11b6e-128">In this syntax, the *type signature* of a member is a list that contains the parameter types in order and the return types, separated by `->` tokens and/or `*` tokens as appropriate for curried and tupled parameters.</span></span> <span data-ttu-id="11b6e-129">抽象成員型別簽章的語法是相同簽章檔案中使用，而且在 Visual Studio 程式碼編輯器中 intellisense 所示。</span><span class="sxs-lookup"><span data-stu-id="11b6e-129">The syntax for abstract member type signatures is the same as that used in signature files and that shown by IntelliSense in the Visual Studio Code Editor.</span></span>

<span data-ttu-id="11b6e-130">下列程式碼說明的抽象類別圖形，有兩個非抽象衍生的類別，正方形和圓形。</span><span class="sxs-lookup"><span data-stu-id="11b6e-130">The following code illustrates an abstract class Shape, which has two non-abstract derived classes, Square and Circle.</span></span> <span data-ttu-id="11b6e-131">此範例示範如何使用抽象類別、 方法和屬性。</span><span class="sxs-lookup"><span data-stu-id="11b6e-131">The example shows how to use abstract classes, methods, and properties.</span></span> <span data-ttu-id="11b6e-132">在範例中，抽象類別圖形表示的具象實體圓形和正方形的一般元素。</span><span class="sxs-lookup"><span data-stu-id="11b6e-132">In the example, the abstract class Shape represents the common elements of the concrete entities circle and square.</span></span> <span data-ttu-id="11b6e-133">（在二維的座標系統） 的所有圖形的常見功能抽取出 Shape 類別： 方格、 旋轉的角度和面積和周長屬性上的位置。</span><span class="sxs-lookup"><span data-stu-id="11b6e-133">The common features of all shapes (in a two-dimensional coordinate system) are abstracted out into the Shape class: the position on the grid, an angle of rotation, and the area and perimeter properties.</span></span> <span data-ttu-id="11b6e-134">這些可以被覆寫，除了位置，其中個別圖形不能變更的行為。</span><span class="sxs-lookup"><span data-stu-id="11b6e-134">These can be overridden, except for position, the behavior of which individual shapes cannot change.</span></span>

<span data-ttu-id="11b6e-135">旋轉方法可以覆寫，如同 Circle 類別中，這是因為其對稱的旋轉而異。</span><span class="sxs-lookup"><span data-stu-id="11b6e-135">The rotation method can be overridden, as in the Circle class, which is rotation invariant because of its symmetry.</span></span> <span data-ttu-id="11b6e-136">因此在 Circle 類別中，旋轉方法會取代不執行任何動作的方法。</span><span class="sxs-lookup"><span data-stu-id="11b6e-136">So in the Circle class, the rotation method is replaced by a method that does nothing.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2901.fs)]

<span data-ttu-id="11b6e-137">**輸出：**</span><span class="sxs-lookup"><span data-stu-id="11b6e-137">**Output:**</span></span>

```
Perimeter of square with side length 10.000000 is 40.000000
Circumference of circle with radius 5.000000 is 31.415927
Area of Square: 100.000000
Area of Circle: 78.539816
```

## <a name="see-also"></a><span data-ttu-id="11b6e-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="11b6e-138">See also</span></span>

- [<span data-ttu-id="11b6e-139">類別</span><span class="sxs-lookup"><span data-stu-id="11b6e-139">Classes</span></span>](classes.md)
- [<span data-ttu-id="11b6e-140">成員</span><span class="sxs-lookup"><span data-stu-id="11b6e-140">Members</span></span>](members/index.md)
- [<span data-ttu-id="11b6e-141">方法</span><span class="sxs-lookup"><span data-stu-id="11b6e-141">Methods</span></span>](members/methods.md)
- [<span data-ttu-id="11b6e-142">屬性</span><span class="sxs-lookup"><span data-stu-id="11b6e-142">Properties</span></span>](members/Properties.md)
