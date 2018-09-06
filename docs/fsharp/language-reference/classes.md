---
title: 類別 (F#)
description: '了解如何 F # 類別表示可以有屬性、 方法和事件的物件型別。'
ms.date: 05/16/2016
ms.openlocfilehash: 71cd713d192d28565e879b79b2fc9e0530e5f841
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43802103"
---
# <a name="classes"></a><span data-ttu-id="12567-103">類別</span><span class="sxs-lookup"><span data-stu-id="12567-103">Classes</span></span>

<span data-ttu-id="12567-104">*類別*是型別，代表可以有屬性、 方法和事件的物件。</span><span class="sxs-lookup"><span data-stu-id="12567-104">*Classes* are types that represent objects that can have properties, methods, and events.</span></span>

## <a name="syntax"></a><span data-ttu-id="12567-105">語法</span><span class="sxs-lookup"><span data-stu-id="12567-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="12567-106">備註</span><span class="sxs-lookup"><span data-stu-id="12567-106">Remarks</span></span>

<span data-ttu-id="12567-107">類別代表基本的.NET 物件類型描述此類別是以 F # 支援物件導向程式設計的主要類型概念。</span><span class="sxs-lookup"><span data-stu-id="12567-107">Classes represent the fundamental description of .NET object types; the class is the primary type concept that supports object-oriented programming in F#.</span></span>

<span data-ttu-id="12567-108">在上述語法中，`type-name`是任何有效的識別碼。</span><span class="sxs-lookup"><span data-stu-id="12567-108">In the preceding syntax, the `type-name` is any valid identifier.</span></span> <span data-ttu-id="12567-109">`type-params`描述選擇性的泛型型別參數。</span><span class="sxs-lookup"><span data-stu-id="12567-109">The `type-params` describes optional generic type parameters.</span></span> <span data-ttu-id="12567-110">該包含型別參數名稱和角括弧括住的條件約束 (`<`和`>`)。</span><span class="sxs-lookup"><span data-stu-id="12567-110">It consists of type parameter names and constraints enclosed in angle brackets (`<` and `>`).</span></span> <span data-ttu-id="12567-111">如需詳細資訊，請參閱 <<c0> [ 泛型](generics/index.md)並[條件約束](generics/constraints.md)。</span><span class="sxs-lookup"><span data-stu-id="12567-111">For more information, see [Generics](generics/index.md) and [Constraints](generics/constraints.md).</span></span> <span data-ttu-id="12567-112">`parameter-list`描述建構函式參數。</span><span class="sxs-lookup"><span data-stu-id="12567-112">The `parameter-list` describes constructor parameters.</span></span> <span data-ttu-id="12567-113">第一個存取修飾詞與類型;第二個是關於的主要建構函式。</span><span class="sxs-lookup"><span data-stu-id="12567-113">The first access modifier pertains to the type; the second pertains to the primary constructor.</span></span> <span data-ttu-id="12567-114">在這兩種情況下，預設值是`public`。</span><span class="sxs-lookup"><span data-stu-id="12567-114">In both cases, the default is `public`.</span></span>

<span data-ttu-id="12567-115">使用指定之類別的基底類別`inherit`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="12567-115">You specify the base class for a class by using the `inherit` keyword.</span></span> <span data-ttu-id="12567-116">您必須提供引數以括號，基底類別建構函式。</span><span class="sxs-lookup"><span data-stu-id="12567-116">You must supply arguments, in parentheses, for the base class constructor.</span></span>

<span data-ttu-id="12567-117">您宣告欄位或函式所使用的本機類別的值`let`繫結，而且您必須遵循的一般規則`let`繫結。</span><span class="sxs-lookup"><span data-stu-id="12567-117">You declare fields or function values that are local to the class by using `let` bindings, and you must follow the general rules for `let` bindings.</span></span> <span data-ttu-id="12567-118">`do-bindings`區段包含在物件建構時要執行的程式碼。</span><span class="sxs-lookup"><span data-stu-id="12567-118">The `do-bindings` section includes code to be executed upon object construction.</span></span>

<span data-ttu-id="12567-119">`member-list`其他建構函式、 執行個體和靜態方法宣告、 介面宣告，抽象的繫結，以及屬性和事件宣告所組成。</span><span class="sxs-lookup"><span data-stu-id="12567-119">The `member-list` consists of additional constructors, instance and static method declarations, interface declarations, abstract bindings, and property and event declarations.</span></span> <span data-ttu-id="12567-120">這些所述[成員](members/index.md)。</span><span class="sxs-lookup"><span data-stu-id="12567-120">These are described in [Members](members/index.md).</span></span>

<span data-ttu-id="12567-121">`identifier`搭配選擇性`as`關鍵字可讓執行個體變數或自我識別項，可用於型別定義中參考之型別的執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="12567-121">The `identifier` that is used with the optional `as` keyword gives a name to the instance variable, or self identifier, which can be used in the type definition to refer to the instance of the type.</span></span> <span data-ttu-id="12567-122">如需詳細資訊，請參閱本主題稍後的章節自我識別項。</span><span class="sxs-lookup"><span data-stu-id="12567-122">For more information, see the section Self Identifiers later in this topic.</span></span>

<span data-ttu-id="12567-123">關鍵字`class`和`end`，標記開始和結尾定義為選擇性。</span><span class="sxs-lookup"><span data-stu-id="12567-123">The keywords `class` and `end` that mark the start and end of the definition are optional.</span></span>

<span data-ttu-id="12567-124">相互遞迴類型，也就是彼此參考的類型，加入搭配`and`關鍵字，如同相互遞迴函式會。</span><span class="sxs-lookup"><span data-stu-id="12567-124">Mutually recursive types, which are types that reference each other, are joined together with the `and` keyword just as mutually recursive functions are.</span></span> <span data-ttu-id="12567-125">如需範例，請參閱相互遞迴類型一節。</span><span class="sxs-lookup"><span data-stu-id="12567-125">For an example, see the section Mutually Recursive Types.</span></span>

## <a name="constructors"></a><span data-ttu-id="12567-126">建構函式</span><span class="sxs-lookup"><span data-stu-id="12567-126">Constructors</span></span>

<span data-ttu-id="12567-127">建構函式是建立類別類型的執行個體的程式碼。</span><span class="sxs-lookup"><span data-stu-id="12567-127">The constructor is code that creates an instance of the class type.</span></span> <span data-ttu-id="12567-128">類別建構函式在 F # 中運作方式稍有不同，比在其他.NET 語言。</span><span class="sxs-lookup"><span data-stu-id="12567-128">Constructors for classes work somewhat differently in F# than they do in other .NET languages.</span></span> <span data-ttu-id="12567-129">在 F # 類別中，總是有主要的建構函式的引數中所述`parameter-list`面的型別名稱，而其主體包含`let`(和`let rec`) 繫結的類別宣告，以及開頭`do`遵循的繫結。</span><span class="sxs-lookup"><span data-stu-id="12567-129">In an F# class, there is always a primary constructor whose arguments are described in the `parameter-list` that follows the type name, and whose body consists of the `let` (and `let rec`) bindings at the start of the class declaration and the `do` bindings that follow.</span></span> <span data-ttu-id="12567-130">主要的建構函式的引數會在整個類別宣告的範圍內。</span><span class="sxs-lookup"><span data-stu-id="12567-130">The arguments of the primary constructor are in scope throughout the class declaration.</span></span>

<span data-ttu-id="12567-131">您可以新增額外的建構函式使用`new`關鍵字來將成員，如下所示：</span><span class="sxs-lookup"><span data-stu-id="12567-131">You can add additional constructors by using the `new` keyword to add a member, as follows:</span></span>

<span data-ttu-id="12567-132">`new`(`argument-list`) = `constructor-body`</span><span class="sxs-lookup"><span data-stu-id="12567-132">`new`(`argument-list`) = `constructor-body`</span></span>

<span data-ttu-id="12567-133">新的建構函式的主體必須叫用在類別宣告頂端指定的主要建構函式。</span><span class="sxs-lookup"><span data-stu-id="12567-133">The body of the new constructor must invoke the primary constructor that is specified at the top of the class declaration.</span></span>

<span data-ttu-id="12567-134">下列範例會說明這個概念。</span><span class="sxs-lookup"><span data-stu-id="12567-134">The following example illustrates this concept.</span></span> <span data-ttu-id="12567-135">下列程式碼，`MyClass`有兩個建構函式，接受兩個引數和其他建構函式的主要建構函式會採用任何引數。</span><span class="sxs-lookup"><span data-stu-id="12567-135">In the following code, `MyClass` has two constructors, a primary constructor that takes two arguments and another constructor that takes no arguments.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2401.fs)]

