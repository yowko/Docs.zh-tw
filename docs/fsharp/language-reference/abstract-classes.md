---
title: 抽象類別
description: 瞭解F#抽象類別, 使部分或所有成員不會被啟用, 並代表一組不同物件類型的一般功能。
ms.date: 05/16/2016
ms.openlocfilehash: a6bbfc23b858d5f3833f3f52b6dca46753080f03
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629675"
---
# <a name="abstract-classes"></a><span data-ttu-id="2bb74-103">抽象類別</span><span class="sxs-lookup"><span data-stu-id="2bb74-103">Abstract Classes</span></span>

<span data-ttu-id="2bb74-104">*抽象類別*是讓部分或所有成員不會執行的類別, 以便讓衍生類別能夠提供執行。</span><span class="sxs-lookup"><span data-stu-id="2bb74-104">*Abstract classes* are classes that leave some or all members unimplemented, so that implementations can be provided by derived classes.</span></span>

## <a name="syntax"></a><span data-ttu-id="2bb74-105">語法</span><span class="sxs-lookup"><span data-stu-id="2bb74-105">Syntax</span></span>

```fsharp
// Abstract class syntax.
[<AbstractClass>]
type [ accessibility-modifier ] abstract-class-name =
[ inherit base-class-or-interface-name ]
[ abstract-member-declarations-and-member-definitions ]

// Abstract member syntax.
abstract member member-name : type-signature
```

## <a name="remarks"></a><span data-ttu-id="2bb74-106">備註</span><span class="sxs-lookup"><span data-stu-id="2bb74-106">Remarks</span></span>

<span data-ttu-id="2bb74-107">在物件導向程式設計中, 抽象類別會當做階層的基類使用, 並代表一組不同物件類型的一般功能。</span><span class="sxs-lookup"><span data-stu-id="2bb74-107">In object-oriented programming, an abstract class is used as a base class of a hierarchy, and represents common functionality of a diverse set of object types.</span></span> <span data-ttu-id="2bb74-108">顧名思義, 抽象類別通常不會直接對應到問題網域中的具體實體。</span><span class="sxs-lookup"><span data-stu-id="2bb74-108">As the name "abstract" implies, abstract classes often do not correspond directly onto concrete entities in the problem domain.</span></span> <span data-ttu-id="2bb74-109">不過, 它們確實代表有多少不同的具體實體具有共同的功能。</span><span class="sxs-lookup"><span data-stu-id="2bb74-109">However, they do represent what many different concrete entities have in common.</span></span>

<span data-ttu-id="2bb74-110">抽象類別必須具有`AbstractClass`屬性。</span><span class="sxs-lookup"><span data-stu-id="2bb74-110">Abstract classes must have the `AbstractClass` attribute.</span></span> <span data-ttu-id="2bb74-111">它們可以有已實和未執行的成員。</span><span class="sxs-lookup"><span data-stu-id="2bb74-111">They can have implemented and unimplemented members.</span></span> <span data-ttu-id="2bb74-112">套用至類別時, 使用「*抽象*」一詞, 與其他 .net 語言相同。不過, 套用至方法 (和屬性) 時, 使用「抽象」 ( *abstract* ) 一詞與F#其他 .net 語言中的使用方式稍有不同。</span><span class="sxs-lookup"><span data-stu-id="2bb74-112">The use of the term *abstract* when applied to a class is the same as in other .NET languages; however, the use of the term *abstract* when applied to methods (and properties) is a little different in F# from its use in other .NET languages.</span></span> <span data-ttu-id="2bb74-113">在F#中, 當方法以`abstract`關鍵字標記時, 這表示成員在該類型的虛擬函式的內部資料表中有一個專案, 稱為「*虛擬分派插槽*」。</span><span class="sxs-lookup"><span data-stu-id="2bb74-113">In F#, when a method is marked with the `abstract` keyword, this indicates that a member has an entry, known as a *virtual dispatch slot*, in the internal table of virtual functions for that type.</span></span> <span data-ttu-id="2bb74-114">換句話說, 方法是虛擬的, 但是`virtual`在F#語言中不使用關鍵字。</span><span class="sxs-lookup"><span data-stu-id="2bb74-114">In other words, the method is virtual, although the `virtual` keyword is not used in the F# language.</span></span> <span data-ttu-id="2bb74-115">無論方法`abstract`是否已實作為, 都會在虛擬方法上使用關鍵字。</span><span class="sxs-lookup"><span data-stu-id="2bb74-115">The keyword `abstract` is used on virtual methods regardless of whether the method is implemented.</span></span> <span data-ttu-id="2bb74-116">虛擬分派位置的宣告與該分派插槽的方法定義不同。</span><span class="sxs-lookup"><span data-stu-id="2bb74-116">The declaration of a virtual dispatch slot is separate from the definition of a method for that dispatch slot.</span></span> <span data-ttu-id="2bb74-117">因此, 在F#另一個 .net 語言中, 虛擬方法宣告和定義的對等, 是抽象方法宣告和個別定義的組合, 其中包含`default`關鍵字或`override`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="2bb74-117">Therefore, the F# equivalent of a virtual method declaration and definition in another .NET language is a combination of both an abstract method declaration and a separate definition, with either the `default` keyword or the `override` keyword.</span></span> <span data-ttu-id="2bb74-118">如需詳細資訊和範例, 請參閱[方法](./members/methods.md)。</span><span class="sxs-lookup"><span data-stu-id="2bb74-118">For more information and examples, see [Methods](./members/methods.md).</span></span>

