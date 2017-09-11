---
title: "屬性"
description: "屬性"
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 04/03/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 6950d25a-bba1-4744-b7c7-a3cc90438c55
ms.translationtype: Human Translation
ms.sourcegitcommit: f9eab74a3b259037aff30320753191eee95aa974
ms.openlocfilehash: 763a76a8ea0e48fd6935c951ce584efad50dabb9
ms.contentlocale: zh-tw
ms.lasthandoff: 04/25/2017

---

# <a name="properties"></a><span data-ttu-id="634d2-104">屬性</span><span class="sxs-lookup"><span data-stu-id="634d2-104">Properties</span></span>

<span data-ttu-id="634d2-105">屬性是 C# 中的頭等成員。</span><span class="sxs-lookup"><span data-stu-id="634d2-105">Properties are first class citizens in C#.</span></span> <span data-ttu-id="634d2-106">該語言所定義的語法，可讓開發人員撰寫正確表示其設計意圖的程式碼。</span><span class="sxs-lookup"><span data-stu-id="634d2-106">The language defines syntax that enables developers to write code that accurately expresses their design intent.</span></span>

<span data-ttu-id="634d2-107">屬性在存取時的行為與欄位一樣。</span><span class="sxs-lookup"><span data-stu-id="634d2-107">Properties behave like fields when they are accessed.</span></span>
<span data-ttu-id="634d2-108">不過不同於欄位，屬性是透過存取子來實作，這些存取子會定義存取或指派屬性時所執行的陳述式。</span><span class="sxs-lookup"><span data-stu-id="634d2-108">However, unlike fields, properties are implemented with accessors that define the statements executed when a property is accessed or assigned.</span></span>

## <a name="property-syntax"></a><span data-ttu-id="634d2-109">屬性語法</span><span class="sxs-lookup"><span data-stu-id="634d2-109">Property Syntax</span></span>

<span data-ttu-id="634d2-110">屬性的語法是欄位的自然延伸。</span><span class="sxs-lookup"><span data-stu-id="634d2-110">The syntax for properties is a natural extension to fields.</span></span> <span data-ttu-id="634d2-111">欄位可定義儲存位置：</span><span class="sxs-lookup"><span data-stu-id="634d2-111">A field defines a storage location:</span></span>

```csharp
public class Person
{
    public string FirstName;
    // remaining implementation removed from listing
}
```

<span data-ttu-id="634d2-112">屬性定義包含 `get` 和 `set` 存取子的宣告，以擷取和指派該屬性的值：</span><span class="sxs-lookup"><span data-stu-id="634d2-112">A property definition contains declarations for a `get` and `set` accessor that retrieves and assigns the value of that property:</span></span>

```csharp
public class Person
{
    public string FirstName { get; set; }

    // remaining implementation removed from listing
}
```

<span data-ttu-id="634d2-113">以上所示的語法為「Auto 屬性」語法。</span><span class="sxs-lookup"><span data-stu-id="634d2-113">The syntax shown above is the *auto property* syntax.</span></span> <span data-ttu-id="634d2-114">編譯器會為欄位產生儲存位置，以備份此屬性。</span><span class="sxs-lookup"><span data-stu-id="634d2-114">The compiler generates the storage location for the field that backs up the property.</span></span> <span data-ttu-id="634d2-115">編譯器也會實作 `get` 和 `set` 存取子的主體。</span><span class="sxs-lookup"><span data-stu-id="634d2-115">The compiler also implements the body of the `get` and `set` accessors.</span></span>

<span data-ttu-id="634d2-116">有時候，您需要將屬性初始化為其類型的預設值以外的值。</span><span class="sxs-lookup"><span data-stu-id="634d2-116">Sometimes, you need to initialize a property to a value other than the default for its type.</span></span>  <span data-ttu-id="634d2-117">C# 可讓您在屬性的右括弧之後設定一個值，以執行上述作業。</span><span class="sxs-lookup"><span data-stu-id="634d2-117">C# enables that by setting a value after the closing brace for the property.</span></span> <span data-ttu-id="634d2-118">您可能偏好將 `FirstName` 屬性的初始值設為空字串而非 `null`。</span><span class="sxs-lookup"><span data-stu-id="634d2-118">You may prefer the initial value for the `FirstName` property to be the empty string rather than `null`.</span></span> <span data-ttu-id="634d2-119">您可依下列方式來進行上述設定：</span><span class="sxs-lookup"><span data-stu-id="634d2-119">You would specify that as shown below:</span></span>

