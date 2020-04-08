---
title: 空白參考型態 - C# 參考
description: 瞭解 C# 可空參考型態以及如何使用它們
ms.date: 04/06/2020
ms.openlocfilehash: cbc7397ac76b43b79a4168f4c61fe2c631b4a46b
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888313"
---
# <a name="nullable-reference-types-c-reference"></a><span data-ttu-id="309d4-103">空白引言型態 (C# 引用)</span><span class="sxs-lookup"><span data-stu-id="309d4-103">Nullable reference types (C# reference)</span></span>

> [!NOTE]
> <span data-ttu-id="309d4-104">本文介紹可無效的引用類型。</span><span class="sxs-lookup"><span data-stu-id="309d4-104">This article covers nullable reference types.</span></span> <span data-ttu-id="309d4-105">您可以宣告[空數型態](nullable-value-types.md)。</span><span class="sxs-lookup"><span data-stu-id="309d4-105">You can also declare [nullable value types](nullable-value-types.md).</span></span>

<span data-ttu-id="309d4-106">空引用類型從 C# 8.0 開始可用,在已選擇輸入*空感知上下文*的代碼中。</span><span class="sxs-lookup"><span data-stu-id="309d4-106">Nullable reference types are available beginning with C# 8.0, in code that has opted in to a *nullable aware context*.</span></span> <span data-ttu-id="309d4-107">空引用類型、空靜態分析警告和[允許無效運算符](../operators/null-forgiving.md)是可選的語言功能。</span><span class="sxs-lookup"><span data-stu-id="309d4-107">Nullable reference types, the null static analysis warnings, and the [null-forgiving operator](../operators/null-forgiving.md) are optional language features.</span></span> <span data-ttu-id="309d4-108">默認情況下,所有功能都處於關閉狀態。</span><span class="sxs-lookup"><span data-stu-id="309d4-108">All are turned off by default.</span></span> <span data-ttu-id="309d4-109">在專案等級使用產生設定或在使用實用機制的代碼中控制*可無效上下文*。</span><span class="sxs-lookup"><span data-stu-id="309d4-109">A *nullable context* is controlled at the project level using build settings, or in code using pragmas.</span></span>

 <span data-ttu-id="309d4-110">在可復原的感知的文字中:</span><span class="sxs-lookup"><span data-stu-id="309d4-110">In a nullable aware context:</span></span>

- <span data-ttu-id="309d4-111">引用類型的`T`變數必須用非 null 初始化,並且可能永遠不會分配可能`null`為的值。</span><span class="sxs-lookup"><span data-stu-id="309d4-111">A variable of a reference type `T` must be initialized with non-null, and may never be assigned a value that may be `null`.</span></span>
- <span data-ttu-id="309d4-112">引用類型的`T?`變數可以使用`null`初始化或`null`分配 ,但在取消引用之前`null`需要針對 它進行檢查。</span><span class="sxs-lookup"><span data-stu-id="309d4-112">A variable of a reference type `T?` may be initialized with `null` or assigned `null`, but is required to be checked against `null` before de-referencing.</span></span>
- <span data-ttu-id="309d4-113">在應用`m`null`T?`寬容運算符(如中`m!`)時,類型的變數被視為非 null。</span><span class="sxs-lookup"><span data-stu-id="309d4-113">A variable `m` of type `T?` is considered to be non-null when you apply the null-forgiving operator, as in `m!`.</span></span>

<span data-ttu-id="309d4-114">非可引用類型和空引用類型`T``T?`之間的區別由編譯器對上述規則的解釋強制執行。</span><span class="sxs-lookup"><span data-stu-id="309d4-114">The distinctions between a non-nullable reference type `T` and a nullable reference type `T?` are enforced by the compiler's interpretation of the preceding rules.</span></span> <span data-ttu-id="309d4-115">類型的`T`變數和類型的`T?`變數由相同的 .NET 類型表示。</span><span class="sxs-lookup"><span data-stu-id="309d4-115">A variable of type `T` and a variable of type `T?` are represented by the same .NET type.</span></span> <span data-ttu-id="309d4-116">以下範例宣告一個不可否定的字串和一個空字串,然後使用 null 寬容運算元將值分配給不可否定的字串:</span><span class="sxs-lookup"><span data-stu-id="309d4-116">The following example declares a non-nullable string and a nullable string, and then uses the null-forgiving operator to assign a value to a non-nullable string:</span></span>

:::code language="csharp" source="snippets/NullableReferenceTypes.cs" id="SnippetCoreSyntax":::

