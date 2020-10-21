---
title: 方法
description: '瞭解 F # 方法是一種與型別相關聯的函式，用來公開和執行物件和類型的功能和行為。'
ms.date: 11/04/2019
ms.openlocfilehash: 6f5ae76ea450b07763eb58d0c95b18b30f634551
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/20/2020
ms.locfileid: "92224108"
---
# <a name="methods"></a><span data-ttu-id="a15ce-103">方法</span><span class="sxs-lookup"><span data-stu-id="a15ce-103">Methods</span></span>

<span data-ttu-id="a15ce-104">*方法*是與型別相關聯的函式。</span><span class="sxs-lookup"><span data-stu-id="a15ce-104">A *method* is a function that is associated with a type.</span></span> <span data-ttu-id="a15ce-105">在物件導向程式設計中，會使用方法來公開和執行物件和類型的功能和行為。</span><span class="sxs-lookup"><span data-stu-id="a15ce-105">In object-oriented programming, methods are used to expose and implement the functionality and behavior of objects and types.</span></span>

## <a name="syntax"></a><span data-ttu-id="a15ce-106">語法</span><span class="sxs-lookup"><span data-stu-id="a15ce-106">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="a15ce-107">備註</span><span class="sxs-lookup"><span data-stu-id="a15ce-107">Remarks</span></span>

<span data-ttu-id="a15ce-108">在先前的語法中，您可以看到各種形式的方法宣告和定義。</span><span class="sxs-lookup"><span data-stu-id="a15ce-108">In the previous syntax, you can see the various forms of method declarations and definitions.</span></span> <span data-ttu-id="a15ce-109">在較長的方法主體中，換行字元會在等號 (=) 之後，而整個方法主體會縮排。</span><span class="sxs-lookup"><span data-stu-id="a15ce-109">In longer method bodies, a line break follows the equal sign (=), and the whole method body is indented.</span></span>

<span data-ttu-id="a15ce-110">屬性可以套用至任何方法宣告。</span><span class="sxs-lookup"><span data-stu-id="a15ce-110">Attributes can be applied to any method declaration.</span></span> <span data-ttu-id="a15ce-111">它們優先于方法定義的語法，且通常會列在個別行上。</span><span class="sxs-lookup"><span data-stu-id="a15ce-111">They precede the syntax for a method definition and are usually listed on a separate line.</span></span> <span data-ttu-id="a15ce-112">如需詳細資訊，請參閱[屬性](../attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="a15ce-112">For more information, see [Attributes](../attributes.md).</span></span>

<span data-ttu-id="a15ce-113">可以標示方法 `inline` 。</span><span class="sxs-lookup"><span data-stu-id="a15ce-113">Methods can be marked `inline`.</span></span> <span data-ttu-id="a15ce-114">如需 `inline` 的資訊，請參閱[內嵌函式](../functions/inline-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="a15ce-114">For information about `inline`, see [Inline Functions](../functions/inline-functions.md).</span></span>

<span data-ttu-id="a15ce-115">非內嵌方法可以在型別內以遞迴方式使用;不需要明確使用 `rec` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="a15ce-115">Non-inline methods can be used recursively within the type; there is no need to explicitly use the `rec` keyword.</span></span>

## <a name="instance-methods"></a><span data-ttu-id="a15ce-116">實例方法</span><span class="sxs-lookup"><span data-stu-id="a15ce-116">Instance Methods</span></span>

<span data-ttu-id="a15ce-117">實例方法是以 `member` 關鍵字和 *自我識別碼*宣告，後面接著一個句點 (. ) 和方法名稱和參數。</span><span class="sxs-lookup"><span data-stu-id="a15ce-117">Instance methods are declared with the `member` keyword and a *self-identifier*, followed by a period (.) and the method name and parameters.</span></span> <span data-ttu-id="a15ce-118">如同系結的情況 `let` ， *參數清單* 可以是模式。</span><span class="sxs-lookup"><span data-stu-id="a15ce-118">As is the case for `let` bindings, the *parameter-list* can be a pattern.</span></span> <span data-ttu-id="a15ce-119">通常，您會在元組形式的括弧中括住方法參數，這是方法在以其他 .NET Framework 語言建立時，在 F # 中的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="a15ce-119">Typically, you enclose method parameters in parentheses in a tuple form, which is the way methods appear in F# when they are created in other .NET Framework languages.</span></span> <span data-ttu-id="a15ce-120">不過，局部分隔形式 (參數以空格分隔) 也很常見，而且也支援其他模式。</span><span class="sxs-lookup"><span data-stu-id="a15ce-120">However, the curried form (parameters separated by spaces) is also common, and other patterns are supported also.</span></span>

<span data-ttu-id="a15ce-121">下列範例說明非抽象實例方法的定義和使用方式。</span><span class="sxs-lookup"><span data-stu-id="a15ce-121">The following example illustrates the definition and use of a non-abstract instance method.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3401.fs)]

