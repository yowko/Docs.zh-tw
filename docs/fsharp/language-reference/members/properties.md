---
title: 屬性 (F#)
description: '深入了解 F # 屬性，也就是成員代表與物件相關聯的值。'
ms.date: 05/16/2016
ms.openlocfilehash: 75d21415b44ccc1c26ef5f478d5f5de20c3412e8
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43784890"
---
# <a name="properties"></a><span data-ttu-id="50b57-103">屬性</span><span class="sxs-lookup"><span data-stu-id="50b57-103">Properties</span></span>

<span data-ttu-id="50b57-104">*屬性*成員代表與物件相關聯的值。</span><span class="sxs-lookup"><span data-stu-id="50b57-104">*Properties* are members that represent values associated with an object.</span></span>

## <a name="syntax"></a><span data-ttu-id="50b57-105">語法</span><span class="sxs-lookup"><span data-stu-id="50b57-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="50b57-106">備註</span><span class="sxs-lookup"><span data-stu-id="50b57-106">Remarks</span></span>

<span data-ttu-id="50b57-107">屬性代表 「 擁有 」 關聯性，在物件導向程式設計中，表示物件執行個體或靜態屬性，與類型相關聯的資料。</span><span class="sxs-lookup"><span data-stu-id="50b57-107">Properties represent the "has a" relationship in object-oriented programming, representing data that is associated with object instances or, for static properties, with the type.</span></span>

<span data-ttu-id="50b57-108">您可以宣告兩種方式，取決於您是否要明確指定為 屬性 的 基礎值 （也稱為 「 備份存放區 」），或如果您想要讓編譯器自動產生您的備份存放區中的屬性。</span><span class="sxs-lookup"><span data-stu-id="50b57-108">You can declare properties in two ways, depending on whether you want to explicitly specify the underlying value (also called the backing store) for the property, or if you want to allow the compiler to automatically generate the backing store for you.</span></span> <span data-ttu-id="50b57-109">一般而言，您應該使用更明確的方式，如果屬性有非一般的實作和自動的方式在屬性時只是簡單包裝函式的值或變數。</span><span class="sxs-lookup"><span data-stu-id="50b57-109">Generally, you should use the more explicit way if the property has a non-trivial implementation and the automatic way when the property is just a simple wrapper for a value or variable.</span></span> <span data-ttu-id="50b57-110">若要明確宣告屬性時，使用`member`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="50b57-110">To declare a property explicitly, use the `member` keyword.</span></span> <span data-ttu-id="50b57-111">這個宣告式語法後面指定的語法`get`並`set`方法，也稱為*存取子*。</span><span class="sxs-lookup"><span data-stu-id="50b57-111">This declarative syntax is followed by the syntax that specifies the `get` and `set` methods, also named *accessors*.</span></span> <span data-ttu-id="50b57-112">各種形式的明確語法 」 一節所示的語法用於讀取/寫入、 唯讀和唯寫屬性。</span><span class="sxs-lookup"><span data-stu-id="50b57-112">The various forms of the explicit syntax shown in the syntax section are used for read/write, read-only, and write-only properties.</span></span> <span data-ttu-id="50b57-113">唯讀屬性，您只會定義`get`方法; 唯寫屬性，定義只`set`方法。</span><span class="sxs-lookup"><span data-stu-id="50b57-113">For read-only properties, you define only a `get` method; for write-only properties, define only a `set` method.</span></span> <span data-ttu-id="50b57-114">請注意，當屬性具有`get`和`set`存取子，替代語法可以可讓您指定屬性和不同的每個存取子，如下列程式碼所示的存取範圍修飾詞。</span><span class="sxs-lookup"><span data-stu-id="50b57-114">Note that when a property has both `get` and `set` accessors, the alternative syntax enables you to specify attributes and accessibility modifiers that are different for each accessor, as is shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3201.fs)]

<span data-ttu-id="50b57-115">讀取/寫入屬性，同時擁有`get`並`set`方法時，順序`get`和`set`可反轉。</span><span class="sxs-lookup"><span data-stu-id="50b57-115">For read/write properties, which have both a `get` and `set` method, the order of `get` and `set` can be reversed.</span></span> <span data-ttu-id="50b57-116">或者，您可以在其中提供所顯示的語法`get`只顯示的語法和`set`只而不是使用合併的語法。</span><span class="sxs-lookup"><span data-stu-id="50b57-116">Alternatively, you can provide the syntax shown for `get` only and the syntax shown for `set` only instead of using the combined syntax.</span></span> <span data-ttu-id="50b57-117">如此一來更輕鬆地標記為註解個別`get`或`set`方法，如果是您可能需要執行的項目。</span><span class="sxs-lookup"><span data-stu-id="50b57-117">Doing this makes it easier to comment out the individual `get` or `set` method, if that is something you might need to do.</span></span> <span data-ttu-id="50b57-118">此替代方案，使用合併的語法是由下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="50b57-118">This alternative to using the combined syntax is shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3203.fs)]