<span data-ttu-id="309d4-117">變數`notNull`和`nullable`變數都由<xref:System.String>類型表示。</span><span class="sxs-lookup"><span data-stu-id="309d4-117">The variables `notNull` and `nullable` are both represented by the <xref:System.String> type.</span></span> <span data-ttu-id="309d4-118">由於不可取消和可 null 的類型都儲存為同一類型,因此不允許使用空引用類型。</span><span class="sxs-lookup"><span data-stu-id="309d4-118">Because the non-nullable and nullable types are both stored as the same type, there are several locations where using a nullable reference type isn't allowed.</span></span> <span data-ttu-id="309d4-119">通常,空引用類型不能用作基類或實現的介面。</span><span class="sxs-lookup"><span data-stu-id="309d4-119">In general, a nullable reference type can't be used as a base class or implemented interface.</span></span> <span data-ttu-id="309d4-120">任何物件創建或類型測試表達式都不能使用空引用類型。</span><span class="sxs-lookup"><span data-stu-id="309d4-120">A nullable reference type can't be used in any object creation or type testing expression.</span></span> <span data-ttu-id="309d4-121">空引用類型不能是成員訪問表達式的類型。</span><span class="sxs-lookup"><span data-stu-id="309d4-121">A nullable reference type can't be the type of a member access expression.</span></span> <span data-ttu-id="309d4-122">以下範例顯示以下建構:</span><span class="sxs-lookup"><span data-stu-id="309d4-122">The following examples show these constructs:</span></span>

```csharp
public MyClass : System.Object? // not allowed
{
}

var nullEmpty = System.String?.Empty; // Not allowed
var maybeObject = new object?(); // Not allowed
try
{
    if (thing is string? nullableString) // not allowed
        Console.WriteLine(nullableString);
} catch (Exception? e) // Not Allowed
{
    Console.WriteLine("error");
}
```

## <a name="nullable-references-and-static-analysis"></a><span data-ttu-id="309d4-123">可空參考與靜態分析</span><span class="sxs-lookup"><span data-stu-id="309d4-123">Nullable references and static analysis</span></span>

<span data-ttu-id="309d4-124">上一節中的示例說明了可空引用類型的性質。</span><span class="sxs-lookup"><span data-stu-id="309d4-124">The examples in the previous section illustrate the nature of nullable reference types.</span></span> <span data-ttu-id="309d4-125">空引用類型不是新的類類型,而是對現有引用類型的註釋。</span><span class="sxs-lookup"><span data-stu-id="309d4-125">Nullable reference types aren't new class types, but rather annotations on existing reference types.</span></span> <span data-ttu-id="309d4-126">編譯器使用這些註釋來説明您在代碼中找到潛在的空引用錯誤。</span><span class="sxs-lookup"><span data-stu-id="309d4-126">The compiler uses those annotations to help you find potential null reference errors in your code.</span></span> <span data-ttu-id="309d4-127">不可取消的引用類型和空引用類型之間沒有運行時差異。</span><span class="sxs-lookup"><span data-stu-id="309d4-127">There's no runtime difference between a non-nullable reference type and a nullable reference type.</span></span> <span data-ttu-id="309d4-128">編譯器不添加任何非空引用類型的運行時檢查。</span><span class="sxs-lookup"><span data-stu-id="309d4-128">The compiler doesn't add any runtime checking for non-nullable reference types.</span></span> <span data-ttu-id="309d4-129">好處是在編譯時間分析。</span><span class="sxs-lookup"><span data-stu-id="309d4-129">The benefits are in the compile-time analysis.</span></span> <span data-ttu-id="309d4-130">編譯器會生成警告,以説明您尋找和修復程式碼中的潛在空錯誤。</span><span class="sxs-lookup"><span data-stu-id="309d4-130">The compiler generates warnings that help you find and fix potential null errors in your code.</span></span> <span data-ttu-id="309d4-131">聲明您的意圖,當代碼違反該意圖時,編譯器會發出警告。</span><span class="sxs-lookup"><span data-stu-id="309d4-131">You declare your intent, and the compiler warns you when your code violates that intent.</span></span>

