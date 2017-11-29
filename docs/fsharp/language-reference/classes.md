---
title: "類別 (F#)"
description: "了解 F # 類別的型別，代表物件的屬性、 方法和事件的方式。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: d58679d5-7753-4b3b-a12f-6e9f00ed5ba3
ms.openlocfilehash: 2a73baba1f7c1b0d3bd09d22c9d6d9f0524daef3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="classes"></a><span data-ttu-id="215c9-104">類別</span><span class="sxs-lookup"><span data-stu-id="215c9-104">Classes</span></span>

<span data-ttu-id="215c9-105">*類別*是代表物件的屬性、 方法和事件的型別。</span><span class="sxs-lookup"><span data-stu-id="215c9-105">*Classes* are types that represent objects that can have properties, methods, and events.</span></span>


## <a name="syntax"></a><span data-ttu-id="215c9-106">語法</span><span class="sxs-lookup"><span data-stu-id="215c9-106">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="215c9-107">備註</span><span class="sxs-lookup"><span data-stu-id="215c9-107">Remarks</span></span>
<span data-ttu-id="215c9-108">類別代表基本的.NET 物件類型描述此類別是在 F # 支援物件導向程式設計的主要類型概念。</span><span class="sxs-lookup"><span data-stu-id="215c9-108">Classes represent the fundamental description of .NET object types; the class is the primary type concept that supports object-oriented programming in F#.</span></span>

<span data-ttu-id="215c9-109">在上述語法中，`type-name`是任何有效的識別項。</span><span class="sxs-lookup"><span data-stu-id="215c9-109">In the preceding syntax, the `type-name` is any valid identifier.</span></span> <span data-ttu-id="215c9-110">`type-params`描述選擇性的泛型型別參數。</span><span class="sxs-lookup"><span data-stu-id="215c9-110">The `type-params` describes optional generic type parameters.</span></span> <span data-ttu-id="215c9-111">它包含型別參數名稱和角括弧括住條件約束 (`<`和`>`)。</span><span class="sxs-lookup"><span data-stu-id="215c9-111">It consists of type parameter names and constraints enclosed in angle brackets (`<` and `>`).</span></span> <span data-ttu-id="215c9-112">如需詳細資訊，請參閱[泛型](generics/index.md)和[條件約束](generics/constraints.md)。</span><span class="sxs-lookup"><span data-stu-id="215c9-112">For more information, see [Generics](generics/index.md) and [Constraints](generics/constraints.md).</span></span> <span data-ttu-id="215c9-113">`parameter-list`描述建構函式參數。</span><span class="sxs-lookup"><span data-stu-id="215c9-113">The `parameter-list` describes constructor parameters.</span></span> <span data-ttu-id="215c9-114">第一個存取修飾詞都屬於型別。第二個屬於主要建構函式。</span><span class="sxs-lookup"><span data-stu-id="215c9-114">The first access modifier pertains to the type; the second pertains to the primary constructor.</span></span> <span data-ttu-id="215c9-115">在這兩種情況下，預設值是`public`。</span><span class="sxs-lookup"><span data-stu-id="215c9-115">In both cases, the default is `public`.</span></span>

<span data-ttu-id="215c9-116">使用指定之類別的基底類別`inherit`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="215c9-116">You specify the base class for a class by using the `inherit` keyword.</span></span> <span data-ttu-id="215c9-117">您必須提供引數以括號，基底類別建構函式。</span><span class="sxs-lookup"><span data-stu-id="215c9-117">You must supply arguments, in parentheses, for the base class constructor.</span></span>

<span data-ttu-id="215c9-118">宣告欄位，或函式使用的類別值`let`繫結，而且您必須遵循的一般規則`let`繫結。</span><span class="sxs-lookup"><span data-stu-id="215c9-118">You declare fields or function values that are local to the class by using `let` bindings, and you must follow the general rules for `let` bindings.</span></span> <span data-ttu-id="215c9-119">`do-bindings`區段包含在物件建構時要執行的程式碼。</span><span class="sxs-lookup"><span data-stu-id="215c9-119">The `do-bindings` section includes code to be executed upon object construction.</span></span>

