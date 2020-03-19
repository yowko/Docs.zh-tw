---
title: 方法
description: 瞭解 F# 方法如何與用於公開和實現物件和類型的功能和行為的類型關聯的函數。
ms.date: 11/04/2019
ms.openlocfilehash: 6f5ae76ea450b07763eb58d0c95b18b30f634551
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400208"
---
# <a name="methods"></a><span data-ttu-id="d176c-103">方法</span><span class="sxs-lookup"><span data-stu-id="d176c-103">Methods</span></span>

<span data-ttu-id="d176c-104">*方法*是與類型關聯的函數。</span><span class="sxs-lookup"><span data-stu-id="d176c-104">A *method* is a function that is associated with a type.</span></span> <span data-ttu-id="d176c-105">在物件導向的程式設計中，使用方法公開和實現物件和類型的功能和行為。</span><span class="sxs-lookup"><span data-stu-id="d176c-105">In object-oriented programming, methods are used to expose and implement the functionality and behavior of objects and types.</span></span>

## <a name="syntax"></a><span data-ttu-id="d176c-106">語法</span><span class="sxs-lookup"><span data-stu-id="d176c-106">Syntax</span></span>

```fsharp
// Instance method definition.
[ attributes ]
member [inline] self-identifier.method-name parameter-list [ : return-type ] =
    method-body

// Static method definition.
[ attributes ]
static member [inline] method-name parameter-list [ : return-type ] =
    method-body

// Abstract method declaration or virtual dispatch slot.
[ attributes ]
abstract member method-name : type-signature

// Virtual method declaration and default implementation.
[ attributes ]
abstract member method-name : type-signature
[ attributes ]
default self-identifier.method-name parameter-list [ : return-type ] =
    method-body

// Override of inherited virtual method.
[ attributes ]
override self-identifier.method-name parameter-list [ : return-type ] =
    method-body

// Optional and DefaultParameterValue attributes on input parameters
[ attributes ]
[ modifier ] member [inline] self-identifier.method-name ([<Optional; DefaultParameterValue( default-value )>] input) [ : return-type ]
```

## <a name="remarks"></a><span data-ttu-id="d176c-107">備註</span><span class="sxs-lookup"><span data-stu-id="d176c-107">Remarks</span></span>

<span data-ttu-id="d176c-108">在前面的語法中，您可以看到各種形式的方法聲明和定義。</span><span class="sxs-lookup"><span data-stu-id="d176c-108">In the previous syntax, you can see the various forms of method declarations and definitions.</span></span> <span data-ttu-id="d176c-109">在較長的方法實體中，分行符號遵循等號 （\*），整個方法體縮進。</span><span class="sxs-lookup"><span data-stu-id="d176c-109">In longer method bodies, a line break follows the equal sign (=), and the whole method body is indented.</span></span>

<span data-ttu-id="d176c-110">屬性可以應用於任何方法聲明。</span><span class="sxs-lookup"><span data-stu-id="d176c-110">Attributes can be applied to any method declaration.</span></span> <span data-ttu-id="d176c-111">它們先于方法定義的語法，通常列在單獨的行上。</span><span class="sxs-lookup"><span data-stu-id="d176c-111">They precede the syntax for a method definition and are usually listed on a separate line.</span></span> <span data-ttu-id="d176c-112">如需詳細資訊，請參閱[屬性](../attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="d176c-112">For more information, see [Attributes](../attributes.md).</span></span>

<span data-ttu-id="d176c-113">可以標記`inline`方法。</span><span class="sxs-lookup"><span data-stu-id="d176c-113">Methods can be marked `inline`.</span></span> <span data-ttu-id="d176c-114">如需 `inline` 的資訊，請參閱[內嵌函式](../functions/inline-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="d176c-114">For information about `inline`, see [Inline Functions](../functions/inline-functions.md).</span></span>

<span data-ttu-id="d176c-115">非內聯方法可以在類型中遞迴使用;無需顯式使用 關鍵字`rec`。</span><span class="sxs-lookup"><span data-stu-id="d176c-115">Non-inline methods can be used recursively within the type; there is no need to explicitly use the `rec` keyword.</span></span>

## <a name="instance-methods"></a><span data-ttu-id="d176c-116">實例方法</span><span class="sxs-lookup"><span data-stu-id="d176c-116">Instance Methods</span></span>

<span data-ttu-id="d176c-117">實例方法使用`member`關鍵字和*自識別碼*聲明，後跟句點 （.） 和方法名稱和參數。</span><span class="sxs-lookup"><span data-stu-id="d176c-117">Instance methods are declared with the `member` keyword and a *self-identifier*, followed by a period (.) and the method name and parameters.</span></span> <span data-ttu-id="d176c-118">與綁定的情況`let`一樣，*參數清單*可以是一種模式。</span><span class="sxs-lookup"><span data-stu-id="d176c-118">As is the case for `let` bindings, the *parameter-list* can be a pattern.</span></span> <span data-ttu-id="d176c-119">通常，將方法參數以元組形式包裹在括弧中，這是方法在其他 .NET Framework 語言中創建時在 F# 中顯示的方法。</span><span class="sxs-lookup"><span data-stu-id="d176c-119">Typically, you enclose method parameters in parentheses in a tuple form, which is the way methods appear in F# when they are created in other .NET Framework languages.</span></span> <span data-ttu-id="d176c-120">但是，咖喱形式（由空格分隔的參數）也很常見，並且還支援其他模式。</span><span class="sxs-lookup"><span data-stu-id="d176c-120">However, the curried form (parameters separated by spaces) is also common, and other patterns are supported also.</span></span>

<span data-ttu-id="d176c-121">下面的示例說明了非抽象實例方法的定義和使用。</span><span class="sxs-lookup"><span data-stu-id="d176c-121">The following example illustrates the definition and use of a non-abstract instance method.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3401.fs)]

