---
title: 屬性
description: 瞭解F#屬性，這是代表與物件相關聯之值的成員。
ms.date: 05/16/2016
ms.openlocfilehash: c71d61e033501c2d535b5582c82d36ed8cb2241b
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216427"
---
# <a name="properties"></a><span data-ttu-id="cc55d-103">屬性</span><span class="sxs-lookup"><span data-stu-id="cc55d-103">Properties</span></span>

<span data-ttu-id="cc55d-104">*屬性*（property）是代表與物件相關聯之值的成員。</span><span class="sxs-lookup"><span data-stu-id="cc55d-104">*Properties* are members that represent values associated with an object.</span></span>

## <a name="syntax"></a><span data-ttu-id="cc55d-105">語法</span><span class="sxs-lookup"><span data-stu-id="cc55d-105">Syntax</span></span>

```fsharp
// Property that has both get and set defined.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName
with [accessibility-modifier] get() =
    get-function-body
and [accessibility-modifier] set parameter =
    set-function-body

// Alternative syntax for a property that has get and set.
[ attributes-for-get ]
[ static ] member [accessibility-modifier-for-get] [self-identifier.]PropertyName =
    get-function-body
[ attributes-for-set ]
[ static ] member [accessibility-modifier-for-set] [self-identifier.]PropertyName
with set parameter =
    set-function-body

// Property that has get only.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName =
    get-function-body

// Alternative syntax for property that has get only.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName
with get() =
    get-function-body

// Property that has set only.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName
with set parameter =
    set-function-body

// Automatically implemented properties.
[ attributes ]
[ static ] member val [accessibility-modifier] PropertyName = initialization-expression [ with get, set ]
```

## <a name="remarks"></a><span data-ttu-id="cc55d-106">備註</span><span class="sxs-lookup"><span data-stu-id="cc55d-106">Remarks</span></span>

<span data-ttu-id="cc55d-107">屬性代表物件導向程式設計中的「具有」關聯性，代表與物件實例相關聯的資料，或針對具有類型的靜態屬性。</span><span class="sxs-lookup"><span data-stu-id="cc55d-107">Properties represent the "has a" relationship in object-oriented programming, representing data that is associated with object instances or, for static properties, with the type.</span></span>

<span data-ttu-id="cc55d-108">您可以透過兩種方式宣告屬性，取決於您是否要明確指定屬性的基礎值（也稱為備份存放區），還是要讓編譯器自動為您產生備份存放區。</span><span class="sxs-lookup"><span data-stu-id="cc55d-108">You can declare properties in two ways, depending on whether you want to explicitly specify the underlying value (also called the backing store) for the property, or if you want to allow the compiler to automatically generate the backing store for you.</span></span> <span data-ttu-id="cc55d-109">一般而言，如果屬性具有非一般的實作為，而當屬性只是值或變數的簡單包裝函式時，您應該使用更明確的方式。</span><span class="sxs-lookup"><span data-stu-id="cc55d-109">Generally, you should use the more explicit way if the property has a non-trivial implementation and the automatic way when the property is just a simple wrapper for a value or variable.</span></span> <span data-ttu-id="cc55d-110">若要明確宣告屬性，請使用`member`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="cc55d-110">To declare a property explicitly, use the `member` keyword.</span></span> <span data-ttu-id="cc55d-111">這個宣告式語法後面會接著指定`get`和`set`方法（也稱為*存取*子）的語法。</span><span class="sxs-lookup"><span data-stu-id="cc55d-111">This declarative syntax is followed by the syntax that specifies the `get` and `set` methods, also named *accessors*.</span></span> <span data-ttu-id="cc55d-112">語法一節中顯示的各種明確語法形式，會用於讀取/寫入、唯讀和僅限寫入的屬性。</span><span class="sxs-lookup"><span data-stu-id="cc55d-112">The various forms of the explicit syntax shown in the syntax section are used for read/write, read-only, and write-only properties.</span></span> <span data-ttu-id="cc55d-113">若為唯讀屬性，您只`get`需定義方法; 對於僅限寫入屬性， `set`只定義方法。</span><span class="sxs-lookup"><span data-stu-id="cc55d-113">For read-only properties, you define only a `get` method; for write-only properties, define only a `set` method.</span></span> <span data-ttu-id="cc55d-114">請注意，當屬性同時`get`具有和`set`存取子時，替代語法可讓您指定每個存取子的不同屬性和存取範圍修飾詞，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="cc55d-114">Note that when a property has both `get` and `set` accessors, the alternative syntax enables you to specify attributes and accessibility modifiers that are different for each accessor, as is shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3201.fs)]

