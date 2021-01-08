---
title: 類別
description: '瞭解 F # 類別是代表可以有屬性、方法和事件之物件的類型。'
ms.date: 05/16/2016
ms.openlocfilehash: fd6638e0f1c08cf667a73582e19b2bb5bba46e20
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970163"
---
# <a name="classes"></a><span data-ttu-id="c6f93-103">類別</span><span class="sxs-lookup"><span data-stu-id="c6f93-103">Classes</span></span>

<span data-ttu-id="c6f93-104">*類別* 是代表可以有屬性、方法和事件之物件的類型。</span><span class="sxs-lookup"><span data-stu-id="c6f93-104">*Classes* are types that represent objects that can have properties, methods, and events.</span></span>

## <a name="syntax"></a><span data-ttu-id="c6f93-105">語法</span><span class="sxs-lookup"><span data-stu-id="c6f93-105">Syntax</span></span>

```fsharp
// Class definition:
type [access-modifier] type-name [type-params] [access-modifier] ( parameter-list ) [ as identifier ] =
[ class ]
[ inherit base-type-name(base-constructor-args) ]
[ let-bindings ]
[ do-bindings ]
member-list
...
[ end ]
// Mutually recursive class definitions:
type [access-modifier] type-name1 ...
and [access-modifier] type-name2 ...
...
```

## <a name="remarks"></a><span data-ttu-id="c6f93-106">備註</span><span class="sxs-lookup"><span data-stu-id="c6f93-106">Remarks</span></span>

<span data-ttu-id="c6f93-107">類別代表 .NET 物件類型的基本描述;類別是一種主要類型概念，支援 F # 中的物件導向程式設計。</span><span class="sxs-lookup"><span data-stu-id="c6f93-107">Classes represent the fundamental description of .NET object types; the class is the primary type concept that supports object-oriented programming in F#.</span></span>

<span data-ttu-id="c6f93-108">在上述語法中， `type-name` 是任何有效的識別碼。</span><span class="sxs-lookup"><span data-stu-id="c6f93-108">In the preceding syntax, the `type-name` is any valid identifier.</span></span> <span data-ttu-id="c6f93-109">`type-params`描述選擇性的泛型型別參數。</span><span class="sxs-lookup"><span data-stu-id="c6f93-109">The `type-params` describes optional generic type parameters.</span></span> <span data-ttu-id="c6f93-110">它包含以角括弧括住的型別參數名稱和條件約束 (`<` 和 `>`) 。</span><span class="sxs-lookup"><span data-stu-id="c6f93-110">It consists of type parameter names and constraints enclosed in angle brackets (`<` and `>`).</span></span> <span data-ttu-id="c6f93-111">如需詳細資訊，請參閱 [泛型](./generics/index.md) 和 [條件約束](./generics/constraints.md)。</span><span class="sxs-lookup"><span data-stu-id="c6f93-111">For more information, see [Generics](./generics/index.md) and [Constraints](./generics/constraints.md).</span></span> <span data-ttu-id="c6f93-112">描述函式 `parameter-list` 參數。</span><span class="sxs-lookup"><span data-stu-id="c6f93-112">The `parameter-list` describes constructor parameters.</span></span> <span data-ttu-id="c6f93-113">第一個存取修飾詞與類型有關。第二個則是主要的函式。</span><span class="sxs-lookup"><span data-stu-id="c6f93-113">The first access modifier pertains to the type; the second pertains to the primary constructor.</span></span> <span data-ttu-id="c6f93-114">在這兩種情況下，預設值為 `public` 。</span><span class="sxs-lookup"><span data-stu-id="c6f93-114">In both cases, the default is `public`.</span></span>

<span data-ttu-id="c6f93-115">您可以使用關鍵字來指定類別的基類 `inherit` 。</span><span class="sxs-lookup"><span data-stu-id="c6f93-115">You specify the base class for a class by using the `inherit` keyword.</span></span> <span data-ttu-id="c6f93-116">您必須為基類的函式提供引數（以括弧括住）。</span><span class="sxs-lookup"><span data-stu-id="c6f93-116">You must supply arguments, in parentheses, for the base class constructor.</span></span>