## <a name="let-and-do-bindings"></a><span data-ttu-id="12567-136">讓和 do 繫結</span><span class="sxs-lookup"><span data-stu-id="12567-136">let and do Bindings</span></span>

<span data-ttu-id="12567-137">`let`和`do`類別定義中的繫結表單的主要類別建構函式主體，並因此執行時建立的類別執行個體。</span><span class="sxs-lookup"><span data-stu-id="12567-137">The `let` and `do` bindings in a class definition form the body of the primary class constructor, and therefore they run whenever a class instance is created.</span></span> <span data-ttu-id="12567-138">如果`let`繫結函式，則它會編譯成一個成員。</span><span class="sxs-lookup"><span data-stu-id="12567-138">If a `let` binding is a function, then it is compiled into a member.</span></span> <span data-ttu-id="12567-139">如果`let`繫結是一個值，不會在任何函式或成員，則它會編譯成建構函式的本機變數。</span><span class="sxs-lookup"><span data-stu-id="12567-139">If the `let` binding is a value that is not used in any function or member, then it is compiled into a variable that is local to the constructor.</span></span> <span data-ttu-id="12567-140">否則，它會編譯到類別的欄位。</span><span class="sxs-lookup"><span data-stu-id="12567-140">Otherwise, it is compiled into a field of the class.</span></span> <span data-ttu-id="12567-141">`do`遵循的運算式都會編譯成主要建構函式，並執行每個執行個體的初始化程式碼。</span><span class="sxs-lookup"><span data-stu-id="12567-141">The `do` expressions that follow are compiled into the primary constructor and execute initialization code for every instance.</span></span> <span data-ttu-id="12567-142">任何額外的建構函式一定要呼叫的主要建構函式，因為`let`繫結和`do`繫結一定會執行不論哪一個呼叫建構函式。</span><span class="sxs-lookup"><span data-stu-id="12567-142">Because any additional constructors always call the primary constructor, the `let` bindings and `do` bindings always execute regardless of which constructor is called.</span></span>

