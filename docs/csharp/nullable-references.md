---
title: 可為 Null 的參考型別
description: '本文提供可為 null 的參考型別（在 c # 8.0 中新增）的總覽。 您會了解此功能如何為新及現有的專案，針對 Null 參考例外狀況提供安全。'
ms.technology: csharp-null-safety
ms.date: 04/21/2020
ms.openlocfilehash: 8a86546ef4adfd7695d957f807a62972b00316dc
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94829163"
---
# <a name="nullable-reference-types"></a><span data-ttu-id="ab532-104">可為 Null 的參考型別</span><span class="sxs-lookup"><span data-stu-id="ab532-104">Nullable reference types</span></span>

<span data-ttu-id="ab532-105">C# 8.0 引進 **可為 Null 的參考型別** 及 **不可為 Null 的參考型別**，可讓您針對參考型別變數的屬性撰寫相關重要陳述式：</span><span class="sxs-lookup"><span data-stu-id="ab532-105">C# 8.0 introduces **nullable reference types** and **non-nullable reference types** that enable you to make important statements about the properties for reference type variables:</span></span>

- <span data-ttu-id="ab532-106">**參考不應該是 null**。</span><span class="sxs-lookup"><span data-stu-id="ab532-106">**A reference isn't supposed to be null**.</span></span> <span data-ttu-id="ab532-107">當變數不應該是 null 時，編譯器會強制執行規則，以確保能夠安全地取值這些變數，而不需要先檢查它是否為 null：</span><span class="sxs-lookup"><span data-stu-id="ab532-107">When variables aren't supposed to be null, the compiler enforces rules that ensure it's safe to dereference these variables without first checking that it isn't null:</span></span>
  - <span data-ttu-id="ab532-108">變數必須初始化為非 Null 值。</span><span class="sxs-lookup"><span data-stu-id="ab532-108">The variable must be initialized to a non-null value.</span></span>
  - <span data-ttu-id="ab532-109">變數永遠不可指派 `null` 值。</span><span class="sxs-lookup"><span data-stu-id="ab532-109">The variable can never be assigned the value `null`.</span></span>
- <span data-ttu-id="ab532-110">**參考可能為 Null**。</span><span class="sxs-lookup"><span data-stu-id="ab532-110">**A reference may be null**.</span></span> <span data-ttu-id="ab532-111">當變數可為 Null 時，編譯器會實施不同的規則，確保您已針對 Null 參考正確地進行檢查：</span><span class="sxs-lookup"><span data-stu-id="ab532-111">When variables may be null, the compiler enforces different rules to ensure that you've correctly checked for a null reference:</span></span>
  - <span data-ttu-id="ab532-112">只有在編譯器能保證該值並非為 Null 時，才能對該變數進行取值 (Dereference)。</span><span class="sxs-lookup"><span data-stu-id="ab532-112">The variable may only be dereferenced when the compiler can guarantee that the value isn't null.</span></span>
  - <span data-ttu-id="ab532-113">這些變數可使用預設的 `null` 值初始化，也可以在其他程式碼中指派 `null` 值。</span><span class="sxs-lookup"><span data-stu-id="ab532-113">These variables may be initialized with the default `null` value and may be assigned the value `null` in other code.</span></span>

<span data-ttu-id="ab532-114">這項新功能提供了在舊版 c # 中處理參考變數的優點，而無法從變數宣告判斷設計意圖。</span><span class="sxs-lookup"><span data-stu-id="ab532-114">This new feature provides significant benefits over the handling of reference variables in earlier versions of C# where the design intent can't be determined from the variable declaration.</span></span> <span data-ttu-id="ab532-115">編譯器不針對參考型別的 Null 參考例外狀況提供安全：</span><span class="sxs-lookup"><span data-stu-id="ab532-115">The compiler didn't provide safety against null reference exceptions for reference types:</span></span>

- <span data-ttu-id="ab532-116">**參考可為 Null**。</span><span class="sxs-lookup"><span data-stu-id="ab532-116">**A reference can be null**.</span></span> <span data-ttu-id="ab532-117">當參考型別變數初始化為或之後指派時，編譯器不會發出警告 `null` `null` 。</span><span class="sxs-lookup"><span data-stu-id="ab532-117">The compiler doesn't issue warnings when a reference-type variable is initialized to `null`, or later assigned `null`.</span></span> <span data-ttu-id="ab532-118">當這些變數是在沒有 null 檢查的情況下進行取值時，編譯器會發出警告。</span><span class="sxs-lookup"><span data-stu-id="ab532-118">The compiler issues warnings when these variables are dereferenced without null checks.</span></span>
- <span data-ttu-id="ab532-119">**參考已假設為並非 Null**。</span><span class="sxs-lookup"><span data-stu-id="ab532-119">**A reference is assumed to be not null**.</span></span> <span data-ttu-id="ab532-120">編譯器不會在對參考型別進行取值 (Dereference) 時發出任何警告。</span><span class="sxs-lookup"><span data-stu-id="ab532-120">The compiler doesn't issue any warnings when reference types are dereferenced.</span></span> <span data-ttu-id="ab532-121">如果變數設定為可能為 null 的運算式，則編譯器會發出警告。</span><span class="sxs-lookup"><span data-stu-id="ab532-121">The compiler issues warnings if a variable is set to an expression that may be null.</span></span>