<span data-ttu-id="215c9-120">`member-list`組成其他建構函式、 執行個體和靜態方法宣告、 介面宣告，抽象的繫結，並且屬性和事件宣告。</span><span class="sxs-lookup"><span data-stu-id="215c9-120">The `member-list` consists of additional constructors, instance and static method declarations, interface declarations, abstract bindings, and property and event declarations.</span></span> <span data-ttu-id="215c9-121">這些述[成員](members/index.md)。</span><span class="sxs-lookup"><span data-stu-id="215c9-121">These are described in [Members](members/index.md).</span></span>

<span data-ttu-id="215c9-122">`identifier`搭配選擇性使用`as`關鍵字可讓執行個體變數或自我識別項，可以在類型定義中用來參考類型的執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="215c9-122">The `identifier` that is used with the optional `as` keyword gives a name to the instance variable, or self identifier, which can be used in the type definition to refer to the instance of the type.</span></span> <span data-ttu-id="215c9-123">如需詳細資訊，請參閱本主題稍後的章節自我識別項。</span><span class="sxs-lookup"><span data-stu-id="215c9-123">For more information, see the section Self Identifiers later in this topic.</span></span>

<span data-ttu-id="215c9-124">關鍵字`class`和`end`，標記開始並定義結尾為選擇性。</span><span class="sxs-lookup"><span data-stu-id="215c9-124">The keywords `class` and `end` that mark the start and end of the definition are optional.</span></span>

<span data-ttu-id="215c9-125">相互遞迴類型，都是互相參考的類型，加入並搭配`and`一樣相互遞迴函式是關鍵字。</span><span class="sxs-lookup"><span data-stu-id="215c9-125">Mutually recursive types, which are types that reference each other, are joined together with the `and` keyword just as mutually recursive functions are.</span></span> <span data-ttu-id="215c9-126">如需範例，請參閱相互遞迴類型一節。</span><span class="sxs-lookup"><span data-stu-id="215c9-126">For an example, see the section Mutually Recursive Types.</span></span>


## <a name="constructors"></a><span data-ttu-id="215c9-127">建構函式</span><span class="sxs-lookup"><span data-stu-id="215c9-127">Constructors</span></span>
<span data-ttu-id="215c9-128">建構函式是建立類別類型的執行個體的程式碼。</span><span class="sxs-lookup"><span data-stu-id="215c9-128">The constructor is code that creates an instance of the class type.</span></span> <span data-ttu-id="215c9-129">類別的建構函式在 F # 中運作方式稍有不同，比在其他.NET 語言中。</span><span class="sxs-lookup"><span data-stu-id="215c9-129">Constructors for classes work somewhat differently in F# than they do in other .NET languages.</span></span> <span data-ttu-id="215c9-130">在 F # 類別中，有永遠是主要的建構函式的引數中所述`parameter-list`一節的型別名稱，以及其主體包含`let`(和`let rec`) 繫結的類別宣告和開頭`do`遵循的繫結。</span><span class="sxs-lookup"><span data-stu-id="215c9-130">In an F# class, there is always a primary constructor whose arguments are described in the `parameter-list` that follows the type name, and whose body consists of the `let` (and `let rec`) bindings at the start of the class declaration and the `do` bindings that follow.</span></span> <span data-ttu-id="215c9-131">主要建構函式的引數是在範圍中的類別宣告。</span><span class="sxs-lookup"><span data-stu-id="215c9-131">The arguments of the primary constructor are in scope throughout the class declaration.</span></span>

<span data-ttu-id="215c9-132">您可以加入其他建構函式使用`new`關鍵字來新增成員，如下：</span><span class="sxs-lookup"><span data-stu-id="215c9-132">You can add additional constructors by using the `new` keyword to add a member, as follows:</span></span>