<span data-ttu-id="c6f93-117">您可以使用系結來宣告類別本機的欄位或函式值 `let` ，而且必須遵循系結的一般規則 `let` 。</span><span class="sxs-lookup"><span data-stu-id="c6f93-117">You declare fields or function values that are local to the class by using `let` bindings, and you must follow the general rules for `let` bindings.</span></span> <span data-ttu-id="c6f93-118">`do-bindings`區段包含要在物件結構上執行的程式碼。</span><span class="sxs-lookup"><span data-stu-id="c6f93-118">The `do-bindings` section includes code to be executed upon object construction.</span></span>

<span data-ttu-id="c6f93-119">`member-list`包含其他的函式、實例和靜態方法宣告、介面宣告、抽象系結，以及屬性和事件宣告。</span><span class="sxs-lookup"><span data-stu-id="c6f93-119">The `member-list` consists of additional constructors, instance and static method declarations, interface declarations, abstract bindings, and property and event declarations.</span></span> <span data-ttu-id="c6f93-120">這些是 [成員](./members/index.md)中的描述。</span><span class="sxs-lookup"><span data-stu-id="c6f93-120">These are described in [Members](./members/index.md).</span></span>

<span data-ttu-id="c6f93-121">搭配 `identifier` 選擇性關鍵字使用的會 `as` 提供執行個體變數的名稱或本身的識別碼，可在類型定義中用來參考該類型的實例。</span><span class="sxs-lookup"><span data-stu-id="c6f93-121">The `identifier` that is used with the optional `as` keyword gives a name to the instance variable, or self identifier, which can be used in the type definition to refer to the instance of the type.</span></span> <span data-ttu-id="c6f93-122">如需詳細資訊，請參閱本主題稍後的「自我識別碼」一節。</span><span class="sxs-lookup"><span data-stu-id="c6f93-122">For more information, see the section Self Identifiers later in this topic.</span></span>

<span data-ttu-id="c6f93-123">`class` `end` 標示定義開始和結束的關鍵字是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="c6f93-123">The keywords `class` and `end` that mark the start and end of the definition are optional.</span></span>

<span data-ttu-id="c6f93-124">相互遞迴的型別（也就是彼此參考的型別）會與關鍵字聯結在一起， `and` 就像互相遞迴函數一樣。</span><span class="sxs-lookup"><span data-stu-id="c6f93-124">Mutually recursive types, which are types that reference each other, are joined together with the `and` keyword just as mutually recursive functions are.</span></span> <span data-ttu-id="c6f93-125">如需範例，請參閱「相互遞迴類型」一節。</span><span class="sxs-lookup"><span data-stu-id="c6f93-125">For an example, see the section Mutually Recursive Types.</span></span>

## <a name="constructors"></a><span data-ttu-id="c6f93-126">建構函式</span><span class="sxs-lookup"><span data-stu-id="c6f93-126">Constructors</span></span>

<span data-ttu-id="c6f93-127">此函式是建立類別型別實例的程式碼。</span><span class="sxs-lookup"><span data-stu-id="c6f93-127">The constructor is code that creates an instance of the class type.</span></span> <span data-ttu-id="c6f93-128">類別的函式在 F # 中的運作方式與其他 .NET 語言中的運作方式稍有不同。</span><span class="sxs-lookup"><span data-stu-id="c6f93-128">Constructors for classes work somewhat differently in F# than they do in other .NET languages.</span></span> <span data-ttu-id="c6f93-129">在 F # 類別中，一律會有一個主要的函式，其中的引數會在 `parameter-list` 型別名稱後面，且主體是由 `let` 類別宣告開頭的 (和) 系結 `let rec` ，以及 `do` 接下來的系結所組成。</span><span class="sxs-lookup"><span data-stu-id="c6f93-129">In an F# class, there is always a primary constructor whose arguments are described in the `parameter-list` that follows the type name, and whose body consists of the `let` (and `let rec`) bindings at the start of the class declaration and the `do` bindings that follow.</span></span> <span data-ttu-id="c6f93-130">主要函式的引數位於整個類別宣告的範圍內。</span><span class="sxs-lookup"><span data-stu-id="c6f93-130">The arguments of the primary constructor are in scope throughout the class declaration.</span></span>