<span data-ttu-id="ab532-122">這些警告會在編譯時期發出。</span><span class="sxs-lookup"><span data-stu-id="ab532-122">These warnings are emitted at compile time.</span></span> <span data-ttu-id="ab532-123">編譯器不會在可為 null 的內容中新增任何 null 檢查或其他執行時間結構。</span><span class="sxs-lookup"><span data-stu-id="ab532-123">The compiler doesn't add any null checks or other runtime constructs in a nullable context.</span></span> <span data-ttu-id="ab532-124">在執行時間，可為 null 的參考與不可為 null 的參考是相等的。</span><span class="sxs-lookup"><span data-stu-id="ab532-124">At runtime, a nullable reference and a non-nullable reference are equivalent.</span></span>

<span data-ttu-id="ab532-125">透過新增的可為 Null 參考型別，您可以更清楚地宣告您的意圖。</span><span class="sxs-lookup"><span data-stu-id="ab532-125">With the addition of nullable reference types, you can declare your intent more clearly.</span></span> <span data-ttu-id="ab532-126">`null` 值是表示變數並非指向某個值的正確方式。</span><span class="sxs-lookup"><span data-stu-id="ab532-126">The `null` value is the correct way to represent that a variable doesn't refer to a value.</span></span> <span data-ttu-id="ab532-127">請不要使用這項功能來從您的程式碼中移除所有 `null` 值。</span><span class="sxs-lookup"><span data-stu-id="ab532-127">Don't use this feature to remove all `null` values from your code.</span></span> <span data-ttu-id="ab532-128">相反地，您應該對編譯器及其他閱讀您程式碼之開發人員宣告您的意圖。</span><span class="sxs-lookup"><span data-stu-id="ab532-128">Rather, you should declare your intent to the compiler and other developers that read your code.</span></span> <span data-ttu-id="ab532-129">藉由宣告您的意圖，編譯器會在您撰寫的程式碼與該意圖不一致時通知您。</span><span class="sxs-lookup"><span data-stu-id="ab532-129">By declaring your intent, the compiler informs you when you write code that is inconsistent with that intent.</span></span>

<span data-ttu-id="ab532-130">**可為 Null 參考型別** 的語法與 [可為 Null 實值型別](language-reference/builtin-types/nullable-value-types.md)語法相同：將 `?` 附加至變數的型別。</span><span class="sxs-lookup"><span data-stu-id="ab532-130">A **nullable reference type** is noted using the same syntax as [nullable value types](language-reference/builtin-types/nullable-value-types.md): a `?` is appended to the type of the variable.</span></span> <span data-ttu-id="ab532-131">例如，下列變數宣告代表可為 Null 字串變數，`name`：</span><span class="sxs-lookup"><span data-stu-id="ab532-131">For example, the following variable declaration represents a nullable string variable, `name`:</span></span>

```csharp
string? name;
```

<span data-ttu-id="ab532-132">未 `?` 附加至類型名稱的任何變數都是 **不可為 null 的參考型** 別。</span><span class="sxs-lookup"><span data-stu-id="ab532-132">Any variable where the `?` isn't appended to the type name is a **non-nullable reference type**.</span></span> <span data-ttu-id="ab532-133">當您啟用這項功能時，其中包含現有程式碼中的所有參考型別變數。</span><span class="sxs-lookup"><span data-stu-id="ab532-133">That includes all reference type variables in existing code when you've enabled this feature.</span></span>