<span data-ttu-id="215c9-133">`new`(`argument-list`) = `constructor-body`</span><span class="sxs-lookup"><span data-stu-id="215c9-133">`new`(`argument-list`) = `constructor-body`</span></span>

<span data-ttu-id="215c9-134">新的建構函式的主體必須叫用指定頂端的類別宣告的主要建構函式。</span><span class="sxs-lookup"><span data-stu-id="215c9-134">The body of the new constructor must invoke the primary constructor that is specified at the top of the class declaration.</span></span>

<span data-ttu-id="215c9-135">下列範例說明這個概念。</span><span class="sxs-lookup"><span data-stu-id="215c9-135">The following example illustrates this concept.</span></span> <span data-ttu-id="215c9-136">下列程式碼，`MyClass`有兩個建構函式，接受兩個引數和另一個建構函式的主要建構函式不接受引數。</span><span class="sxs-lookup"><span data-stu-id="215c9-136">In the following code, `MyClass` has two constructors, a primary constructor that takes two arguments and another constructor that takes no arguments.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2401.fs)]
    
## <a name="let-and-do-bindings"></a><span data-ttu-id="215c9-137">let 和 do 繫結</span><span class="sxs-lookup"><span data-stu-id="215c9-137">let and do Bindings</span></span>

<span data-ttu-id="215c9-138">`let`和`do`類別定義中的繫結表單的主要類別建構函式主體，因此執行每次建立類別執行個體時。</span><span class="sxs-lookup"><span data-stu-id="215c9-138">The `let` and `do` bindings in a class definition form the body of the primary class constructor, and therefore they run whenever a class instance is created.</span></span> <span data-ttu-id="215c9-139">如果`let`繫結是函式，則它會先編譯成成員。</span><span class="sxs-lookup"><span data-stu-id="215c9-139">If a `let` binding is a function, then it is compiled into a member.</span></span> <span data-ttu-id="215c9-140">如果`let`繫結是不是在任何函式或成員的值，則它會先編譯成建構函式的本機變數。</span><span class="sxs-lookup"><span data-stu-id="215c9-140">If the `let` binding is a value that is not used in any function or member, then it is compiled into a variable that is local to the constructor.</span></span> <span data-ttu-id="215c9-141">否則，它會編譯為類別的欄位。</span><span class="sxs-lookup"><span data-stu-id="215c9-141">Otherwise, it is compiled into a field of the class.</span></span> <span data-ttu-id="215c9-142">`do`遵循的運算式都會編譯成主要建構函式，和執行每個執行個體的初始化程式碼。</span><span class="sxs-lookup"><span data-stu-id="215c9-142">The `do` expressions that follow are compiled into the primary constructor and execute initialization code for every instance.</span></span> <span data-ttu-id="215c9-143">任何其他建構函式一定要呼叫的主要建構函式，因為`let`繫結和`do`繫結永遠執行無論哪個呼叫建構函式。</span><span class="sxs-lookup"><span data-stu-id="215c9-143">Because any additional constructors always call the primary constructor, the `let` bindings and `do` bindings always execute regardless of which constructor is called.</span></span>

<span data-ttu-id="215c9-144">欄位所建立的`let`繫結可在整個的方法和屬性類別的存取; 不過，無法存取的靜態方法，即使靜態方法會採用做為參數的執行個體變數。</span><span class="sxs-lookup"><span data-stu-id="215c9-144">Fields that are created by `let` bindings can be accessed throughout the methods and properties of the class; however, they cannot be accessed from static methods, even if the static methods take an instance variable as a parameter.</span></span> <span data-ttu-id="215c9-145">無法存取使用自我識別項，如果有的話。</span><span class="sxs-lookup"><span data-stu-id="215c9-145">They cannot be accessed by using the self identifier, if one exists.</span></span>


## <a name="self-identifiers"></a><span data-ttu-id="215c9-146">自我識別項</span><span class="sxs-lookup"><span data-stu-id="215c9-146">Self Identifiers</span></span>