<span data-ttu-id="cc55d-115">對於同時`get`具有`set`和`set`方法的讀取/寫入屬性，和的順序可以反轉。`get`</span><span class="sxs-lookup"><span data-stu-id="cc55d-115">For read/write properties, which have both a `get` and `set` method, the order of `get` and `set` can be reversed.</span></span> <span data-ttu-id="cc55d-116">或者，您可以只提供針對`get`所顯示的語法，以及僅針對`set`所顯示的語法，而不是使用結合的語法。</span><span class="sxs-lookup"><span data-stu-id="cc55d-116">Alternatively, you can provide the syntax shown for `get` only and the syntax shown for `set` only instead of using the combined syntax.</span></span> <span data-ttu-id="cc55d-117">這麼做可讓您更輕鬆地將個別`get`或`set`方法標記為批註，如果這是您可能需要做的事情。</span><span class="sxs-lookup"><span data-stu-id="cc55d-117">Doing this makes it easier to comment out the individual `get` or `set` method, if that is something you might need to do.</span></span> <span data-ttu-id="cc55d-118">下列程式碼顯示使用結合語法的替代方法。</span><span class="sxs-lookup"><span data-stu-id="cc55d-118">This alternative to using the combined syntax is shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3203.fs)]

<span data-ttu-id="cc55d-119">保存屬性資料的私用值稱為「*備份存放區*」。</span><span class="sxs-lookup"><span data-stu-id="cc55d-119">Private values that hold the data for properties are called *backing stores*.</span></span> <span data-ttu-id="cc55d-120">若要讓編譯器自動建立備份存放區，請使用關鍵字`member val`，省略自我識別碼，然後提供運算式來初始化屬性。</span><span class="sxs-lookup"><span data-stu-id="cc55d-120">To have the compiler create the backing store automatically, use the keywords `member val`, omit the self-identifier, then provide an expression to initialize the property.</span></span> <span data-ttu-id="cc55d-121">如果屬性是可變動的，請包含`with get, set`。</span><span class="sxs-lookup"><span data-stu-id="cc55d-121">If the property is to be mutable, include `with get, set`.</span></span> <span data-ttu-id="cc55d-122">例如，下列類別類型包含兩個自動實作為屬性。</span><span class="sxs-lookup"><span data-stu-id="cc55d-122">For example, the following class type includes two automatically implemented properties.</span></span> <span data-ttu-id="cc55d-123">`Property1`是唯讀的，而且會初始化為提供給主要函式的引數， `Property2`而且是可設定的屬性，初始化為空字串：</span><span class="sxs-lookup"><span data-stu-id="cc55d-123">`Property1` is read-only and is initialized to the argument provided to the primary constructor, and `Property2` is a settable property initialized to an empty string:</span></span>

```fsharp
type MyClass(property1 : int) =
member val Property1 = property1
member val Property2 = "" with get, set
```