<span data-ttu-id="12567-143">所建立的欄位`let`繫結可以存取整個方法和類別的屬性; 不過，它們無法存取的靜態方法，即使靜態方法會採用執行個體變數，做為參數。</span><span class="sxs-lookup"><span data-stu-id="12567-143">Fields that are created by `let` bindings can be accessed throughout the methods and properties of the class; however, they cannot be accessed from static methods, even if the static methods take an instance variable as a parameter.</span></span> <span data-ttu-id="12567-144">無法存取使用自我識別項，如果有的話。</span><span class="sxs-lookup"><span data-stu-id="12567-144">They cannot be accessed by using the self identifier, if one exists.</span></span>

## <a name="self-identifiers"></a><span data-ttu-id="12567-145">自我識別項</span><span class="sxs-lookup"><span data-stu-id="12567-145">Self Identifiers</span></span>

<span data-ttu-id="12567-146">A*自我識別項*是代表目前的執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="12567-146">A *self identifier* is a name that represents the current instance.</span></span> <span data-ttu-id="12567-147">自我識別項類似`this`C# 或 c + + 中的關鍵字或`Me`Visual Basic 中。</span><span class="sxs-lookup"><span data-stu-id="12567-147">Self identifiers resemble the `this` keyword in C# or C++ or `Me` in Visual Basic.</span></span> <span data-ttu-id="12567-148">您可以在兩個不同的方式，取決於您是在範圍內的整個類別定義，或只是個別的方法本身的識別項定義自我識別項。</span><span class="sxs-lookup"><span data-stu-id="12567-148">You can define a self identifier in two different ways, depending on whether you want the self identifier to be in scope for the whole class definition or just for an individual method.</span></span>