<span data-ttu-id="215c9-147">A*自我識別項*是代表目前的執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="215c9-147">A *self identifier* is a name that represents the current instance.</span></span> <span data-ttu-id="215c9-148">自我識別項類似`this`關鍵字以 C# 或 c + + 或`Me`在 Visual Basic 中。</span><span class="sxs-lookup"><span data-stu-id="215c9-148">Self identifiers resemble the `this` keyword in C# or C++ or `Me` in Visual Basic.</span></span> <span data-ttu-id="215c9-149">您可以在兩個不同的方式，取決於您在範圍內的整個類別定義，或是只為個別的方法自我識別項中定義自我識別項。</span><span class="sxs-lookup"><span data-stu-id="215c9-149">You can define a self identifier in two different ways, depending on whether you want the self identifier to be in scope for the whole class definition or just for an individual method.</span></span>

<span data-ttu-id="215c9-150">若要定義為整個類別的自我識別項，請使用`as`關鍵字之後的右括號，建構函式參數清單，並指定識別項名稱。</span><span class="sxs-lookup"><span data-stu-id="215c9-150">To define a self identifier for the whole class, use the `as` keyword after the closing parentheses of the constructor parameter list, and specify the identifier name.</span></span>

<span data-ttu-id="215c9-151">若要定義本身的識別項，只有一個方法，提供在成員宣告中之前的方法名稱和做為分隔符號的句號 （.）, 自我識別項。</span><span class="sxs-lookup"><span data-stu-id="215c9-151">To define a self identifier for just one method, provide the self identifier in the member declaration, just before the method name and a period (.) as a separator.</span></span>

<span data-ttu-id="215c9-152">下列程式碼範例說明兩種方式來建立自我識別項。</span><span class="sxs-lookup"><span data-stu-id="215c9-152">The following code example illustrates the two ways to create a self identifier.</span></span> <span data-ttu-id="215c9-153">在第一行，`as`關鍵字用來定義自我識別項。</span><span class="sxs-lookup"><span data-stu-id="215c9-153">In the first line, the `as` keyword is used to define the self identifier.</span></span> <span data-ttu-id="215c9-154">在第五個列中的識別項`this`用來定義它的範圍僅限於方法的自我識別碼`PrintMessage`。</span><span class="sxs-lookup"><span data-stu-id="215c9-154">In the fifth line, the identifier `this` is used to define a self identifier whose scope is restricted to the method `PrintMessage`.</span></span>

```fsharp
type MyClass2(dataIn) as self =
    let data = dataIn
    do
        self.PrintMessage()
    member this.PrintMessage() =
        printf "Creating MyClass2 with Data %d" data
```

<span data-ttu-id="215c9-155">不同於其他.NET 語言中，您可以命名自我識別項想要;您不限於名稱例如`self`， `Me`，或`this`。</span><span class="sxs-lookup"><span data-stu-id="215c9-155">Unlike in other .NET languages, you can name the self identifier however you want; you are not restricted to names such as `self`, `Me`, or `this`.</span></span>

<span data-ttu-id="215c9-156">自我識別項宣告`as`關鍵字未初始化直到之後`let`執行繫結。</span><span class="sxs-lookup"><span data-stu-id="215c9-156">The self identifier that is declared with the `as` keyword is not initialized until after the `let` bindings are executed.</span></span> <span data-ttu-id="215c9-157">因此，它不能在`let`繫結。</span><span class="sxs-lookup"><span data-stu-id="215c9-157">Therefore, it cannot be used in the `let` bindings.</span></span> <span data-ttu-id="215c9-158">您可以使用自我識別項中的`do`繫結區段。</span><span class="sxs-lookup"><span data-stu-id="215c9-158">You can use the self identifier in the `do` bindings section.</span></span>


## <a name="generic-type-parameters"></a><span data-ttu-id="215c9-159">泛型型別參數</span><span class="sxs-lookup"><span data-stu-id="215c9-159">Generic Type Parameters</span></span>

