---
title: 類別
description: 瞭解類別F#如何代表可以有屬性、方法和事件的物件。
ms.date: 05/16/2016
ms.openlocfilehash: 5c012d028bc1f89e3e9f5969b3461faab9aad3a0
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630451"
---
# <a name="classes"></a><span data-ttu-id="431ce-103">類別</span><span class="sxs-lookup"><span data-stu-id="431ce-103">Classes</span></span>

<span data-ttu-id="431ce-104">*類別*是代表可以具有屬性、方法和事件之物件的類型。</span><span class="sxs-lookup"><span data-stu-id="431ce-104">*Classes* are types that represent objects that can have properties, methods, and events.</span></span>

## <a name="syntax"></a><span data-ttu-id="431ce-105">語法</span><span class="sxs-lookup"><span data-stu-id="431ce-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="431ce-106">備註</span><span class="sxs-lookup"><span data-stu-id="431ce-106">Remarks</span></span>

<span data-ttu-id="431ce-107">類別代表 .NET 物件類型的基本描述;類別是在中F#支援物件導向程式設計的主要類型概念。</span><span class="sxs-lookup"><span data-stu-id="431ce-107">Classes represent the fundamental description of .NET object types; the class is the primary type concept that supports object-oriented programming in F#.</span></span>

<span data-ttu-id="431ce-108">在上述語法中, 是`type-name`任何有效的識別碼。</span><span class="sxs-lookup"><span data-stu-id="431ce-108">In the preceding syntax, the `type-name` is any valid identifier.</span></span> <span data-ttu-id="431ce-109">描述`type-params`選擇性的泛型型別參數。</span><span class="sxs-lookup"><span data-stu-id="431ce-109">The `type-params` describes optional generic type parameters.</span></span> <span data-ttu-id="431ce-110">其包含以角括弧 (`<`和`>`) 括住的類型參數名稱和條件約束。</span><span class="sxs-lookup"><span data-stu-id="431ce-110">It consists of type parameter names and constraints enclosed in angle brackets (`<` and `>`).</span></span> <span data-ttu-id="431ce-111">如需詳細資訊, 請參閱[泛型](./generics/index.md)和[條件約束](./generics/constraints.md)。</span><span class="sxs-lookup"><span data-stu-id="431ce-111">For more information, see [Generics](./generics/index.md) and [Constraints](./generics/constraints.md).</span></span> <span data-ttu-id="431ce-112">描述`parameter-list`的是函數參數。</span><span class="sxs-lookup"><span data-stu-id="431ce-112">The `parameter-list` describes constructor parameters.</span></span> <span data-ttu-id="431ce-113">第一個存取修飾詞屬於類型;第二個則與主要的「函式」有關。</span><span class="sxs-lookup"><span data-stu-id="431ce-113">The first access modifier pertains to the type; the second pertains to the primary constructor.</span></span> <span data-ttu-id="431ce-114">在這兩種情況下, `public`預設值為。</span><span class="sxs-lookup"><span data-stu-id="431ce-114">In both cases, the default is `public`.</span></span>

<span data-ttu-id="431ce-115">您可以使用`inherit`關鍵字來指定類別的基類。</span><span class="sxs-lookup"><span data-stu-id="431ce-115">You specify the base class for a class by using the `inherit` keyword.</span></span> <span data-ttu-id="431ce-116">您必須為基類的參數提供引數 (以括弧括住)。</span><span class="sxs-lookup"><span data-stu-id="431ce-116">You must supply arguments, in parentheses, for the base class constructor.</span></span>

<span data-ttu-id="431ce-117">您可以使用`let`系結來宣告類別的本機欄位或函數值, 而且必須遵循系結的一般`let`規則。</span><span class="sxs-lookup"><span data-stu-id="431ce-117">You declare fields or function values that are local to the class by using `let` bindings, and you must follow the general rules for `let` bindings.</span></span> <span data-ttu-id="431ce-118">`do-bindings`區段包含要在物件結構上執行的程式碼。</span><span class="sxs-lookup"><span data-stu-id="431ce-118">The `do-bindings` section includes code to be executed upon object construction.</span></span>

