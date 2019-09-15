---
title: using 指示詞 - C# 參考
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- using directive [C#]
ms.assetid: b42b8e61-5e7e-439c-bb71-370094b44ae8
ms.openlocfilehash: d6e3667861c2b1ac9a84ca7b4e2cabb5784d793d
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2019
ms.locfileid: "70970050"
---
# <a name="using-directive-c-reference"></a><span data-ttu-id="be5dd-102">using 指示詞 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="be5dd-102">using directive (C# Reference)</span></span>

<span data-ttu-id="be5dd-103">`using` 指示詞有三個用途：</span><span class="sxs-lookup"><span data-stu-id="be5dd-103">The `using` directive has three uses:</span></span>

- <span data-ttu-id="be5dd-104">若要允許在命名空間中使用類型，使得您不需限定在該命名空間中使用的類型：</span><span class="sxs-lookup"><span data-stu-id="be5dd-104">To allow the use of types in a namespace so that you do not have to qualify the use of a type in that namespace:</span></span>

    ```csharp
    using System.Text;
    ```

- <span data-ttu-id="be5dd-105">允許您存取類型的靜態成員和巢狀類型，但不必以類型名稱限定存取。</span><span class="sxs-lookup"><span data-stu-id="be5dd-105">To allow you to access static members and nested types of a type without having to qualify the access with the type name.</span></span>

    ```csharp
    using static System.Math;
    ```

    <span data-ttu-id="be5dd-106">如需詳細資訊，請參閱 [using static 指示詞](using-static.md)。</span><span class="sxs-lookup"><span data-stu-id="be5dd-106">For more information, see the [using static directive](using-static.md).</span></span>

- <span data-ttu-id="be5dd-107">若要建立命名空間或類型的別名。</span><span class="sxs-lookup"><span data-stu-id="be5dd-107">To create an alias for a namespace or a type.</span></span> <span data-ttu-id="be5dd-108">這稱為 *using alias 指示詞*。</span><span class="sxs-lookup"><span data-stu-id="be5dd-108">This is called a *using alias directive*.</span></span>

    ```csharp
    using Project = PC.MyCompany.Project;
    ```

<span data-ttu-id="be5dd-109">`using` 關鍵字也用來建立 *using 陳述式*，協助確保能夠正確處理 <xref:System.IDisposable> 物件 (例如檔案和字型)。</span><span class="sxs-lookup"><span data-stu-id="be5dd-109">The `using` keyword is also used to create *using statements*, which help ensure that <xref:System.IDisposable> objects such as files and fonts are handled correctly.</span></span> <span data-ttu-id="be5dd-110">如需詳細資訊，請參閱 [sing 陳述式](using-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="be5dd-110">See [using Statement](using-statement.md) for more information.</span></span>

## <a name="using-static-type"></a><span data-ttu-id="be5dd-111">Using static 類型</span><span class="sxs-lookup"><span data-stu-id="be5dd-111">Using static type</span></span>

<span data-ttu-id="be5dd-112">您可以存取類型的靜態成員，而不需以類型名稱限定存取：</span><span class="sxs-lookup"><span data-stu-id="be5dd-112">You can access static members of a type without having to qualify the access with the type name:</span></span>

```csharp
using static System.Console;
using static System.Math;
class Program
{
    static void Main()
    {
        WriteLine(Sqrt(3*3 + 4*4));
    }
}
```

## <a name="remarks"></a><span data-ttu-id="be5dd-113">備註</span><span class="sxs-lookup"><span data-stu-id="be5dd-113">Remarks</span></span>

<span data-ttu-id="be5dd-114">`using` 指示詞的範圍僅限於其出現的檔案。</span><span class="sxs-lookup"><span data-stu-id="be5dd-114">The scope of a `using` directive is limited to the file in which it appears.</span></span>

<span data-ttu-id="be5dd-115">`using` 指示詞會出現：</span><span class="sxs-lookup"><span data-stu-id="be5dd-115">The `using` directive can appear:</span></span>

- <span data-ttu-id="be5dd-116">位於原始程式碼檔的開頭，在任何命名空間或類型定義之前。</span><span class="sxs-lookup"><span data-stu-id="be5dd-116">At the beginning of a source code file, before any namespace or type definitions.</span></span>
- <span data-ttu-id="be5dd-117">在任何命名空間中，但在任何命名空間或類型於此命名空間宣告之前。</span><span class="sxs-lookup"><span data-stu-id="be5dd-117">In any namespace, but before any namespace or types declared in this namespace.</span></span>

<span data-ttu-id="be5dd-118">否則，就會發生編譯器錯誤 [CS1529](../../misc/cs1529.md)。</span><span class="sxs-lookup"><span data-stu-id="be5dd-118">Otherwise, compiler error [CS1529](../../misc/cs1529.md) is generated.</span></span>

<span data-ttu-id="be5dd-119">建立 `using` 別名指示詞，讓您更輕鬆地將識別碼限定在命名空間或類型。</span><span class="sxs-lookup"><span data-stu-id="be5dd-119">Create a `using` alias directive to make it easier to qualify an identifier to a namespace or type.</span></span> <span data-ttu-id="be5dd-120">在任何 `using` 指示詞中，必須使用完整的命名空間或類型，不論 `using` 指示詞是否在它前面。</span><span class="sxs-lookup"><span data-stu-id="be5dd-120">In any `using` directive, the fully-qualified namespace or type must be used regardless of the `using` directives that come before it.</span></span> <span data-ttu-id="be5dd-121">`using` 指示詞的宣告中不可使用任何 `using` 別名。</span><span class="sxs-lookup"><span data-stu-id="be5dd-121">No `using` alias can be used in the declaration of a `using` directive.</span></span> <span data-ttu-id="be5dd-122">例如，下列內容會產生編譯器錯誤：</span><span class="sxs-lookup"><span data-stu-id="be5dd-122">For example, the following generates a compiler error:</span></span>

```csharp
using s = System.Text;
using s.RegularExpressions;
```

<span data-ttu-id="be5dd-123">建立 `using` 指示詞，以在命名空間中使用類型，而無需指定命名空間。</span><span class="sxs-lookup"><span data-stu-id="be5dd-123">Create a `using` directive to use the types in a namespace without having to specify the namespace.</span></span> <span data-ttu-id="be5dd-124">`using` 指示詞不會授予巢狀於您指定的命名空間中的任何命名空間的存取權。</span><span class="sxs-lookup"><span data-stu-id="be5dd-124">A `using` directive does not give you access to any namespaces that are nested in the namespace you specify.</span></span>

<span data-ttu-id="be5dd-125">命名空間有兩種類型：使用者定義和系統定義。</span><span class="sxs-lookup"><span data-stu-id="be5dd-125">Namespaces come in two categories: user-defined and system-defined.</span></span> <span data-ttu-id="be5dd-126">使用者定義的命名空間是在程式碼中定義的命名空間。</span><span class="sxs-lookup"><span data-stu-id="be5dd-126">User-defined namespaces are namespaces defined in your code.</span></span> <span data-ttu-id="be5dd-127">如需系統定義的命名空間清單，請參閱 [.NET API 瀏覽器](../../../../api/index.md)。</span><span class="sxs-lookup"><span data-stu-id="be5dd-127">For a list of the system-defined namespaces, see [.NET API Browser](../../../../api/index.md).</span></span>

## <a name="example-1"></a><span data-ttu-id="be5dd-128">範例 1</span><span class="sxs-lookup"><span data-stu-id="be5dd-128">Example 1</span></span>

<span data-ttu-id="be5dd-129">下列範例示範如何定義和使用命名空間的 `using` 別名：</span><span class="sxs-lookup"><span data-stu-id="be5dd-129">The following example shows how to define and use a `using` alias for a namespace:</span></span>

[!code-csharp[csrefKeywordsNamespace#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace2.cs#8)]

<span data-ttu-id="be5dd-130">using alias 指示詞的右邊不能有開放式的泛型類型。</span><span class="sxs-lookup"><span data-stu-id="be5dd-130">A using alias directive cannot have an open generic type on the right hand side.</span></span> <span data-ttu-id="be5dd-131">例如，您無法為 `List<T>` 建立 using 別名，但是可以為 `List<int>` 建立。</span><span class="sxs-lookup"><span data-stu-id="be5dd-131">For example, you cannot create a using alias for a `List<T>`, but you can create one for a `List<int>`.</span></span>

## <a name="example-2"></a><span data-ttu-id="be5dd-132">範例 2</span><span class="sxs-lookup"><span data-stu-id="be5dd-132">Example 2</span></span>

<span data-ttu-id="be5dd-133">下列範例示範如何定義類別的 `using` 指示詞和 `using` 別名：</span><span class="sxs-lookup"><span data-stu-id="be5dd-133">The following example shows how to define a `using` directive and a `using` alias for a class:</span></span>

[!code-csharp[csrefKeywordsNamespace#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace2.cs#9)]

## <a name="c-language-specification"></a><span data-ttu-id="be5dd-134">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="be5dd-134">C# language specification</span></span>

<span data-ttu-id="be5dd-135">如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的 [Using 指示詞](~/_csharplang/spec/namespaces.md#using-directives)。</span><span class="sxs-lookup"><span data-stu-id="be5dd-135">For more information, see [Using directives](~/_csharplang/spec/namespaces.md#using-directives) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="be5dd-136">語言規格是 C# 語法及用法的限定來源。</span><span class="sxs-lookup"><span data-stu-id="be5dd-136">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="be5dd-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be5dd-137">See also</span></span>

- [<span data-ttu-id="be5dd-138">C# 參考</span><span class="sxs-lookup"><span data-stu-id="be5dd-138">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="be5dd-139">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="be5dd-139">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="be5dd-140">使用命名空間</span><span class="sxs-lookup"><span data-stu-id="be5dd-140">Using Namespaces</span></span>](../../programming-guide/namespaces/using-namespaces.md)
- [<span data-ttu-id="be5dd-141">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="be5dd-141">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="be5dd-142">命名空間</span><span class="sxs-lookup"><span data-stu-id="be5dd-142">Namespaces</span></span>](../../programming-guide/namespaces/index.md)
- [<span data-ttu-id="be5dd-143">using 陳述式</span><span class="sxs-lookup"><span data-stu-id="be5dd-143">using Statement</span></span>](using-statement.md)