<span data-ttu-id="50b57-119">私用值屬性的資料呼叫該按住不放*備份存放區*。</span><span class="sxs-lookup"><span data-stu-id="50b57-119">Private values that hold the data for properties are called *backing stores*.</span></span> <span data-ttu-id="50b57-120">若要讓編譯器自動建立的備份存放區，使用關鍵字`member val`，省略自我識別項，然後提供運算式以初始化屬性。</span><span class="sxs-lookup"><span data-stu-id="50b57-120">To have the compiler create the backing store automatically, use the keywords `member val`, omit the self-identifier, then provide an expression to initialize the property.</span></span> <span data-ttu-id="50b57-121">如果屬性是可變動的包括`with get, set`。</span><span class="sxs-lookup"><span data-stu-id="50b57-121">If the property is to be mutable, include `with get, set`.</span></span> <span data-ttu-id="50b57-122">比方說，下列的類別類型包含兩個自動實作的屬性。</span><span class="sxs-lookup"><span data-stu-id="50b57-122">For example, the following class type includes two automatically implemented properties.</span></span> <span data-ttu-id="50b57-123">`Property1` 是唯讀的而且初始化為提供的主要建構函式的引數和`Property2`是可設定的屬性初始化為空字串：</span><span class="sxs-lookup"><span data-stu-id="50b57-123">`Property1` is read-only and is initialized to the argument provided to the primary constructor, and `Property2` is a settable property initialized to an empty string:</span></span>

```fsharp
type MyClass(property1 : int) =
member val Property1 = property1
member val Property2 = "" with get, set
```

<span data-ttu-id="50b57-124">自動實作的屬性是一個型別，初始化的一部分，讓它們必須包含其他成員定義之前一樣`let`繫結和`do`型別定義中的繫結。</span><span class="sxs-lookup"><span data-stu-id="50b57-124">Automatically implemented properties are part of the initialization of a type, so they must be included before any other member definitions, just like `let` bindings and `do` bindings in a type definition.</span></span> <span data-ttu-id="50b57-125">請注意在初始化時，以及每次存取該屬性時不只會評估運算式，以初始化自動實作的屬性。</span><span class="sxs-lookup"><span data-stu-id="50b57-125">Note that the expression that initializes an automatically implemented property is only evaluated upon initialization, and not every time the property is accessed.</span></span> <span data-ttu-id="50b57-126">此行為是明確地實作之屬性的行為相反。</span><span class="sxs-lookup"><span data-stu-id="50b57-126">This behavior is in contrast to the behavior of an explicitly implemented property.</span></span> <span data-ttu-id="50b57-127">這實際上就表示，初始化這些屬性的程式碼會新增至類別的建構函式。</span><span class="sxs-lookup"><span data-stu-id="50b57-127">What this effectively means is that the code to initialize these properties is added to the constructor of a class.</span></span> <span data-ttu-id="50b57-128">請考慮下列程式碼顯示這項差異：</span><span class="sxs-lookup"><span data-stu-id="50b57-128">Consider the following code that shows this difference:</span></span>

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

<span data-ttu-id="50b57-129">**輸出**</span><span class="sxs-lookup"><span data-stu-id="50b57-129">**Output**</span></span>

```
class1.AutoProperty = 1853799794
class1.AutoProperty = 1853799794
class1.ExplicitProperty = 978922705
class1.ExplicitProperty = 1131210765
```

<span data-ttu-id="50b57-130">上述程式碼的輸出會顯示值的 AutoProperty 是不變時重複呼叫而 ExplicitProperty 變更每次呼叫時。</span><span class="sxs-lookup"><span data-stu-id="50b57-130">The output of the preceding code shows that the value of AutoProperty is unchanged when called repeatedly, whereas the ExplicitProperty changes each time it is called.</span></span> <span data-ttu-id="50b57-131">這示範自動實作屬性的運算式不會評估每次都是明確的屬性的 getter 方法。</span><span class="sxs-lookup"><span data-stu-id="50b57-131">This demonstrates that the expression for an automatically implemented property is not evaluated each time, as is the getter method for the explicit property.</span></span>