<span data-ttu-id="431ce-119">`member-list`包含額外的函式、實例和靜態方法宣告、介面宣告、抽象系結, 以及屬性和事件宣告。</span><span class="sxs-lookup"><span data-stu-id="431ce-119">The `member-list` consists of additional constructors, instance and static method declarations, interface declarations, abstract bindings, and property and event declarations.</span></span> <span data-ttu-id="431ce-120">這些內容會在[成員](./members/index.md)中說明。</span><span class="sxs-lookup"><span data-stu-id="431ce-120">These are described in [Members](./members/index.md).</span></span>

<span data-ttu-id="431ce-121">搭配`identifier` 選擇性`as`關鍵字使用的會提供執行個體變數的名稱, 或自我識別碼, 可以在類型定義中用來參考該類型的實例。</span><span class="sxs-lookup"><span data-stu-id="431ce-121">The `identifier` that is used with the optional `as` keyword gives a name to the instance variable, or self identifier, which can be used in the type definition to refer to the instance of the type.</span></span> <span data-ttu-id="431ce-122">如需詳細資訊, 請參閱本主題稍後的「自我識別碼」一節。</span><span class="sxs-lookup"><span data-stu-id="431ce-122">For more information, see the section Self Identifiers later in this topic.</span></span>

<span data-ttu-id="431ce-123">關鍵字`class` 和`end`標示定義的開始和結束是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="431ce-123">The keywords `class` and `end` that mark the start and end of the definition are optional.</span></span>

<span data-ttu-id="431ce-124">相互遞迴類型 (互相參考的類型) 與`and`關鍵字聯結在一起, 就像是互相遞迴函式一樣。</span><span class="sxs-lookup"><span data-stu-id="431ce-124">Mutually recursive types, which are types that reference each other, are joined together with the `and` keyword just as mutually recursive functions are.</span></span> <span data-ttu-id="431ce-125">如需範例, 請參閱相互遞迴類型一節。</span><span class="sxs-lookup"><span data-stu-id="431ce-125">For an example, see the section Mutually Recursive Types.</span></span>

## <a name="constructors"></a><span data-ttu-id="431ce-126">建構函式</span><span class="sxs-lookup"><span data-stu-id="431ce-126">Constructors</span></span>

<span data-ttu-id="431ce-127">此函式是建立類別類型實例的程式碼。</span><span class="sxs-lookup"><span data-stu-id="431ce-127">The constructor is code that creates an instance of the class type.</span></span> <span data-ttu-id="431ce-128">類別的函式F#與其他 .net 語言的處理方式稍有不同。</span><span class="sxs-lookup"><span data-stu-id="431ce-128">Constructors for classes work somewhat differently in F# than they do in other .NET languages.</span></span> <span data-ttu-id="431ce-129">在F#類別中, 一律會有一個主要的函式, 其引數`parameter-list`會在型別名稱後面的中描述, 而其`let`主體則`let rec`是由類別宣告開頭的 (和) 系結所組成, 而`do`遵循的系結。</span><span class="sxs-lookup"><span data-stu-id="431ce-129">In an F# class, there is always a primary constructor whose arguments are described in the `parameter-list` that follows the type name, and whose body consists of the `let` (and `let rec`) bindings at the start of the class declaration and the `do` bindings that follow.</span></span> <span data-ttu-id="431ce-130">主要函式的引數會在整個類別宣告的範圍中。</span><span class="sxs-lookup"><span data-stu-id="431ce-130">The arguments of the primary constructor are in scope throughout the class declaration.</span></span>

<span data-ttu-id="431ce-131">您可以使用`new`關鍵字新增其他的函式, 以加入成員, 如下所示:</span><span class="sxs-lookup"><span data-stu-id="431ce-131">You can add additional constructors by using the `new` keyword to add a member, as follows:</span></span>

<span data-ttu-id="431ce-132">`new`(`argument-list`) = `constructor-body`</span><span class="sxs-lookup"><span data-stu-id="431ce-132">`new`(`argument-list`) = `constructor-body`</span></span>