<span data-ttu-id="12567-149">若要定義整個類別的自我識別項，請使用`as`關鍵字之後的左括號的建構函式參數清單，並指定識別項名稱。</span><span class="sxs-lookup"><span data-stu-id="12567-149">To define a self identifier for the whole class, use the `as` keyword after the closing parentheses of the constructor parameter list, and specify the identifier name.</span></span>

<span data-ttu-id="12567-150">若要定義本身的識別項，只有一個方法，提供在成員宣告中之前的方法名稱和句號 （.） 做為分隔符號, 的自我識別項。</span><span class="sxs-lookup"><span data-stu-id="12567-150">To define a self identifier for just one method, provide the self identifier in the member declaration, just before the method name and a period (.) as a separator.</span></span>

<span data-ttu-id="12567-151">下列程式碼範例說明兩種方式來建立自我識別項。</span><span class="sxs-lookup"><span data-stu-id="12567-151">The following code example illustrates the two ways to create a self identifier.</span></span> <span data-ttu-id="12567-152">在第一行，`as`關鍵字用以定義自我識別項。</span><span class="sxs-lookup"><span data-stu-id="12567-152">In the first line, the `as` keyword is used to define the self identifier.</span></span> <span data-ttu-id="12567-153">在第五個列中，識別項`this`用來定義本身的識別項，其範圍限於方法`PrintMessage`。</span><span class="sxs-lookup"><span data-stu-id="12567-153">In the fifth line, the identifier `this` is used to define a self identifier whose scope is restricted to the method `PrintMessage`.</span></span>

```fsharp
type MyClass2(dataIn) as self =
    let data = dataIn
    do
        self.PrintMessage()
    member this.PrintMessage() =
        printf "Creating MyClass2 with Data %d" data
```

<span data-ttu-id="12567-154">不同於其他.NET 語言，您可以命名自我識別項但您想要的選項;您不受限於名稱這類`self`， `Me`，或`this`。</span><span class="sxs-lookup"><span data-stu-id="12567-154">Unlike in other .NET languages, you can name the self identifier however you want; you are not restricted to names such as `self`, `Me`, or `this`.</span></span>

<span data-ttu-id="12567-155">自我識別項宣告`as`之前沒有初始化關鍵字之後`let`執行繫結。</span><span class="sxs-lookup"><span data-stu-id="12567-155">The self identifier that is declared with the `as` keyword is not initialized until after the `let` bindings are executed.</span></span> <span data-ttu-id="12567-156">因此，它不能在`let`繫結。</span><span class="sxs-lookup"><span data-stu-id="12567-156">Therefore, it cannot be used in the `let` bindings.</span></span> <span data-ttu-id="12567-157">您可以使用中的自我識別項`do`繫結區段。</span><span class="sxs-lookup"><span data-stu-id="12567-157">You can use the self identifier in the `do` bindings section.</span></span>

## <a name="generic-type-parameters"></a><span data-ttu-id="12567-158">泛型型別參數</span><span class="sxs-lookup"><span data-stu-id="12567-158">Generic Type Parameters</span></span>