<span data-ttu-id="215c9-160">角括號中指定泛型型別參數 (`<`和`>`)、 單引號接識別項的形式。</span><span class="sxs-lookup"><span data-stu-id="215c9-160">Generic type parameters are specified in angle brackets (`<` and `>`), in the form of a single quotation mark followed by an identifier.</span></span> <span data-ttu-id="215c9-161">以逗號分隔多個泛型型別參數。</span><span class="sxs-lookup"><span data-stu-id="215c9-161">Multiple generic type parameters are separated by commas.</span></span> <span data-ttu-id="215c9-162">泛型型別參數是在範圍中宣告。</span><span class="sxs-lookup"><span data-stu-id="215c9-162">The generic type parameter is in scope throughout the declaration.</span></span> <span data-ttu-id="215c9-163">下列程式碼範例示範如何指定泛型型別參數。</span><span class="sxs-lookup"><span data-stu-id="215c9-163">The following code example shows how to specify generic type parameters.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2403.fs)]

<span data-ttu-id="215c9-164">使用類型時，就會推斷型別引數。</span><span class="sxs-lookup"><span data-stu-id="215c9-164">Type arguments are inferred when the type is used.</span></span> <span data-ttu-id="215c9-165">在下列程式碼中，推斷的型別會是 tuple 的一連串。</span><span class="sxs-lookup"><span data-stu-id="215c9-165">In the following code, the inferred type is a sequence of tuples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet24031.fs)]
    
## <a name="specifying-inheritance"></a><span data-ttu-id="215c9-166">指定繼承</span><span class="sxs-lookup"><span data-stu-id="215c9-166">Specifying Inheritance</span></span>

<span data-ttu-id="215c9-167">`inherit`子句會識別直接基底類別，如果有的話。</span><span class="sxs-lookup"><span data-stu-id="215c9-167">The `inherit` clause identifies the direct base class, if there is one.</span></span> <span data-ttu-id="215c9-168">在 F # 中，允許只能有一個直接基底類別。</span><span class="sxs-lookup"><span data-stu-id="215c9-168">In F#, only one direct base class is allowed.</span></span> <span data-ttu-id="215c9-169">類別實作的介面不會視為基底類別。</span><span class="sxs-lookup"><span data-stu-id="215c9-169">Interfaces that a class implements are not considered base classes.</span></span> <span data-ttu-id="215c9-170">介面中會討論[介面](Interfaces.md)主題。</span><span class="sxs-lookup"><span data-stu-id="215c9-170">Interfaces are discussed in the [Interfaces](Interfaces.md) topic.</span></span>

<span data-ttu-id="215c9-171">您可以從衍生類別存取的方法和屬性的基底類別，使用該語言關鍵字`base`做為識別項，後面接著句號 （.） 和成員的名稱。</span><span class="sxs-lookup"><span data-stu-id="215c9-171">You can access the methods and properties of the base class from the derived class by using the language keyword `base` as an identifier, followed by a period (.) and the name of the member.</span></span>

<span data-ttu-id="215c9-172">如需詳細資訊，請參閱[繼承](inheritance.md)。</span><span class="sxs-lookup"><span data-stu-id="215c9-172">For more information, see [Inheritance](inheritance.md).</span></span>


## <a name="members-section"></a><span data-ttu-id="215c9-173">成員 區段</span><span class="sxs-lookup"><span data-stu-id="215c9-173">Members Section</span></span>
<span data-ttu-id="215c9-174">本節中，您可以定義靜態或執行個體方法、 屬性、 介面實作，抽象成員、 事件宣告和其他建構函式。</span><span class="sxs-lookup"><span data-stu-id="215c9-174">You can define static or instance methods, properties, interface implementations, abstract members, event declarations, and additional constructors in this section.</span></span> <span data-ttu-id="215c9-175">可讓和執行繫結不能出現在這一節。</span><span class="sxs-lookup"><span data-stu-id="215c9-175">Let and do bindings cannot appear in this section.</span></span> <span data-ttu-id="215c9-176">因為成員可以加入至各種不同的 F # 型別除了類別之外，因此它們會在不同的主題，討論[成員](members/index.md)。</span><span class="sxs-lookup"><span data-stu-id="215c9-176">Because members can be added to a variety of F# types in addition to classes, they are discussed in a separate topic, [Members](members/index.md).</span></span>


