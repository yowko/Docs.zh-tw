---
title: 屬性
description: 了解 C# 屬性，其中包含驗證、計算值、延遲評估和屬性變更通知的功能。
ms.date: 04/25/2018
ms.openlocfilehash: 6638ae74516d7546882c8a380eed9b03ff3d18e9
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69587397"
---
# <a name="properties"></a><span data-ttu-id="5019e-103">屬性</span><span class="sxs-lookup"><span data-stu-id="5019e-103">Properties</span></span>

<span data-ttu-id="5019e-104">屬性是 C# 中的頭等成員。</span><span class="sxs-lookup"><span data-stu-id="5019e-104">Properties are first class citizens in C#.</span></span> <span data-ttu-id="5019e-105">該語言所定義的語法，可讓開發人員撰寫正確表示其設計意圖的程式碼。</span><span class="sxs-lookup"><span data-stu-id="5019e-105">The language defines syntax that enables developers to write code that accurately expresses their design intent.</span></span>

<span data-ttu-id="5019e-106">屬性在存取時的行為與欄位一樣。</span><span class="sxs-lookup"><span data-stu-id="5019e-106">Properties behave like fields when they are accessed.</span></span>
<span data-ttu-id="5019e-107">不過不同於欄位，屬性是透過存取子來實作，這些存取子會定義存取或指派屬性時所執行的陳述式。</span><span class="sxs-lookup"><span data-stu-id="5019e-107">However, unlike fields, properties are implemented with accessors that define the statements executed when a property is accessed or assigned.</span></span>

## <a name="property-syntax"></a><span data-ttu-id="5019e-108">屬性語法</span><span class="sxs-lookup"><span data-stu-id="5019e-108">Property syntax</span></span>

<span data-ttu-id="5019e-109">屬性的語法是欄位的自然延伸。</span><span class="sxs-lookup"><span data-stu-id="5019e-109">The syntax for properties is a natural extension to fields.</span></span> <span data-ttu-id="5019e-110">欄位可定義儲存位置：</span><span class="sxs-lookup"><span data-stu-id="5019e-110">A field defines a storage location:</span></span>