<span data-ttu-id="ab532-134">編譯器會使用靜態分析來判斷可為 Null 參考是否已知並非為 Null。</span><span class="sxs-lookup"><span data-stu-id="ab532-134">The compiler uses static analysis to determine if a nullable reference is known to be non-null.</span></span> <span data-ttu-id="ab532-135">若您在可為 Null 參考可能為 Null 時對其進行取值 (Dereference)，編譯器會警告您。</span><span class="sxs-lookup"><span data-stu-id="ab532-135">The compiler warns you if you dereference a nullable reference when it may be null.</span></span> <span data-ttu-id="ab532-136">您可以在變數名稱後面使用 [容許運算子](language-reference/operators/null-forgiving.md)來覆寫此行為 `!` 。</span><span class="sxs-lookup"><span data-stu-id="ab532-136">You can override this behavior by using the [null-forgiving operator](language-reference/operators/null-forgiving.md) `!` following a variable name.</span></span> <span data-ttu-id="ab532-137">例如，若您知道 `name` 變數並非為 Null，但編譯器卻發出警告，您可以撰寫下列程式碼來覆寫編譯器的分析：</span><span class="sxs-lookup"><span data-stu-id="ab532-137">For example, if you know the `name` variable isn't null but the compiler issues a warning, you can write the following code to override the compiler's analysis:</span></span>

```csharp
name!.Length;
```

## <a name="nullability-of-types"></a><span data-ttu-id="ab532-138">型別的可 NULL 性</span><span class="sxs-lookup"><span data-stu-id="ab532-138">Nullability of types</span></span>

<span data-ttu-id="ab532-139">任何參考型別都可擁有四種「可 NULL 性」中的其中一種，其描述警告產生的時機：</span><span class="sxs-lookup"><span data-stu-id="ab532-139">Any reference type can have one of four *nullabilities*, which describes when warnings are generated:</span></span>

- <span data-ttu-id="ab532-140">*不可為 null*： Null 無法指派給此類型的變數。</span><span class="sxs-lookup"><span data-stu-id="ab532-140">*Nonnullable*: Null can't be assigned to variables of this type.</span></span> <span data-ttu-id="ab532-141">此型別的變數不需進行 Null 檢查即可進行取值 (Dereference)。</span><span class="sxs-lookup"><span data-stu-id="ab532-141">Variables of this type don't need to be null-checked before dereferencing.</span></span>
- <span data-ttu-id="ab532-142">*Nullable*： null 可以指派給這個型別的變數。</span><span class="sxs-lookup"><span data-stu-id="ab532-142">*Nullable*: Null can be assigned to variables of this type.</span></span> <span data-ttu-id="ab532-143">若沒有事先檢查是否為 `null` 即對此型別的變數進行取值 (Dereference)，即會產生警告。</span><span class="sxs-lookup"><span data-stu-id="ab532-143">Dereferencing variables of this type without first checking for `null` causes a warning.</span></span>
- <span data-ttu-id="ab532-144">*無警示*：無警示是 C # 8.0 之前的狀態。</span><span class="sxs-lookup"><span data-stu-id="ab532-144">*Oblivious*: Oblivious is the pre-C# 8.0 state.</span></span> <span data-ttu-id="ab532-145">此型別的變數可進行取值或指派，且皆不會產生警告。</span><span class="sxs-lookup"><span data-stu-id="ab532-145">Variables of this type can be dereferenced or assigned without warnings.</span></span>
- <span data-ttu-id="ab532-146">*未知*：通常是因為類型參數的條件約束不會告訴編譯器，類型必須可 *為 null* 或 *不可為 null*。</span><span class="sxs-lookup"><span data-stu-id="ab532-146">*Unknown*: Unknown is generally for type parameters where constraints don't tell the compiler that the type must be *nullable* or *nonnullable*.</span></span>

<span data-ttu-id="ab532-147">變數宣告中型別的可 NULL 性會由宣告該變數的「可為 Null 內容」控制。</span><span class="sxs-lookup"><span data-stu-id="ab532-147">The nullability of a type in a variable declaration is controlled by the *nullable context* in which the variable is declared.</span></span>

## <a name="nullable-contexts"></a><span data-ttu-id="ab532-148">可為 Null 內容</span><span class="sxs-lookup"><span data-stu-id="ab532-148">Nullable contexts</span></span>

<span data-ttu-id="ab532-149">可為 Null 內容可讓您對編譯器解譯參考型別變數的方式進行細部控制。</span><span class="sxs-lookup"><span data-stu-id="ab532-149">Nullable contexts enable fine-grained control for how the compiler interprets reference type variables.</span></span> <span data-ttu-id="ab532-150">任何指定原始程式列的 **可為 null 注釋內容** 為啟用或停用。</span><span class="sxs-lookup"><span data-stu-id="ab532-150">The **nullable annotation context** of any given source line is either enabled or disabled.</span></span> <span data-ttu-id="ab532-151">您可以將 C # 8.0 編譯器視為在停用的可為 null 內容中編譯您的所有程式碼：任何參考型別都可以是 null。</span><span class="sxs-lookup"><span data-stu-id="ab532-151">You can think of the pre-C# 8.0 compiler as compiling all your code in a disabled nullable context: any reference type may be null.</span></span> <span data-ttu-id="ab532-152">也可以啟用或停用 **可為 null 的警告內容** 。</span><span class="sxs-lookup"><span data-stu-id="ab532-152">The **nullable warnings context** may also be enabled or disabled.</span></span> <span data-ttu-id="ab532-153">可為 Null 警告內容會指定編譯器使用其流程分析所產生的警告。</span><span class="sxs-lookup"><span data-stu-id="ab532-153">The nullable warnings context specifies the warnings generated by the compiler using its flow analysis.</span></span>