<span data-ttu-id="cc55d-124">自動執行的屬性是型別初始化的一部分，因此必須包含在其他任何成員定義之前，就像型別`let`定義中`do`的系結和系結一樣。</span><span class="sxs-lookup"><span data-stu-id="cc55d-124">Automatically implemented properties are part of the initialization of a type, so they must be included before any other member definitions, just like `let` bindings and `do` bindings in a type definition.</span></span> <span data-ttu-id="cc55d-125">請注意，初始化自動執行之屬性的運算式，只會在初始化時評估，而且不會在每次存取屬性時進行評估。</span><span class="sxs-lookup"><span data-stu-id="cc55d-125">Note that the expression that initializes an automatically implemented property is only evaluated upon initialization, and not every time the property is accessed.</span></span> <span data-ttu-id="cc55d-126">這種行為與明確實作為屬性的行為相較之下。</span><span class="sxs-lookup"><span data-stu-id="cc55d-126">This behavior is in contrast to the behavior of an explicitly implemented property.</span></span> <span data-ttu-id="cc55d-127">這實際上的意思是，將這些屬性初始化的程式碼會新增至類別的函式。</span><span class="sxs-lookup"><span data-stu-id="cc55d-127">What this effectively means is that the code to initialize these properties is added to the constructor of a class.</span></span> <span data-ttu-id="cc55d-128">請考慮下列顯示這項差異的程式碼：</span><span class="sxs-lookup"><span data-stu-id="cc55d-128">Consider the following code that shows this difference:</span></span>

```fsharp
type MyClass() =
    let random  = new System.Random()
    member val AutoProperty = random.Next() with get, set
    member this.ExplicitProperty = random.Next()

let class1 = new MyClass()

printfn "class1.AutoProperty = %d" class1.AutoProperty
printfn "class1.AutoProperty = %d" class1.AutoProperty
printfn "class1.ExplicitProperty = %d" class1.ExplicitProperty
printfn "class1.ExplicitProperty = %d" class1.ExplicitProperty
```

<span data-ttu-id="cc55d-129">**輸出**</span><span class="sxs-lookup"><span data-stu-id="cc55d-129">**Output**</span></span>

```console
class1.AutoProperty = 1853799794
class1.AutoProperty = 1853799794
class1.ExplicitProperty = 978922705
class1.ExplicitProperty = 1131210765
```

<span data-ttu-id="cc55d-130">上述程式碼的輸出顯示重複呼叫時，AutoProperty 的值不變，而 ExplicitProperty 會在每次呼叫時變更。</span><span class="sxs-lookup"><span data-stu-id="cc55d-130">The output of the preceding code shows that the value of AutoProperty is unchanged when called repeatedly, whereas the ExplicitProperty changes each time it is called.</span></span> <span data-ttu-id="cc55d-131">這會示範每次不會評估自動執行之屬性的運算式，這是明確屬性的 getter 方法。</span><span class="sxs-lookup"><span data-stu-id="cc55d-131">This demonstrates that the expression for an automatically implemented property is not evaluated each time, as is the getter method for the explicit property.</span></span>

>[!WARNING]
><span data-ttu-id="cc55d-132">有一些程式庫（例如 Entity Framework （`System.Data.Entity`），它會在基類處理常式中執行自訂作業，而這些函式無法與自動執行之屬性的初始化搭配運作。</span><span class="sxs-lookup"><span data-stu-id="cc55d-132">There are some libraries, such as the Entity Framework (`System.Data.Entity`) that perform custom operations in base class constructors that don't work well with the initialization of automatically implemented properties.</span></span> <span data-ttu-id="cc55d-133">在這些情況下，請嘗試使用明確的屬性。</span><span class="sxs-lookup"><span data-stu-id="cc55d-133">In those cases, try using explicit properties.</span></span>

<span data-ttu-id="cc55d-134">屬性可以是類別、結構、區分等位、記錄、介面和類型延伸的成員，而且也可以在物件運算式中定義。</span><span class="sxs-lookup"><span data-stu-id="cc55d-134">Properties can be members of classes, structures, discriminated unions, records, interfaces, and type extensions and can also be defined in object expressions.</span></span>