<span data-ttu-id="431ce-133">新的函式的主體必須叫用在類別宣告最上方指定的主要函式。</span><span class="sxs-lookup"><span data-stu-id="431ce-133">The body of the new constructor must invoke the primary constructor that is specified at the top of the class declaration.</span></span>

<span data-ttu-id="431ce-134">下列範例說明此概念。</span><span class="sxs-lookup"><span data-stu-id="431ce-134">The following example illustrates this concept.</span></span> <span data-ttu-id="431ce-135">在下列程式碼中`MyClass` , 有兩個函式, 這是採用兩個引數的主要函式, 以及不接受引數的另一個函式。</span><span class="sxs-lookup"><span data-stu-id="431ce-135">In the following code, `MyClass` has two constructors, a primary constructor that takes two arguments and another constructor that takes no arguments.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2401.fs)]

## <a name="let-and-do-bindings"></a><span data-ttu-id="431ce-136">let 和 do 系結</span><span class="sxs-lookup"><span data-stu-id="431ce-136">let and do Bindings</span></span>

<span data-ttu-id="431ce-137">類別`let`定義`do`中的和系結會形成主要類別的函式主體, 因此每當建立類別實例時, 就會執行這些系結。</span><span class="sxs-lookup"><span data-stu-id="431ce-137">The `let` and `do` bindings in a class definition form the body of the primary class constructor, and therefore they run whenever a class instance is created.</span></span> <span data-ttu-id="431ce-138">`let`如果系結是函式, 則會將它編譯成成員。</span><span class="sxs-lookup"><span data-stu-id="431ce-138">If a `let` binding is a function, then it is compiled into a member.</span></span> <span data-ttu-id="431ce-139">`let`如果系結是不會在任何函式或成員中使用的值, 則會將它編譯成此函式的本機變數。</span><span class="sxs-lookup"><span data-stu-id="431ce-139">If the `let` binding is a value that is not used in any function or member, then it is compiled into a variable that is local to the constructor.</span></span> <span data-ttu-id="431ce-140">否則, 它會編譯成類別的欄位。</span><span class="sxs-lookup"><span data-stu-id="431ce-140">Otherwise, it is compiled into a field of the class.</span></span> <span data-ttu-id="431ce-141">接`do`下來的運算式會編譯成主要的函式, 並對每個實例執行初始化程式碼。</span><span class="sxs-lookup"><span data-stu-id="431ce-141">The `do` expressions that follow are compiled into the primary constructor and execute initialization code for every instance.</span></span> <span data-ttu-id="431ce-142">由於任何其他的函式一律會呼叫主要的`let`函式`do` , 因此不論呼叫哪一個函式, 系結和系結一律會執行。</span><span class="sxs-lookup"><span data-stu-id="431ce-142">Because any additional constructors always call the primary constructor, the `let` bindings and `do` bindings always execute regardless of which constructor is called.</span></span>

<span data-ttu-id="431ce-143">系結所建立`let`的欄位可以在類別的方法和屬性中存取, 不過, 它們無法從靜態方法存取, 即使靜態方法採用執行個體變數做為參數也一樣。</span><span class="sxs-lookup"><span data-stu-id="431ce-143">Fields that are created by `let` bindings can be accessed throughout the methods and properties of the class; however, they cannot be accessed from static methods, even if the static methods take an instance variable as a parameter.</span></span> <span data-ttu-id="431ce-144">您無法使用本身的識別碼 (如果有的話) 來存取它們。</span><span class="sxs-lookup"><span data-stu-id="431ce-144">They cannot be accessed by using the self identifier, if one exists.</span></span>

## <a name="self-identifiers"></a><span data-ttu-id="431ce-145">自我識別碼</span><span class="sxs-lookup"><span data-stu-id="431ce-145">Self Identifiers</span></span>

