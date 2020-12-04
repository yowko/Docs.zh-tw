---
description: using 指示詞 - C# 參考
title: using 指示詞 - C# 參考
ms.date: 07/20/2015
f1_keywords:
- using_CSharpKeyword
helpviewer_keywords:
- using directive [C#]
ms.assetid: b42b8e61-5e7e-439c-bb71-370094b44ae8
ms.openlocfilehash: 77d9c894dae9adc24343ce3a639a4afb904fb0a1
ms.sourcegitcommit: 9d525bb8109216ca1dc9e39c149d4902f4b43da5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2020
ms.locfileid: "96599405"
---
# <a name="using-directive-c-reference"></a><span data-ttu-id="9c6af-103">using 指示詞 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="9c6af-103">using directive (C# Reference)</span></span>

<span data-ttu-id="9c6af-104">`using` 指示詞有三個用途：</span><span class="sxs-lookup"><span data-stu-id="9c6af-104">The `using` directive has three uses:</span></span>

- <span data-ttu-id="9c6af-105">若要允許在命名空間中使用類型，使得您不需限定在該命名空間中使用的類型：</span><span class="sxs-lookup"><span data-stu-id="9c6af-105">To allow the use of types in a namespace so that you do not have to qualify the use of a type in that namespace:</span></span>

    ```csharp
    using System.Text;
    ```

- <span data-ttu-id="9c6af-106">允許您存取類型的靜態成員和巢狀類型，但不必以類型名稱限定存取。</span><span class="sxs-lookup"><span data-stu-id="9c6af-106">To allow you to access static members and nested types of a type without having to qualify the access with the type name.</span></span>

    ```csharp
    using static System.Math;
    ```

    <span data-ttu-id="9c6af-107">如需詳細資訊，請參閱 [using static 指示詞](using-static.md)。</span><span class="sxs-lookup"><span data-stu-id="9c6af-107">For more information, see the [using static directive](using-static.md).</span></span>

- <span data-ttu-id="9c6af-108">若要建立命名空間或類型的別名。</span><span class="sxs-lookup"><span data-stu-id="9c6af-108">To create an alias for a namespace or a type.</span></span> <span data-ttu-id="9c6af-109">這稱為 *using alias 指示詞*。</span><span class="sxs-lookup"><span data-stu-id="9c6af-109">This is called a *using alias directive*.</span></span>

    ```csharp
    using Project = PC.MyCompany.Project;
    ```

<span data-ttu-id="9c6af-110">`using` 關鍵字也用來建立 *using 陳述式*，協助確保能夠正確處理 <xref:System.IDisposable> 物件 (例如檔案和字型)。</span><span class="sxs-lookup"><span data-stu-id="9c6af-110">The `using` keyword is also used to create *using statements*, which help ensure that <xref:System.IDisposable> objects such as files and fonts are handled correctly.</span></span> <span data-ttu-id="9c6af-111">如需詳細資訊，請參閱 [using 陳述式](using-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="9c6af-111">See [using Statement](using-statement.md) for more information.</span></span>

## <a name="using-static-type"></a><span data-ttu-id="9c6af-112">Using static 類型</span><span class="sxs-lookup"><span data-stu-id="9c6af-112">Using static type</span></span>

<span data-ttu-id="9c6af-113">您可以存取類型的靜態成員，而不需以類型名稱限定存取：</span><span class="sxs-lookup"><span data-stu-id="9c6af-113">You can access static members of a type without having to qualify the access with the type name:</span></span>

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

## <a name="remarks"></a><span data-ttu-id="9c6af-114">備註</span><span class="sxs-lookup"><span data-stu-id="9c6af-114">Remarks</span></span>

<span data-ttu-id="9c6af-115">`using` 指示詞的範圍僅限於其出現的檔案。</span><span class="sxs-lookup"><span data-stu-id="9c6af-115">The scope of a `using` directive is limited to the file in which it appears.</span></span>

<span data-ttu-id="9c6af-116">`using` 指示詞會出現：</span><span class="sxs-lookup"><span data-stu-id="9c6af-116">The `using` directive can appear:</span></span>

- <span data-ttu-id="9c6af-117">位於原始程式碼檔的開頭，在任何命名空間或類型定義之前。</span><span class="sxs-lookup"><span data-stu-id="9c6af-117">At the beginning of a source code file, before any namespace or type definitions.</span></span>
- <span data-ttu-id="9c6af-118">在任何命名空間中，但在任何命名空間或類型於此命名空間宣告之前。</span><span class="sxs-lookup"><span data-stu-id="9c6af-118">In any namespace, but before any namespace or types declared in this namespace.</span></span>

<span data-ttu-id="9c6af-119">否則，就會發生編譯器錯誤 [CS1529](../../misc/cs1529.md)。</span><span class="sxs-lookup"><span data-stu-id="9c6af-119">Otherwise, compiler error [CS1529](../../misc/cs1529.md) is generated.</span></span>

<span data-ttu-id="9c6af-120">建立 `using` 別名指示詞，讓您更輕鬆地將識別碼限定在命名空間或類型。</span><span class="sxs-lookup"><span data-stu-id="9c6af-120">Create a `using` alias directive to make it easier to qualify an identifier to a namespace or type.</span></span> <span data-ttu-id="9c6af-121">在任何 `using` 指示詞中，必須使用完整的命名空間或類型，不論 `using` 指示詞是否在它前面。</span><span class="sxs-lookup"><span data-stu-id="9c6af-121">In any `using` directive, the fully-qualified namespace or type must be used regardless of the `using` directives that come before it.</span></span> <span data-ttu-id="9c6af-122">`using` 指示詞的宣告中不可使用任何 `using` 別名。</span><span class="sxs-lookup"><span data-stu-id="9c6af-122">No `using` alias can be used in the declaration of a `using` directive.</span></span> <span data-ttu-id="9c6af-123">例如，下列內容會產生編譯器錯誤：</span><span class="sxs-lookup"><span data-stu-id="9c6af-123">For example, the following generates a compiler error:</span></span>

```csharp
using s = System.Text;
using s.RegularExpressions; // Generates a compiler error.
```

<span data-ttu-id="9c6af-124">建立 `using` 指示詞，以在命名空間中使用類型，而無需指定命名空間。</span><span class="sxs-lookup"><span data-stu-id="9c6af-124">Create a `using` directive to use the types in a namespace without having to specify the namespace.</span></span> <span data-ttu-id="9c6af-125">`using` 指示詞不會授予巢狀於您指定的命名空間中的任何命名空間的存取權。</span><span class="sxs-lookup"><span data-stu-id="9c6af-125">A `using` directive does not give you access to any namespaces that are nested in the namespace you specify.</span></span>

<span data-ttu-id="9c6af-126">命名空間有兩種類型：使用者定義和系統定義。</span><span class="sxs-lookup"><span data-stu-id="9c6af-126">Namespaces come in two categories: user-defined and system-defined.</span></span> <span data-ttu-id="9c6af-127">使用者定義的命名空間是在程式碼中定義的命名空間。</span><span class="sxs-lookup"><span data-stu-id="9c6af-127">User-defined namespaces are namespaces defined in your code.</span></span> <span data-ttu-id="9c6af-128">如需系統定義的命名空間清單，請參閱 [.NET API 瀏覽器](../../../../api/index.md)。</span><span class="sxs-lookup"><span data-stu-id="9c6af-128">For a list of the system-defined namespaces, see [.NET API Browser](../../../../api/index.md).</span></span>

## <a name="example-1"></a><span data-ttu-id="9c6af-129">範例 1</span><span class="sxs-lookup"><span data-stu-id="9c6af-129">Example 1</span></span>

<span data-ttu-id="9c6af-130">下列範例示範如何定義和使用命名空間的 `using` 別名：</span><span class="sxs-lookup"><span data-stu-id="9c6af-130">The following example shows how to define and use a `using` alias for a namespace:</span></span>

[!code-csharp[csrefKeywordsNamespace#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace2.cs#8)]

<span data-ttu-id="9c6af-131">using alias 指示詞的右邊不能有開放式的泛型類型。</span><span class="sxs-lookup"><span data-stu-id="9c6af-131">A using alias directive cannot have an open generic type on the right hand side.</span></span> <span data-ttu-id="9c6af-132">例如，您無法為 `List<T>` 建立 using 別名，但是可以為 `List<int>` 建立。</span><span class="sxs-lookup"><span data-stu-id="9c6af-132">For example, you cannot create a using alias for a `List<T>`, but you can create one for a `List<int>`.</span></span>

## <a name="example-2"></a><span data-ttu-id="9c6af-133">範例 2</span><span class="sxs-lookup"><span data-stu-id="9c6af-133">Example 2</span></span>

<span data-ttu-id="9c6af-134">下列範例示範如何定義類別的 `using` 指示詞和 `using` 別名：</span><span class="sxs-lookup"><span data-stu-id="9c6af-134">The following example shows how to define a `using` directive and a `using` alias for a class:</span></span>

[!code-csharp[csrefKeywordsNamespace#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace2.cs#9)]

## <a name="c-language-specification"></a><span data-ttu-id="9c6af-135">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="9c6af-135">C# language specification</span></span>

<span data-ttu-id="9c6af-136">如需詳細資訊，請參閱 [C# 語言規格](/dotnet/csharp/language-reference/language-specification/introduction)的 [Using 指示詞](~/_csharplang/spec/namespaces.md#using-directives)。</span><span class="sxs-lookup"><span data-stu-id="9c6af-136">For more information, see [Using directives](~/_csharplang/spec/namespaces.md#using-directives) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="9c6af-137">語言規格是 C# 語法及用法的限定來源。</span><span class="sxs-lookup"><span data-stu-id="9c6af-137">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="9c6af-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9c6af-138">See also</span></span>

- [<span data-ttu-id="9c6af-139">C # 參考</span><span class="sxs-lookup"><span data-stu-id="9c6af-139">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="9c6af-140">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="9c6af-140">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="9c6af-141">使用命名空間</span><span class="sxs-lookup"><span data-stu-id="9c6af-141">Using Namespaces</span></span>](../../programming-guide/namespaces/using-namespaces.md)
- [<span data-ttu-id="9c6af-142">C # 關鍵字</span><span class="sxs-lookup"><span data-stu-id="9c6af-142">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="9c6af-143">命名空間</span><span class="sxs-lookup"><span data-stu-id="9c6af-143">Namespaces</span></span>](../../programming-guide/namespaces/index.md)
- [<span data-ttu-id="9c6af-144">using 陳述式</span><span class="sxs-lookup"><span data-stu-id="9c6af-144">using Statement</span></span>](using-statement.md)