<span data-ttu-id="ab532-154">您可以使用 .csproj 檔案中的元素，為專案設定可為 null 的注釋內容和可為 null 的警告內容 `Nullable` 。 *.csproj*</span><span class="sxs-lookup"><span data-stu-id="ab532-154">The nullable annotation context and nullable warning context can be set for a project using the `Nullable` element in your *.csproj* file.</span></span> <span data-ttu-id="ab532-155">此項目會設定編譯器解譯型別可 NULL 性的方式及所產生警告。</span><span class="sxs-lookup"><span data-stu-id="ab532-155">This element configures how the compiler interprets the nullability of types and what warnings are generated.</span></span> <span data-ttu-id="ab532-156">有效的設定如下：</span><span class="sxs-lookup"><span data-stu-id="ab532-156">Valid settings are:</span></span>

- <span data-ttu-id="ab532-157">`enable`：可為 null 注釋內容已 **啟用**。</span><span class="sxs-lookup"><span data-stu-id="ab532-157">`enable`: The nullable annotation context is **enabled**.</span></span> <span data-ttu-id="ab532-158">可為 Null 警告內容為 **啟用**。</span><span class="sxs-lookup"><span data-stu-id="ab532-158">The nullable warning context is **enabled**.</span></span>
  - <span data-ttu-id="ab532-159">參考型別變數 (例如 `string`) 不可為 Null。</span><span class="sxs-lookup"><span data-stu-id="ab532-159">Variables of a reference type, `string` for example, are non-nullable.</span></span>  <span data-ttu-id="ab532-160">啟用所有可 NULL 性警告。</span><span class="sxs-lookup"><span data-stu-id="ab532-160">All nullability warnings are enabled.</span></span>
- <span data-ttu-id="ab532-161">`warnings`：可為 null 注釋內容已 **停用**。</span><span class="sxs-lookup"><span data-stu-id="ab532-161">`warnings`: The nullable annotation context is **disabled**.</span></span> <span data-ttu-id="ab532-162">可為 Null 警告內容為 **啟用**。</span><span class="sxs-lookup"><span data-stu-id="ab532-162">The nullable warning context is **enabled**.</span></span>
  - <span data-ttu-id="ab532-163">參考型別變數為遺忘式。</span><span class="sxs-lookup"><span data-stu-id="ab532-163">Variables of a reference type are oblivious.</span></span> <span data-ttu-id="ab532-164">啟用所有可 NULL 性警告。</span><span class="sxs-lookup"><span data-stu-id="ab532-164">All nullability warnings are enabled.</span></span>
- <span data-ttu-id="ab532-165">`annotations`：可為 null 注釋內容已 **啟用**。</span><span class="sxs-lookup"><span data-stu-id="ab532-165">`annotations`: The nullable annotation context is **enabled**.</span></span> <span data-ttu-id="ab532-166">可為 Null 警告內容為 **停用**。</span><span class="sxs-lookup"><span data-stu-id="ab532-166">The nullable warning context is **disabled**.</span></span>
  - <span data-ttu-id="ab532-167">例如，參考型別的變數不可以是 null。</span><span class="sxs-lookup"><span data-stu-id="ab532-167">Variables of a reference type, string for example, are non-nullable.</span></span> <span data-ttu-id="ab532-168">停用所有可 NULL 性警告。</span><span class="sxs-lookup"><span data-stu-id="ab532-168">All nullability warnings are disabled.</span></span>
- <span data-ttu-id="ab532-169">`disable`：可為 null 注釋內容已 **停用**。</span><span class="sxs-lookup"><span data-stu-id="ab532-169">`disable`: The nullable annotation context is **disabled**.</span></span> <span data-ttu-id="ab532-170">可為 Null 警告內容為 **停用**。</span><span class="sxs-lookup"><span data-stu-id="ab532-170">The nullable warning context is **disabled**.</span></span>
  - <span data-ttu-id="ab532-171">參考型別變數為遺忘式，與先前版本的 C# 相似。</span><span class="sxs-lookup"><span data-stu-id="ab532-171">Variables of a reference type are oblivious, just like earlier versions of C#.</span></span> <span data-ttu-id="ab532-172">停用所有可 NULL 性警告。</span><span class="sxs-lookup"><span data-stu-id="ab532-172">All nullability warnings are disabled.</span></span>