>[!WARNING]
<span data-ttu-id="50b57-132">有一些程式庫，例如 Entity Framework (`System.Data.Entity`)，也不使用初始化自動實作屬性的基底類別建構函式中執行的自訂作業。</span><span class="sxs-lookup"><span data-stu-id="50b57-132">There are some libraries, such as the Entity Framework (`System.Data.Entity`) that perform custom operations in base class constructors that don't work well with the initialization of automatically implemented properties.</span></span> <span data-ttu-id="50b57-133">在這些情況下，請嘗試使用明確的屬性。</span><span class="sxs-lookup"><span data-stu-id="50b57-133">In those cases, try using explicit properties.</span></span>

<span data-ttu-id="50b57-134">屬性可以是類別、 結構、 差別聯的集、 記錄、 介面和型別延伸模組的成員，也可以在物件運算式中定義。</span><span class="sxs-lookup"><span data-stu-id="50b57-134">Properties can be members of classes, structures, discriminated unions, records, interfaces, and type extensions and can also be defined in object expressions.</span></span>

<span data-ttu-id="50b57-135">屬性可以套用至屬性。</span><span class="sxs-lookup"><span data-stu-id="50b57-135">Attributes can be applied to properties.</span></span> <span data-ttu-id="50b57-136">若要將屬性套用至屬性，撰寫屬性的屬性之前的個別行上。</span><span class="sxs-lookup"><span data-stu-id="50b57-136">To apply an attribute to a property, write the attribute on a separate line before the property.</span></span> <span data-ttu-id="50b57-137">如需詳細資訊，請參閱[屬性](../attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="50b57-137">For more information, see [Attributes](../attributes.md).</span></span>

<span data-ttu-id="50b57-138">根據預設，屬性是公用的。</span><span class="sxs-lookup"><span data-stu-id="50b57-138">By default, properties are public.</span></span> <span data-ttu-id="50b57-139">存取範圍修飾詞也可以套用至屬性。</span><span class="sxs-lookup"><span data-stu-id="50b57-139">Accessibility modifiers can also be applied to properties.</span></span> <span data-ttu-id="50b57-140">若要套用的存取範圍修飾詞，將其新增的屬性名稱之前，立即若它用來同時適用於`get`並`set`方法，將它之前新增`get`和`set`關鍵字，如果不同的存取範圍是每個存取子的必要項。</span><span class="sxs-lookup"><span data-stu-id="50b57-140">To apply an accessibility modifier, add it immediately before the name of the property if it is meant to apply to both the `get` and `set` methods; add it before the `get` and `set` keywords if different accessibility is required for each accessor.</span></span> <span data-ttu-id="50b57-141">*存取範圍修飾詞*可以是下列其中之一： `public`， `private`， `internal`。</span><span class="sxs-lookup"><span data-stu-id="50b57-141">The *accessibility-modifier* can be one of the following: `public`, `private`, `internal`.</span></span> <span data-ttu-id="50b57-142">如需詳細資訊，請參閱[存取控制](../access-control.md)。</span><span class="sxs-lookup"><span data-stu-id="50b57-142">For more information, see [Access Control](../access-control.md).</span></span>

<span data-ttu-id="50b57-143">屬性的實作會執行每次存取時的屬性。</span><span class="sxs-lookup"><span data-stu-id="50b57-143">Property implementations are executed each time a property is accessed.</span></span>

## <a name="static-and-instance-properties"></a><span data-ttu-id="50b57-144">靜態和執行個體屬性</span><span class="sxs-lookup"><span data-stu-id="50b57-144">Static and Instance Properties</span></span>

<span data-ttu-id="50b57-145">屬性可以是靜態或執行個體屬性。</span><span class="sxs-lookup"><span data-stu-id="50b57-145">Properties can be static or instance properties.</span></span> <span data-ttu-id="50b57-146">沒有執行個體就可以叫用靜態屬性，以及用於不具有個別物件的類型相關聯的值。</span><span class="sxs-lookup"><span data-stu-id="50b57-146">Static properties can be invoked without an instance and are used for values associated with the type, not with individual objects.</span></span> <span data-ttu-id="50b57-147">靜態屬性，請省略自我識別項。</span><span class="sxs-lookup"><span data-stu-id="50b57-147">For static properties, omit the self-identifier.</span></span> <span data-ttu-id="50b57-148">執行個體屬性需要自我識別項。</span><span class="sxs-lookup"><span data-stu-id="50b57-148">The self-identifier is required for instance properties.</span></span>

<span data-ttu-id="50b57-149">下列的靜態屬性定義為基礎的案例中，您有靜態欄位`myStaticValue`也就是屬性的備份存放區。</span><span class="sxs-lookup"><span data-stu-id="50b57-149">The following static property definition is based on a scenario in which you have a static field `myStaticValue` that is the backing store for the property.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3204.fs)]