<span data-ttu-id="a15ce-122">在實例方法中，請勿使用自我識別碼來存取使用 let 系結所定義的欄位。</span><span class="sxs-lookup"><span data-stu-id="a15ce-122">Within instance methods, do not use the self identifier to access fields defined by using let bindings.</span></span> <span data-ttu-id="a15ce-123">存取其他成員和屬性時，請使用自我識別碼。</span><span class="sxs-lookup"><span data-stu-id="a15ce-123">Use the self identifier when accessing other members and properties.</span></span>

## <a name="static-methods"></a><span data-ttu-id="a15ce-124">靜態方法</span><span class="sxs-lookup"><span data-stu-id="a15ce-124">Static Methods</span></span>

<span data-ttu-id="a15ce-125">關鍵字 `static` 是用來指定在沒有實例的情況下呼叫方法，而且不會與物件實例相關聯。</span><span class="sxs-lookup"><span data-stu-id="a15ce-125">The keyword `static` is used to specify that a method can be called without an instance and is not associated with an object instance.</span></span> <span data-ttu-id="a15ce-126">否則，方法是實例方法。</span><span class="sxs-lookup"><span data-stu-id="a15ce-126">Otherwise, methods are instance methods.</span></span>

<span data-ttu-id="a15ce-127">下一節中的範例會顯示使用關鍵字宣告的欄位 `let` 、使用關鍵字宣告的屬性成員 `member` ，以及使用關鍵字宣告的靜態方法 `static` 。</span><span class="sxs-lookup"><span data-stu-id="a15ce-127">The example in the next section shows fields declared with the `let` keyword, property members declared with the `member` keyword, and a static method declared with the `static` keyword.</span></span>

<span data-ttu-id="a15ce-128">下列範例說明靜態方法的定義和使用方式。</span><span class="sxs-lookup"><span data-stu-id="a15ce-128">The following example illustrates the definition and use of static methods.</span></span> <span data-ttu-id="a15ce-129">假設這些方法定義是在 `SomeType` 上一節的類別中。</span><span class="sxs-lookup"><span data-stu-id="a15ce-129">Assume that these method definitions are in the `SomeType` class in the previous section.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3402.fs)]

## <a name="abstract-and-virtual-methods"></a><span data-ttu-id="a15ce-130">抽象和虛擬方法</span><span class="sxs-lookup"><span data-stu-id="a15ce-130">Abstract and Virtual Methods</span></span>

<span data-ttu-id="a15ce-131">關鍵字 `abstract` 指出方法具有虛擬分派位置，而且在類別中可能沒有定義。</span><span class="sxs-lookup"><span data-stu-id="a15ce-131">The keyword `abstract` indicates that a method has a virtual dispatch slot and might not have a definition in the class.</span></span> <span data-ttu-id="a15ce-132">*虛擬分派*位置是在內部維護的函式資料表中的專案，可在執行時間用來查詢物件導向型別中的虛擬函式呼叫。</span><span class="sxs-lookup"><span data-stu-id="a15ce-132">A *virtual dispatch slot* is an entry in an internally maintained table of functions that is used at run time to look up virtual function calls in an object-oriented type.</span></span> <span data-ttu-id="a15ce-133">虛擬分派機制是實架構的 *機制，這*是物件導向程式設計的一項重要功能。</span><span class="sxs-lookup"><span data-stu-id="a15ce-133">The virtual dispatch mechanism is the mechanism that implements *polymorphism*, an important feature of object-oriented programming.</span></span> <span data-ttu-id="a15ce-134">至少有一個沒有定義之抽象方法的類別是 *抽象類別*，這表示不可以建立該類別的實例。</span><span class="sxs-lookup"><span data-stu-id="a15ce-134">A class that has at least one abstract method without a definition is an *abstract class*, which means that no instances can be created of that class.</span></span> <span data-ttu-id="a15ce-135">如需抽象類別的詳細資訊，請參閱 [抽象類別](../abstract-classes.md)。</span><span class="sxs-lookup"><span data-stu-id="a15ce-135">For more information about abstract classes, see [Abstract Classes](../abstract-classes.md).</span></span>