<span data-ttu-id="ab532-173">**範例**：</span><span class="sxs-lookup"><span data-stu-id="ab532-173">**Example**:</span></span>

```xml
<Nullable>enable</Nullable>
```

<span data-ttu-id="ab532-174">您也可以使用指示詞，在您專案中的任何位置設定相同內容：</span><span class="sxs-lookup"><span data-stu-id="ab532-174">You can also use directives to set these same contexts anywhere in your project:</span></span>

- <span data-ttu-id="ab532-175">`#nullable enable`：將可為 null 注釋內容和可為 null 的警告內容設定為 **已啟用**。</span><span class="sxs-lookup"><span data-stu-id="ab532-175">`#nullable enable`: Sets the nullable annotation context and nullable warning context to **enabled**.</span></span>
- <span data-ttu-id="ab532-176">`#nullable disable`：將可為 null 注釋內容和可為 null 警告內容設定為 **停用**。</span><span class="sxs-lookup"><span data-stu-id="ab532-176">`#nullable disable`: Sets the nullable annotation context and nullable warning context to **disabled**.</span></span>
- <span data-ttu-id="ab532-177">`#nullable restore`：將可為 null 注釋內容和可為 null 警告內容還原至專案設定。</span><span class="sxs-lookup"><span data-stu-id="ab532-177">`#nullable restore`: Restores the nullable annotation context and nullable warning context to the project settings.</span></span>
- <span data-ttu-id="ab532-178">`#nullable disable warnings`：將可為 null 的警告內容設定為 **停用**。</span><span class="sxs-lookup"><span data-stu-id="ab532-178">`#nullable disable warnings`: Set the nullable warning context to **disabled**.</span></span>
- <span data-ttu-id="ab532-179">`#nullable enable warnings`：將可為 null 的警告內容設定為 **已啟用**。</span><span class="sxs-lookup"><span data-stu-id="ab532-179">`#nullable enable warnings`: Set the nullable warning context to **enabled**.</span></span>
- <span data-ttu-id="ab532-180">`#nullable restore warnings`：將可為 null 警告內容還原至專案設定。</span><span class="sxs-lookup"><span data-stu-id="ab532-180">`#nullable restore warnings`: Restores the nullable warning context to the project settings.</span></span>
- <span data-ttu-id="ab532-181">`#nullable disable annotations`：將可為 null 注釋內容設定為 **停用**。</span><span class="sxs-lookup"><span data-stu-id="ab532-181">`#nullable disable annotations`: Set the nullable annotation context to **disabled**.</span></span>
- <span data-ttu-id="ab532-182">`#nullable enable annotations`：將可為 null 注釋內容設定為 **已啟用**。</span><span class="sxs-lookup"><span data-stu-id="ab532-182">`#nullable enable annotations`: Set the nullable annotation context to **enabled**.</span></span>
- <span data-ttu-id="ab532-183">`#nullable restore annotations`：將批註警告內容還原至專案設定。</span><span class="sxs-lookup"><span data-stu-id="ab532-183">`#nullable restore annotations`: Restores the annotation warning context to the project settings.</span></span>

<span data-ttu-id="ab532-184">預設會 **停用** 可為 null 的注釋和警告內容，包括新的專案。</span><span class="sxs-lookup"><span data-stu-id="ab532-184">By default, nullable annotation and warning contexts are **disabled**, including new projects.</span></span> <span data-ttu-id="ab532-185">這表示您現有的程式碼在沒有變更的情況下進行編譯，而不會產生任何新的警告。</span><span class="sxs-lookup"><span data-stu-id="ab532-185">That means that your existing code compiles without changes and without generating any new warnings.</span></span>

<span data-ttu-id="ab532-186">這些選項提供兩種不同的策略來 [更新現有的程式碼基](nullable-migration-strategies.md) 底，以使用可為 null 的參考型別。</span><span class="sxs-lookup"><span data-stu-id="ab532-186">These options provide two distinct strategies to [update an existing codebase](nullable-migration-strategies.md) to use nullable reference types.</span></span>

## <a name="nullable-annotation-context"></a><span data-ttu-id="ab532-187">可為 Null 註釋內容</span><span class="sxs-lookup"><span data-stu-id="ab532-187">Nullable annotation context</span></span>

<span data-ttu-id="ab532-188">編譯器會在停用的可為 Null 註釋內容中使用下列規則：</span><span class="sxs-lookup"><span data-stu-id="ab532-188">The compiler uses the following rules in a disabled nullable annotation context:</span></span>