<span data-ttu-id="50b57-150">屬性也可以與陣列在此情況下呼叫它們*編製索引屬性*。</span><span class="sxs-lookup"><span data-stu-id="50b57-150">Properties can also be array-like, in which case they are called *indexed properties*.</span></span> <span data-ttu-id="50b57-151">如需詳細資訊，請參閱 <<c0> [ 編製索引的屬性](indexed-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="50b57-151">For more information, see [Indexed Properties](indexed-properties.md).</span></span>

## <a name="type-annotation-for-properties"></a><span data-ttu-id="50b57-152">屬性的型別註釋</span><span class="sxs-lookup"><span data-stu-id="50b57-152">Type Annotation for Properties</span></span>

<span data-ttu-id="50b57-153">在許多情況下，編譯器有足夠的資訊來推斷的類型屬性，以從備份存放區的類型，但您可以明確設定類型，加上型別註釋。</span><span class="sxs-lookup"><span data-stu-id="50b57-153">In many cases, the compiler has enough information to infer the type of a property from the type of the backing store, but you can set the type explicitly by adding a type annotation.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3205.fs)]

## <a name="using-property-set-accessors"></a><span data-ttu-id="50b57-154">使用屬性 set 存取子</span><span class="sxs-lookup"><span data-stu-id="50b57-154">Using Property set Accessors</span></span>

<span data-ttu-id="50b57-155">您可以設定屬性，可提供`set`存取子使用`<-`運算子。</span><span class="sxs-lookup"><span data-stu-id="50b57-155">You can set properties that provide `set` accessors by using the `<-` operator.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3206.fs)]

<span data-ttu-id="50b57-156">輸出是**20**。</span><span class="sxs-lookup"><span data-stu-id="50b57-156">The output is **20**.</span></span>

## <a name="abstract-properties"></a><span data-ttu-id="50b57-157">抽象屬性</span><span class="sxs-lookup"><span data-stu-id="50b57-157">Abstract Properties</span></span>

<span data-ttu-id="50b57-158">屬性可以是抽象的。</span><span class="sxs-lookup"><span data-stu-id="50b57-158">Properties can be abstract.</span></span> <span data-ttu-id="50b57-159">如同方法`abstract`只是表示是虛擬的分派與屬性相關聯。</span><span class="sxs-lookup"><span data-stu-id="50b57-159">As with methods, `abstract` just means that there is a virtual dispatch associated with the property.</span></span> <span data-ttu-id="50b57-160">抽象屬性可以是真正抽象的也就是沒有相同的類別中定義。</span><span class="sxs-lookup"><span data-stu-id="50b57-160">Abstract properties can be truly abstract, that is, without a definition in the same class.</span></span> <span data-ttu-id="50b57-161">包含這類屬性的類別，因此是抽象類別。</span><span class="sxs-lookup"><span data-stu-id="50b57-161">The class that contains such a property is therefore an abstract class.</span></span> <span data-ttu-id="50b57-162">或者，屬性是虛擬的，和在此情況下，必須存在於相同的類別定義，可以只是抽象。</span><span class="sxs-lookup"><span data-stu-id="50b57-162">Alternatively, abstract can just mean that a property is virtual, and in that case, a definition must be present in the same class.</span></span> <span data-ttu-id="50b57-163">請注意，抽象屬性不是私人的而且如果其中一個存取子是 abstract，另也必須為抽象。</span><span class="sxs-lookup"><span data-stu-id="50b57-163">Note that abstract properties must not be private, and if one accessor is abstract, the other must also be abstract.</span></span> <span data-ttu-id="50b57-164">如需抽象類別的詳細資訊，請參閱[抽象類別](../abstract-classes.md)。</span><span class="sxs-lookup"><span data-stu-id="50b57-164">For more information about abstract classes, see [Abstract Classes](../abstract-classes.md).</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3207.fs)]

## <a name="see-also"></a><span data-ttu-id="50b57-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="50b57-165">See also</span></span>

- [<span data-ttu-id="50b57-166">成員</span><span class="sxs-lookup"><span data-stu-id="50b57-166">Members</span></span>](index.md)
- [<span data-ttu-id="50b57-167">方法</span><span class="sxs-lookup"><span data-stu-id="50b57-167">Methods</span></span>](methods.md)