<span data-ttu-id="c6f93-131">您可以使用關鍵字加入其他的函式 `new` ，以新增成員，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c6f93-131">You can add additional constructors by using the `new` keyword to add a member, as follows:</span></span>

<span data-ttu-id="c6f93-132">`new`(`argument-list`) = `constructor-body`</span><span class="sxs-lookup"><span data-stu-id="c6f93-132">`new`(`argument-list`) = `constructor-body`</span></span>

<span data-ttu-id="c6f93-133">新的函式主體必須叫用在類別宣告頂端指定的主要函式。</span><span class="sxs-lookup"><span data-stu-id="c6f93-133">The body of the new constructor must invoke the primary constructor that is specified at the top of the class declaration.</span></span>

<span data-ttu-id="c6f93-134">下列範例將說明這個概念。</span><span class="sxs-lookup"><span data-stu-id="c6f93-134">The following example illustrates this concept.</span></span> <span data-ttu-id="c6f93-135">在下列程式碼中， `MyClass` 有兩個函式，這是採用兩個引數的主要函式，以及不接受引數的另一個函式。</span><span class="sxs-lookup"><span data-stu-id="c6f93-135">In the following code, `MyClass` has two constructors, a primary constructor that takes two arguments and another constructor that takes no arguments.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2401.fs)]

## <a name="let-and-do-bindings"></a><span data-ttu-id="c6f93-136">let 和 do 系結</span><span class="sxs-lookup"><span data-stu-id="c6f93-136">let and do Bindings</span></span>

<span data-ttu-id="c6f93-137">`let`類別定義中的和系結 `do` 會形成主要類別的函式內文，因此每當建立類別實例時，就會執行這些系結。</span><span class="sxs-lookup"><span data-stu-id="c6f93-137">The `let` and `do` bindings in a class definition form the body of the primary class constructor, and therefore they run whenever a class instance is created.</span></span> <span data-ttu-id="c6f93-138">如果系結 `let` 是函數，則會將它編譯成成員。</span><span class="sxs-lookup"><span data-stu-id="c6f93-138">If a `let` binding is a function, then it is compiled into a member.</span></span> <span data-ttu-id="c6f93-139">如果系結 `let` 是未在任何函式或成員中使用的值，則會將它編譯成函式的本機變數。</span><span class="sxs-lookup"><span data-stu-id="c6f93-139">If the `let` binding is a value that is not used in any function or member, then it is compiled into a variable that is local to the constructor.</span></span> <span data-ttu-id="c6f93-140">否則，它會編譯成類別的欄位。</span><span class="sxs-lookup"><span data-stu-id="c6f93-140">Otherwise, it is compiled into a field of the class.</span></span> <span data-ttu-id="c6f93-141">`do`接下來的運算式會編譯成主要的函式，並對每個實例執行初始化程式碼。</span><span class="sxs-lookup"><span data-stu-id="c6f93-141">The `do` expressions that follow are compiled into the primary constructor and execute initialization code for every instance.</span></span> <span data-ttu-id="c6f93-142">因為任何其他的函式一律會呼叫主要的函式，所以不論呼叫哪一個函式，系結和系結 `let` `do` 一律都會執行。</span><span class="sxs-lookup"><span data-stu-id="c6f93-142">Because any additional constructors always call the primary constructor, the `let` bindings and `do` bindings always execute regardless of which constructor is called.</span></span>

<span data-ttu-id="c6f93-143">系結所建立的欄位 `let` 可以在類別的方法和屬性中存取，不過，即使靜態方法採用執行個體變數作為參數，也無法從靜態方法存取這些欄位。</span><span class="sxs-lookup"><span data-stu-id="c6f93-143">Fields that are created by `let` bindings can be accessed throughout the methods and properties of the class; however, they cannot be accessed from static methods, even if the static methods take an instance variable as a parameter.</span></span> <span data-ttu-id="c6f93-144">如果有的話，就無法使用自我識別碼來存取它們。</span><span class="sxs-lookup"><span data-stu-id="c6f93-144">They cannot be accessed by using the self identifier, if one exists.</span></span>

## <a name="self-identifiers"></a><span data-ttu-id="c6f93-145">自我識別碼</span><span class="sxs-lookup"><span data-stu-id="c6f93-145">Self Identifiers</span></span>