<span data-ttu-id="d176c-122">在實例方法中，不要使用自識別碼訪問使用 let 綁定定義的欄位。</span><span class="sxs-lookup"><span data-stu-id="d176c-122">Within instance methods, do not use the self identifier to access fields defined by using let bindings.</span></span> <span data-ttu-id="d176c-123">訪問其他成員和屬性時，請使用自識別碼。</span><span class="sxs-lookup"><span data-stu-id="d176c-123">Use the self identifier when accessing other members and properties.</span></span>

## <a name="static-methods"></a><span data-ttu-id="d176c-124">靜態方法</span><span class="sxs-lookup"><span data-stu-id="d176c-124">Static Methods</span></span>

<span data-ttu-id="d176c-125">關鍵字`static`用於指定可以在沒有實例的情況下調用方法，並且不與物件實例關聯。</span><span class="sxs-lookup"><span data-stu-id="d176c-125">The keyword `static` is used to specify that a method can be called without an instance and is not associated with an object instance.</span></span> <span data-ttu-id="d176c-126">否則，方法是實例方法。</span><span class="sxs-lookup"><span data-stu-id="d176c-126">Otherwise, methods are instance methods.</span></span>

<span data-ttu-id="d176c-127">下一節中的示例顯示使用 關鍵字聲明的`let`欄位、使用`member`關鍵字聲明的屬性成員以及用 關鍵字聲明的`static`靜態方法。</span><span class="sxs-lookup"><span data-stu-id="d176c-127">The example in the next section shows fields declared with the `let` keyword, property members declared with the `member` keyword, and a static method declared with the `static` keyword.</span></span>

<span data-ttu-id="d176c-128">下面的示例說明了靜態方法的定義和使用。</span><span class="sxs-lookup"><span data-stu-id="d176c-128">The following example illustrates the definition and use of static methods.</span></span> <span data-ttu-id="d176c-129">假設這些方法定義位於上一節中的`SomeType`類中。</span><span class="sxs-lookup"><span data-stu-id="d176c-129">Assume that these method definitions are in the `SomeType` class in the previous section.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3402.fs)]

## <a name="abstract-and-virtual-methods"></a><span data-ttu-id="d176c-130">抽象和虛擬方法</span><span class="sxs-lookup"><span data-stu-id="d176c-130">Abstract and Virtual Methods</span></span>

<span data-ttu-id="d176c-131">關鍵字`abstract`指示方法具有虛擬調度槽，並且類中可能沒有定義。</span><span class="sxs-lookup"><span data-stu-id="d176c-131">The keyword `abstract` indicates that a method has a virtual dispatch slot and might not have a definition in the class.</span></span> <span data-ttu-id="d176c-132">*虛擬調度槽*是內部維護的函數表中的條目，用於在運行時查找物件導向的類型的虛擬函式呼叫。</span><span class="sxs-lookup"><span data-stu-id="d176c-132">A *virtual dispatch slot* is an entry in an internally maintained table of functions that is used at run time to look up virtual function calls in an object-oriented type.</span></span> <span data-ttu-id="d176c-133">虛擬調度機制是實現*多態性的*機制，是物件導向程式設計的一個重要特徵。</span><span class="sxs-lookup"><span data-stu-id="d176c-133">The virtual dispatch mechanism is the mechanism that implements *polymorphism*, an important feature of object-oriented programming.</span></span> <span data-ttu-id="d176c-134">至少有一個沒有定義的抽象方法的類是*抽象類別*，這意味著不能創建該類的實例。</span><span class="sxs-lookup"><span data-stu-id="d176c-134">A class that has at least one abstract method without a definition is an *abstract class*, which means that no instances can be created of that class.</span></span> <span data-ttu-id="d176c-135">有關抽象類別的詳細資訊，請參閱[抽象類別](../abstract-classes.md)。</span><span class="sxs-lookup"><span data-stu-id="d176c-135">For more information about abstract classes, see [Abstract Classes](../abstract-classes.md).</span></span>