<span data-ttu-id="2bb74-119">只有在有已宣告但未定義的抽象方法時, 才會將類別視為抽象。</span><span class="sxs-lookup"><span data-stu-id="2bb74-119">A class is considered abstract only if there are abstract methods that are declared but not defined.</span></span> <span data-ttu-id="2bb74-120">因此, 具有抽象方法的類別不一定是抽象類別。</span><span class="sxs-lookup"><span data-stu-id="2bb74-120">Therefore, classes that have abstract methods are not necessarily abstract classes.</span></span> <span data-ttu-id="2bb74-121">除非類別有未定義的抽象方法, 否則請不要使用**AbstractClass**屬性。</span><span class="sxs-lookup"><span data-stu-id="2bb74-121">Unless a class has undefined abstract methods, do not use the **AbstractClass** attribute.</span></span>

<span data-ttu-id="2bb74-122">在先前的語法中,*協助工具修飾*詞`public`可以`private`是`internal`、或。</span><span class="sxs-lookup"><span data-stu-id="2bb74-122">In the previous syntax, *accessibility-modifier* can be `public`, `private` or `internal`.</span></span> <span data-ttu-id="2bb74-123">如需詳細資訊，請參閱[存取控制](access-control.md)。</span><span class="sxs-lookup"><span data-stu-id="2bb74-123">For more information, see [Access Control](access-control.md).</span></span>

<span data-ttu-id="2bb74-124">如同其他類型, 抽象類別可以有基類和一或多個基底介面。</span><span class="sxs-lookup"><span data-stu-id="2bb74-124">As with other types, abstract classes can have a base class and one or more base interfaces.</span></span> <span data-ttu-id="2bb74-125">每個基類或介面都會與`inherit`關鍵字一起出現在不同的行上。</span><span class="sxs-lookup"><span data-stu-id="2bb74-125">Each base class or interface appears on a separate line together with the `inherit` keyword.</span></span>