```csharp
public class Person
{
    public string FirstName { get; set; } = string.Empty;

    // remaining implementation removed from listing
}
```

<span data-ttu-id="634d2-120">如您在本主題稍後所見，這麼做最適合用於唯讀屬性。</span><span class="sxs-lookup"><span data-stu-id="634d2-120">This is most useful for read-only properties, as you'll see later in this topic.</span></span>

<span data-ttu-id="634d2-121">您也可以自行定義儲存體，如下所示：</span><span class="sxs-lookup"><span data-stu-id="634d2-121">You can also define the storage yourself, as shown below:</span></span>

```csharp
public class Person
{
    public string FirstName
    {
        get { return firstName; }
        set { firstName = value; }
    }
    private string firstName;
    // remaining implementation removed from listing
}
```

<span data-ttu-id="634d2-122">當屬性實作為單一運算式時，您可以針對 getter 或 setter 使用「運算式主體成員」：</span><span class="sxs-lookup"><span data-stu-id="634d2-122">When a property implementation is a single expression, you can use *expression bodied members* for the getter or setter:</span></span>

```csharp
public class Person
{
    public string FirstName
    {
        get => firstName;
        set => firstName = value;
    }
    private string firstName;
    // remaining implementation removed from listing
}
```

<span data-ttu-id="634d2-123">本主題會在適用的所有情況下使用這種簡化語法。</span><span class="sxs-lookup"><span data-stu-id="634d2-123">This simplified syntax will be used where applicable throughout this topic.</span></span>

<span data-ttu-id="634d2-124">以上所示的屬性定義為讀寫屬性。</span><span class="sxs-lookup"><span data-stu-id="634d2-124">The property definition shown above is a read-write property.</span></span> <span data-ttu-id="634d2-125">請注意 set 存取子中的關鍵字 `value`。</span><span class="sxs-lookup"><span data-stu-id="634d2-125">Notice the keyword `value` in the set accessor.</span></span> <span data-ttu-id="634d2-126">`set` 存取子一定會有一個名為 `value` 的參數。</span><span class="sxs-lookup"><span data-stu-id="634d2-126">The `set` accessor always has a single parameter named `value`.</span></span> <span data-ttu-id="634d2-127">`get` 存取子必須傳回可轉換成屬性類型 (在此範例中為 `string`) 的值。</span><span class="sxs-lookup"><span data-stu-id="634d2-127">The `get` accessor must return a value that is convertible to the type of the property (`string` in this example).</span></span>
 
<span data-ttu-id="634d2-128">這是此語法的基本概念。</span><span class="sxs-lookup"><span data-stu-id="634d2-128">That's the basics of the syntax.</span></span> <span data-ttu-id="634d2-129">還有許多不同的變化，可支援各種不同的設計慣例。</span><span class="sxs-lookup"><span data-stu-id="634d2-129">There are many different variations that support a variety of different design idioms.</span></span> <span data-ttu-id="634d2-130">讓我們探索並了解各自的語法選項。</span><span class="sxs-lookup"><span data-stu-id="634d2-130">Let's explore those, and learn the syntax options for each.</span></span>

## <a name="scenarios"></a><span data-ttu-id="634d2-131">案例</span><span class="sxs-lookup"><span data-stu-id="634d2-131">Scenarios</span></span>

<span data-ttu-id="634d2-132">上述範例顯示屬性定義的一個最簡單案例，那就是不具驗證的讀/寫屬性。</span><span class="sxs-lookup"><span data-stu-id="634d2-132">The examples above showed one of the simplest cases of property definition: a read-write property with no validation.</span></span> <span data-ttu-id="634d2-133">藉由在 `get` 和 `set` 存取子中撰寫您所需的程式碼，您就可以建立許多不同的案例。</span><span class="sxs-lookup"><span data-stu-id="634d2-133">By writing the code you want in the `get` and `set` accessors, you can create many different scenarios.</span></span>