<span data-ttu-id="12567-159">角括號中指定泛型型別參數 (`<`和`>`)、 單引號後面接著識別項的形式。</span><span class="sxs-lookup"><span data-stu-id="12567-159">Generic type parameters are specified in angle brackets (`<` and `>`), in the form of a single quotation mark followed by an identifier.</span></span> <span data-ttu-id="12567-160">以逗號分隔多個泛型型別參數。</span><span class="sxs-lookup"><span data-stu-id="12567-160">Multiple generic type parameters are separated by commas.</span></span> <span data-ttu-id="12567-161">泛型型別參數是在範圍中宣告。</span><span class="sxs-lookup"><span data-stu-id="12567-161">The generic type parameter is in scope throughout the declaration.</span></span> <span data-ttu-id="12567-162">下列程式碼範例示範如何指定泛型型別參數。</span><span class="sxs-lookup"><span data-stu-id="12567-162">The following code example shows how to specify generic type parameters.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2403.fs)]

<span data-ttu-id="12567-163">使用類型時，就會推斷類型引數。</span><span class="sxs-lookup"><span data-stu-id="12567-163">Type arguments are inferred when the type is used.</span></span> <span data-ttu-id="12567-164">在下列程式碼中，推斷的型別會是一系列 tuple。</span><span class="sxs-lookup"><span data-stu-id="12567-164">In the following code, the inferred type is a sequence of tuples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet24031.fs)]

## <a name="specifying-inheritance"></a><span data-ttu-id="12567-165">指定的繼承</span><span class="sxs-lookup"><span data-stu-id="12567-165">Specifying Inheritance</span></span>

<span data-ttu-id="12567-166">`inherit`子句會識別直接基底類別中，如果有的話。</span><span class="sxs-lookup"><span data-stu-id="12567-166">The `inherit` clause identifies the direct base class, if there is one.</span></span> <span data-ttu-id="12567-167">在 F # 中，允許只能有一個直接的基底類別。</span><span class="sxs-lookup"><span data-stu-id="12567-167">In F#, only one direct base class is allowed.</span></span> <span data-ttu-id="12567-168">類別實作的介面不會考慮基底類別。</span><span class="sxs-lookup"><span data-stu-id="12567-168">Interfaces that a class implements are not considered base classes.</span></span> <span data-ttu-id="12567-169">介面會討論[介面](Interfaces.md)主題。</span><span class="sxs-lookup"><span data-stu-id="12567-169">Interfaces are discussed in the [Interfaces](Interfaces.md) topic.</span></span>

<span data-ttu-id="12567-170">您可以從衍生類別存取的方法和屬性的基底類別，使用該語言關鍵字`base`做為識別項，後面接著句號 （.） 和成員的名稱。</span><span class="sxs-lookup"><span data-stu-id="12567-170">You can access the methods and properties of the base class from the derived class by using the language keyword `base` as an identifier, followed by a period (.) and the name of the member.</span></span>

<span data-ttu-id="12567-171">如需詳細資訊，請參閱[繼承](inheritance.md)。</span><span class="sxs-lookup"><span data-stu-id="12567-171">For more information, see [Inheritance](inheritance.md).</span></span>

## <a name="members-section"></a><span data-ttu-id="12567-172">成員 區段</span><span class="sxs-lookup"><span data-stu-id="12567-172">Members Section</span></span>

<span data-ttu-id="12567-173">在本節中，您可以定義靜態或執行個體方法、 屬性、 介面實作，抽象成員、 事件宣告和其他建構函式。</span><span class="sxs-lookup"><span data-stu-id="12567-173">You can define static or instance methods, properties, interface implementations, abstract members, event declarations, and additional constructors in this section.</span></span> <span data-ttu-id="12567-174">可讓和執行繫結不能出現在這一節。</span><span class="sxs-lookup"><span data-stu-id="12567-174">Let and do bindings cannot appear in this section.</span></span> <span data-ttu-id="12567-175">成員可以加入各種不同的 F # 型別除了類別之外，因為它們位於不同的主題，討論[成員](members/index.md)。</span><span class="sxs-lookup"><span data-stu-id="12567-175">Because members can be added to a variety of F# types in addition to classes, they are discussed in a separate topic, [Members](members/index.md).</span></span>