<span data-ttu-id="a15ce-136">抽象方法宣告不包含方法主體。</span><span class="sxs-lookup"><span data-stu-id="a15ce-136">Abstract method declarations do not include a method body.</span></span> <span data-ttu-id="a15ce-137">相反地，方法的名稱後面會接著冒號 (： ) 和方法的類型簽章。</span><span class="sxs-lookup"><span data-stu-id="a15ce-137">Instead, the name of the method is followed by a colon (:) and a type signature for the method.</span></span> <span data-ttu-id="a15ce-138">當您將滑鼠指標暫停在 Visual Studio Code 編輯器中的方法名稱上方（但不含參數名稱）時，方法的類型簽章與 IntelliSense 所顯示的類型簽章相同。</span><span class="sxs-lookup"><span data-stu-id="a15ce-138">The type signature of a method is the same as that shown by IntelliSense when you pause the mouse pointer over a method name in the Visual Studio Code Editor, except without parameter names.</span></span> <span data-ttu-id="a15ce-139">當您以互動方式工作時，解譯器也會顯示型別簽章（fsi.exe）。</span><span class="sxs-lookup"><span data-stu-id="a15ce-139">Type signatures are also displayed by the interpreter, fsi.exe, when you are working interactively.</span></span> <span data-ttu-id="a15ce-140">方法的類型簽章是藉由列出參數的類型，後面接著傳回型別，並以適當的分隔符號號來形成。</span><span class="sxs-lookup"><span data-stu-id="a15ce-140">The type signature of a method is formed by listing out the types of the parameters, followed by the return type, with appropriate separator symbols.</span></span> <span data-ttu-id="a15ce-141">局部擴充參數會以分隔 `->` ，而且元組參數會以分隔 `*` 。</span><span class="sxs-lookup"><span data-stu-id="a15ce-141">Curried parameters are separated by `->` and tuple parameters are separated by `*`.</span></span> <span data-ttu-id="a15ce-142">傳回值一律與引數以 `->` 符號分隔。</span><span class="sxs-lookup"><span data-stu-id="a15ce-142">The return value is always separated from the arguments by a `->` symbol.</span></span> <span data-ttu-id="a15ce-143">括弧可以用來將複雜參數分組，例如當函式類型是參數時，或指出元組視為單一參數，而不是兩個參數。</span><span class="sxs-lookup"><span data-stu-id="a15ce-143">Parentheses can be used to group complex parameters, such as when a function type is a parameter, or to indicate when a tuple is treated as a single parameter rather than as two parameters.</span></span>

<span data-ttu-id="a15ce-144">您也可以將定義新增至類別，並使用 `default` 關鍵字（如本主題中的語法區塊所示），以提供抽象方法的預設定義。</span><span class="sxs-lookup"><span data-stu-id="a15ce-144">You can also give abstract methods default definitions by adding the definition to the class and using the `default` keyword, as shown in the syntax block in this topic.</span></span> <span data-ttu-id="a15ce-145">在相同類別中具有定義的抽象方法，相當於其他 .NET Framework 語言中的虛擬方法。</span><span class="sxs-lookup"><span data-stu-id="a15ce-145">An abstract method that has a definition in the same class is equivalent to a virtual method in other .NET Framework languages.</span></span> <span data-ttu-id="a15ce-146">無論定義是否存在， `abstract` 關鍵字都會在類別的虛擬函式資料表中建立新的分派位置。</span><span class="sxs-lookup"><span data-stu-id="a15ce-146">Whether or not a definition exists, the `abstract` keyword creates a new dispatch slot in the virtual function table for the class.</span></span>

<span data-ttu-id="a15ce-147">無論基類是否實作為抽象方法，衍生類別都可以提供抽象方法的執行。</span><span class="sxs-lookup"><span data-stu-id="a15ce-147">Regardless of whether a base class implements its abstract methods, derived classes can provide implementations of abstract methods.</span></span> <span data-ttu-id="a15ce-148">若要在衍生類別中執行抽象方法，請在衍生類別中定義具有相同名稱和簽章的方法（使用 `override` 或關鍵字除外 `default` ），並提供方法主體。</span><span class="sxs-lookup"><span data-stu-id="a15ce-148">To implement an abstract method in a derived class, define a method that has the same name and signature in the derived class, except use the `override` or `default` keyword, and provide the method body.</span></span> <span data-ttu-id="a15ce-149">關鍵字 `override` 和 `default` 表示完全相同的內容。</span><span class="sxs-lookup"><span data-stu-id="a15ce-149">The keywords `override` and `default` mean exactly the same thing.</span></span> <span data-ttu-id="a15ce-150">`override`如果新的方法會覆寫基類執行，請使用， `default` 當您在與原始抽象宣告相同的類別中建立實值時，請使用。</span><span class="sxs-lookup"><span data-stu-id="a15ce-150">Use `override` if the new method overrides a base class implementation; use `default` when you create an implementation in the same class as the original abstract declaration.</span></span> <span data-ttu-id="a15ce-151">請勿 `abstract` 在執行基類中宣告為抽象方法的方法上使用關鍵字。</span><span class="sxs-lookup"><span data-stu-id="a15ce-151">Do not use the `abstract` keyword on the method that implements the method that was declared abstract in the base class.</span></span>