### <a name="validation"></a><span data-ttu-id="634d2-134">驗證</span><span class="sxs-lookup"><span data-stu-id="634d2-134">Validation</span></span>

<span data-ttu-id="634d2-135">您可以在 `set` 存取子中撰寫程式碼，以確保由屬性所表示的值一定有效。</span><span class="sxs-lookup"><span data-stu-id="634d2-135">You can write code in the `set` accessor to ensure that the values represented by a property are always valid.</span></span> <span data-ttu-id="634d2-136">例如，假設 `Person` 類別的一項規則是名稱不可為空白或空白字元。</span><span class="sxs-lookup"><span data-stu-id="634d2-136">For example, suppose one rule for the `Person` class is that the name cannot be blank, or whitespace.</span></span> <span data-ttu-id="634d2-137">您可以撰寫如下：</span><span class="sxs-lookup"><span data-stu-id="634d2-137">You would write that as follows:</span></span>

```csharp
public class Person
{
    public string FirstName
    {
        get => firstName;
        set
        {
            if (string.IsNullOrWhiteSpace(value))
                throw new ArgumentException("First name must not be blank");
            firstName = value;
        }
    }
    private string firstName;
    // remaining implementation removed from listing
}
```

<span data-ttu-id="634d2-138">上述範例會強制執行第一個名稱不得為空白或空白字元的規則。</span><span class="sxs-lookup"><span data-stu-id="634d2-138">The example above enforces the rule that the first name must not be blank, or whitespace.</span></span> <span data-ttu-id="634d2-139">如果開發人員撰寫</span><span class="sxs-lookup"><span data-stu-id="634d2-139">If a developer writes</span></span>

```csharp
hero.FirstName = "";
```

<span data-ttu-id="634d2-140">該指派會擲回 `ArgumentException`。</span><span class="sxs-lookup"><span data-stu-id="634d2-140">That assignment throws an `ArgumentException`.</span></span> <span data-ttu-id="634d2-141">由於屬性的 set 存取子必須有無效的傳回型別，因此您擲回一個例外狀況來回報 set 存取子中發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="634d2-141">Because a property set accessor must have a void return type, you report errors in the set accessor by throwing an exception.</span></span>

<span data-ttu-id="634d2-142">這是簡單的驗證案例。</span><span class="sxs-lookup"><span data-stu-id="634d2-142">That is a simple case of validation.</span></span> <span data-ttu-id="634d2-143">您可以將同一個語法擴充為案例所需的任何語法。</span><span class="sxs-lookup"><span data-stu-id="634d2-143">You can extend this same syntax to anything needed in your scenario.</span></span> <span data-ttu-id="634d2-144">您可以檢查不同屬性之間的關聯性，或針對任何外部條件進行驗證。</span><span class="sxs-lookup"><span data-stu-id="634d2-144">You can check the relationships between different properties, or validate against any external conditions.</span></span> <span data-ttu-id="634d2-145">任何有效的 C# 陳述式在屬性存取子中都是有效的。</span><span class="sxs-lookup"><span data-stu-id="634d2-145">Any valid C# statements are valid in a property accessor.</span></span>

### <a name="read-only"></a><span data-ttu-id="634d2-146">唯讀</span><span class="sxs-lookup"><span data-stu-id="634d2-146">Read-only</span></span>