## <a name="mutually-recursive-types"></a><span data-ttu-id="12567-176">相互遞迴類型</span><span class="sxs-lookup"><span data-stu-id="12567-176">Mutually Recursive Types</span></span>

<span data-ttu-id="12567-177">當您定義的循環方式彼此參考的類型時，您串接在一起的類型定義使用`and`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="12567-177">When you define types that reference each other in a circular way, you string together the type definitions by using the `and` keyword.</span></span> <span data-ttu-id="12567-178">`and`關鍵字取代`type`上以外，如下所示的第一個定義的所有關鍵字。</span><span class="sxs-lookup"><span data-stu-id="12567-178">The `and` keyword replaces the `type` keyword on all except the first definition, as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2404.fs)]

<span data-ttu-id="12567-179">輸出是一份目前的目錄中的所有檔案。</span><span class="sxs-lookup"><span data-stu-id="12567-179">The output is a list of all the files in the current directory.</span></span>

## <a name="when-to-use-classes-unions-records-and-structures"></a><span data-ttu-id="12567-180">使用類別、 聯集、 記錄和結構的時機</span><span class="sxs-lookup"><span data-stu-id="12567-180">When to Use Classes, Unions, Records, and Structures</span></span>

<span data-ttu-id="12567-181">提供的各種可從中選擇的類型，必須有充分的了解什麼每種類型專為以選取適當的型別為特定的情況。</span><span class="sxs-lookup"><span data-stu-id="12567-181">Given the variety of types to choose from, you need to have a good understanding of what each type is designed for to select the appropriate type for a particular situation.</span></span> <span data-ttu-id="12567-182">類別專為在物件導向程式設計內容中。</span><span class="sxs-lookup"><span data-stu-id="12567-182">Classes are designed for use in object-oriented programming contexts.</span></span> <span data-ttu-id="12567-183">物件導向程式設計是專為.NET Framework 撰寫的應用程式中使用的主要架構。</span><span class="sxs-lookup"><span data-stu-id="12567-183">Object-oriented programming is the dominant paradigm used in applications that are written for the .NET Framework.</span></span> <span data-ttu-id="12567-184">F # 程式碼是否與.NET Framework 或另一個物件導向程式庫密切合作，尤其是如果您的物件導向的型別系統，例如 UI 程式庫可以從擴充類別是可能適當。</span><span class="sxs-lookup"><span data-stu-id="12567-184">If your F# code has to work closely with the .NET Framework or another object-oriented library, and especially if you have to extend from an object-oriented type system such as a UI library, classes are probably appropriate.</span></span>

<span data-ttu-id="12567-185">如果您不緊密與物件導向程式碼互通，或如果您正在撰寫是各自獨立，因此防範頻繁互動以物件導向的程式碼的程式碼，您應該考慮使用記錄和差別聯集。</span><span class="sxs-lookup"><span data-stu-id="12567-185">If you are not interoperating closely with object-oriented code, or if you are writing code that is self-contained and therefore protected from frequent interaction with object-oriented code, you should consider using records and discriminated unions.</span></span> <span data-ttu-id="12567-186">單一也想到 – 逾時已區分的聯集，以及適當的模式比對程式碼中，通常可用來當做物件階層架構較簡單的替代方案。</span><span class="sxs-lookup"><span data-stu-id="12567-186">A single, well thought–out discriminated union, together with appropriate pattern matching code, can often be used as a simpler alternative to an object hierarchy.</span></span> <span data-ttu-id="12567-187">如需差別聯集的詳細資訊，請參閱[差別聯集](discriminated-unions.md)。</span><span class="sxs-lookup"><span data-stu-id="12567-187">For more information about discriminated unions, see [Discriminated Unions](discriminated-unions.md).</span></span>