<span data-ttu-id="cc55d-135">屬性可以套用至屬性。</span><span class="sxs-lookup"><span data-stu-id="cc55d-135">Attributes can be applied to properties.</span></span> <span data-ttu-id="cc55d-136">若要將屬性套用至屬性，請在屬性前面的個別行上寫入屬性。</span><span class="sxs-lookup"><span data-stu-id="cc55d-136">To apply an attribute to a property, write the attribute on a separate line before the property.</span></span> <span data-ttu-id="cc55d-137">如需詳細資訊，請參閱[屬性](../attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="cc55d-137">For more information, see [Attributes](../attributes.md).</span></span>

<span data-ttu-id="cc55d-138">根據預設，屬性是公用的。</span><span class="sxs-lookup"><span data-stu-id="cc55d-138">By default, properties are public.</span></span> <span data-ttu-id="cc55d-139">協助工具修飾詞也可以套用至屬性。</span><span class="sxs-lookup"><span data-stu-id="cc55d-139">Accessibility modifiers can also be applied to properties.</span></span> <span data-ttu-id="cc55d-140">若要套用協助工具修飾詞，請在屬性名稱前面加上它（如果它要套用`get`至和`set`方法），如果有不同的存取範圍`set` ，請在`get`和關鍵字之前加入每個存取子的必要項。</span><span class="sxs-lookup"><span data-stu-id="cc55d-140">To apply an accessibility modifier, add it immediately before the name of the property if it is meant to apply to both the `get` and `set` methods; add it before the `get` and `set` keywords if different accessibility is required for each accessor.</span></span> <span data-ttu-id="cc55d-141">*協助工具修飾*詞可以是下列其中一項： `public`、 `private`、 `internal`。</span><span class="sxs-lookup"><span data-stu-id="cc55d-141">The *accessibility-modifier* can be one of the following: `public`, `private`, `internal`.</span></span> <span data-ttu-id="cc55d-142">如需詳細資訊，請參閱[存取控制](../access-control.md)。</span><span class="sxs-lookup"><span data-stu-id="cc55d-142">For more information, see [Access Control](../access-control.md).</span></span>

<span data-ttu-id="cc55d-143">每次存取屬性時，都會執行屬性部署。</span><span class="sxs-lookup"><span data-stu-id="cc55d-143">Property implementations are executed each time a property is accessed.</span></span>

## <a name="static-and-instance-properties"></a><span data-ttu-id="cc55d-144">靜態和實例屬性</span><span class="sxs-lookup"><span data-stu-id="cc55d-144">Static and Instance Properties</span></span>

<span data-ttu-id="cc55d-145">屬性可以是靜態或實例屬性。</span><span class="sxs-lookup"><span data-stu-id="cc55d-145">Properties can be static or instance properties.</span></span> <span data-ttu-id="cc55d-146">靜態屬性可以在不使用實例的情況下叫用，並用於與類型相關聯的值，而不是個別物件。</span><span class="sxs-lookup"><span data-stu-id="cc55d-146">Static properties can be invoked without an instance and are used for values associated with the type, not with individual objects.</span></span> <span data-ttu-id="cc55d-147">若為靜態屬性，請省略自我識別碼。</span><span class="sxs-lookup"><span data-stu-id="cc55d-147">For static properties, omit the self-identifier.</span></span> <span data-ttu-id="cc55d-148">實例屬性需要自我識別碼。</span><span class="sxs-lookup"><span data-stu-id="cc55d-148">The self-identifier is required for instance properties.</span></span>

<span data-ttu-id="cc55d-149">下列靜態屬性定義是以您具有靜態欄位`myStaticValue`的實例為基礎，該屬性是屬性的備份存放區。</span><span class="sxs-lookup"><span data-stu-id="cc55d-149">The following static property definition is based on a scenario in which you have a static field `myStaticValue` that is the backing store for the property.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3204.fs)]