<span data-ttu-id="634d2-147">到目前為止，您所看到的所有屬性定義都是具有 public 存取子的讀取/寫入屬性。</span><span class="sxs-lookup"><span data-stu-id="634d2-147">Up to this point, all the property definitions you have seen are read/write properties with public accessors.</span></span> <span data-ttu-id="634d2-148">這不是屬性唯一有效的存取範圍。</span><span class="sxs-lookup"><span data-stu-id="634d2-148">That's not the only valid accessibility for properties.</span></span>
<span data-ttu-id="634d2-149">您可以建立唯讀屬性，或是為 set 和 get 存取子提供不同的存取範圍。</span><span class="sxs-lookup"><span data-stu-id="634d2-149">You can create read-only properties, or give different accessibility to the set and get accessors.</span></span> <span data-ttu-id="634d2-150">假設您的 `Person` 類別只能允許從該類別中的其他方法變更 `FirstName` 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="634d2-150">Suppose that your `Person` class should only enable changing the value of the `FirstName` property from other methods in that class.</span></span> <span data-ttu-id="634d2-151">您可以為 set 存取子提供 `private` 存取範圍，而不是 `public`：</span><span class="sxs-lookup"><span data-stu-id="634d2-151">You could give the set accessor `private` accessibility instead of `public`:</span></span>

```csharp
public class Person
{
    public string FirstName { get; private set; }

    // remaining implementation removed from listing
}
```

<span data-ttu-id="634d2-152">現在，`FirstName` 屬性可從任何程式碼存取，但只能從 `Person` 類別中的其他程式碼指派。</span><span class="sxs-lookup"><span data-stu-id="634d2-152">Now, the `FirstName` property can be accessed from any code, but it can only be assigned from other code in the `Person` class.</span></span>

<span data-ttu-id="634d2-153">您可以將任何嚴格的存取修飾詞新增至 set 或 get 存取子。</span><span class="sxs-lookup"><span data-stu-id="634d2-153">You can add any restrictive access modifier to either the set or get accessors.</span></span> <span data-ttu-id="634d2-154">您放在個別存取子上的任何存取修飾詞，必須比屬性定義上的存取修飾詞具有更多限制。</span><span class="sxs-lookup"><span data-stu-id="634d2-154">Any access modifier you place on the individual accessor must be more limited than the access modifier on the property definition.</span></span> <span data-ttu-id="634d2-155">由於 `FirstName` 屬性為 `public`，但 set 存取子為 `private`，因此上述範例合法。</span><span class="sxs-lookup"><span data-stu-id="634d2-155">The above is legal because the `FirstName` property is `public`, but the set accessor is `private`.</span></span> <span data-ttu-id="634d2-156">您無法使用 `public` 存取子宣告 `private` 屬性。</span><span class="sxs-lookup"><span data-stu-id="634d2-156">You could not declare a `private` property with a `public` accessor.</span></span> <span data-ttu-id="634d2-157">屬性宣告也可以宣告為 `protected`、`internal`、`protected internal`，甚至是 `private`。</span><span class="sxs-lookup"><span data-stu-id="634d2-157">Property declarations can also be declared `protected`, `internal`, `protected internal` or even `private`.</span></span>   

<span data-ttu-id="634d2-158">您也可以將更嚴格的修飾詞放在 `get` 存取子上。</span><span class="sxs-lookup"><span data-stu-id="634d2-158">It is also legal to place the more restrictive modifier on the `get` accessor.</span></span> <span data-ttu-id="634d2-159">例如，您可能會有 `public` 屬性，但將 `get` 存取子限制為 `private`。</span><span class="sxs-lookup"><span data-stu-id="634d2-159">For example, you could have a `public` property, but restrict the `get` accessor to `private`.</span></span> <span data-ttu-id="634d2-160">這種情況在實務上很罕見。</span><span class="sxs-lookup"><span data-stu-id="634d2-160">That scenario is rarely done in practice.</span></span>

<span data-ttu-id="634d2-161">您也可以限制屬性的修改，只在建構函式或屬性的初始設定式中加以設定。</span><span class="sxs-lookup"><span data-stu-id="634d2-161">You can also restrict modifications to a property so that it can only be set in a constructor or a property initializer.</span></span> <span data-ttu-id="634d2-162">您可以修改 `Person` 類別，如下所示：</span><span class="sxs-lookup"><span data-stu-id="634d2-162">You can modify the `Person` class so as follows:</span></span>