<span data-ttu-id="2bb74-126">抽象類別的類型定義可以包含完整定義的成員, 但也可以包含抽象成員。</span><span class="sxs-lookup"><span data-stu-id="2bb74-126">The type definition of an abstract class can contain fully defined members, but it can also contain abstract members.</span></span> <span data-ttu-id="2bb74-127">Abstract 成員的語法會分別顯示在先前的語法中。</span><span class="sxs-lookup"><span data-stu-id="2bb74-127">The syntax for abstract members is shown separately in the previous syntax.</span></span> <span data-ttu-id="2bb74-128">在此語法中, 成員的*型*別簽章是一份清單, 其中包含依`->`序排列的參數類型和傳回型別, 並以標記和/或`*` token 分隔, 以適用于擴充和元組參數。</span><span class="sxs-lookup"><span data-stu-id="2bb74-128">In this syntax, the *type signature* of a member is a list that contains the parameter types in order and the return types, separated by `->` tokens and/or `*` tokens as appropriate for curried and tupled parameters.</span></span> <span data-ttu-id="2bb74-129">抽象成員類型簽章的語法與簽章檔案中所使用的語法相同, 以及 IntelliSense 在 Visual Studio Code 編輯器中所顯示的語法。</span><span class="sxs-lookup"><span data-stu-id="2bb74-129">The syntax for abstract member type signatures is the same as that used in signature files and that shown by IntelliSense in the Visual Studio Code Editor.</span></span>

<span data-ttu-id="2bb74-130">下列程式碼說明抽象類別圖形, 其中包含兩個非抽象衍生類別: 方形和 Circle。</span><span class="sxs-lookup"><span data-stu-id="2bb74-130">The following code illustrates an abstract class Shape, which has two non-abstract derived classes, Square and Circle.</span></span> <span data-ttu-id="2bb74-131">此範例示範如何使用抽象類別、方法和屬性。</span><span class="sxs-lookup"><span data-stu-id="2bb74-131">The example shows how to use abstract classes, methods, and properties.</span></span> <span data-ttu-id="2bb74-132">在此範例中, 「抽象類別」圖形代表具體實體 circle 和正方形的通用元素。</span><span class="sxs-lookup"><span data-stu-id="2bb74-132">In the example, the abstract class Shape represents the common elements of the concrete entities circle and square.</span></span> <span data-ttu-id="2bb74-133">所有圖形 (在二維座標系統中) 的一般功能會被抽象化成 Shape 類別: 格線上的位置、旋轉角度, 以及區域和周邊屬性。</span><span class="sxs-lookup"><span data-stu-id="2bb74-133">The common features of all shapes (in a two-dimensional coordinate system) are abstracted out into the Shape class: the position on the grid, an angle of rotation, and the area and perimeter properties.</span></span> <span data-ttu-id="2bb74-134">這些可以覆寫, 但位置除外, 個別圖形無法變更的行為。</span><span class="sxs-lookup"><span data-stu-id="2bb74-134">These can be overridden, except for position, the behavior of which individual shapes cannot change.</span></span>

<span data-ttu-id="2bb74-135">可以覆寫旋轉方法, 如同 Circle 類別, 這是因為其對稱而旋轉不變。</span><span class="sxs-lookup"><span data-stu-id="2bb74-135">The rotation method can be overridden, as in the Circle class, which is rotation invariant because of its symmetry.</span></span> <span data-ttu-id="2bb74-136">因此, 在 Circle 類別中, 旋轉方法會由不執行任何動作的方法所取代。</span><span class="sxs-lookup"><span data-stu-id="2bb74-136">So in the Circle class, the rotation method is replaced by a method that does nothing.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2901.fs)]

<span data-ttu-id="2bb74-137">**輸出：**</span><span class="sxs-lookup"><span data-stu-id="2bb74-137">**Output:**</span></span>

```
Perimeter of square with side length 10.000000 is 40.000000
Circumference of circle with radius 5.000000 is 31.415927
Area of Square: 100.000000
Area of Circle: 78.539816
```

## <a name="see-also"></a><span data-ttu-id="2bb74-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2bb74-138">See also</span></span>

- [<span data-ttu-id="2bb74-139">類別</span><span class="sxs-lookup"><span data-stu-id="2bb74-139">Classes</span></span>](classes.md)
- [<span data-ttu-id="2bb74-140">成員</span><span class="sxs-lookup"><span data-stu-id="2bb74-140">Members</span></span>](./members/index.md)
- [<span data-ttu-id="2bb74-141">方法</span><span class="sxs-lookup"><span data-stu-id="2bb74-141">Methods</span></span>](./members/methods.md)
- [<span data-ttu-id="2bb74-142">屬性</span><span class="sxs-lookup"><span data-stu-id="2bb74-142">Properties</span></span>](./members/Properties.md)