<span data-ttu-id="d176c-136">抽象方法聲明不包括方法體。</span><span class="sxs-lookup"><span data-stu-id="d176c-136">Abstract method declarations do not include a method body.</span></span> <span data-ttu-id="d176c-137">相反，方法的名稱後跟冒號 （:)和 方法的類型簽名。</span><span class="sxs-lookup"><span data-stu-id="d176c-137">Instead, the name of the method is followed by a colon (:) and a type signature for the method.</span></span> <span data-ttu-id="d176c-138">方法的類型簽名與 IntelliSense 在 Visual Studio 代碼編輯器中將滑鼠指標懸停在方法名稱上時顯示的簽名相同，但沒有參數名稱。</span><span class="sxs-lookup"><span data-stu-id="d176c-138">The type signature of a method is the same as that shown by IntelliSense when you pause the mouse pointer over a method name in the Visual Studio Code Editor, except without parameter names.</span></span> <span data-ttu-id="d176c-139">當您以對話模式工作時，解譯器 fsi.exe 也會顯示類型簽名。</span><span class="sxs-lookup"><span data-stu-id="d176c-139">Type signatures are also displayed by the interpreter, fsi.exe, when you are working interactively.</span></span> <span data-ttu-id="d176c-140">方法的類型簽名是通過列出參數的類型（後跟返回類型）以及適當的分隔符號符號來形成的。</span><span class="sxs-lookup"><span data-stu-id="d176c-140">The type signature of a method is formed by listing out the types of the parameters, followed by the return type, with appropriate separator symbols.</span></span> <span data-ttu-id="d176c-141">咖喱參數由 分隔`->`，元組參數由 分隔。 `*`</span><span class="sxs-lookup"><span data-stu-id="d176c-141">Curried parameters are separated by `->` and tuple parameters are separated by `*`.</span></span> <span data-ttu-id="d176c-142">傳回值始終由`->`符號與參數分隔。</span><span class="sxs-lookup"><span data-stu-id="d176c-142">The return value is always separated from the arguments by a `->` symbol.</span></span> <span data-ttu-id="d176c-143">括弧可用於對複雜參數進行分組，例如當函數類型為參數時，或指示元組何時被視為單個參數而不是兩個參數。</span><span class="sxs-lookup"><span data-stu-id="d176c-143">Parentheses can be used to group complex parameters, such as when a function type is a parameter, or to indicate when a tuple is treated as a single parameter rather than as two parameters.</span></span>

<span data-ttu-id="d176c-144">還可以通過將定義添加到類並使用`default`關鍵字來提供抽象方法預設定義，如本主題中的語法塊所示。</span><span class="sxs-lookup"><span data-stu-id="d176c-144">You can also give abstract methods default definitions by adding the definition to the class and using the `default` keyword, as shown in the syntax block in this topic.</span></span> <span data-ttu-id="d176c-145">在同一類中具有定義的抽象方法等效于其他 .NET Framework 語言中的虛擬方法。</span><span class="sxs-lookup"><span data-stu-id="d176c-145">An abstract method that has a definition in the same class is equivalent to a virtual method in other .NET Framework languages.</span></span> <span data-ttu-id="d176c-146">無論定義是否存在，關鍵字都會`abstract`在類的虛擬函數表中創建一個新的調度槽。</span><span class="sxs-lookup"><span data-stu-id="d176c-146">Whether or not a definition exists, the `abstract` keyword creates a new dispatch slot in the virtual function table for the class.</span></span>

<span data-ttu-id="d176c-147">無論基類是否實現其抽象方法，派生類都可以提供抽象方法的實現。</span><span class="sxs-lookup"><span data-stu-id="d176c-147">Regardless of whether a base class implements its abstract methods, derived classes can provide implementations of abstract methods.</span></span> <span data-ttu-id="d176c-148">要在派生類中實現抽象方法，請定義派生類中具有相同名稱和簽名的方法，但使用`override`or`default`關鍵字除外，並提供方法正文。</span><span class="sxs-lookup"><span data-stu-id="d176c-148">To implement an abstract method in a derived class, define a method that has the same name and signature in the derived class, except use the `override` or `default` keyword, and provide the method body.</span></span> <span data-ttu-id="d176c-149">關鍵字`override`和`default`含義完全相同的東西。</span><span class="sxs-lookup"><span data-stu-id="d176c-149">The keywords `override` and `default` mean exactly the same thing.</span></span> <span data-ttu-id="d176c-150">如果`override`新方法重寫基類實現，請使用 ;在`default`與原始抽象聲明相同的類中創建實現時使用。</span><span class="sxs-lookup"><span data-stu-id="d176c-150">Use `override` if the new method overrides a base class implementation; use `default` when you create an implementation in the same class as the original abstract declaration.</span></span> <span data-ttu-id="d176c-151">不要在`abstract`實現基類中聲明為抽象的方法上使用 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="d176c-151">Do not use the `abstract` keyword on the method that implements the method that was declared abstract in the base class.</span></span>