<span data-ttu-id="c6f93-146">*自我識別碼* 是表示目前實例的名稱。</span><span class="sxs-lookup"><span data-stu-id="c6f93-146">A *self identifier* is a name that represents the current instance.</span></span> <span data-ttu-id="c6f93-147">自我識別碼與 `this` c # 或 c + + 或 `Me` Visual Basic 中的關鍵字類似。</span><span class="sxs-lookup"><span data-stu-id="c6f93-147">Self identifiers resemble the `this` keyword in C# or C++ or `Me` in Visual Basic.</span></span> <span data-ttu-id="c6f93-148">您可以使用兩種不同的方式來定義自我識別碼，視您是否要讓自我識別碼位於整個類別定義的範圍中，或僅針對個別的方法而定。</span><span class="sxs-lookup"><span data-stu-id="c6f93-148">You can define a self identifier in two different ways, depending on whether you want the self identifier to be in scope for the whole class definition or just for an individual method.</span></span>

<span data-ttu-id="c6f93-149">若要定義整個類別的自我識別碼，請在 [函式 `as` 參數清單] 的右括弧後面使用關鍵字，並指定識別碼名稱。</span><span class="sxs-lookup"><span data-stu-id="c6f93-149">To define a self identifier for the whole class, use the `as` keyword after the closing parentheses of the constructor parameter list, and specify the identifier name.</span></span>

<span data-ttu-id="c6f93-150">若只要定義一個方法的自我識別碼，請在方法名稱和句點 ( 之前，在成員宣告中提供自我識別碼。 ) 為分隔符號。</span><span class="sxs-lookup"><span data-stu-id="c6f93-150">To define a self identifier for just one method, provide the self identifier in the member declaration, just before the method name and a period (.) as a separator.</span></span>

<span data-ttu-id="c6f93-151">下列程式碼範例說明建立自我識別碼的兩種方式。</span><span class="sxs-lookup"><span data-stu-id="c6f93-151">The following code example illustrates the two ways to create a self identifier.</span></span> <span data-ttu-id="c6f93-152">在第一行中， `as` 關鍵字是用來定義自我識別碼。</span><span class="sxs-lookup"><span data-stu-id="c6f93-152">In the first line, the `as` keyword is used to define the self identifier.</span></span> <span data-ttu-id="c6f93-153">在第五行中，識別碼 `this` 是用來定義其範圍限制為方法的自我識別碼 `PrintMessage` 。</span><span class="sxs-lookup"><span data-stu-id="c6f93-153">In the fifth line, the identifier `this` is used to define a self identifier whose scope is restricted to the method `PrintMessage`.</span></span>

```fsharp
type MyClass2(dataIn) as self =
    let data = dataIn
    do
        self.PrintMessage()
    member this.PrintMessage() =
        printf "Creating MyClass2 with Data %d" data
```

<span data-ttu-id="c6f93-154">不同于其他 .NET 語言，您可以在想要的情況下命名自我識別碼;您不受限於、或之類的 `self` 名稱 `Me` `this` 。</span><span class="sxs-lookup"><span data-stu-id="c6f93-154">Unlike in other .NET languages, you can name the self identifier however you want; you are not restricted to names such as `self`, `Me`, or `this`.</span></span>

<span data-ttu-id="c6f93-155">使用關鍵字宣告的自我識別碼，在 `as` 基底的函式之前都不會初始化。</span><span class="sxs-lookup"><span data-stu-id="c6f93-155">The self identifier that is declared with the `as` keyword is not initialized until after the base constructor.</span></span> <span data-ttu-id="c6f93-156">因此，在基底函式之前或內部使用時， `System.InvalidOperationException: The initialization of an object or value resulted in an object or value being accessed recursively before it was fully initialized.` 會在執行時間引發。</span><span class="sxs-lookup"><span data-stu-id="c6f93-156">Therefore, when used before or inside the base constructor, `System.InvalidOperationException: The initialization of an object or value resulted in an object or value being accessed recursively before it was fully initialized.` will be raised during runtime.</span></span> <span data-ttu-id="c6f93-157">您可以在基底的函式之後自由使用自我識別碼，例如在系結或系結中 `let` `do` 。</span><span class="sxs-lookup"><span data-stu-id="c6f93-157">You can use the self identifier freely after the base constructor, such as in `let` bindings or `do` bindings.</span></span>