<span data-ttu-id="a15ce-152">下列範例說明 `Rotate` 具有預設實值的抽象方法，相當於 .NET Framework 的虛擬方法。</span><span class="sxs-lookup"><span data-stu-id="a15ce-152">The following example illustrates an abstract method `Rotate` that has a default implementation, the equivalent of a .NET Framework virtual method.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3403.fs)]

<span data-ttu-id="a15ce-153">下列範例說明會覆寫基類方法的衍生類別。</span><span class="sxs-lookup"><span data-stu-id="a15ce-153">The following example illustrates a derived class that overrides a base class method.</span></span> <span data-ttu-id="a15ce-154">在此情況下，覆寫會變更行為，使該方法不會執行任何動作。</span><span class="sxs-lookup"><span data-stu-id="a15ce-154">In this case, the override changes the behavior so that the method does nothing.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3404.fs)]

## <a name="overloaded-methods"></a><span data-ttu-id="a15ce-155">多載方法</span><span class="sxs-lookup"><span data-stu-id="a15ce-155">Overloaded Methods</span></span>

<span data-ttu-id="a15ce-156">多載方法是在指定類型中具有相同名稱但有不同引數的方法。</span><span class="sxs-lookup"><span data-stu-id="a15ce-156">Overloaded methods are methods that have identical names in a given type but that have different arguments.</span></span> <span data-ttu-id="a15ce-157">在 F # 中，通常會使用選擇性引數，而不是多載的方法。</span><span class="sxs-lookup"><span data-stu-id="a15ce-157">In F#, optional arguments are usually used instead of overloaded methods.</span></span> <span data-ttu-id="a15ce-158">但是，如果引數是採用元組格式，而非局部引數，則允許在語言中使用多載的方法。</span><span class="sxs-lookup"><span data-stu-id="a15ce-158">However, overloaded methods are permitted in the language, provided that the arguments are in tuple form, not curried form.</span></span>

## <a name="optional-arguments"></a><span data-ttu-id="a15ce-159">選擇性引數</span><span class="sxs-lookup"><span data-stu-id="a15ce-159">Optional Arguments</span></span>

<span data-ttu-id="a15ce-160">從 F # 4.1 開始，您也可以在方法中有選擇性的引數搭配預設參數值。</span><span class="sxs-lookup"><span data-stu-id="a15ce-160">Starting with F# 4.1, you can also have optional arguments with a default parameter value in methods.</span></span>  <span data-ttu-id="a15ce-161">這是為了協助加速與 c # 程式碼的交互操作。</span><span class="sxs-lookup"><span data-stu-id="a15ce-161">This is to help facilitate interoperation with C# code.</span></span>  <span data-ttu-id="a15ce-162">下列範例示範語法：</span><span class="sxs-lookup"><span data-stu-id="a15ce-162">The following example demonstrates the syntax:</span></span>

```fsharp
// A class with a method M, which takes in an optional integer argument.
type C() =
    _.M([<Optional; DefaultParameterValue(12)>] i) = i + 1
```

<span data-ttu-id="a15ce-163">請注意，傳入的值 `DefaultParameterValue` 必須符合輸入類型。</span><span class="sxs-lookup"><span data-stu-id="a15ce-163">Note that the value passed in for `DefaultParameterValue` must match the input type.</span></span>  <span data-ttu-id="a15ce-164">在上述範例中，它是 `int` 。</span><span class="sxs-lookup"><span data-stu-id="a15ce-164">In the above sample, it is an `int`.</span></span>  <span data-ttu-id="a15ce-165">嘗試傳遞非整數值 `DefaultParameterValue` 會導致編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="a15ce-165">Attempting to pass a non-integer value into `DefaultParameterValue` would result in a compile error.</span></span>

## <a name="example-properties-and-methods"></a><span data-ttu-id="a15ce-166">範例：屬性和方法</span><span class="sxs-lookup"><span data-stu-id="a15ce-166">Example: Properties and Methods</span></span>

<span data-ttu-id="a15ce-167">下列範例包含型別，其中包含欄位、私用函式、屬性和靜態方法的範例。</span><span class="sxs-lookup"><span data-stu-id="a15ce-167">The following example contains a type that has examples of fields, private functions, properties, and a static method.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3406.fs)]

## <a name="see-also"></a><span data-ttu-id="a15ce-168">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a15ce-168">See also</span></span>

- [<span data-ttu-id="a15ce-169">成員</span><span class="sxs-lookup"><span data-stu-id="a15ce-169">Members</span></span>](index.md)