- <span data-ttu-id="ab532-189">您無法在停用的內容中宣告可為 Null 參考。</span><span class="sxs-lookup"><span data-stu-id="ab532-189">You can't declare nullable references in a disabled context.</span></span>
- <span data-ttu-id="ab532-190">您可以為所有參考變數指派 null 值。</span><span class="sxs-lookup"><span data-stu-id="ab532-190">All reference variables may be assigned a value of null.</span></span>
- <span data-ttu-id="ab532-191">當對參考型別的變數進行取值 (Dereference) 時，不會產生任何警告。</span><span class="sxs-lookup"><span data-stu-id="ab532-191">No warnings are generated when a variable of a reference type is dereferenced.</span></span>
- <span data-ttu-id="ab532-192">Null 容許運算子不可用於停用內容中。</span><span class="sxs-lookup"><span data-stu-id="ab532-192">The null-forgiving operator may not be used in a disabled context.</span></span>

<span data-ttu-id="ab532-193">行為與先前版本的 C# 相同。</span><span class="sxs-lookup"><span data-stu-id="ab532-193">The behavior is the same as previous versions of C#.</span></span>

<span data-ttu-id="ab532-194">編譯器會在啟用的可為 Null 註釋內容中使用下列規則：</span><span class="sxs-lookup"><span data-stu-id="ab532-194">The compiler uses the following rules in an enabled nullable annotation context:</span></span>

- <span data-ttu-id="ab532-195">參考型別的任何變數都是 **不可為 Null 參考**。</span><span class="sxs-lookup"><span data-stu-id="ab532-195">Any variable of a reference type is a **non-nullable reference**.</span></span>
- <span data-ttu-id="ab532-196">任何不可為 Null 參考都可安全地進行取值 (Dereference)。</span><span class="sxs-lookup"><span data-stu-id="ab532-196">Any non-nullable reference may be dereferenced safely.</span></span>
- <span data-ttu-id="ab532-197">任何可為 Null 參考型別 (在變數宣告中的型別後方標註 `?`) 都可為 Null。</span><span class="sxs-lookup"><span data-stu-id="ab532-197">Any nullable reference type (noted by `?` after the type in the variable declaration) may be null.</span></span> <span data-ttu-id="ab532-198">靜態分析會判斷值在取值時是否已知為非 null。</span><span class="sxs-lookup"><span data-stu-id="ab532-198">Static analysis determines if the value is known to be non-null when it's dereferenced.</span></span> <span data-ttu-id="ab532-199">若否，則編譯器會警告您。</span><span class="sxs-lookup"><span data-stu-id="ab532-199">If not, the compiler warns you.</span></span>
- <span data-ttu-id="ab532-200">您可以使用 Null 容許運算子來宣告可為 Null 參考並非為 Null。</span><span class="sxs-lookup"><span data-stu-id="ab532-200">You can use the null-forgiving operator to declare that a nullable reference isn't null.</span></span>

<span data-ttu-id="ab532-201">在啟用的可為 Null 註釋內容中，`?` 字元會附加至宣告 **可為 Null 參考型別** 的參考型別。</span><span class="sxs-lookup"><span data-stu-id="ab532-201">In an enabled nullable annotation context, the `?` character appended to a reference type declares a **nullable reference type**.</span></span> <span data-ttu-id="ab532-202">**Null 容許運算子** `!` 可以附加至運算式，以宣告運算式不是 null。</span><span class="sxs-lookup"><span data-stu-id="ab532-202">The **null-forgiving operator** `!` may be appended to an expression to declare that the expression isn't null.</span></span>

## <a name="nullable-warning-context"></a><span data-ttu-id="ab532-203">可為 Null 警告內容</span><span class="sxs-lookup"><span data-stu-id="ab532-203">Nullable warning context</span></span>