<span data-ttu-id="12567-188">記錄都有的優點是比類別更簡單，但類型的需求超過功能可以使用它們簡便易行完成時，未適當的記錄。</span><span class="sxs-lookup"><span data-stu-id="12567-188">Records have the advantage of being simpler than classes, but records are not appropriate when the demands of a type exceed what can be accomplished with their simplicity.</span></span> <span data-ttu-id="12567-189">記錄是基本上簡單的彙總的值，可以執行自訂動作的不同建構函式，不含隱藏的欄位，而不繼承或介面的實作。</span><span class="sxs-lookup"><span data-stu-id="12567-189">Records are basically simple aggregates of values, without separate constructors that can perform custom actions, without hidden fields, and without inheritance or interface implementations.</span></span> <span data-ttu-id="12567-190">雖然屬性和方法等成員可以加入，使其行為更複雜的記錄中，儲存在記錄的欄位仍是以簡單的彙總的值。</span><span class="sxs-lookup"><span data-stu-id="12567-190">Although members such as properties and methods can be added to records to make their behavior more complex, the fields stored in a record are still a simple aggregate of values.</span></span> <span data-ttu-id="12567-191">如需有關記錄的詳細資訊，請參閱 <<c0> [ 記錄](records.md)。</span><span class="sxs-lookup"><span data-stu-id="12567-191">For more information about records, see [Records](records.md).</span></span>

<span data-ttu-id="12567-192">結構也適用於小型的彙總的資料，但它們不同於類別和記錄，因為它們是.NET 實值型別。</span><span class="sxs-lookup"><span data-stu-id="12567-192">Structures are also useful for small aggregates of data, but they differ from classes and records in that they are .NET value types.</span></span> <span data-ttu-id="12567-193">類別和記錄是.NET 參考型別。</span><span class="sxs-lookup"><span data-stu-id="12567-193">Classes and records are .NET reference types.</span></span> <span data-ttu-id="12567-194">由值傳遞實值型別，是不同的實值型別和參考型別語意。</span><span class="sxs-lookup"><span data-stu-id="12567-194">The semantics of value types and reference types are different in that value types are passed by value.</span></span> <span data-ttu-id="12567-195">這表示它們會複製做為參數傳遞或函式傳回時，位元的位元。</span><span class="sxs-lookup"><span data-stu-id="12567-195">This means that they are copied bit for bit when they are passed as a parameter or returned from a function.</span></span> <span data-ttu-id="12567-196">它們也儲存在堆疊上或者，如果做為欄位，內嵌於父物件，而不是儲存在他們自己在堆積上不同的位置。</span><span class="sxs-lookup"><span data-stu-id="12567-196">They are also stored on the stack or, if they are used as a field, embedded inside the parent object instead of stored in their own separate location on the heap.</span></span> <span data-ttu-id="12567-197">因此，結構是適用於經常存取的資料，存取在堆積的額外負荷的記憶體問題時。</span><span class="sxs-lookup"><span data-stu-id="12567-197">Therefore, structures are appropriate for frequently accessed data when the overhead of accessing the heap is a problem.</span></span> <span data-ttu-id="12567-198">如需結構的詳細資訊，請參閱[結構](structures.md)。</span><span class="sxs-lookup"><span data-stu-id="12567-198">For more information about structures, see [Structures](structures.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="12567-199">另請參閱</span><span class="sxs-lookup"><span data-stu-id="12567-199">See also</span></span>

- [<span data-ttu-id="12567-200">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="12567-200">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="12567-201">成員</span><span class="sxs-lookup"><span data-stu-id="12567-201">Members</span></span>](members/index.md)
- [<span data-ttu-id="12567-202">繼承</span><span class="sxs-lookup"><span data-stu-id="12567-202">Inheritance</span></span>](inheritance.md)
- [<span data-ttu-id="12567-203">介面</span><span class="sxs-lookup"><span data-stu-id="12567-203">Interfaces</span></span>](interfaces.md)
