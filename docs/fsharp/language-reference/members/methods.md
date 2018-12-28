---
title: 方法
description: 了解如何F#方法是用來公開及實作的功能和行為的物件與型別的型別相關聯的函式。
ms.date: 05/16/2016
ms.openlocfilehash: 03150cc67f79bfde58cf27e4a9d4dfa9e9ff3f55
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2018
ms.locfileid: "53614021"
---
# <a name="methods"></a><span data-ttu-id="98425-103">方法</span><span class="sxs-lookup"><span data-stu-id="98425-103">Methods</span></span>

<span data-ttu-id="98425-104">A*方法*是與類型相關聯的函式。</span><span class="sxs-lookup"><span data-stu-id="98425-104">A *method* is a function that is associated with a type.</span></span> <span data-ttu-id="98425-105">在物件導向程式設計中，方法用來公開及實作的功能和行為的物件和型別。</span><span class="sxs-lookup"><span data-stu-id="98425-105">In object-oriented programming, methods are used to expose and implement the functionality and behavior of objects and types.</span></span>

## <a name="syntax"></a><span data-ttu-id="98425-106">語法</span><span class="sxs-lookup"><span data-stu-id="98425-106">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="98425-107">備註</span><span class="sxs-lookup"><span data-stu-id="98425-107">Remarks</span></span>

<span data-ttu-id="98425-108">在先前的語法中，您可以看到各種形式的方法宣告和定義。</span><span class="sxs-lookup"><span data-stu-id="98425-108">In the previous syntax, you can see the various forms of method declarations and definitions.</span></span> <span data-ttu-id="98425-109">在較長的方法主體，換行符號後面接著等號 （=），而整個方法本文縮排。</span><span class="sxs-lookup"><span data-stu-id="98425-109">In longer method bodies, a line break follows the equal sign (=), and the whole method body is indented.</span></span>

<span data-ttu-id="98425-110">屬性可以套用至任何方法宣告。</span><span class="sxs-lookup"><span data-stu-id="98425-110">Attributes can be applied to any method declaration.</span></span> <span data-ttu-id="98425-111">在之前的方法定義的語法，而且通常會列在不同行。</span><span class="sxs-lookup"><span data-stu-id="98425-111">They precede the syntax for a method definition and are usually listed on a separate line.</span></span> <span data-ttu-id="98425-112">如需詳細資訊，請參閱[屬性](../attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="98425-112">For more information, see [Attributes](../attributes.md).</span></span>

<span data-ttu-id="98425-113">方法會標記`inline`。</span><span class="sxs-lookup"><span data-stu-id="98425-113">Methods can be marked `inline`.</span></span> <span data-ttu-id="98425-114">如需 `inline` 的資訊，請參閱[內嵌函式](../functions/inline-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="98425-114">For information about `inline`, see [Inline Functions](../functions/inline-functions.md).</span></span>

<span data-ttu-id="98425-115">非內嵌方法可以是遞迴的類型; 內使用不需要明確使用`rec`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="98425-115">Non-inline methods can be used recursively within the type; there is no need to explicitly use the `rec` keyword.</span></span>

## <a name="instance-methods"></a><span data-ttu-id="98425-116">執行個體方法</span><span class="sxs-lookup"><span data-stu-id="98425-116">Instance Methods</span></span>

<span data-ttu-id="98425-117">執行個體方法會以宣告`member`關鍵字和*自我識別項*，後面接著句號 （.） 的方法名稱和參數。</span><span class="sxs-lookup"><span data-stu-id="98425-117">Instance methods are declared with the `member` keyword and a *self-identifier*, followed by a period (.) and the method name and parameters.</span></span> <span data-ttu-id="98425-118">在此情況下，如`let`繫結*參數清單*可以是一種模式。</span><span class="sxs-lookup"><span data-stu-id="98425-118">As is the case for `let` bindings, the *parameter-list* can be a pattern.</span></span> <span data-ttu-id="98425-119">一般而言，括住括弧括住 tuple 的形式，也就是方式方法的參數會出現在方法F#在其他.NET Framework 語言中的建立時。</span><span class="sxs-lookup"><span data-stu-id="98425-119">Typically, you enclose method parameters in parentheses in a tuple form, which is the way methods appear in F# when they are created in other .NET Framework languages.</span></span> <span data-ttu-id="98425-120">不過，局部調用的形式 （以空格分隔的參數） 也很常見，而且也支援其他模式。</span><span class="sxs-lookup"><span data-stu-id="98425-120">However, the curried form (parameters separated by spaces) is also common, and other patterns are supported also.</span></span>

<span data-ttu-id="98425-121">下列範例說明如何定義和使用非抽象的執行個體方法。</span><span class="sxs-lookup"><span data-stu-id="98425-121">The following example illustrates the definition and use of a non-abstract instance method.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3401.fs)]