<span data-ttu-id="ab532-204">可為 Null 警告內容與可為 Null 註釋內容不同。</span><span class="sxs-lookup"><span data-stu-id="ab532-204">The nullable warning context is distinct from the nullable annotation context.</span></span> <span data-ttu-id="ab532-205">即使停用新的註釋，仍可啟用警告。</span><span class="sxs-lookup"><span data-stu-id="ab532-205">Warnings can be enabled even when the new annotations are disabled.</span></span> <span data-ttu-id="ab532-206">編譯器會使用靜態分析來判斷任何參考的 **Null 狀態**。</span><span class="sxs-lookup"><span data-stu-id="ab532-206">The compiler uses static flow analysis to determine the **null state** of any reference.</span></span> <span data-ttu-id="ab532-207">當並未「停用」*可為 Null 警告內容* 時，Null 狀態不是 **並非為 Null**，就是 **可能為 Null**。</span><span class="sxs-lookup"><span data-stu-id="ab532-207">The null state is either **not null** or **maybe null** when the *nullable warning context* isn't **disabled**.</span></span> <span data-ttu-id="ab532-208">若您在編譯器已判斷其 **可能為 Null** 時對參考進行取值 (Dereference)，則編譯器會警告您。</span><span class="sxs-lookup"><span data-stu-id="ab532-208">If you dereference a reference when the compiler has determined it's **maybe null**, the compiler warns you.</span></span> <span data-ttu-id="ab532-209">除非編譯器可判斷下列兩個狀況的其中一種狀況，否則參考的狀態就會是 **可能為 Null**：</span><span class="sxs-lookup"><span data-stu-id="ab532-209">The state of a reference is **maybe null** unless the compiler can determine one of two conditions:</span></span>

1. <span data-ttu-id="ab532-210">已明確指派非 null 值給變數。</span><span class="sxs-lookup"><span data-stu-id="ab532-210">The variable has been definitely assigned a non-null value.</span></span>
1. <span data-ttu-id="ab532-211">變數或運算式已在取值 (Dereference) 之前針對 Null 進行檢查。</span><span class="sxs-lookup"><span data-stu-id="ab532-211">The variable or expression has been checked against null before de-referencing it.</span></span>

<span data-ttu-id="ab532-212">當您對可為 null 的警告內容中 **可能為 null** 的變數或運算式進行取值時，編譯器會產生警告。</span><span class="sxs-lookup"><span data-stu-id="ab532-212">The compiler generates warnings when you dereference a variable or expression that is **maybe null** in a nullable warning context.</span></span> <span data-ttu-id="ab532-213">此外，如果在啟用的可為 null 注釋內容中指派了 **可能為 null** 的變數或運算式，則編譯器會在不可為 null 的參考型別變數時產生警告。</span><span class="sxs-lookup"><span data-stu-id="ab532-213">Furthermore, the compiler generates warnings when a nonnullable reference-type variable is assigned a **maybe null** variable or expression in an enabled nullable annotation context.</span></span>

## <a name="attributes-describe-apis"></a><span data-ttu-id="ab532-214">屬性描述 Api</span><span class="sxs-lookup"><span data-stu-id="ab532-214">Attributes describe APIs</span></span>

<span data-ttu-id="ab532-215">您可以將屬性新增至 Api，以提供編譯器有關引數或傳回值何時可以或不能是 null 的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="ab532-215">You add attributes to APIs that provide the compiler more information about when arguments or return values can or can't be null.</span></span> <span data-ttu-id="ab532-216">您可以在本文中以涵蓋 [可為 null 屬性](language-reference/attributes/nullable-analysis.md)的語言參考，深入瞭解這些屬性。</span><span class="sxs-lookup"><span data-stu-id="ab532-216">You can learn more about these attributes in our article in the language reference covering the [nullable attributes](language-reference/attributes/nullable-analysis.md).</span></span> <span data-ttu-id="ab532-217">這些屬性會在目前和即將發行的版本中新增至 .NET 程式庫。</span><span class="sxs-lookup"><span data-stu-id="ab532-217">These attributes are being added to .NET libraries over current and upcoming releases.</span></span> <span data-ttu-id="ab532-218">最常使用的 Api 會先更新。</span><span class="sxs-lookup"><span data-stu-id="ab532-218">The most commonly used APIs are being updated first.</span></span>

## <a name="known-pitfalls"></a><span data-ttu-id="ab532-219">已知陷阱</span><span class="sxs-lookup"><span data-stu-id="ab532-219">Known pitfalls</span></span>

<span data-ttu-id="ab532-220">包含參考型別的陣列和結構是可為 null 的參考型別功能的已知陷阱。</span><span class="sxs-lookup"><span data-stu-id="ab532-220">Arrays and structs that contain reference types are known pitfalls in nullable reference types feature.</span></span>

### <a name="structs"></a><span data-ttu-id="ab532-221">結構</span><span class="sxs-lookup"><span data-stu-id="ab532-221">Structs</span></span>

<span data-ttu-id="ab532-222">包含不可為 null 的參考型別的結構，可讓您 `default` 不需要任何警告即可指派。</span><span class="sxs-lookup"><span data-stu-id="ab532-222">A struct that contains non-nullable reference types allows assigning `default` for it without any warnings.</span></span> <span data-ttu-id="ab532-223">請考慮下列範例：</span><span class="sxs-lookup"><span data-stu-id="ab532-223">Consider the following example:</span></span>