<span data-ttu-id="d176c-152">下面的示例演示了具有預設實現`Rotate`（等效于 .NET Framework 虛擬方法）的抽象方法。</span><span class="sxs-lookup"><span data-stu-id="d176c-152">The following example illustrates an abstract method `Rotate` that has a default implementation, the equivalent of a .NET Framework virtual method.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3403.fs)]

<span data-ttu-id="d176c-153">下面的示例演示了重寫基類方法的派生類。</span><span class="sxs-lookup"><span data-stu-id="d176c-153">The following example illustrates a derived class that overrides a base class method.</span></span> <span data-ttu-id="d176c-154">在這種情況下，重寫會更改行為，以便方法不執行任何操作。</span><span class="sxs-lookup"><span data-stu-id="d176c-154">In this case, the override changes the behavior so that the method does nothing.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3404.fs)]

## <a name="overloaded-methods"></a><span data-ttu-id="d176c-155">多載的方法</span><span class="sxs-lookup"><span data-stu-id="d176c-155">Overloaded Methods</span></span>

<span data-ttu-id="d176c-156">重載方法是給定類型中名稱相同但參數不同的方法。</span><span class="sxs-lookup"><span data-stu-id="d176c-156">Overloaded methods are methods that have identical names in a given type but that have different arguments.</span></span> <span data-ttu-id="d176c-157">在 F# 中，通常使用可選參數而不是重載方法。</span><span class="sxs-lookup"><span data-stu-id="d176c-157">In F#, optional arguments are usually used instead of overloaded methods.</span></span> <span data-ttu-id="d176c-158">但是，在語言中允許重載方法，前提是參數以元組形式，而不是咖喱形式。</span><span class="sxs-lookup"><span data-stu-id="d176c-158">However, overloaded methods are permitted in the language, provided that the arguments are in tuple form, not curried form.</span></span>

## <a name="optional-arguments"></a><span data-ttu-id="d176c-159">選擇性引數</span><span class="sxs-lookup"><span data-stu-id="d176c-159">Optional Arguments</span></span>

<span data-ttu-id="d176c-160">從 F# 4.1 開始，還可以在方法中具有具有預設參數值的可選參數。</span><span class="sxs-lookup"><span data-stu-id="d176c-160">Starting with F# 4.1, you can also have optional arguments with a default parameter value in methods.</span></span>  <span data-ttu-id="d176c-161">這有助於促進 C# 代碼的交互操作。</span><span class="sxs-lookup"><span data-stu-id="d176c-161">This is to help facilitate interoperation with C# code.</span></span>  <span data-ttu-id="d176c-162">下面的示例演示了語法：</span><span class="sxs-lookup"><span data-stu-id="d176c-162">The following example demonstrates the syntax:</span></span>

```fsharp
// A class with a method M, which takes in an optional integer argument.
type C() =
    _.M([<Optional; DefaultParameterValue(12)>] i) = i + 1
```

<span data-ttu-id="d176c-163">請注意，傳入`DefaultParameterValue`的值必須與輸入類型匹配。</span><span class="sxs-lookup"><span data-stu-id="d176c-163">Note that the value passed in for `DefaultParameterValue` must match the input type.</span></span>  <span data-ttu-id="d176c-164">在上述示例中，它是 一個`int`。</span><span class="sxs-lookup"><span data-stu-id="d176c-164">In the above sample, it is an `int`.</span></span>  <span data-ttu-id="d176c-165">嘗試將非整數值傳遞到中`DefaultParameterValue`將導致編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="d176c-165">Attempting to pass a non-integer value into `DefaultParameterValue` would result in a compile error.</span></span>

## <a name="example-properties-and-methods"></a><span data-ttu-id="d176c-166">示例：屬性和方法</span><span class="sxs-lookup"><span data-stu-id="d176c-166">Example: Properties and Methods</span></span>

<span data-ttu-id="d176c-167">下面的示例包含一個類型，其中包含欄位、私有函數、屬性和靜態方法的示例。</span><span class="sxs-lookup"><span data-stu-id="d176c-167">The following example contains a type that has examples of fields, private functions, properties, and a static method.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3406.fs)]

## <a name="see-also"></a><span data-ttu-id="d176c-168">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d176c-168">See also</span></span>

- [<span data-ttu-id="d176c-169">成員</span><span class="sxs-lookup"><span data-stu-id="d176c-169">Members</span></span>](index.md)