[!code-csharp[Person class with public fields](../../samples/snippets/csharp/properties/Person.cs#1)]

<span data-ttu-id="5019e-111">屬性定義包含 `get` 和 `set` 存取子的宣告，以擷取和指派該屬性的值：</span><span class="sxs-lookup"><span data-stu-id="5019e-111">A property definition contains declarations for a `get` and `set` accessor that retrieves and assigns the value of that property:</span></span>

[!code-csharp[Person class with public properties](../../samples/snippets/csharp/properties/Person.cs#2)]

<span data-ttu-id="5019e-112">以上所示的語法為「Auto 屬性」  語法。</span><span class="sxs-lookup"><span data-stu-id="5019e-112">The syntax shown above is the *auto property* syntax.</span></span> <span data-ttu-id="5019e-113">編譯器會為欄位產生儲存位置，以備份此屬性。</span><span class="sxs-lookup"><span data-stu-id="5019e-113">The compiler generates the storage location for the field that backs up the property.</span></span> <span data-ttu-id="5019e-114">編譯器也會實作 `get` 和 `set` 存取子的主體。</span><span class="sxs-lookup"><span data-stu-id="5019e-114">The compiler also implements the body of the `get` and `set` accessors.</span></span>

<span data-ttu-id="5019e-115">有時候，您需要將屬性初始化為其類型的預設值以外的值。</span><span class="sxs-lookup"><span data-stu-id="5019e-115">Sometimes, you need to initialize a property to a value other than the default for its type.</span></span>  <span data-ttu-id="5019e-116">C# 可讓您在屬性的右括弧之後設定一個值，以執行上述作業。</span><span class="sxs-lookup"><span data-stu-id="5019e-116">C# enables that by setting a value after the closing brace for the property.</span></span> <span data-ttu-id="5019e-117">您可能偏好將 `FirstName` 屬性的初始值設為空字串而非 `null`。</span><span class="sxs-lookup"><span data-stu-id="5019e-117">You may prefer the initial value for the `FirstName` property to be the empty string rather than `null`.</span></span> <span data-ttu-id="5019e-118">您可依下列方式來進行上述設定：</span><span class="sxs-lookup"><span data-stu-id="5019e-118">You would specify that as shown below:</span></span>

[!code-csharp[Person class with properties and initializer](../../samples/snippets/csharp/properties/Person.cs#3)]

<span data-ttu-id="5019e-119">如您在本文稍後所見，特定的初始化最適合用於唯讀屬性。</span><span class="sxs-lookup"><span data-stu-id="5019e-119">Specific initialization is most useful for read-only properties, as you'll see later in this article.</span></span>

<span data-ttu-id="5019e-120">您也可以自行定義儲存體，如下所示：</span><span class="sxs-lookup"><span data-stu-id="5019e-120">You can also define the storage yourself, as shown below:</span></span>

[!code-csharp[Person class with properties and backing field](../../samples/snippets/csharp/properties/Person.cs#4)]

<span data-ttu-id="5019e-121">當屬性實作為單一運算式時，您可以針對 getter 或 setter 使用「運算式主體成員」  ：</span><span class="sxs-lookup"><span data-stu-id="5019e-121">When a property implementation is a single expression, you can use *expression-bodied members* for the getter or setter:</span></span>

[!code-csharp[Person class with properties and expression bodied getters and setters](../../samples/snippets/csharp/properties/Person.cs#5)]

<span data-ttu-id="5019e-122">本文會在適用的所有情況下使用這種簡化語法。</span><span class="sxs-lookup"><span data-stu-id="5019e-122">This simplified syntax will be used where applicable throughout this article.</span></span>

<span data-ttu-id="5019e-123">以上所示的屬性定義為讀寫屬性。</span><span class="sxs-lookup"><span data-stu-id="5019e-123">The property definition shown above is a read-write property.</span></span> <span data-ttu-id="5019e-124">請注意 set 存取子中的關鍵字 `value`。</span><span class="sxs-lookup"><span data-stu-id="5019e-124">Notice the keyword `value` in the set accessor.</span></span> <span data-ttu-id="5019e-125">`set` 存取子一定會有一個名為 `value` 的參數。</span><span class="sxs-lookup"><span data-stu-id="5019e-125">The `set` accessor always has a single parameter named `value`.</span></span> <span data-ttu-id="5019e-126">`get` 存取子必須傳回可轉換成屬性類型 (在此範例中為 `string`) 的值。</span><span class="sxs-lookup"><span data-stu-id="5019e-126">The `get` accessor must return a value that is convertible to the type of the property (`string` in this example).</span></span>

<span data-ttu-id="5019e-127">這是此語法的基本概念。</span><span class="sxs-lookup"><span data-stu-id="5019e-127">That's the basics of the syntax.</span></span> <span data-ttu-id="5019e-128">還有許多不同的變化，可支援各種不同的設計慣例。</span><span class="sxs-lookup"><span data-stu-id="5019e-128">There are many different variations that support a variety of different design idioms.</span></span> <span data-ttu-id="5019e-129">讓我們探索並了解各自的語法選項。</span><span class="sxs-lookup"><span data-stu-id="5019e-129">Let's explore, and learn the syntax options for each.</span></span>

## <a name="scenarios"></a><span data-ttu-id="5019e-130">案例</span><span class="sxs-lookup"><span data-stu-id="5019e-130">Scenarios</span></span>

<span data-ttu-id="5019e-131">上述範例顯示屬性定義的一個最簡單案例，那就是不具驗證的讀/寫屬性。</span><span class="sxs-lookup"><span data-stu-id="5019e-131">The examples above showed one of the simplest cases of property definition: a read-write property with no validation.</span></span> <span data-ttu-id="5019e-132">藉由在 `get` 和 `set` 存取子中撰寫您所需的程式碼，您就可以建立許多不同的案例。</span><span class="sxs-lookup"><span data-stu-id="5019e-132">By writing the code you want in the `get` and `set` accessors, you can create many different scenarios.</span></span>

### <a name="validation"></a><span data-ttu-id="5019e-133">驗證</span><span class="sxs-lookup"><span data-stu-id="5019e-133">Validation</span></span>

<span data-ttu-id="5019e-134">您可以在 `set` 存取子中撰寫程式碼，以確保由屬性所表示的值一定有效。</span><span class="sxs-lookup"><span data-stu-id="5019e-134">You can write code in the `set` accessor to ensure that the values represented by a property are always valid.</span></span> <span data-ttu-id="5019e-135">例如，假設 `Person` 類別的一項規則是名稱不可為空白或空白字元。</span><span class="sxs-lookup"><span data-stu-id="5019e-135">For example, suppose one rule for the `Person` class is that the name cannot be blank or white space.</span></span> <span data-ttu-id="5019e-136">您可以撰寫如下：</span><span class="sxs-lookup"><span data-stu-id="5019e-136">You would write that as follows:</span></span>

[!code-csharp[Validating property setters](../../samples/snippets/csharp/properties/Person.cs#6)]

<span data-ttu-id="5019e-137">使用 `throw` 運算式作為屬性 setter 驗證的一部分，即可簡化上述範例：</span><span class="sxs-lookup"><span data-stu-id="5019e-137">The preceding example can be simplified by using a`throw` expression as part of the property setter validation:</span></span>

[!code-csharp[Validating property setters](../../samples/snippets/csharp/properties/Person.cs#7)]

<span data-ttu-id="5019e-138">上述範例會強制執行第一個名稱不得為空白或空白字元的規則。</span><span class="sxs-lookup"><span data-stu-id="5019e-138">The example above enforces the rule that the first name must not be blank or white space.</span></span> <span data-ttu-id="5019e-139">如果開發人員撰寫</span><span class="sxs-lookup"><span data-stu-id="5019e-139">If a developer writes</span></span>

```csharp
hero.FirstName = "";
```

<span data-ttu-id="5019e-140">該指派會擲回 `ArgumentException`。</span><span class="sxs-lookup"><span data-stu-id="5019e-140">That assignment throws an `ArgumentException`.</span></span> <span data-ttu-id="5019e-141">由於屬性的 set 存取子必須有無效的傳回型別，因此您擲回一個例外狀況來回報 set 存取子中發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="5019e-141">Because a property set accessor must have a void return type, you report errors in the set accessor by throwing an exception.</span></span>

<span data-ttu-id="5019e-142">您可以將同一個語法擴充為案例所需的任何語法。</span><span class="sxs-lookup"><span data-stu-id="5019e-142">You can extend this same syntax to anything needed in your scenario.</span></span> <span data-ttu-id="5019e-143">您可以檢查不同屬性之間的關聯性，或針對任何外部條件進行驗證。</span><span class="sxs-lookup"><span data-stu-id="5019e-143">You can check the relationships between different properties, or validate against any external conditions.</span></span> <span data-ttu-id="5019e-144">任何有效的 C# 陳述式在屬性存取子中都是有效的。</span><span class="sxs-lookup"><span data-stu-id="5019e-144">Any valid C# statements are valid in a property accessor.</span></span>

### <a name="read-only"></a><span data-ttu-id="5019e-145">唯讀</span><span class="sxs-lookup"><span data-stu-id="5019e-145">Read-only</span></span>

<span data-ttu-id="5019e-146">到目前為止，您所看到的所有屬性定義都是具有 public 存取子的讀取/寫入屬性。</span><span class="sxs-lookup"><span data-stu-id="5019e-146">Up to this point, all the property definitions you have seen are read/write properties with public accessors.</span></span> <span data-ttu-id="5019e-147">這不是屬性唯一有效的存取範圍。</span><span class="sxs-lookup"><span data-stu-id="5019e-147">That's not the only valid accessibility for properties.</span></span>
<span data-ttu-id="5019e-148">您可以建立唯讀屬性，或是為 set 和 get 存取子提供不同的存取範圍。</span><span class="sxs-lookup"><span data-stu-id="5019e-148">You can create read-only properties, or give different accessibility to the set and get accessors.</span></span> <span data-ttu-id="5019e-149">假設您的 `Person` 類別只能允許從該類別中的其他方法變更 `FirstName` 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="5019e-149">Suppose that your `Person` class should only enable changing the value of the `FirstName` property from other methods in that class.</span></span> <span data-ttu-id="5019e-150">您可以為 set 存取子提供 `private` 存取範圍，而不是 `public`：</span><span class="sxs-lookup"><span data-stu-id="5019e-150">You could give the set accessor `private` accessibility instead of `public`:</span></span>

[!code-csharp[Using a private setter for a publicly readonly property](../../samples/snippets/csharp/properties/Person.cs#8)]

<span data-ttu-id="5019e-151">現在，`FirstName` 屬性可從任何程式碼存取，但只能從 `Person` 類別中的其他程式碼指派。</span><span class="sxs-lookup"><span data-stu-id="5019e-151">Now, the `FirstName` property can be accessed from any code, but it can only be assigned from other code in the `Person` class.</span></span>

<span data-ttu-id="5019e-152">您可以將任何嚴格的存取修飾詞新增至 set 或 get 存取子。</span><span class="sxs-lookup"><span data-stu-id="5019e-152">You can add any restrictive access modifier to either the set or get accessors.</span></span> <span data-ttu-id="5019e-153">您放在個別存取子上的任何存取修飾詞，必須比屬性定義上的存取修飾詞具有更多限制。</span><span class="sxs-lookup"><span data-stu-id="5019e-153">Any access modifier you place on the individual accessor must be more limited than the access modifier on the property definition.</span></span> <span data-ttu-id="5019e-154">由於 `FirstName` 屬性為 `public`，但 set 存取子為 `private`，因此上述範例合法。</span><span class="sxs-lookup"><span data-stu-id="5019e-154">The above is legal because the `FirstName` property is `public`, but the set accessor is `private`.</span></span> <span data-ttu-id="5019e-155">您無法使用 `public` 存取子宣告 `private` 屬性。</span><span class="sxs-lookup"><span data-stu-id="5019e-155">You could not declare a `private` property with a `public` accessor.</span></span> <span data-ttu-id="5019e-156">屬性宣告也可以宣告為 `protected`、`internal`、`protected internal`，甚至是 `private`。</span><span class="sxs-lookup"><span data-stu-id="5019e-156">Property declarations can also be declared `protected`, `internal`, `protected internal`, or, even `private`.</span></span>

<span data-ttu-id="5019e-157">您也可以將更嚴格的修飾詞放在 `get` 存取子上。</span><span class="sxs-lookup"><span data-stu-id="5019e-157">It is also legal to place the more restrictive modifier on the `get` accessor.</span></span> <span data-ttu-id="5019e-158">例如，您可能會有 `public` 屬性，但將 `get` 存取子限制為 `private`。</span><span class="sxs-lookup"><span data-stu-id="5019e-158">For example, you could have a `public` property, but restrict the `get` accessor to `private`.</span></span> <span data-ttu-id="5019e-159">這種情況在實務上很罕見。</span><span class="sxs-lookup"><span data-stu-id="5019e-159">That scenario is rarely done in practice.</span></span>

<span data-ttu-id="5019e-160">您也可以限制屬性的修改，只在建構函式或屬性的初始設定式中加以設定。</span><span class="sxs-lookup"><span data-stu-id="5019e-160">You can also restrict modifications to a property so that it can only be set in a constructor or a property initializer.</span></span> <span data-ttu-id="5019e-161">您可以修改 `Person` 類別，如下所示：</span><span class="sxs-lookup"><span data-stu-id="5019e-161">You can modify the `Person` class so as follows:</span></span>

[!code-csharp[A readonly auto implemented property](../../samples/snippets/csharp/properties/Person.cs#9)]

<span data-ttu-id="5019e-162">這項功能最常用於初始化會公開為唯讀屬性的集合：</span><span class="sxs-lookup"><span data-stu-id="5019e-162">This feature is most commonly used for initializing collections that are exposed as read-only properties:</span></span>

```csharp
public class Measurements
{
    public ICollection<DataPoint> points { get; } = new List<DataPoint>();
}
```

### <a name="computed-properties"></a><span data-ttu-id="5019e-163">計算屬性</span><span class="sxs-lookup"><span data-stu-id="5019e-163">Computed properties</span></span>

<span data-ttu-id="5019e-164">屬性不需要直接傳回成員欄位的值。</span><span class="sxs-lookup"><span data-stu-id="5019e-164">A property does not need to simply return the value of a member field.</span></span> <span data-ttu-id="5019e-165">您可以建立傳回計算值的屬性。</span><span class="sxs-lookup"><span data-stu-id="5019e-165">You can create properties that return a computed value.</span></span> <span data-ttu-id="5019e-166">讓我們展開 `Person` 物件，以傳回串連名字和姓氏計算得到的完整名稱：</span><span class="sxs-lookup"><span data-stu-id="5019e-166">Let's expand the `Person` object to return the full name, computed by concatenating the first and last names:</span></span>

[!code-csharp[A computed property](../../samples/snippets/csharp/properties/Person.cs#10)]

<span data-ttu-id="5019e-167">上述範例使用[字串內插補點](./language-reference/tokens/interpolated.md)功能，來建立完整名稱的格式化字串。</span><span class="sxs-lookup"><span data-stu-id="5019e-167">The example above uses the [string interpolation](./language-reference/tokens/interpolated.md) feature to create the formatted string for the full name.</span></span>

<span data-ttu-id="5019e-168">您也可以使用「運算式主體成員」  ，以提供更簡潔的方法來建立計算的 `FullName` 屬性：</span><span class="sxs-lookup"><span data-stu-id="5019e-168">You can also use an *expression-bodied member*, which provides a more succinct way to create the computed `FullName` property:</span></span>

[!code-csharp[A computed property using an expression bodied member](../../samples/snippets/csharp/properties/Person.cs#11)]

<span data-ttu-id="5019e-169">「運算式主體成員」  使用「Lambda 運算式」  語法來定義包含單一運算式的方法。</span><span class="sxs-lookup"><span data-stu-id="5019e-169">*Expression-bodied members* use the *lambda expression* syntax to define methods that contain a single expression.</span></span> <span data-ttu-id="5019e-170">在這裡，該運算式會傳回 person 物件的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="5019e-170">Here, that expression returns the full name for the person object.</span></span>

### <a name="cached-evaluated-properties"></a><span data-ttu-id="5019e-171">快取的評估屬性</span><span class="sxs-lookup"><span data-stu-id="5019e-171">Cached evaluated properties</span></span>

<span data-ttu-id="5019e-172">您可以混合計算屬性與儲存體的概念，然後建立「快取的評估屬性」  。</span><span class="sxs-lookup"><span data-stu-id="5019e-172">You can mix the concept of a computed property with storage and create a *cached evaluated property*.</span></span>  <span data-ttu-id="5019e-173">例如，您可以更新 `FullName` 屬性，只在第一次存取時設定字串格式：</span><span class="sxs-lookup"><span data-stu-id="5019e-173">For example, you could update the `FullName` property so that the string formatting only happened the first time it was accessed:</span></span>

[!code-csharp[Caching the value of a computed property](../../samples/snippets/csharp/properties/Person.cs#12)]

<span data-ttu-id="5019e-174">不過，上述程式碼含有 Bug。</span><span class="sxs-lookup"><span data-stu-id="5019e-174">The above code contains a bug though.</span></span> <span data-ttu-id="5019e-175">如果程式碼更新 `FirstName` 或 `LastName` 屬性的值，先前評估的 `fullName` 欄位會無效。</span><span class="sxs-lookup"><span data-stu-id="5019e-175">If code updates the value of either the `FirstName` or `LastName` property, the previously evaluated `fullName` field is invalid.</span></span> <span data-ttu-id="5019e-176">您可以修改 `FirstName` 和 `LastName` 屬性的 `set` 存取子，以便重新計算 `fullName` 欄位：</span><span class="sxs-lookup"><span data-stu-id="5019e-176">You modify the `set` accessors of the `FirstName` and `LastName` property so that the `fullName` field is calculated again:</span></span>

[!code-csharp[Invalidating the cache correctly](../../samples/snippets/csharp/properties/Person.cs#13)]

<span data-ttu-id="5019e-177">這個最終版本只會在必要時評估 `FullName` 屬性。</span><span class="sxs-lookup"><span data-stu-id="5019e-177">This final version evaluates the `FullName` property only when needed.</span></span>
<span data-ttu-id="5019e-178">如果先前計算的版本有效，則會使用該版本。</span><span class="sxs-lookup"><span data-stu-id="5019e-178">If the previously calculated version is valid, it's used.</span></span> <span data-ttu-id="5019e-179">如果另一個狀態變更使得先前計算的版本失效，則會重新計算。</span><span class="sxs-lookup"><span data-stu-id="5019e-179">If another state change invalidates the previously calculated version, it will be recalculated.</span></span> <span data-ttu-id="5019e-180">使用此類別的開發人員不需要知道實作的細節。</span><span class="sxs-lookup"><span data-stu-id="5019e-180">Developers that use this class do not need to know the details of the implementation.</span></span> <span data-ttu-id="5019e-181">這些內部變更不會影響 Person 物件的使用。</span><span class="sxs-lookup"><span data-stu-id="5019e-181">None of these internal changes affect the use of the Person object.</span></span> <span data-ttu-id="5019e-182">這是使用屬性來公開物件之資料成員的主要原因。</span><span class="sxs-lookup"><span data-stu-id="5019e-182">That's the key reason for using Properties to expose data members of an object.</span></span>

### <a name="attaching-attributes-to-auto-implemented-properties"></a><span data-ttu-id="5019e-183">將屬性 (attribute) 附加至自動實作屬性 (property)</span><span class="sxs-lookup"><span data-stu-id="5019e-183">Attaching attributes to auto-implemented properties</span></span>

<span data-ttu-id="5019e-184">從 C# 7.3 開始，可以將欄位屬性 (attribute) 附加至自動實作屬性 (property) 中編譯器產生的支援欄位。</span><span class="sxs-lookup"><span data-stu-id="5019e-184">Beginning with C# 7.3, field attributes can be attached to the compiler generated backing field in auto-implemented properties.</span></span> <span data-ttu-id="5019e-185">例如，考慮要修訂可新增唯一整數 `Id` 屬性的 `Person` 類別。</span><span class="sxs-lookup"><span data-stu-id="5019e-185">For example, consider a revision to the `Person` class that adds a unique integer `Id` property.</span></span>
<span data-ttu-id="5019e-186">您可以使用自動實作屬性撰寫 `Id` 屬性，但是您的設計不會要求保存 `Id` 屬性。</span><span class="sxs-lookup"><span data-stu-id="5019e-186">You write the`Id` property using an auto-implemented property, but your design does not call for persisting the `Id` property.</span></span> <span data-ttu-id="5019e-187"><xref:System.NonSerializedAttribute> 只能附加至欄位，而不是屬性。</span><span class="sxs-lookup"><span data-stu-id="5019e-187">The <xref:System.NonSerializedAttribute> can only be attached to fields, not properties.</span></span> <span data-ttu-id="5019e-188">您可以藉由在屬性 (attribute) 上使用 `field:` 指定名稱，將 <xref:System.NonSerializedAttribute> 附加至 `Id` 屬性 (property) 的支援欄位，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="5019e-188">You can attach the <xref:System.NonSerializedAttribute> to the backing field for the `Id` property by using the `field:` specifier on the attribute, as shown in the following example:</span></span>

[!code-csharp[Attaching attributes to a backing field](../../samples/snippets/csharp/properties/Person.cs#14)]

<span data-ttu-id="5019e-189">此技術適用於任何您附加至自動實作屬性 (property) 支援欄位的屬性 (attribute)。</span><span class="sxs-lookup"><span data-stu-id="5019e-189">This technique works for any attribute you attach to the backing field on the auto-implemented property.</span></span>

### <a name="implementing-inotifypropertychanged"></a><span data-ttu-id="5019e-190">實作 INotifyPropertyChanged</span><span class="sxs-lookup"><span data-stu-id="5019e-190">Implementing INotifyPropertyChanged</span></span>

<span data-ttu-id="5019e-191">您必須在屬性存取子中撰寫程式碼的最後一個案例是為了支援 <xref:System.ComponentModel.INotifyPropertyChanged> 介面，該介面可用來通知資料繫結用戶端已有值變更。</span><span class="sxs-lookup"><span data-stu-id="5019e-191">A final scenario where you need to write code in a property accessor is to support the <xref:System.ComponentModel.INotifyPropertyChanged> interface used to notify data binding clients that a value has changed.</span></span> <span data-ttu-id="5019e-192">當屬性的值變更時，物件會引發 <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged?displayProperty=nameWithType> 事件以指出此變更。</span><span class="sxs-lookup"><span data-stu-id="5019e-192">When the value of a property changes, the object raises the <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged?displayProperty=nameWithType> event to indicate the change.</span></span> <span data-ttu-id="5019e-193">資料繫結程式庫會接著根據該項變更來更新顯示項目。</span><span class="sxs-lookup"><span data-stu-id="5019e-193">The data binding libraries, in turn, update display elements based on that change.</span></span> <span data-ttu-id="5019e-194">下列程式碼示範如何針對此 person 類別的 `FirstName` 屬性實作 `INotifyPropertyChanged`。</span><span class="sxs-lookup"><span data-stu-id="5019e-194">The code below shows how you would implement `INotifyPropertyChanged` for the `FirstName` property of this person class.</span></span>

[!code-csharp[invalidating the cache correctly](../../samples/snippets/csharp/properties/Person.cs#15)]

<span data-ttu-id="5019e-195">`?.` 運算子稱為「null 條件運算子」  。</span><span class="sxs-lookup"><span data-stu-id="5019e-195">The `?.` operator is called the *null conditional operator*.</span></span> <span data-ttu-id="5019e-196">它會檢查是否有 null 參考，再評估運算子的右邊。</span><span class="sxs-lookup"><span data-stu-id="5019e-196">It checks for a null reference before evaluating the right side of the operator.</span></span> <span data-ttu-id="5019e-197">最後結果是，如果沒有 `PropertyChanged` 事件的訂閱者，則不會執行引發事件的程式碼。</span><span class="sxs-lookup"><span data-stu-id="5019e-197">The end result is that if there are no subscribers to the `PropertyChanged` event, the code to raise the event doesn't execute.</span></span> <span data-ttu-id="5019e-198">在此情況下，它會擲回 `NullReferenceException` 而不進行這項檢查。</span><span class="sxs-lookup"><span data-stu-id="5019e-198">It would throw a `NullReferenceException` without this check in that case.</span></span> <span data-ttu-id="5019e-199">如需詳細資訊，請參閱 [`events`](events-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="5019e-199">For more information, see [`events`](events-overview.md).</span></span> <span data-ttu-id="5019e-200">此範例也會使用新的 `nameof` 運算子，從屬性名稱符號轉換成其文字表示。</span><span class="sxs-lookup"><span data-stu-id="5019e-200">This example also uses the new `nameof` operator to convert from the property name symbol to its text representation.</span></span>
<span data-ttu-id="5019e-201">使用 `nameof` 可減少鍵入錯誤屬性名稱時所發生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="5019e-201">Using `nameof` can reduce errors where you have mistyped the name of the property.</span></span>

<span data-ttu-id="5019e-202">同樣地，實作 <xref:System.ComponentModel.INotifyPropertyChanged> 是您可以在存取子中撰寫程式碼來支援所需案例的範例。</span><span class="sxs-lookup"><span data-stu-id="5019e-202">Again, implementing <xref:System.ComponentModel.INotifyPropertyChanged> is an example of a case where you can write code in your accessors to support the scenarios you need.</span></span>

## <a name="summing-up"></a><span data-ttu-id="5019e-203">總結</span><span class="sxs-lookup"><span data-stu-id="5019e-203">Summing up</span></span>

<span data-ttu-id="5019e-204">屬性是類別或物件中的一種智慧型欄位。</span><span class="sxs-lookup"><span data-stu-id="5019e-204">Properties are a form of smart fields in a class or object.</span></span> <span data-ttu-id="5019e-205">從物件外部來看，屬性就像是物件中的欄位。</span><span class="sxs-lookup"><span data-stu-id="5019e-205">From outside the object, they appear like fields in the object.</span></span> <span data-ttu-id="5019e-206">不過，您可以使用完整的 C# 功能選擇區來實作屬性。</span><span class="sxs-lookup"><span data-stu-id="5019e-206">However, properties can be implemented using the full palette of C# functionality.</span></span>
<span data-ttu-id="5019e-207">您可以提供驗證、不同的存取範圍、延遲評估，或是您的案例所需的任何需求。</span><span class="sxs-lookup"><span data-stu-id="5019e-207">You can provide validation, different accessibility, lazy evaluation, or any requirements your scenarios need.</span></span>