```csharp
using System;

#nullable enable

public struct Student
{
    public string FirstName;
    public string? MiddleName;
    public string LastName;
}

public static class Program
{
    public static void PrintStudent(Student student)
    {
        Console.WriteLine($"First name: {student.FirstName.ToUpper()}");
        Console.WriteLine($"Middle name: {student.MiddleName.ToUpper()}");
        Console.WriteLine($"Last name: {student.LastName.ToUpper()}");
    }

    public static void Main() => PrintStudent(default);
}
```

<span data-ttu-id="ab532-224">在上述範例中，在 `PrintStudent(default)` 不可為 null 的參考型別和為 null 時，不會出現警告 `FirstName` `LastName` 。</span><span class="sxs-lookup"><span data-stu-id="ab532-224">In the preceding example, there is no warning in `PrintStudent(default)` while the non-nullable reference types `FirstName` and `LastName` are null.</span></span>

<span data-ttu-id="ab532-225">另一個更常見的情況是當您處理泛型結構時。</span><span class="sxs-lookup"><span data-stu-id="ab532-225">Another more common case is when you deal with generic structs.</span></span> <span data-ttu-id="ab532-226">請考慮下列範例：</span><span class="sxs-lookup"><span data-stu-id="ab532-226">Consider the following example:</span></span>

```csharp
#nullable enable

public struct Foo<T>
{
    public T Bar { get; set; }
}

public static class Program
{
    public static void Main()
    {
        string s = default(Foo<string>).Bar;
    }
}
```

<span data-ttu-id="ab532-227">在上述範例中，屬性 `Bar` 會 `null` 在執行時間，而且會指派給不可為 null 的字串，而不會出現任何警告。</span><span class="sxs-lookup"><span data-stu-id="ab532-227">In the preceding example, the property `Bar` is going to be `null` at runtime, and it's assigned to non-nullable string without any warnings.</span></span>

### <a name="arrays"></a><span data-ttu-id="ab532-228">陣列</span><span class="sxs-lookup"><span data-stu-id="ab532-228">Arrays</span></span>

<span data-ttu-id="ab532-229">陣列也是可為 null 的參考型別的已知缺陷。</span><span class="sxs-lookup"><span data-stu-id="ab532-229">Arrays are also a known pitfall in nullable reference types.</span></span> <span data-ttu-id="ab532-230">請看看下列未產生任何警告的範例：</span><span class="sxs-lookup"><span data-stu-id="ab532-230">Consider the following example which doesn't produce any warnings:</span></span>

```csharp
using System;

#nullable enable

public static class Program
{
    public static void Main()
    {
        string[] values = new string[10];
        string s = values[0];
        Console.WriteLine(s.ToUpper());
    }
}
```

<span data-ttu-id="ab532-231">在上述範例中，陣列的宣告會顯示為不可為 null 的字串，而其元素全部初始化為 null。</span><span class="sxs-lookup"><span data-stu-id="ab532-231">In the preceding example, the declaration of the array shows it holds non-nullable strings, while its elements are all initialized to null.</span></span> <span data-ttu-id="ab532-232">然後，會將 `s` null 值指派給變數， (陣列) 的第一個元素。</span><span class="sxs-lookup"><span data-stu-id="ab532-232">Then, the variable `s` is assigned a null value (the first element of the array).</span></span> <span data-ttu-id="ab532-233">最後，變數 `s` 會被取值，導致執行時間例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ab532-233">Finally, the variable `s` is dereferenced causing a runtime exception.</span></span>

## <a name="see-also"></a><span data-ttu-id="ab532-234">請參閱</span><span class="sxs-lookup"><span data-stu-id="ab532-234">See also</span></span>

- [<span data-ttu-id="ab532-235">草稿可為 null 的參考型別規格</span><span class="sxs-lookup"><span data-stu-id="ab532-235">Draft nullable reference types specification</span></span>](~/_csharplang/proposals/csharp-9.0/nullable-reference-types-specification.md)
- [<span data-ttu-id="ab532-236">可為 Null 參考教學課程簡介</span><span class="sxs-lookup"><span data-stu-id="ab532-236">Intro to nullable references tutorial</span></span>](tutorials/nullable-reference-types.md)
- [<span data-ttu-id="ab532-237">將現有的程式碼基底遷移至可為 Null 參考</span><span class="sxs-lookup"><span data-stu-id="ab532-237">Migrate an existing codebase to nullable references</span></span>](tutorials/upgrade-to-nullable-references.md)
- [<span data-ttu-id="ab532-238">-可為 null (c # 編譯器選項) </span><span class="sxs-lookup"><span data-stu-id="ab532-238">-nullable (C# Compiler option)</span></span>](language-reference/compiler-options/nullable-compiler-option.md)