```csharp
public class Person
{
    public Person(string firstName)
    {
        this.FirstName = firstName;
    }

    public string FirstName { get; }

    // remaining implementation removed from listing
}
```

<span data-ttu-id="634d2-163">這項功能最常用於初始化會公開為唯讀屬性的集合：</span><span class="sxs-lookup"><span data-stu-id="634d2-163">This feature is most commonly used for initializing collections that are exposed as read-only properties:</span></span>

```csharp
public class Measurements
{
    public ICollection<DataPoint> points { get; } = new List<DataPoint>();
}
```

### <a name="computed-properties"></a><span data-ttu-id="634d2-164">計算的屬性</span><span class="sxs-lookup"><span data-stu-id="634d2-164">Computed Properties</span></span>

<span data-ttu-id="634d2-165">屬性不需要直接傳回成員欄位的值。</span><span class="sxs-lookup"><span data-stu-id="634d2-165">A property does not need to simply return the value of a member field.</span></span> <span data-ttu-id="634d2-166">您可以建立傳回計算值的屬性。</span><span class="sxs-lookup"><span data-stu-id="634d2-166">You can create properties that return a computed value.</span></span> <span data-ttu-id="634d2-167">讓我們展開 `Person` 物件，以傳回串連名字和姓氏計算得到的完整名稱：</span><span class="sxs-lookup"><span data-stu-id="634d2-167">Let's expand the `Person` object to return the full name, computed by concatenating the first and last names:</span></span>

```csharp
public class Person
{
    public string FirstName { get; set; }

    public string LastName { get; set; }

    public string FullName { get { return $"{FirstName} {LastName}"; } }
}
```

<span data-ttu-id="634d2-168">上述範例使用「字串插值」語法，來建立完整名稱的格式化字串。</span><span class="sxs-lookup"><span data-stu-id="634d2-168">The example above uses the *String Interpolation* syntax to create the formatted string for the full name.</span></span>

<span data-ttu-id="634d2-169">您也可以使用「運算式主體成員」，以提供更簡潔的方法來建立計算的 `FullName` 屬性：</span><span class="sxs-lookup"><span data-stu-id="634d2-169">You can also use *Expression-bodied Members*, which provides a more succinct way to create the computed `FullName` property:</span></span>

```csharp
public class Person
{
    public string FirstName { get; set; }

    public string LastName { get; set; }

    public string FullName =>  $"{FirstName} {LastName}";
}
```
 
<span data-ttu-id="634d2-170">「運算式主體成員」使用「Lambda 運算式」語法來定義包含單一運算式的方法。</span><span class="sxs-lookup"><span data-stu-id="634d2-170">*Expression-bodied Members* use the *lambda expression* syntax to define a method that contain a single expression.</span></span> <span data-ttu-id="634d2-171">在這裡，該運算式會傳回 person 物件的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="634d2-171">Here, that expression returns the full name for the person object.</span></span>

### <a name="lazy-evaluated-properties"></a><span data-ttu-id="634d2-172">延遲評估的屬性</span><span class="sxs-lookup"><span data-stu-id="634d2-172">Lazy Evaluated Properties</span></span>

<span data-ttu-id="634d2-173">您可以混合計算的屬性與儲存體的概念，然後建立「延遲評估的屬性」。</span><span class="sxs-lookup"><span data-stu-id="634d2-173">You can mix the concept of a computed property with storage and create a *lazy evaluated property*.</span></span>  <span data-ttu-id="634d2-174">例如，您可以更新 `FullName` 屬性，只在第一次存取時設定字串格式：</span><span class="sxs-lookup"><span data-stu-id="634d2-174">For example, you could update the `FullName` property so that the string formatting only happened the first time it was accessed:</span></span>

```csharp
public class Person
{
    public string FirstName { get; set; }

    public string LastName { get; set; }

    private string fullName;
    public string FullName
    {
        get
        {
            if (fullName == null)
                fullName = $"{FirstName} {LastName}";
            return fullName;
        }
    }
}
```