<span data-ttu-id="cc55d-150">屬性也可以是類似陣列，在這種情況下，它們稱為*索引的屬性*。</span><span class="sxs-lookup"><span data-stu-id="cc55d-150">Properties can also be array-like, in which case they are called *indexed properties*.</span></span> <span data-ttu-id="cc55d-151">如需詳細資訊，請參閱已[編制索引的屬性](indexed-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="cc55d-151">For more information, see [Indexed Properties](indexed-properties.md).</span></span>

## <a name="type-annotation-for-properties"></a><span data-ttu-id="cc55d-152">屬性的類型注釋</span><span class="sxs-lookup"><span data-stu-id="cc55d-152">Type Annotation for Properties</span></span>

<span data-ttu-id="cc55d-153">在許多情況下，編譯器會有足夠的資訊可從備份存放區的類型推斷屬性的類型，但您可以藉由加入類型注釋來明確設定類型。</span><span class="sxs-lookup"><span data-stu-id="cc55d-153">In many cases, the compiler has enough information to infer the type of a property from the type of the backing store, but you can set the type explicitly by adding a type annotation.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3205.fs)]

## <a name="using-property-set-accessors"></a><span data-ttu-id="cc55d-154">使用屬性集存取子</span><span class="sxs-lookup"><span data-stu-id="cc55d-154">Using Property set Accessors</span></span>

<span data-ttu-id="cc55d-155">您可以`set` `<-`使用運算子來設定提供存取子的屬性。</span><span class="sxs-lookup"><span data-stu-id="cc55d-155">You can set properties that provide `set` accessors by using the `<-` operator.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3206.fs)]

<span data-ttu-id="cc55d-156">輸出為**20**。</span><span class="sxs-lookup"><span data-stu-id="cc55d-156">The output is **20**.</span></span>

## <a name="abstract-properties"></a><span data-ttu-id="cc55d-157">抽象屬性</span><span class="sxs-lookup"><span data-stu-id="cc55d-157">Abstract Properties</span></span>

<span data-ttu-id="cc55d-158">屬性可以是抽象的。</span><span class="sxs-lookup"><span data-stu-id="cc55d-158">Properties can be abstract.</span></span> <span data-ttu-id="cc55d-159">如同方法， `abstract`只是表示有與屬性相關聯的虛擬分派。</span><span class="sxs-lookup"><span data-stu-id="cc55d-159">As with methods, `abstract` just means that there is a virtual dispatch associated with the property.</span></span> <span data-ttu-id="cc55d-160">抽象屬性可以是真正抽象的，也就是沒有相同類別中的定義。</span><span class="sxs-lookup"><span data-stu-id="cc55d-160">Abstract properties can be truly abstract, that is, without a definition in the same class.</span></span> <span data-ttu-id="cc55d-161">因此，包含這類屬性的類別是抽象類別。</span><span class="sxs-lookup"><span data-stu-id="cc55d-161">The class that contains such a property is therefore an abstract class.</span></span> <span data-ttu-id="cc55d-162">或者，abstract 也可以表示屬性是虛擬的，在此情況下，定義必須存在於相同的類別中。</span><span class="sxs-lookup"><span data-stu-id="cc55d-162">Alternatively, abstract can just mean that a property is virtual, and in that case, a definition must be present in the same class.</span></span> <span data-ttu-id="cc55d-163">請注意，抽象屬性不得為私用，如果一個存取子是抽象的，另一個則必須是 abstract。</span><span class="sxs-lookup"><span data-stu-id="cc55d-163">Note that abstract properties must not be private, and if one accessor is abstract, the other must also be abstract.</span></span> <span data-ttu-id="cc55d-164">如需抽象類別的詳細資訊，請參閱[抽象類別](../abstract-classes.md)。</span><span class="sxs-lookup"><span data-stu-id="cc55d-164">For more information about abstract classes, see [Abstract Classes](../abstract-classes.md).</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3207.fs)]

## <a name="see-also"></a><span data-ttu-id="cc55d-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cc55d-165">See also</span></span>

- [<span data-ttu-id="cc55d-166">成員</span><span class="sxs-lookup"><span data-stu-id="cc55d-166">Members</span></span>](index.md)
- [<span data-ttu-id="cc55d-167">方法</span><span class="sxs-lookup"><span data-stu-id="cc55d-167">Methods</span></span>](methods.md)