<span data-ttu-id="431ce-146">*自我識別碼*是代表目前實例的名稱。</span><span class="sxs-lookup"><span data-stu-id="431ce-146">A *self identifier* is a name that represents the current instance.</span></span> <span data-ttu-id="431ce-147">自我識別碼類似C#或`this` C++或`Me`中的關鍵字, Visual Basic。</span><span class="sxs-lookup"><span data-stu-id="431ce-147">Self identifiers resemble the `this` keyword in C# or C++ or `Me` in Visual Basic.</span></span> <span data-ttu-id="431ce-148">您可以使用兩種不同的方式定義自我識別碼, 取決於您想要讓自我識別碼位於整個類別定義的範圍內, 還是僅適用于個別的方法。</span><span class="sxs-lookup"><span data-stu-id="431ce-148">You can define a self identifier in two different ways, depending on whether you want the self identifier to be in scope for the whole class definition or just for an individual method.</span></span>

<span data-ttu-id="431ce-149">若要定義整個類別的自我識別碼, 請在 [ `as`函式參數清單] 的右括弧後面使用關鍵字, 並指定識別碼名稱。</span><span class="sxs-lookup"><span data-stu-id="431ce-149">To define a self identifier for the whole class, use the `as` keyword after the closing parentheses of the constructor parameter list, and specify the identifier name.</span></span>

<span data-ttu-id="431ce-150">若只要定義一個方法的自我識別碼, 請在成員宣告中提供自我識別碼, 方法名稱和句號 (.) 的前面都是分隔符號。</span><span class="sxs-lookup"><span data-stu-id="431ce-150">To define a self identifier for just one method, provide the self identifier in the member declaration, just before the method name and a period (.) as a separator.</span></span>

<span data-ttu-id="431ce-151">下列程式碼範例說明建立自我識別碼的兩種方式。</span><span class="sxs-lookup"><span data-stu-id="431ce-151">The following code example illustrates the two ways to create a self identifier.</span></span> <span data-ttu-id="431ce-152">在第一行中, `as`關鍵字是用來定義自我識別碼。</span><span class="sxs-lookup"><span data-stu-id="431ce-152">In the first line, the `as` keyword is used to define the self identifier.</span></span> <span data-ttu-id="431ce-153">在第五行中, 識別碼`this`是用來定義本身的識別碼, 其範圍限制為方法。 `PrintMessage`</span><span class="sxs-lookup"><span data-stu-id="431ce-153">In the fifth line, the identifier `this` is used to define a self identifier whose scope is restricted to the method `PrintMessage`.</span></span>

```fsharp
type MyClass2(dataIn) as self =
    let data = dataIn
    do
        self.PrintMessage()
    member this.PrintMessage() =
        printf "Creating MyClass2 with Data %d" data
```

<span data-ttu-id="431ce-154">不同于其他 .NET 語言, 您可以將自己的識別碼命名為, 但不像您想要的名稱;您不受限於`self`、 `Me`或`this`之類的名稱。</span><span class="sxs-lookup"><span data-stu-id="431ce-154">Unlike in other .NET languages, you can name the self identifier however you want; you are not restricted to names such as `self`, `Me`, or `this`.</span></span>

<span data-ttu-id="431ce-155">在執行系結`as` `let`之後, 才會初始化使用關鍵字宣告的自我識別碼。</span><span class="sxs-lookup"><span data-stu-id="431ce-155">The self identifier that is declared with the `as` keyword is not initialized until after the `let` bindings are executed.</span></span> <span data-ttu-id="431ce-156">因此, 它不能用在系`let`結中。</span><span class="sxs-lookup"><span data-stu-id="431ce-156">Therefore, it cannot be used in the `let` bindings.</span></span> <span data-ttu-id="431ce-157">您可以在 [ `do`系結] 區段中使用自我識別碼。</span><span class="sxs-lookup"><span data-stu-id="431ce-157">You can use the self identifier in the `do` bindings section.</span></span>

## <a name="generic-type-parameters"></a><span data-ttu-id="431ce-158">泛型類型參數</span><span class="sxs-lookup"><span data-stu-id="431ce-158">Generic Type Parameters</span></span>

