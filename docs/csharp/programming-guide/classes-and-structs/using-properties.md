---
title: 使用屬性 - C# 程式設計手冊
ms.date: 07/20/2015
helpviewer_keywords:
- set accessor [C#]
- get accessor [C#]
- properties [C#], about properties
ms.assetid: f7f67b05-0983-4cdb-96af-1855d24c967c
ms.openlocfilehash: d873f626b660bb6bd94710add4543e21e11823d6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "77452015"
---
# <a name="using-properties-c-programming-guide"></a><span data-ttu-id="4b48e-102">使用屬性 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="4b48e-102">Using Properties (C# Programming Guide)</span></span>

<span data-ttu-id="4b48e-103">屬性會合併欄位和方法的各個層面。</span><span class="sxs-lookup"><span data-stu-id="4b48e-103">Properties combine aspects of both fields and methods.</span></span> <span data-ttu-id="4b48e-104">對物件的使用者而言，屬性會呈現為欄位，而存取屬性需要相同的語法。</span><span class="sxs-lookup"><span data-stu-id="4b48e-104">To the user of an object, a property appears to be a field, accessing the property requires the same syntax.</span></span> <span data-ttu-id="4b48e-105">對於類別的實作器而言，屬性是一或兩個程式碼區塊，代表 [get](../../language-reference/keywords/get.md) 存取子和 (或) [set](../../language-reference/keywords/set.md) 存取子。</span><span class="sxs-lookup"><span data-stu-id="4b48e-105">To the implementer of a class, a property is one or two code blocks, representing a [get](../../language-reference/keywords/get.md) accessor and/or a [set](../../language-reference/keywords/set.md) accessor.</span></span> <span data-ttu-id="4b48e-106">讀取屬性時，會執行 `get` 存取子的程式碼區塊；指派屬性的新值時，會執行 `set` 存取子的程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="4b48e-106">The code block for the `get` accessor is executed when the property is read; the code block for the `set` accessor is executed when the property is assigned a new value.</span></span> <span data-ttu-id="4b48e-107">沒有 `set` 存取子的屬性會視為唯讀。</span><span class="sxs-lookup"><span data-stu-id="4b48e-107">A property without a `set` accessor is considered read-only.</span></span> <span data-ttu-id="4b48e-108">沒有 `get` 存取子的屬性則視為唯寫。</span><span class="sxs-lookup"><span data-stu-id="4b48e-108">A property without a `get` accessor is considered write-only.</span></span> <span data-ttu-id="4b48e-109">具有這兩個存取子的屬性是讀寫。</span><span class="sxs-lookup"><span data-stu-id="4b48e-109">A property that has both accessors is read-write.</span></span>

<span data-ttu-id="4b48e-110">與欄位不同，屬性不會分類為變數。</span><span class="sxs-lookup"><span data-stu-id="4b48e-110">Unlike fields, properties are not classified as variables.</span></span> <span data-ttu-id="4b48e-111">因此，您無法將屬性傳遞為 [ref](../../language-reference/keywords/ref.md) 或 [out](../../language-reference/keywords/out-parameter-modifier.md) 參數。</span><span class="sxs-lookup"><span data-stu-id="4b48e-111">Therefore, you cannot pass a property as a [ref](../../language-reference/keywords/ref.md) or [out](../../language-reference/keywords/out-parameter-modifier.md) parameter.</span></span>

<span data-ttu-id="4b48e-112">屬性有許多用途：它們可以先驗證資料，再允許變更；它們會以透明方式公開類別上的資料，而該資料實際是從某個其他來源 (例如資料庫) 所擷取；資料變更時 (例如，引發事件，或變更其他欄位的值)，它們可以採取動作。</span><span class="sxs-lookup"><span data-stu-id="4b48e-112">Properties have many uses: they can validate data before allowing a change; they can transparently expose data on a class where that data is actually retrieved from some other source, such as a database; they can take an action when data is changed, such as raising an event, or changing the value of other fields.</span></span>

<span data-ttu-id="4b48e-113">在類別區塊中宣告屬性的方式是指定欄位存取層級，其後依序接著屬性類型、屬性名稱，以及宣告 `get` 存取子和 (或) `set` 存取子的程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="4b48e-113">Properties are declared in the class block by specifying the access level of the field, followed by the type of the property, followed by the name of the property, and followed by a code block that declares a `get`-accessor and/or a `set` accessor.</span></span> <span data-ttu-id="4b48e-114">例如：</span><span class="sxs-lookup"><span data-stu-id="4b48e-114">For example:</span></span>

[!code-csharp[csProgGuideProperties#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#7)]

<span data-ttu-id="4b48e-115">在此範例中，將 `Month` 宣告為屬性，因此，`set` 存取子可以確定設定的 `Month` 值介於 1 與 12 之間。</span><span class="sxs-lookup"><span data-stu-id="4b48e-115">In this example, `Month` is declared as a property so that the `set` accessor can make sure that the `Month` value is set between 1 and 12.</span></span> <span data-ttu-id="4b48e-116">`Month` 屬性使用私用欄位來追蹤實際值。</span><span class="sxs-lookup"><span data-stu-id="4b48e-116">The `Month` property uses a private field to track the actual value.</span></span> <span data-ttu-id="4b48e-117">屬性資料的實際位置通常稱為屬性的「備份存放區」。</span><span class="sxs-lookup"><span data-stu-id="4b48e-117">The real location of a property's data is often referred to as the property's "backing store."</span></span> <span data-ttu-id="4b48e-118">屬性經常使用私用欄位作為備份存放區。</span><span class="sxs-lookup"><span data-stu-id="4b48e-118">It is common for properties to use private fields as a backing store.</span></span> <span data-ttu-id="4b48e-119">此欄位標示為私用，以確認只有呼叫屬性才能進行變更。</span><span class="sxs-lookup"><span data-stu-id="4b48e-119">The field is marked private in order to make sure that it can only be changed by calling the property.</span></span> <span data-ttu-id="4b48e-120">如需公用和私用存取限制的詳細資訊，請參閱[存取修飾詞](./access-modifiers.md)。</span><span class="sxs-lookup"><span data-stu-id="4b48e-120">For more information about public and private access restrictions, see [Access Modifiers](./access-modifiers.md).</span></span>

<span data-ttu-id="4b48e-121">自動實作屬性提供簡單屬性宣告的簡化語法。</span><span class="sxs-lookup"><span data-stu-id="4b48e-121">Auto-implemented properties provide simplified syntax for simple property declarations.</span></span> <span data-ttu-id="4b48e-122">如需詳細資訊，請參閱[自動實作的屬性](auto-implemented-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="4b48e-122">For more information, see [Auto-Implemented Properties](auto-implemented-properties.md).</span></span>

## <a name="the-get-accessor"></a><span data-ttu-id="4b48e-123">get 存取子</span><span class="sxs-lookup"><span data-stu-id="4b48e-123">The get Accessor</span></span>

<span data-ttu-id="4b48e-124">`get` 存取子的主體與方法的主體類似。</span><span class="sxs-lookup"><span data-stu-id="4b48e-124">The body of the `get` accessor resembles that of a method.</span></span> <span data-ttu-id="4b48e-125">它必須傳回屬性類型的值。</span><span class="sxs-lookup"><span data-stu-id="4b48e-125">It must return a value of the property type.</span></span> <span data-ttu-id="4b48e-126">執行 `get` 存取子相當於讀取欄位的值。</span><span class="sxs-lookup"><span data-stu-id="4b48e-126">The execution of the `get` accessor is equivalent to reading the value of the field.</span></span> <span data-ttu-id="4b48e-127">例如，當您要從 `get` 存取子傳回私用變數並啟用最佳化時，則編譯器會內嵌 `get` 存取子方法呼叫，因此沒有任何方法呼叫額外負荷。</span><span class="sxs-lookup"><span data-stu-id="4b48e-127">For example, when you are returning the private variable from the `get` accessor and optimizations are enabled, the call to the `get` accessor method is inlined by the compiler so there is no method-call overhead.</span></span> <span data-ttu-id="4b48e-128">不過，因為編譯器在編譯時間不知道執行階段實際呼叫的方法，所以無法內嵌虛擬 `get` 存取子方法。</span><span class="sxs-lookup"><span data-stu-id="4b48e-128">However, a virtual `get` accessor method cannot be inlined because the compiler does not know at compile-time which method may actually be called at run time.</span></span> <span data-ttu-id="4b48e-129">下列 `get` 存取子會傳回私用欄位 `_name` 的值：</span><span class="sxs-lookup"><span data-stu-id="4b48e-129">The following is a `get` accessor that returns the value of a private field `_name`:</span></span>

[!code-csharp[csProgGuideProperties#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#8)]

<span data-ttu-id="4b48e-130">當您參考指派目標以外的屬性時，會叫用 `get` 存取子來讀取屬性的值。</span><span class="sxs-lookup"><span data-stu-id="4b48e-130">When you reference the property, except as the target of an assignment, the `get` accessor is invoked to read the value of the property.</span></span> <span data-ttu-id="4b48e-131">例如：</span><span class="sxs-lookup"><span data-stu-id="4b48e-131">For example:</span></span>

[!code-csharp[csProgGuideProperties#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#9)]

<span data-ttu-id="4b48e-132">`get` 存取子必須結束於 [return](../../language-reference/keywords/return.md) 或 [throw](../../language-reference/keywords/throw.md) 陳述式，而且控制無法離開存取子主體。</span><span class="sxs-lookup"><span data-stu-id="4b48e-132">The `get` accessor must end in a [return](../../language-reference/keywords/return.md) or [throw](../../language-reference/keywords/throw.md) statement, and control cannot flow off the accessor body.</span></span>

<span data-ttu-id="4b48e-133">這是使用 `get` 存取子變更物件狀態的不良程式設計樣式。</span><span class="sxs-lookup"><span data-stu-id="4b48e-133">It is a bad programming style to change the state of the object by using the `get` accessor.</span></span> <span data-ttu-id="4b48e-134">例如，下列存取子會產生每次存取 `_number` 欄位時都變更物件狀態的副作用。</span><span class="sxs-lookup"><span data-stu-id="4b48e-134">For example, the following accessor produces the side effect of changing the state of the object every time that the `_number` field is accessed.</span></span>

[!code-csharp[csProgGuideProperties#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#10)]

<span data-ttu-id="4b48e-135">`get` 存取子可用來傳回欄位值或計算它，並傳回它。</span><span class="sxs-lookup"><span data-stu-id="4b48e-135">The `get` accessor can be used to return the field value or to compute it and return it.</span></span> <span data-ttu-id="4b48e-136">例如：</span><span class="sxs-lookup"><span data-stu-id="4b48e-136">For example:</span></span>

[!code-csharp[csProgGuideProperties#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#11)]

<span data-ttu-id="4b48e-137">在前面的程式碼片段中，如果不為`Name`屬性賦值，它將傳回值`NA`。</span><span class="sxs-lookup"><span data-stu-id="4b48e-137">In the previous code segment, if you do not assign a value to the `Name` property, it will return the value `NA`.</span></span>

## <a name="the-set-accessor"></a><span data-ttu-id="4b48e-138">set 存取子</span><span class="sxs-lookup"><span data-stu-id="4b48e-138">The set Accessor</span></span>

<span data-ttu-id="4b48e-139">`set` 存取子與傳回型別為 [void](../../language-reference/builtin-types/void.md) 的方法類似。</span><span class="sxs-lookup"><span data-stu-id="4b48e-139">The `set` accessor resembles a method whose return type is [void](../../language-reference/builtin-types/void.md).</span></span> <span data-ttu-id="4b48e-140">它使用稱為 `value` 的隱含參數，其類型為屬性的類型。</span><span class="sxs-lookup"><span data-stu-id="4b48e-140">It uses an implicit parameter called `value`, whose type is the type of the property.</span></span> <span data-ttu-id="4b48e-141">在下列範例中，將 `set` 存取子新增至 `Name` 屬性：</span><span class="sxs-lookup"><span data-stu-id="4b48e-141">In the following example, a `set` accessor is added to the `Name` property:</span></span>

[!code-csharp[csProgGuideProperties#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#12)]

<span data-ttu-id="4b48e-142">當您指派屬性的值時，會使用提供新值的引數來叫用 `set` 存取子。</span><span class="sxs-lookup"><span data-stu-id="4b48e-142">When you assign a value to the property, the `set` accessor is invoked by using an argument that provides the new value.</span></span> <span data-ttu-id="4b48e-143">例如：</span><span class="sxs-lookup"><span data-stu-id="4b48e-143">For example:</span></span>

[!code-csharp[csProgGuideProperties#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#13)]

<span data-ttu-id="4b48e-144">在 `set` 存取子中使用區域變數宣告的隱含參數名稱 `value` 是錯誤的。</span><span class="sxs-lookup"><span data-stu-id="4b48e-144">It is an error to use the implicit parameter name, `value`, for a local variable declaration in a `set` accessor.</span></span>

## <a name="remarks"></a><span data-ttu-id="4b48e-145">備註</span><span class="sxs-lookup"><span data-stu-id="4b48e-145">Remarks</span></span>

<span data-ttu-id="4b48e-146">屬性可標記為 `public`、`private`、`protected`、`internal`、`protected internal` 或 `private protected`。</span><span class="sxs-lookup"><span data-stu-id="4b48e-146">Properties can be marked as `public`, `private`, `protected`, `internal`, `protected internal` or `private protected`.</span></span> <span data-ttu-id="4b48e-147">這些存取修飾詞定義類別使用者如何存取屬性。</span><span class="sxs-lookup"><span data-stu-id="4b48e-147">These access modifiers define how users of the class can access the property.</span></span> <span data-ttu-id="4b48e-148">相同屬性的 `get` 和 `set` 存取子可能會有不同的存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="4b48e-148">The `get` and `set` accessors for the same property may have different access modifiers.</span></span> <span data-ttu-id="4b48e-149">例如，`get` 可能是 `public` 以允許從類型外部進行唯讀存取，而 `set` 可能是 `private` 或 `protected`。</span><span class="sxs-lookup"><span data-stu-id="4b48e-149">For example, the `get` may be `public` to allow read-only access from outside the type, and the `set` may be `private` or `protected`.</span></span> <span data-ttu-id="4b48e-150">如需詳細資訊，請參閱[存取修飾詞](./access-modifiers.md)。</span><span class="sxs-lookup"><span data-stu-id="4b48e-150">For more information, see [Access Modifiers](./access-modifiers.md).</span></span>

<span data-ttu-id="4b48e-151">屬性可以使用 `static` 關鍵字宣告為靜態屬性。</span><span class="sxs-lookup"><span data-stu-id="4b48e-151">A property may be declared as a static property by using the `static` keyword.</span></span> <span data-ttu-id="4b48e-152">這可隨時向呼叫者提供屬性，即使沒有任何類別執行個體也是一樣。</span><span class="sxs-lookup"><span data-stu-id="4b48e-152">This makes the property available to callers at any time, even if no instance of the class exists.</span></span> <span data-ttu-id="4b48e-153">有關詳細資訊，請參閱[靜態類和靜態類成員](./static-classes-and-static-class-members.md)。</span><span class="sxs-lookup"><span data-stu-id="4b48e-153">For more information, see [Static Classes and Static Class Members](./static-classes-and-static-class-members.md).</span></span>

<span data-ttu-id="4b48e-154">屬性可以使用 [virtual](../../language-reference/keywords/virtual.md) 關鍵字標示為虛擬屬性。</span><span class="sxs-lookup"><span data-stu-id="4b48e-154">A property may be marked as a virtual property by using the [virtual](../../language-reference/keywords/virtual.md) keyword.</span></span> <span data-ttu-id="4b48e-155">這可讓衍生類別使用 [override](../../language-reference/keywords/override.md) 關鍵字覆寫屬性行為。</span><span class="sxs-lookup"><span data-stu-id="4b48e-155">This enables derived classes to override the property behavior by using the [override](../../language-reference/keywords/override.md) keyword.</span></span> <span data-ttu-id="4b48e-156">如需這些選項的詳細資訊，請參閱[繼承](inheritance.md)。</span><span class="sxs-lookup"><span data-stu-id="4b48e-156">For more information about these options, see [Inheritance](inheritance.md).</span></span>

<span data-ttu-id="4b48e-157">覆寫虛擬屬性的屬性也可為 [sealed](../../language-reference/keywords/sealed.md)，指定它對衍生類別而言不再是虛擬。</span><span class="sxs-lookup"><span data-stu-id="4b48e-157">A property overriding a virtual property can also be [sealed](../../language-reference/keywords/sealed.md), specifying that for derived classes it is no longer virtual.</span></span> <span data-ttu-id="4b48e-158">最後，屬性可以宣告為 [abstract](../../language-reference/keywords/abstract.md)。</span><span class="sxs-lookup"><span data-stu-id="4b48e-158">Lastly, a property can be declared [abstract](../../language-reference/keywords/abstract.md).</span></span> <span data-ttu-id="4b48e-159">這表示類別中沒有任何實作，而且衍生類別必須撰寫自己的實作。</span><span class="sxs-lookup"><span data-stu-id="4b48e-159">This means that there is no implementation in the class, and derived classes must write their own implementation.</span></span> <span data-ttu-id="4b48e-160">如需這些選項的詳細資訊，請參閱[抽象和密封類別以及類別成員](abstract-and-sealed-classes-and-class-members.md)。</span><span class="sxs-lookup"><span data-stu-id="4b48e-160">For more information about these options, see [Abstract and Sealed Classes and Class Members](abstract-and-sealed-classes-and-class-members.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="4b48e-161">在 [static](../../language-reference/keywords/static.md) 屬性的存取子上使用 [virtual](../../language-reference/keywords/virtual.md)、[abstract](../../language-reference/keywords/abstract.md) 或 [override](../../language-reference/keywords/override.md) 修飾詞是錯誤的。</span><span class="sxs-lookup"><span data-stu-id="4b48e-161">It is an error to use a [virtual](../../language-reference/keywords/virtual.md), [abstract](../../language-reference/keywords/abstract.md), or [override](../../language-reference/keywords/override.md) modifier on an accessor of a [static](../../language-reference/keywords/static.md) property.</span></span>

## <a name="example"></a><span data-ttu-id="4b48e-162">範例</span><span class="sxs-lookup"><span data-stu-id="4b48e-162">Example</span></span>

<span data-ttu-id="4b48e-163">此範例示範執行個體、靜態和唯讀屬性。</span><span class="sxs-lookup"><span data-stu-id="4b48e-163">This example demonstrates instance, static, and read-only properties.</span></span> <span data-ttu-id="4b48e-164">它會從鍵盤接受員工姓名、將 `NumberOfEmployees` 增加 1，並顯示員工姓名和編號。</span><span class="sxs-lookup"><span data-stu-id="4b48e-164">It accepts the name of the employee from the keyboard, increments `NumberOfEmployees` by 1, and displays the Employee name and number.</span></span>

[!code-csharp[csProgGuideProperties#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#2)]

## <a name="example"></a><span data-ttu-id="4b48e-165">範例</span><span class="sxs-lookup"><span data-stu-id="4b48e-165">Example</span></span>

<span data-ttu-id="4b48e-166">此示例演示如何訪問基類中由派生類中具有相同名稱的另一個屬性隱藏的屬性：</span><span class="sxs-lookup"><span data-stu-id="4b48e-166">This example demonstrates how to access a property in a base class that is hidden by another property that has the same name in a derived class:</span></span>

[!code-csharp[csProgGuideProperties#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#3)]

<span data-ttu-id="4b48e-167">上述範例中的重點如下：</span><span class="sxs-lookup"><span data-stu-id="4b48e-167">The following are important points in the previous example:</span></span>

- <span data-ttu-id="4b48e-168">衍生類別中的 `Name` 屬性會隱藏基底類別中的 `Name` 屬性。</span><span class="sxs-lookup"><span data-stu-id="4b48e-168">The property `Name` in the derived class hides the property `Name` in the base class.</span></span> <span data-ttu-id="4b48e-169">在這類情況下，`new` 修飾詞用在衍生類別的屬性宣告中：</span><span class="sxs-lookup"><span data-stu-id="4b48e-169">In such a case, the `new` modifier is used in the declaration of the property in the derived class:</span></span>

     [!code-csharp[csProgGuideProperties#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#4)]  

- <span data-ttu-id="4b48e-170">轉型 `(Employee)` 用來存取基底類別中的隱藏屬性：</span><span class="sxs-lookup"><span data-stu-id="4b48e-170">The cast `(Employee)` is used to access the hidden property in the base class:</span></span>

     [!code-csharp[csProgGuideProperties#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#5)]

     <span data-ttu-id="4b48e-171">如需隱藏成員的詳細資訊，請參閱 [new 修飾詞](../../language-reference/keywords/new-modifier.md)。</span><span class="sxs-lookup"><span data-stu-id="4b48e-171">For more information about hiding members, see the [new Modifier](../../language-reference/keywords/new-modifier.md).</span></span>

## <a name="example"></a><span data-ttu-id="4b48e-172">範例</span><span class="sxs-lookup"><span data-stu-id="4b48e-172">Example</span></span>

<span data-ttu-id="4b48e-173">在此範例中，`Cube` 和 `Square` 這兩個類別會實作抽象類別 `Shape`，並覆寫其抽象 `Area` 屬性。</span><span class="sxs-lookup"><span data-stu-id="4b48e-173">In this example, two classes, `Cube` and `Square`, implement an abstract class, `Shape`, and override its abstract `Area` property.</span></span> <span data-ttu-id="4b48e-174">請注意如何在屬性上使用 [override](../../language-reference/keywords/override.md) 修飾詞。</span><span class="sxs-lookup"><span data-stu-id="4b48e-174">Note the use of the [override](../../language-reference/keywords/override.md) modifier on the properties.</span></span> <span data-ttu-id="4b48e-175">程式接受這端作為輸入，並計算正方形和立方體的區域。</span><span class="sxs-lookup"><span data-stu-id="4b48e-175">The program accepts the side as an input and calculates the areas for the square and cube.</span></span> <span data-ttu-id="4b48e-176">它也接受區域作為輸入，並計算正方形和立方體的對應端。</span><span class="sxs-lookup"><span data-stu-id="4b48e-176">It also accepts the area as an input and calculates the corresponding side for the square and cube.</span></span>

[!code-csharp[csProgGuideProperties#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#6)]

## <a name="see-also"></a><span data-ttu-id="4b48e-177">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b48e-177">See also</span></span>

- [<span data-ttu-id="4b48e-178">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="4b48e-178">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="4b48e-179">屬性</span><span class="sxs-lookup"><span data-stu-id="4b48e-179">Properties</span></span>](properties.md)
- [<span data-ttu-id="4b48e-180">介面屬性</span><span class="sxs-lookup"><span data-stu-id="4b48e-180">Interface Properties</span></span>](interface-properties.md)
- [<span data-ttu-id="4b48e-181">自動實現屬性</span><span class="sxs-lookup"><span data-stu-id="4b48e-181">Auto-Implemented Properties</span></span>](auto-implemented-properties.md)