## <a name="generic-type-parameters"></a><span data-ttu-id="c6f93-158">泛型類型參數</span><span class="sxs-lookup"><span data-stu-id="c6f93-158">Generic Type Parameters</span></span>

<span data-ttu-id="c6f93-159">泛型型別參數是以角括弧 (`<` 和 `>`) 來指定，並以單引號的形式加上識別碼。</span><span class="sxs-lookup"><span data-stu-id="c6f93-159">Generic type parameters are specified in angle brackets (`<` and `>`), in the form of a single quotation mark followed by an identifier.</span></span> <span data-ttu-id="c6f93-160">多個泛型型別參數會以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="c6f93-160">Multiple generic type parameters are separated by commas.</span></span> <span data-ttu-id="c6f93-161">泛型型別參數在整個宣告的範圍中。</span><span class="sxs-lookup"><span data-stu-id="c6f93-161">The generic type parameter is in scope throughout the declaration.</span></span> <span data-ttu-id="c6f93-162">下列程式碼範例示範如何指定泛型型別參數。</span><span class="sxs-lookup"><span data-stu-id="c6f93-162">The following code example shows how to specify generic type parameters.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2403.fs)]

<span data-ttu-id="c6f93-163">使用型別時，會推斷型別引數。</span><span class="sxs-lookup"><span data-stu-id="c6f93-163">Type arguments are inferred when the type is used.</span></span> <span data-ttu-id="c6f93-164">在下列程式碼中，推斷的型別是一系列的元組。</span><span class="sxs-lookup"><span data-stu-id="c6f93-164">In the following code, the inferred type is a sequence of tuples.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet24031.fs)]

## <a name="specifying-inheritance"></a><span data-ttu-id="c6f93-165">指定繼承</span><span class="sxs-lookup"><span data-stu-id="c6f93-165">Specifying Inheritance</span></span>

<span data-ttu-id="c6f93-166">`inherit`子句會識別直接基類（如果有的話）。</span><span class="sxs-lookup"><span data-stu-id="c6f93-166">The `inherit` clause identifies the direct base class, if there is one.</span></span> <span data-ttu-id="c6f93-167">在 F # 中，只允許一個直接基類。</span><span class="sxs-lookup"><span data-stu-id="c6f93-167">In F#, only one direct base class is allowed.</span></span> <span data-ttu-id="c6f93-168">類別所執行的介面不會被視為基類。</span><span class="sxs-lookup"><span data-stu-id="c6f93-168">Interfaces that a class implements are not considered base classes.</span></span> <span data-ttu-id="c6f93-169">[介面主題中](Interfaces.md)會討論介面。</span><span class="sxs-lookup"><span data-stu-id="c6f93-169">Interfaces are discussed in the [Interfaces](Interfaces.md) topic.</span></span>

<span data-ttu-id="c6f93-170">您可以從衍生類別存取基類的方法和屬性，方法是使用 language 關鍵字 `base` 做為識別碼，後面接著一個句點 (。 ) 和成員的名稱。</span><span class="sxs-lookup"><span data-stu-id="c6f93-170">You can access the methods and properties of the base class from the derived class by using the language keyword `base` as an identifier, followed by a period (.) and the name of the member.</span></span>

<span data-ttu-id="c6f93-171">如需詳細資訊，請參閱[繼承](inheritance.md)。</span><span class="sxs-lookup"><span data-stu-id="c6f93-171">For more information, see [Inheritance](inheritance.md).</span></span>

## <a name="members-section"></a><span data-ttu-id="c6f93-172">成員區段</span><span class="sxs-lookup"><span data-stu-id="c6f93-172">Members Section</span></span>

<span data-ttu-id="c6f93-173">您可以在本節中定義靜態或實例方法、屬性、介面執行、抽象成員、事件宣告和其他的函式。</span><span class="sxs-lookup"><span data-stu-id="c6f93-173">You can define static or instance methods, properties, interface implementations, abstract members, event declarations, and additional constructors in this section.</span></span> <span data-ttu-id="c6f93-174">此區段中不能出現 Let 和 do 系結。</span><span class="sxs-lookup"><span data-stu-id="c6f93-174">Let and do bindings cannot appear in this section.</span></span> <span data-ttu-id="c6f93-175">因為成員可以新增至類別以外的各種 F # 型別，所以會在個別的主題中討論 [成員](./members/index.md)。</span><span class="sxs-lookup"><span data-stu-id="c6f93-175">Because members can be added to a variety of F# types in addition to classes, they are discussed in a separate topic, [Members](./members/index.md).</span></span>