<span data-ttu-id="431ce-159">泛型型別參數是以角括弧 (`<`和`>`) 來指定, 其格式為單引號, 後面接著識別碼。</span><span class="sxs-lookup"><span data-stu-id="431ce-159">Generic type parameters are specified in angle brackets (`<` and `>`), in the form of a single quotation mark followed by an identifier.</span></span> <span data-ttu-id="431ce-160">多個泛型型別參數會以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="431ce-160">Multiple generic type parameters are separated by commas.</span></span> <span data-ttu-id="431ce-161">泛型型別參數在整個宣告的範圍中。</span><span class="sxs-lookup"><span data-stu-id="431ce-161">The generic type parameter is in scope throughout the declaration.</span></span> <span data-ttu-id="431ce-162">下列程式碼範例顯示如何指定泛型型別參數。</span><span class="sxs-lookup"><span data-stu-id="431ce-162">The following code example shows how to specify generic type parameters.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2403.fs)]

<span data-ttu-id="431ce-163">使用類型時, 會推斷型別引數。</span><span class="sxs-lookup"><span data-stu-id="431ce-163">Type arguments are inferred when the type is used.</span></span> <span data-ttu-id="431ce-164">在下列程式碼中, 推斷的型別是一系列的元組。</span><span class="sxs-lookup"><span data-stu-id="431ce-164">In the following code, the inferred type is a sequence of tuples.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet24031.fs)]

## <a name="specifying-inheritance"></a><span data-ttu-id="431ce-165">指定繼承</span><span class="sxs-lookup"><span data-stu-id="431ce-165">Specifying Inheritance</span></span>

<span data-ttu-id="431ce-166">`inherit`子句會識別直接基類 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="431ce-166">The `inherit` clause identifies the direct base class, if there is one.</span></span> <span data-ttu-id="431ce-167">在F#中, 只允許一個直接基底類別。</span><span class="sxs-lookup"><span data-stu-id="431ce-167">In F#, only one direct base class is allowed.</span></span> <span data-ttu-id="431ce-168">類別所執行的介面不會被視為基類。</span><span class="sxs-lookup"><span data-stu-id="431ce-168">Interfaces that a class implements are not considered base classes.</span></span> <span data-ttu-id="431ce-169">[介面](Interfaces.md)主題中會討論介面。</span><span class="sxs-lookup"><span data-stu-id="431ce-169">Interfaces are discussed in the [Interfaces](Interfaces.md) topic.</span></span>

<span data-ttu-id="431ce-170">您可以從衍生類別存取基類的方法和屬性, 方法是使用 language 關鍵字`base`做為識別碼, 後面接著句號 (.) 和成員的名稱。</span><span class="sxs-lookup"><span data-stu-id="431ce-170">You can access the methods and properties of the base class from the derived class by using the language keyword `base` as an identifier, followed by a period (.) and the name of the member.</span></span>

<span data-ttu-id="431ce-171">如需詳細資訊，請參閱[繼承](inheritance.md)。</span><span class="sxs-lookup"><span data-stu-id="431ce-171">For more information, see [Inheritance](inheritance.md).</span></span>

## <a name="members-section"></a><span data-ttu-id="431ce-172">成員區段</span><span class="sxs-lookup"><span data-stu-id="431ce-172">Members Section</span></span>

<span data-ttu-id="431ce-173">您可以在此區段中定義靜態或實例方法、屬性、介面執行、抽象成員、事件宣告和其他函數。</span><span class="sxs-lookup"><span data-stu-id="431ce-173">You can define static or instance methods, properties, interface implementations, abstract members, event declarations, and additional constructors in this section.</span></span> <span data-ttu-id="431ce-174">「Let」和「do 系結」無法出現在此區段中。</span><span class="sxs-lookup"><span data-stu-id="431ce-174">Let and do bindings cannot appear in this section.</span></span> <span data-ttu-id="431ce-175">由於成員除了類別之外, 也可以新增F#至各種類型, 因此會在個別的[成員](./members/index.md)中加以討論。</span><span class="sxs-lookup"><span data-stu-id="431ce-175">Because members can be added to a variety of F# types in addition to classes, they are discussed in a separate topic, [Members](./members/index.md).</span></span>