<span data-ttu-id="634d2-175">不過，上述程式碼含有 Bug。</span><span class="sxs-lookup"><span data-stu-id="634d2-175">The above code contains a bug though.</span></span> <span data-ttu-id="634d2-176">如果程式碼更新 `FirstName` 或 `LastName` 屬性的值，先前評估的 `fullName` 欄位會無效。</span><span class="sxs-lookup"><span data-stu-id="634d2-176">If code updates the value of either the `FirstName` or `LastName` property, the previously evaluated `fullName` field is invalid.</span></span> <span data-ttu-id="634d2-177">您必須更新 `FirstName` 和 `LastName` 屬性的 `set` 存取子，以便重新計算 `fullName`欄位：</span><span class="sxs-lookup"><span data-stu-id="634d2-177">You need to update the `set` accessors of the `FirstName` and `LastName` property so that the `fullName` field is calculated again:</span></span>

```csharp
public class Person
{
    private string firstName;
    public string FirstName
    {
        get => firstName;
        set
        {
            firstName = value;
            fullName = null;
        }
    }

    private string lastName;
    public string LastName
    {
        get => lastName;
        set
        {
            lastName = value;
            fullName = null;
        }
    }

    private string fullName;
    public string FullName
    {
        get
        {
            if (fullName == null)
                fullName = $"{FirstName} {LastName}";
            return fullName;
        }
    }
}
```

<span data-ttu-id="634d2-178">這個最終版本只會在必要時評估 `FullName` 屬性。</span><span class="sxs-lookup"><span data-stu-id="634d2-178">This final version evaluates the `FullName` property only when needed.</span></span>
<span data-ttu-id="634d2-179">如果先前計算的版本有效，則會使用該版本。</span><span class="sxs-lookup"><span data-stu-id="634d2-179">If the previously calculated version is valid, it's used.</span></span> <span data-ttu-id="634d2-180">如果另一個狀態變更使得先前計算的版本失效，則會重新計算。</span><span class="sxs-lookup"><span data-stu-id="634d2-180">If another state change invalidates the previously calculated version, it will be recalculated.</span></span> <span data-ttu-id="634d2-181">使用此類別的開發人員不需要知道實作的細節。</span><span class="sxs-lookup"><span data-stu-id="634d2-181">Developers that use this class do not need to know the details of the implementation.</span></span> <span data-ttu-id="634d2-182">這些內部變更不會影響 Person 物件的使用。</span><span class="sxs-lookup"><span data-stu-id="634d2-182">None of these internal changes affect the use of the Person object.</span></span> <span data-ttu-id="634d2-183">這是使用屬性來公開物件之資料成員的主要原因。</span><span class="sxs-lookup"><span data-stu-id="634d2-183">That's the key reason for using Properties to expose data members of an object.</span></span>
 
### <a name="inotifypropertychanged"></a><span data-ttu-id="634d2-184">INotifyPropertyChanged</span><span class="sxs-lookup"><span data-stu-id="634d2-184">INotifyPropertyChanged</span></span>

<span data-ttu-id="634d2-185">您必須在屬性存取子中撰寫程式碼的最後一個案例是為了支援 `INotifyPropertyChanged` 介面，該介面可用來通知資料繫結用戶端已有值變更。</span><span class="sxs-lookup"><span data-stu-id="634d2-185">A final scenario where you need to write code in a property accessor is to support the `INotifyPropertyChanged` interface used to notify data binding clients that a value has changed.</span></span> <span data-ttu-id="634d2-186">當屬性的值變更時，物件會引發 `PropertyChanged` 事件以指出此變更。</span><span class="sxs-lookup"><span data-stu-id="634d2-186">When the value of a property changes, the object raises the `PropertyChanged` event to indicate the change.</span></span> <span data-ttu-id="634d2-187">資料繫結程式庫會接著根據該項變更來更新顯示項目。</span><span class="sxs-lookup"><span data-stu-id="634d2-187">The data binding libraries, in turn, update display elements based on that change.</span></span> <span data-ttu-id="634d2-188">下列程式碼示範如何針對此 person 類別的 `FirstName` 屬性實作 `INotifyPropertyChanged`。</span><span class="sxs-lookup"><span data-stu-id="634d2-188">The code below shows how you would implement `INotifyPropertyChanged` for the `FirstName` property of this person class.</span></span>