## <a name="mutually-recursive-types"></a><span data-ttu-id="215c9-177">相互遞迴類型</span><span class="sxs-lookup"><span data-stu-id="215c9-177">Mutually Recursive Types</span></span>
<span data-ttu-id="215c9-178">當您定義的循環方式互相參考的類型時，您的字串一起型別定義使用`and`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="215c9-178">When you define types that reference each other in a circular way, you string together the type definitions by using the `and` keyword.</span></span> <span data-ttu-id="215c9-179">`and`關鍵字取代`type`以外，如下所示的第一個定義的所有關鍵字。</span><span class="sxs-lookup"><span data-stu-id="215c9-179">The `and` keyword replaces the `type` keyword on all except the first definition, as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2404.fs)]

<span data-ttu-id="215c9-180">輸出是一份目前的目錄中的所有檔案。</span><span class="sxs-lookup"><span data-stu-id="215c9-180">The output is a list of all the files in the current directory.</span></span>


## <a name="when-to-use-classes-unions-records-and-structures"></a><span data-ttu-id="215c9-181">使用類別、 聯集、 記錄和結構的時機</span><span class="sxs-lookup"><span data-stu-id="215c9-181">When to Use Classes, Unions, Records, and Structures</span></span>
<span data-ttu-id="215c9-182">提供的各種可從中選擇的類型，您需要深入了解的項目每個類型針對設計來選取在特定情況下的適當型別。</span><span class="sxs-lookup"><span data-stu-id="215c9-182">Given the variety of types to choose from, you need to have a good understanding of what each type is designed for to select the appropriate type for a particular situation.</span></span> <span data-ttu-id="215c9-183">類別被設計來在物件導向程式設計內容中。</span><span class="sxs-lookup"><span data-stu-id="215c9-183">Classes are designed for use in object-oriented programming contexts.</span></span> <span data-ttu-id="215c9-184">物件導向程式設計是.NET framework 撰寫的應用程式中使用的主控架構。</span><span class="sxs-lookup"><span data-stu-id="215c9-184">Object-oriented programming is the dominant paradigm used in applications that are written for the .NET Framework.</span></span> <span data-ttu-id="215c9-185">如果 F # 程式碼與.NET Framework 或另一個物件導向程式庫密切合作，尤其是如果您要擴充的物件導向的型別系統，例如 UI 程式庫類別是可能適合。</span><span class="sxs-lookup"><span data-stu-id="215c9-185">If your F# code has to work closely with the .NET Framework or another object-oriented library, and especially if you have to extend from an object-oriented type system such as a UI library, classes are probably appropriate.</span></span>

<span data-ttu-id="215c9-186">如果您不緊密地與物件導向程式碼互通，或如果您要撰寫獨立且從經常與物件導向的程式碼的互動，因此受保護的程式碼，您應該考慮使用記錄和差別等位。</span><span class="sxs-lookup"><span data-stu-id="215c9-186">If you are not interoperating closely with object-oriented code, or if you are writing code that is self-contained and therefore protected from frequent interaction with object-oriented code, you should consider using records and discriminated unions.</span></span> <span data-ttu-id="215c9-187">單一也思考外延展差別聯集，以及適當的模式比對程式碼中，通常可用來當作物件階層架構較簡單的替代方案。</span><span class="sxs-lookup"><span data-stu-id="215c9-187">A single, well thought–out discriminated union, together with appropriate pattern matching code, can often be used as a simpler alternative to an object hierarchy.</span></span> <span data-ttu-id="215c9-188">如需差別聯集的詳細資訊，請參閱[差別等位](discriminated-unions.md)。</span><span class="sxs-lookup"><span data-stu-id="215c9-188">For more information about discriminated unions, see [Discriminated Unions](discriminated-unions.md).</span></span>