## <a name="mutually-recursive-types"></a><span data-ttu-id="431ce-176">相互遞迴類型</span><span class="sxs-lookup"><span data-stu-id="431ce-176">Mutually Recursive Types</span></span>

<span data-ttu-id="431ce-177">當您定義以迴圈方式參考彼此的型別時, 您可以使用`and`關鍵字, 將型別定義加上字串。</span><span class="sxs-lookup"><span data-stu-id="431ce-177">When you define types that reference each other in a circular way, you string together the type definitions by using the `and` keyword.</span></span> <span data-ttu-id="431ce-178">關鍵字會取代第一個定義以外的所有關鍵字,如下所示。`type` `and`</span><span class="sxs-lookup"><span data-stu-id="431ce-178">The `and` keyword replaces the `type` keyword on all except the first definition, as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2404.fs)]

<span data-ttu-id="431ce-179">輸出是目前目錄中所有檔案的清單。</span><span class="sxs-lookup"><span data-stu-id="431ce-179">The output is a list of all the files in the current directory.</span></span>

## <a name="when-to-use-classes-unions-records-and-structures"></a><span data-ttu-id="431ce-180">使用類別、等位、記錄和結構的時機</span><span class="sxs-lookup"><span data-stu-id="431ce-180">When to Use Classes, Unions, Records, and Structures</span></span>

<span data-ttu-id="431ce-181">假設有各種類型可供選擇, 您必須充分瞭解每種類型的設計, 才能針對特定情況選取適當的類型。</span><span class="sxs-lookup"><span data-stu-id="431ce-181">Given the variety of types to choose from, you need to have a good understanding of what each type is designed for to select the appropriate type for a particular situation.</span></span> <span data-ttu-id="431ce-182">類別是設計用來在物件導向的程式設計內容中使用。</span><span class="sxs-lookup"><span data-stu-id="431ce-182">Classes are designed for use in object-oriented programming contexts.</span></span> <span data-ttu-id="431ce-183">物件導向程式設計是針對 .NET Framework 所撰寫的應用程式中所使用的主要架構。</span><span class="sxs-lookup"><span data-stu-id="431ce-183">Object-oriented programming is the dominant paradigm used in applications that are written for the .NET Framework.</span></span> <span data-ttu-id="431ce-184">如果您F#的程式碼必須與 .NET Framework 或其他物件導向程式庫密切合作, 特別是當您必須從物件導向的類型系統 (例如 UI 程式庫) 進行擴充時, 類別可能是適當的。</span><span class="sxs-lookup"><span data-stu-id="431ce-184">If your F# code has to work closely with the .NET Framework or another object-oriented library, and especially if you have to extend from an object-oriented type system such as a UI library, classes are probably appropriate.</span></span>

<span data-ttu-id="431ce-185">如果您不會與物件導向程式碼緊密互通, 或如果您撰寫的程式碼是獨立的, 因而受到保護, 而無法經常與物件導向的程式碼互動, 您應該考慮使用記錄和區分等位。</span><span class="sxs-lookup"><span data-stu-id="431ce-185">If you are not interoperating closely with object-oriented code, or if you are writing code that is self-contained and therefore protected from frequent interaction with object-oriented code, you should consider using records and discriminated unions.</span></span> <span data-ttu-id="431ce-186">單一且仔細思考的區分等位, 以及適當的模式比對程式碼, 通常可用來做為物件階層的較簡單替代方案。</span><span class="sxs-lookup"><span data-stu-id="431ce-186">A single, well thought–out discriminated union, together with appropriate pattern matching code, can often be used as a simpler alternative to an object hierarchy.</span></span> <span data-ttu-id="431ce-187">如需有關區分等位的詳細資訊, 請參閱[區分](discriminated-unions.md)等位。</span><span class="sxs-lookup"><span data-stu-id="431ce-187">For more information about discriminated unions, see [Discriminated Unions](discriminated-unions.md).</span></span>