<span data-ttu-id="309d4-132">在啟用的可啟用的上下文中,編譯器對任何引用類型的變數執行靜態分析,這些變數都是空的和不可否定的。</span><span class="sxs-lookup"><span data-stu-id="309d4-132">In a nullable enabled context, the compiler performs static analysis on variables of any reference type, both nullable and non-nullable.</span></span> <span data-ttu-id="309d4-133">編譯器將每個引用變數的 null 狀態追蹤為*不為 null*或*可能為 null*。</span><span class="sxs-lookup"><span data-stu-id="309d4-133">The compiler tracks the null state of each reference variable as either *not null* or *maybe null*.</span></span> <span data-ttu-id="309d4-134">無法空引的預設狀態*為 null*。</span><span class="sxs-lookup"><span data-stu-id="309d4-134">The default state of a non-nullable reference is *not null*.</span></span> <span data-ttu-id="309d4-135">空引言的預設狀態*可能為 null*。</span><span class="sxs-lookup"><span data-stu-id="309d4-135">The default state of a nullable reference is *maybe null*.</span></span>

<span data-ttu-id="309d4-136">無法空的引用類型應始終安全取消引用,因為它們的 null 狀態不是*null*。</span><span class="sxs-lookup"><span data-stu-id="309d4-136">Non-nullable reference types should always be safe to dereference because their null state is *not null*.</span></span> <span data-ttu-id="309d4-137">要強制執行該規則,如果非空引用類型未初始化為非 null 值,編譯器將發出警告。</span><span class="sxs-lookup"><span data-stu-id="309d4-137">To enforce that rule, the compiler issues warnings if a non-nullable reference type isn't initialized to a non-null value.</span></span> <span data-ttu-id="309d4-138">必須將局部變數指定在聲明位置。</span><span class="sxs-lookup"><span data-stu-id="309d4-138">Local variables must be assigned where they're declared.</span></span> <span data-ttu-id="309d4-139">每個構造函數必須分配每個欄位,無論是在其正文中,還是調用構造函數,要麼使用欄位初始化器。</span><span class="sxs-lookup"><span data-stu-id="309d4-139">Every constructor must assign every field, either in its body, a called constructor, or using a field initializer.</span></span> <span data-ttu-id="309d4-140">如果將不可取消的引用分配給狀態*可能為空*的引用,編譯器將發出警告。</span><span class="sxs-lookup"><span data-stu-id="309d4-140">The compiler issues warnings if a non-nullable reference is assigned to a reference whose state is *maybe null*.</span></span> <span data-ttu-id="309d4-141">但是,由於不可空引用*不為空*,因此當取消引用這些變數時,不會發出警告。</span><span class="sxs-lookup"><span data-stu-id="309d4-141">However, because a non-nullable reference is *not null*, no warnings are issued when those variables are de-referenced.</span></span>

<span data-ttu-id="309d4-142">可空引為型態可以初始化或`null`分配給 。</span><span class="sxs-lookup"><span data-stu-id="309d4-142">Nullable reference types may be initialized or assigned to `null`.</span></span> <span data-ttu-id="309d4-143">因此,靜態分析必須在取消引用變數之前確定變數*不是 null。*</span><span class="sxs-lookup"><span data-stu-id="309d4-143">Therefore, static analysis must determine that a variable is *not null* before it's dereferenced.</span></span> <span data-ttu-id="309d4-144">如果確定可空引用*為空*,則無法將其分配給不可取消的引用變數。</span><span class="sxs-lookup"><span data-stu-id="309d4-144">If a nullable reference is determined to be *maybe null*, it can't be assigned to a non-nullable reference variable.</span></span> <span data-ttu-id="309d4-145">以下類別顯示了這些警告的範例:</span><span class="sxs-lookup"><span data-stu-id="309d4-145">The following class shows examples of these warnings:</span></span>

:::code language="csharp" source="snippets/NullableReferenceTypes.cs" id="SnippetClassWithNullable":::

<span data-ttu-id="309d4-146">以下代碼片段顯示編譯器在使用此類時發出警告的位置:</span><span class="sxs-lookup"><span data-stu-id="309d4-146">The following snippet shows where the compiler emits warnings when using this class:</span></span>

:::code language="csharp" source="snippets/NullableReferenceTypes.cs" id="SnippetLocalWarnings":::