## <a name="mutually-recursive-types"></a><span data-ttu-id="c6f93-176">相互遞迴類型</span><span class="sxs-lookup"><span data-stu-id="c6f93-176">Mutually Recursive Types</span></span>

<span data-ttu-id="c6f93-177">當您定義以迴圈方式參考彼此的型別時，您可以使用關鍵字將型別定義組成一串 `and` 。</span><span class="sxs-lookup"><span data-stu-id="c6f93-177">When you define types that reference each other in a circular way, you string together the type definitions by using the `and` keyword.</span></span> <span data-ttu-id="c6f93-178">`and`關鍵字會取代 `type` 第一個定義以外的所有關鍵詞，如下所示。</span><span class="sxs-lookup"><span data-stu-id="c6f93-178">The `and` keyword replaces the `type` keyword on all except the first definition, as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2404.fs)]

<span data-ttu-id="c6f93-179">輸出是目前目錄中所有檔案的清單。</span><span class="sxs-lookup"><span data-stu-id="c6f93-179">The output is a list of all the files in the current directory.</span></span>

## <a name="when-to-use-classes-unions-records-and-structures"></a><span data-ttu-id="c6f93-180">使用類別、等位、記錄和結構的時機</span><span class="sxs-lookup"><span data-stu-id="c6f93-180">When to Use Classes, Unions, Records, and Structures</span></span>

<span data-ttu-id="c6f93-181">由於有各種類型可供選擇，因此您需要充分瞭解每種類型的設計目的，以針對特定情況選取適當的類型。</span><span class="sxs-lookup"><span data-stu-id="c6f93-181">Given the variety of types to choose from, you need to have a good understanding of what each type is designed for to select the appropriate type for a particular situation.</span></span> <span data-ttu-id="c6f93-182">類別是設計用來在物件導向程式設計環境中使用。</span><span class="sxs-lookup"><span data-stu-id="c6f93-182">Classes are designed for use in object-oriented programming contexts.</span></span> <span data-ttu-id="c6f93-183">物件導向程式設計是針對 .NET Framework 所撰寫的應用程式中所使用的主要範例。</span><span class="sxs-lookup"><span data-stu-id="c6f93-183">Object-oriented programming is the dominant paradigm used in applications that are written for the .NET Framework.</span></span> <span data-ttu-id="c6f93-184">如果您的 F # 程式碼必須與 .NET Framework 或另一個物件導向的程式庫密切合作，特別是當您必須從物件導向的型別系統（例如 UI 程式庫）延伸時，類別可能很適合。</span><span class="sxs-lookup"><span data-stu-id="c6f93-184">If your F# code has to work closely with the .NET Framework or another object-oriented library, and especially if you have to extend from an object-oriented type system such as a UI library, classes are probably appropriate.</span></span>

<span data-ttu-id="c6f93-185">如果您未與物件導向程式碼緊密地互通，或您正在撰寫獨立的程式碼，因而受到保護而無法經常與物件導向程式碼互動，您應該考慮使用記錄和區分等位。</span><span class="sxs-lookup"><span data-stu-id="c6f93-185">If you are not interoperating closely with object-oriented code, or if you are writing code that is self-contained and therefore protected from frequent interaction with object-oriented code, you should consider using records and discriminated unions.</span></span> <span data-ttu-id="c6f93-186">您可以使用一種簡單的方法，也就是使用適當的模式比對程式碼，將其視為更簡單的物件階層替代方法。</span><span class="sxs-lookup"><span data-stu-id="c6f93-186">A single, well thought–out discriminated union, together with appropriate pattern matching code, can often be used as a simpler alternative to an object hierarchy.</span></span> <span data-ttu-id="c6f93-187">如需差異聯集的詳細資訊，請參閱 [區分](discriminated-unions.md)聯集。</span><span class="sxs-lookup"><span data-stu-id="c6f93-187">For more information about discriminated unions, see [Discriminated Unions](discriminated-unions.md).</span></span>