<span data-ttu-id="98425-122">執行個體在方法內，請勿使用自我識別項來使用 let 繫結來定義存取欄位。</span><span class="sxs-lookup"><span data-stu-id="98425-122">Within instance methods, do not use the self identifier to access fields defined by using let bindings.</span></span> <span data-ttu-id="98425-123">存取其他成員和屬性時，請使用自我識別項。</span><span class="sxs-lookup"><span data-stu-id="98425-123">Use the self identifier when accessing other members and properties.</span></span>

## <a name="static-methods"></a><span data-ttu-id="98425-124">靜態方法</span><span class="sxs-lookup"><span data-stu-id="98425-124">Static Methods</span></span>

<span data-ttu-id="98425-125">關鍵字`static`用來指定可以沒有執行個體中呼叫的方法，並不是物件執行個體相關聯。</span><span class="sxs-lookup"><span data-stu-id="98425-125">The keyword `static` is used to specify that a method can be called without an instance and is not associated with an object instance.</span></span> <span data-ttu-id="98425-126">否則，方法是執行個體方法。</span><span class="sxs-lookup"><span data-stu-id="98425-126">Otherwise, methods are instance methods.</span></span>

<span data-ttu-id="98425-127">下一節中的範例示範使用宣告的欄位`let`關鍵字，以宣告的屬性成員`member`關鍵字，並以宣告的靜態方法`static`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="98425-127">The example in the next section shows fields declared with the `let` keyword, property members declared with the `member` keyword, and a static method declared with the `static` keyword.</span></span>

<span data-ttu-id="98425-128">下列範例說明如何定義和使用靜態方法。</span><span class="sxs-lookup"><span data-stu-id="98425-128">The following example illustrates the definition and use of static methods.</span></span> <span data-ttu-id="98425-129">假設這些方法的定義位於`SomeType`上一節中的類別。</span><span class="sxs-lookup"><span data-stu-id="98425-129">Assume that these method definitions are in the `SomeType` class in the previous section.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3402.fs)]

## <a name="abstract-and-virtual-methods"></a><span data-ttu-id="98425-130">抽象和虛擬方法</span><span class="sxs-lookup"><span data-stu-id="98425-130">Abstract and Virtual Methods</span></span>

<span data-ttu-id="98425-131">關鍵字`abstract`表示一種方法有虛擬分派位置，而且可能沒有定義類別中。</span><span class="sxs-lookup"><span data-stu-id="98425-131">The keyword `abstract` indicates that a method has a virtual dispatch slot and might not have a definition in the class.</span></span> <span data-ttu-id="98425-132">A*虛擬分派介面槽*是物件導向的型別中，呼叫的函式在執行階段用來查閱虛擬函式的內部維護表格中的項目。</span><span class="sxs-lookup"><span data-stu-id="98425-132">A *virtual dispatch slot* is an entry in an internally maintained table of functions that is used at run time to look up virtual function calls in an object-oriented type.</span></span> <span data-ttu-id="98425-133">虛擬分派機制是實作的機制*多型*，物件導向程式設計的重要功能。</span><span class="sxs-lookup"><span data-stu-id="98425-133">The virtual dispatch mechanism is the mechanism that implements *polymorphism*, an important feature of object-oriented programming.</span></span> <span data-ttu-id="98425-134">具有至少一個抽象的方法，而不需定義的類別是*抽象類別*，這表示該類別，可以建立任何執行個體。</span><span class="sxs-lookup"><span data-stu-id="98425-134">A class that has at least one abstract method without a definition is an *abstract class*, which means that no instances can be created of that class.</span></span> <span data-ttu-id="98425-135">如需抽象類別的詳細資訊，請參閱[抽象類別](../abstract-classes.md)。</span><span class="sxs-lookup"><span data-stu-id="98425-135">For more information about abstract classes, see [Abstract Classes](../abstract-classes.md).</span></span>