<span data-ttu-id="309d4-147">前面的範例演示了編譯器的靜態分析,以確定引用變數的 null 狀態。</span><span class="sxs-lookup"><span data-stu-id="309d4-147">The preceding examples demonstrate the compiler's static analysis to determine the null state of reference variables.</span></span> <span data-ttu-id="309d4-148">編譯器對空檢查和賦值應用語言規則來通知其分析。</span><span class="sxs-lookup"><span data-stu-id="309d4-148">The compiler applies language rules for null checks and assignments to inform its analysis.</span></span>  <span data-ttu-id="309d4-149">編譯器不能對方法或屬性的語義進行假設。</span><span class="sxs-lookup"><span data-stu-id="309d4-149">The compiler can't make assumptions about the semantics of methods or properties.</span></span> <span data-ttu-id="309d4-150">如果調用執行空檢查的方法,編譯器無法知道這些方法會影響變數的 null 狀態。</span><span class="sxs-lookup"><span data-stu-id="309d4-150">If you call methods that perform null checks, the compiler can't know those methods affect a variable's null state.</span></span> <span data-ttu-id="309d4-151">有許多屬性可以添加到 API 中,以便通知編譯器參數和返回值的語義。</span><span class="sxs-lookup"><span data-stu-id="309d4-151">There are a number of attributes you can add to your APIs to inform the compiler about the semantics of arguments and return values.</span></span> <span data-ttu-id="309d4-152">這些屬性已應用於 .NET 核心庫中的許多常見 API。</span><span class="sxs-lookup"><span data-stu-id="309d4-152">These attributes have been applied to many common APIs in the .NET Core libraries.</span></span> <span data-ttu-id="309d4-153">例如,<xref:System.String.IsNullOrEmpty%2A>已更新,編譯器將該方法正確解釋為空檢查。</span><span class="sxs-lookup"><span data-stu-id="309d4-153">For example, <xref:System.String.IsNullOrEmpty%2A> has been updated, and the compiler correctly interprets that method as a null check.</span></span> <span data-ttu-id="309d4-154">有關應用於空狀態靜態分析的屬性的詳細資訊,請參閱關於[null 可屬性](../../nullable-attributes.md)的文章。</span><span class="sxs-lookup"><span data-stu-id="309d4-154">For more information about the attributes that apply to null state static analysis, see the article on [Nullable attributes](../../nullable-attributes.md).</span></span>

## <a name="setting-the-nullable-context"></a><span data-ttu-id="309d4-155">設定可無效的內容</span><span class="sxs-lookup"><span data-stu-id="309d4-155">Setting the nullable context</span></span>

<span data-ttu-id="309d4-156">有兩種方法可以控制可無效上下文。</span><span class="sxs-lookup"><span data-stu-id="309d4-156">There are two ways to control the nullable context.</span></span> <span data-ttu-id="309d4-157">在項目級別,可以添加`<Nullable>enable</Nullable>`專案設置。</span><span class="sxs-lookup"><span data-stu-id="309d4-157">At the project level, you can add the `<Nullable>enable</Nullable>` project setting.</span></span> <span data-ttu-id="309d4-158">在單個 C# 源檔案中,`#nullable enable`可以新增雜注以啟用可 null 上下文。</span><span class="sxs-lookup"><span data-stu-id="309d4-158">In a single C# source file, you can add the `#nullable enable` pragma to enable the nullable context.</span></span> <span data-ttu-id="309d4-159">請參閱有關[設置空策略](../../nullable-attributes.md)的文章。</span><span class="sxs-lookup"><span data-stu-id="309d4-159">See the article on [setting a nullable strategy](../../nullable-attributes.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="309d4-160">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="309d4-160">C# language specification</span></span>

<span data-ttu-id="309d4-161">有關詳細資訊,請參閱[以下 C# 語言規範](~/_csharplang/spec/introduction.md)的建議:</span><span class="sxs-lookup"><span data-stu-id="309d4-161">For more information, see the following proposals for the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="309d4-162">可為 Null 的參考型別</span><span class="sxs-lookup"><span data-stu-id="309d4-162">Nullable reference types</span></span>](~/_csharplang/proposals/csharp-8.0/nullable-reference-types.md)
- [<span data-ttu-id="309d4-163">草稿空參考類型規範</span><span class="sxs-lookup"><span data-stu-id="309d4-163">Draft nullable reference types specification</span></span>](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md)

## <a name="see-also"></a><span data-ttu-id="309d4-164">另請參閱</span><span class="sxs-lookup"><span data-stu-id="309d4-164">See also</span></span>

- [<span data-ttu-id="309d4-165">C# 參考</span><span class="sxs-lookup"><span data-stu-id="309d4-165">C# reference</span></span>](../index.md)
- [<span data-ttu-id="309d4-166">可為 Null 的實值型別</span><span class="sxs-lookup"><span data-stu-id="309d4-166">Nullable value types</span></span>](nullable-value-types.md)