<span data-ttu-id="431ce-188">記錄的優點是比類別簡單, 但當類型的需求超過可透過其簡單性完成的內容時, 不適合使用記錄。</span><span class="sxs-lookup"><span data-stu-id="431ce-188">Records have the advantage of being simpler than classes, but records are not appropriate when the demands of a type exceed what can be accomplished with their simplicity.</span></span> <span data-ttu-id="431ce-189">記錄基本上是值的簡單匯總, 沒有個別的可執行自訂動作的函式, 也不需要隱藏的欄位, 也不需要繼承或介面的實現。</span><span class="sxs-lookup"><span data-stu-id="431ce-189">Records are basically simple aggregates of values, without separate constructors that can perform custom actions, without hidden fields, and without inheritance or interface implementations.</span></span> <span data-ttu-id="431ce-190">雖然屬性和方法之類的成員可以加入記錄以使其行為更複雜, 但儲存在記錄中的欄位仍是簡單的值匯總。</span><span class="sxs-lookup"><span data-stu-id="431ce-190">Although members such as properties and methods can be added to records to make their behavior more complex, the fields stored in a record are still a simple aggregate of values.</span></span> <span data-ttu-id="431ce-191">如需記錄的詳細資訊, 請參閱[記錄](records.md)。</span><span class="sxs-lookup"><span data-stu-id="431ce-191">For more information about records, see [Records](records.md).</span></span>

<span data-ttu-id="431ce-192">結構也適用于資料的小型匯總, 但它們與類別和記錄不同, 因為它們都是 .NET 實數值型別。</span><span class="sxs-lookup"><span data-stu-id="431ce-192">Structures are also useful for small aggregates of data, but they differ from classes and records in that they are .NET value types.</span></span> <span data-ttu-id="431ce-193">類別和記錄是 .NET 參考型別。</span><span class="sxs-lookup"><span data-stu-id="431ce-193">Classes and records are .NET reference types.</span></span> <span data-ttu-id="431ce-194">實值型別和參考型別的語義在值型別中是以傳值方式來傳遞。</span><span class="sxs-lookup"><span data-stu-id="431ce-194">The semantics of value types and reference types are different in that value types are passed by value.</span></span> <span data-ttu-id="431ce-195">這表示當以參數的形式傳遞或從函式傳回時, 它們會複製位。</span><span class="sxs-lookup"><span data-stu-id="431ce-195">This means that they are copied bit for bit when they are passed as a parameter or returned from a function.</span></span> <span data-ttu-id="431ce-196">它們也會儲存在堆疊上, 如果當做欄位使用, 則內嵌于父物件中, 而不是儲存在堆積上的個別位置。</span><span class="sxs-lookup"><span data-stu-id="431ce-196">They are also stored on the stack or, if they are used as a field, embedded inside the parent object instead of stored in their own separate location on the heap.</span></span> <span data-ttu-id="431ce-197">因此, 當存取堆積的額外負荷造成問題時, 結構適用于經常存取的資料。</span><span class="sxs-lookup"><span data-stu-id="431ce-197">Therefore, structures are appropriate for frequently accessed data when the overhead of accessing the heap is a problem.</span></span> <span data-ttu-id="431ce-198">如需結構的詳細資訊, 請參閱[結構](structures.md)。</span><span class="sxs-lookup"><span data-stu-id="431ce-198">For more information about structures, see [Structures](structures.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="431ce-199">另請參閱</span><span class="sxs-lookup"><span data-stu-id="431ce-199">See also</span></span>

- [<span data-ttu-id="431ce-200">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="431ce-200">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="431ce-201">成員</span><span class="sxs-lookup"><span data-stu-id="431ce-201">Members</span></span>](./members/index.md)
- [<span data-ttu-id="431ce-202">繼承</span><span class="sxs-lookup"><span data-stu-id="431ce-202">Inheritance</span></span>](inheritance.md)
- [<span data-ttu-id="431ce-203">介面</span><span class="sxs-lookup"><span data-stu-id="431ce-203">Interfaces</span></span>](interfaces.md)