```csharp
public class Person : INotifyPropertyChanged
{
    public string FirstName
    {
        get => firstName;
        set
        {
            if (string.IsNullOrWhiteSpace(value))
                throw new ArgumentException("First name must not be blank");
            if (value != firstName)
            {
                PropertyChanged?.Invoke(this, 
                    new PropertyChangedEventArgs(nameof(FirstName)));
            }
            firstName = value;
        }
    }
    private string firstName;

    public event PropertyChangedEventHandler PropertyChanged;
    // remaining implementation removed from listing
}
```

<span data-ttu-id="634d2-189">`?.` 運算子稱為「null 條件運算子」。</span><span class="sxs-lookup"><span data-stu-id="634d2-189">The `?.` operator is called the *null conditional operator*.</span></span> <span data-ttu-id="634d2-190">它會檢查是否有 null 參考，再評估運算子的右邊。</span><span class="sxs-lookup"><span data-stu-id="634d2-190">It checks for a null reference before evaluating the right side of the operator.</span></span> <span data-ttu-id="634d2-191">最後結果是，如果沒有 `PropertyChanged` 事件的訂閱者，則不會執行引發事件的程式碼。</span><span class="sxs-lookup"><span data-stu-id="634d2-191">The end result is that if there are no subscribers to the `PropertyChanged` event, the code to raise the event doesn't execute.</span></span> <span data-ttu-id="634d2-192">在此情況下，它會擲回 `NullReferenceException` 而不進行這項檢查。</span><span class="sxs-lookup"><span data-stu-id="634d2-192">It would throw a `NullReferenceException` without this check in that case.</span></span> <span data-ttu-id="634d2-193">如需詳細資訊，請參閱 [`events`](delegates-events.md) 上的頁面。</span><span class="sxs-lookup"><span data-stu-id="634d2-193">See the page on [`events`](delegates-events.md) for more details.</span></span> <span data-ttu-id="634d2-194">此範例也會使用新的 `nameof` 運算子，從屬性名稱符號轉換成其文字表示。</span><span class="sxs-lookup"><span data-stu-id="634d2-194">This example also uses the new `nameof` operator to convert from the property name symbol to its text representation.</span></span>
<span data-ttu-id="634d2-195">使用 `nameof` 可減少鍵入錯誤屬性名稱時所發生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="634d2-195">Using `nameof` can reduce errors where you have mistyped the name of the property.</span></span>

<span data-ttu-id="634d2-196">同樣地，這是您可以在存取子中撰寫程式碼來支援所需案例的範例。</span><span class="sxs-lookup"><span data-stu-id="634d2-196">Again, this is an example of a case where you can write code in your accessors to support the scenarios you need.</span></span>

## <a name="summing-up"></a><span data-ttu-id="634d2-197">總結</span><span class="sxs-lookup"><span data-stu-id="634d2-197">Summing up</span></span>

<span data-ttu-id="634d2-198">屬性是類別或物件中的一種智慧型欄位。</span><span class="sxs-lookup"><span data-stu-id="634d2-198">Properties are a form of smart fields in a class or object.</span></span> <span data-ttu-id="634d2-199">從物件外部來看，屬性就像是物件中的欄位。</span><span class="sxs-lookup"><span data-stu-id="634d2-199">From outside the object, they appear like fields in the object.</span></span> <span data-ttu-id="634d2-200">不過，您可以使用完整的 C# 功能選擇區來實作屬性。</span><span class="sxs-lookup"><span data-stu-id="634d2-200">However, properties can be implemented using the full palette of C# functionality.</span></span>
<span data-ttu-id="634d2-201">您可以提供驗證、不同的存取範圍、延遲評估，或是您的案例所需的任何需求。</span><span class="sxs-lookup"><span data-stu-id="634d2-201">You can provide validation, different accessibility, lazy evaluation, or any requirements your scenarios need.</span></span>