<span data-ttu-id="98425-136">抽象方法宣告不包含方法主體。</span><span class="sxs-lookup"><span data-stu-id="98425-136">Abstract method declarations do not include a method body.</span></span> <span data-ttu-id="98425-137">相反地，方法的名稱被後面接著冒號 （:） 和方法的型別簽章。</span><span class="sxs-lookup"><span data-stu-id="98425-137">Instead, the name of the method is followed by a colon (:) and a type signature for the method.</span></span> <span data-ttu-id="98425-138">方法的型別簽章會顯示 intellisense，當您暫停滑鼠指標的方法名稱在 Visual Studio 程式碼編輯器 」 中，除了沒有參數的名稱相同。</span><span class="sxs-lookup"><span data-stu-id="98425-138">The type signature of a method is the same as that shown by IntelliSense when you pause the mouse pointer over a method name in the Visual Studio Code Editor, except without parameter names.</span></span> <span data-ttu-id="98425-139">當您以互動方式使用時，解譯器 fsi.exe，也會顯示型別簽章。</span><span class="sxs-lookup"><span data-stu-id="98425-139">Type signatures are also displayed by the interpreter, fsi.exe, when you are working interactively.</span></span> <span data-ttu-id="98425-140">方法的型別簽章是 out 參數，後面接著傳回的型別，使用適當的分隔符號類型的清單所形成的。</span><span class="sxs-lookup"><span data-stu-id="98425-140">The type signature of a method is formed by listing out the types of the parameters, followed by the return type, with appropriate separator symbols.</span></span> <span data-ttu-id="98425-141">局部調用的參數會以分隔`->`並以分隔 tuple 參數`*`。</span><span class="sxs-lookup"><span data-stu-id="98425-141">Curried parameters are separated by `->` and tuple parameters are separated by `*`.</span></span> <span data-ttu-id="98425-142">傳回值一律會分開的引數`->`符號。</span><span class="sxs-lookup"><span data-stu-id="98425-142">The return value is always separated from the arguments by a `->` symbol.</span></span> <span data-ttu-id="98425-143">可以用括號，將複雜的參數，例如，當函式型別為參數，或表示做為單一參數，而不是兩個參數，當處理 tuple。</span><span class="sxs-lookup"><span data-stu-id="98425-143">Parentheses can be used to group complex parameters, such as when a function type is a parameter, or to indicate when a tuple is treated as a single parameter rather than as two parameters.</span></span>

<span data-ttu-id="98425-144">您也可以讓抽象方法 default 定義加入至類別的定義並使用`default`關鍵字，如本主題中的語法區塊所示。</span><span class="sxs-lookup"><span data-stu-id="98425-144">You can also give abstract methods default definitions by adding the definition to the class and using the `default` keyword, as shown in the syntax block in this topic.</span></span> <span data-ttu-id="98425-145">相同類別中有定義的抽象方法相當於其他.NET Framework 語言中的虛擬方法。</span><span class="sxs-lookup"><span data-stu-id="98425-145">An abstract method that has a definition in the same class is equivalent to a virtual method in other .NET Framework languages.</span></span> <span data-ttu-id="98425-146">定義是否存在，`abstract`關鍵字會建立一個新分派位置虛擬函式資料表中的類別。</span><span class="sxs-lookup"><span data-stu-id="98425-146">Whether or not a definition exists, the `abstract` keyword creates a new dispatch slot in the virtual function table for the class.</span></span>

<span data-ttu-id="98425-147">不論是否基底類別實作其抽象方法，衍生的類別可以提供抽象方法的實作。</span><span class="sxs-lookup"><span data-stu-id="98425-147">Regardless of whether a base class implements its abstract methods, derived classes can provide implementations of abstract methods.</span></span> <span data-ttu-id="98425-148">若要在衍生類別中實作抽象方法，定義在衍生類別中，除了使用具有相同名稱和簽章的方法`override`或`default`關鍵字，並提供方法主體。</span><span class="sxs-lookup"><span data-stu-id="98425-148">To implement an abstract method in a derived class, define a method that has the same name and signature in the derived class, except use the `override` or `default` keyword, and provide the method body.</span></span> <span data-ttu-id="98425-149">關鍵字`override`和`default`表示完全相同的動作。</span><span class="sxs-lookup"><span data-stu-id="98425-149">The keywords `override` and `default` mean exactly the same thing.</span></span> <span data-ttu-id="98425-150">使用 `override`新的方法會覆寫基底類別實作; 如果使用`default`當您建立實作在與原始的抽象宣告相同的類別。</span><span class="sxs-lookup"><span data-stu-id="98425-150">Use `override` if the new method overrides a base class implementation; use `default` when you create an implementation in the same class as the original abstract declaration.</span></span> <span data-ttu-id="98425-151">請勿使用`abstract`方法會實作已宣告為抽象基底類別中的方法上的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="98425-151">Do not use the `abstract` keyword on the method that implements the method that was declared abstract in the base class.</span></span>