<span data-ttu-id="215c9-189">記錄都有的優點是類別，比簡單，但記錄類型的要求超過其簡化可完成什麼時並不適當。</span><span class="sxs-lookup"><span data-stu-id="215c9-189">Records have the advantage of being simpler than classes, but records are not appropriate when the demands of a type exceed what can be accomplished with their simplicity.</span></span> <span data-ttu-id="215c9-190">記錄會以基本上簡單彙總的值，可以執行自訂動作的不同建構函式、 不含隱藏欄位，而不繼承或介面的實作。</span><span class="sxs-lookup"><span data-stu-id="215c9-190">Records are basically simple aggregates of values, without separate constructors that can perform custom actions, without hidden fields, and without inheritance or interface implementations.</span></span> <span data-ttu-id="215c9-191">雖然成員例如屬性和方法可以加入至記錄，使其行為更複雜，儲存在記錄的欄位仍是值的簡單彙總。</span><span class="sxs-lookup"><span data-stu-id="215c9-191">Although members such as properties and methods can be added to records to make their behavior more complex, the fields stored in a record are still a simple aggregate of values.</span></span> <span data-ttu-id="215c9-192">如需記錄的詳細資訊，請參閱[記錄](records.md)。</span><span class="sxs-lookup"><span data-stu-id="215c9-192">For more information about records, see [Records](records.md).</span></span>

<span data-ttu-id="215c9-193">結構也適用於小型的彙總的資料，但它們不同於類別與記錄，因為它們是.NET 實值類型。</span><span class="sxs-lookup"><span data-stu-id="215c9-193">Structures are also useful for small aggregates of data, but they differ from classes and records in that they are .NET value types.</span></span> <span data-ttu-id="215c9-194">類別與記錄是.NET 參考類型。</span><span class="sxs-lookup"><span data-stu-id="215c9-194">Classes and records are .NET reference types.</span></span> <span data-ttu-id="215c9-195">實值類型和參考類型的語意，在於傳值方式傳遞的實值型別都不同。</span><span class="sxs-lookup"><span data-stu-id="215c9-195">The semantics of value types and reference types are different in that value types are passed by value.</span></span> <span data-ttu-id="215c9-196">這表示它們複製做為參數傳遞或傳回從函式時，位元的位元。</span><span class="sxs-lookup"><span data-stu-id="215c9-196">This means that they are copied bit for bit when they are passed as a parameter or returned from a function.</span></span> <span data-ttu-id="215c9-197">位也儲存在堆疊上，或者，如果它們做為欄位，內嵌於父物件，而不是使用儲存在他們自己在堆積上不同的位置。</span><span class="sxs-lookup"><span data-stu-id="215c9-197">They are also stored on the stack or, if they are used as a field, embedded inside the parent object instead of stored in their own separate location on the heap.</span></span> <span data-ttu-id="215c9-198">因此，結構是適用於經常存取之資料的額外負荷，存取在堆積的問題時。</span><span class="sxs-lookup"><span data-stu-id="215c9-198">Therefore, structures are appropriate for frequently accessed data when the overhead of accessing the heap is a problem.</span></span> <span data-ttu-id="215c9-199">如需結構的詳細資訊，請參閱[結構](structures.md)。</span><span class="sxs-lookup"><span data-stu-id="215c9-199">For more information about structures, see [Structures](structures.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="215c9-200">另請參閱</span><span class="sxs-lookup"><span data-stu-id="215c9-200">See Also</span></span>
[<span data-ttu-id="215c9-201">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="215c9-201">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="215c9-202">成員</span><span class="sxs-lookup"><span data-stu-id="215c9-202">Members</span></span>](members/index.md)

[<span data-ttu-id="215c9-203">繼承</span><span class="sxs-lookup"><span data-stu-id="215c9-203">Inheritance</span></span>](inheritance.md)

[<span data-ttu-id="215c9-204">介面</span><span class="sxs-lookup"><span data-stu-id="215c9-204">Interfaces</span></span>](interfaces.md)