<span data-ttu-id="c6f93-188">記錄的優點是比類別更簡單，但是當類型的需求超過其簡單的需求時，記錄就不適用。</span><span class="sxs-lookup"><span data-stu-id="c6f93-188">Records have the advantage of being simpler than classes, but records are not appropriate when the demands of a type exceed what can be accomplished with their simplicity.</span></span> <span data-ttu-id="c6f93-189">記錄基本上是值的簡單匯總，沒有可執行自訂動作的個別函式，而不需要隱藏的欄位，也不需要繼承或介面。</span><span class="sxs-lookup"><span data-stu-id="c6f93-189">Records are basically simple aggregates of values, without separate constructors that can perform custom actions, without hidden fields, and without inheritance or interface implementations.</span></span> <span data-ttu-id="c6f93-190">雖然可以將屬性和方法等成員新增至記錄，以使其行為更複雜，但儲存在記錄中的欄位仍是值的簡單匯總。</span><span class="sxs-lookup"><span data-stu-id="c6f93-190">Although members such as properties and methods can be added to records to make their behavior more complex, the fields stored in a record are still a simple aggregate of values.</span></span> <span data-ttu-id="c6f93-191">如需記錄的詳細資訊，請參閱 [記錄](records.md)。</span><span class="sxs-lookup"><span data-stu-id="c6f93-191">For more information about records, see [Records](records.md).</span></span>

<span data-ttu-id="c6f93-192">結構也適用于小型資料匯總，但它們與類別和記錄不同，因為它們是 .NET 實數值型別。</span><span class="sxs-lookup"><span data-stu-id="c6f93-192">Structures are also useful for small aggregates of data, but they differ from classes and records in that they are .NET value types.</span></span> <span data-ttu-id="c6f93-193">類別和記錄是 .NET 參考型別。</span><span class="sxs-lookup"><span data-stu-id="c6f93-193">Classes and records are .NET reference types.</span></span> <span data-ttu-id="c6f93-194">實值型別和參考型別的語義在實值型別是以傳值方式傳遞的。</span><span class="sxs-lookup"><span data-stu-id="c6f93-194">The semantics of value types and reference types are different in that value types are passed by value.</span></span> <span data-ttu-id="c6f93-195">這表示當其以參數形式傳遞或從函式傳回時，會為位複製位。</span><span class="sxs-lookup"><span data-stu-id="c6f93-195">This means that they are copied bit for bit when they are passed as a parameter or returned from a function.</span></span> <span data-ttu-id="c6f93-196">它們也會儲存在堆疊上，或者，如果當做欄位使用，則內嵌于父物件中，而不是儲存在堆積上的個別位置。</span><span class="sxs-lookup"><span data-stu-id="c6f93-196">They are also stored on the stack or, if they are used as a field, embedded inside the parent object instead of stored in their own separate location on the heap.</span></span> <span data-ttu-id="c6f93-197">因此，當存取堆積的額外負荷發生問題時，結構適用于經常存取的資料。</span><span class="sxs-lookup"><span data-stu-id="c6f93-197">Therefore, structures are appropriate for frequently accessed data when the overhead of accessing the heap is a problem.</span></span> <span data-ttu-id="c6f93-198">如需結構的詳細資訊，請參閱 [結構](structures.md)。</span><span class="sxs-lookup"><span data-stu-id="c6f93-198">For more information about structures, see [Structures](structures.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c6f93-199">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c6f93-199">See also</span></span>

- [<span data-ttu-id="c6f93-200">F # 語言參考</span><span class="sxs-lookup"><span data-stu-id="c6f93-200">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="c6f93-201">成員</span><span class="sxs-lookup"><span data-stu-id="c6f93-201">Members</span></span>](./members/index.md)
- [<span data-ttu-id="c6f93-202">繼承</span><span class="sxs-lookup"><span data-stu-id="c6f93-202">Inheritance</span></span>](inheritance.md)
- [<span data-ttu-id="c6f93-203">介面</span><span class="sxs-lookup"><span data-stu-id="c6f93-203">Interfaces</span></span>](interfaces.md)