<span data-ttu-id="98425-152">下列範例說明抽象方法`Rotate`，其預設實作，相當於.NET Framework 的虛擬方法。</span><span class="sxs-lookup"><span data-stu-id="98425-152">The following example illustrates an abstract method `Rotate` that has a default implementation, the equivalent of a .NET Framework virtual method.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3403.fs)]

<span data-ttu-id="98425-153">下列範例說明在衍生的類別會覆寫基底類別方法。</span><span class="sxs-lookup"><span data-stu-id="98425-153">The following example illustrates a derived class that overrides a base class method.</span></span> <span data-ttu-id="98425-154">在此情況下，覆寫變更的行為，使方法不做任何動作。</span><span class="sxs-lookup"><span data-stu-id="98425-154">In this case, the override changes the behavior so that the method does nothing.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3404.fs)]

## <a name="overloaded-methods"></a><span data-ttu-id="98425-155">多載的方法</span><span class="sxs-lookup"><span data-stu-id="98425-155">Overloaded Methods</span></span>

<span data-ttu-id="98425-156">多載的方法是指定的型別中具有相同名稱但有不同的引數的方法。</span><span class="sxs-lookup"><span data-stu-id="98425-156">Overloaded methods are methods that have identical names in a given type but that have different arguments.</span></span> <span data-ttu-id="98425-157">在F#，而不是多載的方法通常用於選擇性引數。</span><span class="sxs-lookup"><span data-stu-id="98425-157">In F#, optional arguments are usually used instead of overloaded methods.</span></span> <span data-ttu-id="98425-158">不過，多載的方法允許在語言中，前提是引數是 tuple 形式，不局部調用形式。</span><span class="sxs-lookup"><span data-stu-id="98425-158">However, overloaded methods are permitted in the language, provided that the arguments are in tuple form, not curried form.</span></span>

## <a name="optional-arguments"></a><span data-ttu-id="98425-159">選擇性引數</span><span class="sxs-lookup"><span data-stu-id="98425-159">Optional Arguments</span></span>

<span data-ttu-id="98425-160">開頭為F#4.1，您也可以在方法中有預設參數值的選擇性引數。</span><span class="sxs-lookup"><span data-stu-id="98425-160">Starting with F# 4.1, you can also have optional arguments with a default parameter value in methods.</span></span>  <span data-ttu-id="98425-161">這是為了協助使用 C# 程式碼的互通性。</span><span class="sxs-lookup"><span data-stu-id="98425-161">This is to help facilitate interoperation with C# code.</span></span>  <span data-ttu-id="98425-162">下列範例示範的語法：</span><span class="sxs-lookup"><span data-stu-id="98425-162">The following example demonstrates the syntax:</span></span>

```fsharp
// A class with a method M, which takes in an optional integer argument.
type C() =
    __.M([<Optional; DefaultParameterValue(12)>] i) = i + 1
```

<span data-ttu-id="98425-163">請注意，傳入的值`DefaultParameterValue`必須符合的輸入的類型。</span><span class="sxs-lookup"><span data-stu-id="98425-163">Note that the value passed in for `DefaultParameterValue` must match the input type.</span></span>  <span data-ttu-id="98425-164">在上述範例中，它是`int`。</span><span class="sxs-lookup"><span data-stu-id="98425-164">In the above sample, it is an `int`.</span></span>  <span data-ttu-id="98425-165">嘗試傳遞非整數值至`DefaultParameterValue`會導致編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="98425-165">Attempting to pass a non-integer value into `DefaultParameterValue` would result in a compile error.</span></span>

## <a name="example-properties-and-methods"></a><span data-ttu-id="98425-166">範例：屬性和方法</span><span class="sxs-lookup"><span data-stu-id="98425-166">Example: Properties and Methods</span></span>

<span data-ttu-id="98425-167">下列範例包含具有範例的欄位、 私用函式、 屬性和靜態方法的類型。</span><span class="sxs-lookup"><span data-stu-id="98425-167">The following example contains a type that has examples of fields, private functions, properties, and a static method.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3406.fs)]

## <a name="see-also"></a><span data-ttu-id="98425-168">另請參閱</span><span class="sxs-lookup"><span data-stu-id="98425-168">See also</span></span>

- [<span data-ttu-id="98425-169">成員</span><span class="sxs-lookup"><span data-stu-id="98425-169">Members</span></span>](index.md)