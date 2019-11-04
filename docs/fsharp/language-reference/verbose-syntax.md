---
title: 詳細語法
description: 瞭解程式F#設計語言中的詳細資訊和輕量語法差異。
ms.date: 05/16/2016
ms.openlocfilehash: 575585b201acc1366980cfc5cf523c4117259084
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73421171"
---
# <a name="verbose-syntax"></a><span data-ttu-id="8eaae-103">詳細語法</span><span class="sxs-lookup"><span data-stu-id="8eaae-103">Verbose Syntax</span></span>

<span data-ttu-id="8eaae-104">有兩種形式的語法可用於F#語言中的許多結構： *verbose 語法*和*輕量語法*。</span><span class="sxs-lookup"><span data-stu-id="8eaae-104">There are two forms of syntax available for many constructs in the F# language: *verbose syntax* and *lightweight syntax*.</span></span> <span data-ttu-id="8eaae-105">詳細資訊語法不常用，但具有較不敏感的縮排。</span><span class="sxs-lookup"><span data-stu-id="8eaae-105">The verbose syntax is not as commonly used, but has the advantage of being less sensitive to indentation.</span></span> <span data-ttu-id="8eaae-106">輕量語法較短，並使用縮排來表示結構的開頭和結尾，而不是像 `begin`、`end`、`in`等等的其他關鍵字。</span><span class="sxs-lookup"><span data-stu-id="8eaae-106">The lightweight syntax is shorter and uses indentation to signal the beginning and end of constructs, rather than additional keywords like `begin`, `end`, `in`, and so on.</span></span> <span data-ttu-id="8eaae-107">預設語法是輕量語法。</span><span class="sxs-lookup"><span data-stu-id="8eaae-107">The default syntax is the lightweight syntax.</span></span> <span data-ttu-id="8eaae-108">本主題描述未啟用輕F#量語法時的結構語法。</span><span class="sxs-lookup"><span data-stu-id="8eaae-108">This topic describes the syntax for F# constructs when lightweight syntax is not enabled.</span></span> <span data-ttu-id="8eaae-109">Verbose 語法一律會啟用，因此即使您啟用了輕量語法，仍然可以針對某些結構使用 verbose 語法。</span><span class="sxs-lookup"><span data-stu-id="8eaae-109">Verbose syntax is always enabled, so even if you enable lightweight syntax, you can still use verbose syntax for some constructs.</span></span> <span data-ttu-id="8eaae-110">您可以使用 `#light "off"` 指示詞來停用輕量語法。</span><span class="sxs-lookup"><span data-stu-id="8eaae-110">You can disable lightweight syntax by using the `#light "off"` directive.</span></span>

## <a name="table-of-constructs"></a><span data-ttu-id="8eaae-111">結構表</span><span class="sxs-lookup"><span data-stu-id="8eaae-111">Table of Constructs</span></span>

<span data-ttu-id="8eaae-112">下表顯示在這兩種形式之間有F#差異的內容中，語言結構的輕量和詳細語法。</span><span class="sxs-lookup"><span data-stu-id="8eaae-112">The following table shows the lightweight and verbose syntax for F# language constructs in contexts where there is a difference between the two forms.</span></span> <span data-ttu-id="8eaae-113">在此資料表中，角括弧（&lt;&gt;）會括住使用者提供的語法元素。</span><span class="sxs-lookup"><span data-stu-id="8eaae-113">In this table, angle brackets (&lt;&gt;) enclose user-supplied syntax elements.</span></span> <span data-ttu-id="8eaae-114">請參閱每個語言結構的檔，以取得有關這些結構內所使用之語法的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="8eaae-114">Refer to the documentation for each language construct for more detailed information about the syntax used within these constructs.</span></span>

<table>
<tr>
<th><span data-ttu-id="8eaae-115">語言結構</span><span class="sxs-lookup"><span data-stu-id="8eaae-115">Language construct</span></span></th>
<th><span data-ttu-id="8eaae-116">輕量語法</span><span class="sxs-lookup"><span data-stu-id="8eaae-116">Lightweight syntax</span></span></th>
<th><span data-ttu-id="8eaae-117">詳細資訊語法</span><span class="sxs-lookup"><span data-stu-id="8eaae-117">Verbose syntax</span></span></th>
</tr>
<tr>
<td>
<span data-ttu-id="8eaae-118">複合運算式</span><span class="sxs-lookup"><span data-stu-id="8eaae-118">compound expressions</span></span>
</td>
<td>

```xml
<expression1>
<expression2>
```

</td><td>

```fsharp
<expression1>; <expression2>
```

</td>
</tr>
<tr><td>

<span data-ttu-id="8eaae-119">嵌套 `let` 系結</span><span class="sxs-lookup"><span data-stu-id="8eaae-119">nested `let` bindings</span></span>

</td><td>

```fsharp
let f x =
    let a = 1
    let b = 2
    x + a + b
```

</td><td>

```fsharp
let f x =
    let a = 1 in
    let b = 2 in
    x + a + b
```

</td>
</tr>
<tr><td>
<span data-ttu-id="8eaae-120">程式碼區塊</span><span class="sxs-lookup"><span data-stu-id="8eaae-120">code block</span></span>
</td><td>

```fsharp
(
    <expression1>
    <expression2>
)
```

</td><td>

```fsharp
begin
    <expression1>;
    <expression2>;
end
```

</td>
</tr>
<tr><td>
`for...do`
</td><td>

```fsharp
for counter = start to finish do
    ...
```

</td><td>

```fsharp
for counter = start to finish do
    ...
done
```

</td>
</tr>
<tr><td>
`while...do`
</td><td>

```fsharp
while <condition> do
    ...
```

</td><td>

```fsharp
while <condition> do
    ...
done
```

</td>
</tr>
<tr><td>
`for...in`
</td><td>

```fsharp
for var in start .. finish do
    ...
```

</td><td>

```fsharp
for var in start .. finish do
    ...
done
```

</td>
</tr>
<tr><td>
`do`
</td><td>

```fsharp
do
    ...
```

</td><td>

```fsharp
do
    ...
in
```

</td>
</tr>
<tr><td><span data-ttu-id="8eaae-121">記錄</span><span class="sxs-lookup"><span data-stu-id="8eaae-121">record</span></span>
</td><td>

```fsharp
type <record-name> =
    {
        <field-declarations>
    }
    <value-or-member-definitions>
```

</td><td>

```fsharp
type <record-name> =
    {
        <field-declarations>
    }
    with
        <value-or-member-definitions>
    end
```

</td>
</tr>
<tr><td><span data-ttu-id="8eaae-122">Class - 類別</span><span class="sxs-lookup"><span data-stu-id="8eaae-122">class</span></span>
</td><td>

```fsharp
type <class-name>(<params>) =
    ...
```

</td><td>

```fsharp
type <class-name>(<params>) =
    class
        ...
    end
```

</td>
</tr>
<tr><td><span data-ttu-id="8eaae-123">結構</span><span class="sxs-lookup"><span data-stu-id="8eaae-123">structure</span></span></td><td>

```fsharp
[<StructAttribute>]
type <structure-name> =
    ...
```

</td><td>

```fsharp
type <structure-name> =
    struct
        ...
    end
```

</td>
</tr>
<tr><td><span data-ttu-id="8eaae-124">區分聯集</span><span class="sxs-lookup"><span data-stu-id="8eaae-124">discriminated union</span></span></td><td>

```fsharp
type <union-name> =
    | ...
    | ...
    ...
    <value-or-member definitions>
```

</td><td>

```fsharp
type <union-name> =
    | ...
    | ...
    ...
    with
        <value-or-member-definitions>
    end
```

</td>
</tr>
<tr><td><span data-ttu-id="8eaae-125">interface</span><span class="sxs-lookup"><span data-stu-id="8eaae-125">interface</span></span></td><td>

```fsharp
type <interface-name> =
    ...
```

</td><td>

```fsharp
type <interface-name> =
    interface
        ...
    end
```

</td>
</tr>
<tr><td><span data-ttu-id="8eaae-126">物件運算式</span><span class="sxs-lookup"><span data-stu-id="8eaae-126">object expression</span></span></td><td>

```fsharp
{ new <type-name>
    with
        <value-or-member-definitions>
        <interface-implementations>
}
```

</td><td>

```fsharp
{ new <type-name>
    with
        <value-or-member-definitions>
    end
    <interface-implementations>
}
```

</td>
</tr>
<tr><td><span data-ttu-id="8eaae-127">介面實作</span><span class="sxs-lookup"><span data-stu-id="8eaae-127">interface implementation</span></span></td><td>

```fsharp
interface <interface-name>
    with
        <value-or-member-definitions>
```

</td><td>

```fsharp
interface <interface-name>
    with
        <value-or-member-definitions>
    end
```

</td>
</tr>
<tr><td><span data-ttu-id="8eaae-128">類型延伸</span><span class="sxs-lookup"><span data-stu-id="8eaae-128">type extension</span></span></td><td>

```fsharp
type <type-name>
    with
        <value-or-member-definitions>
```

</td><td>

```fsharp
type <type-name>
    with
        <value-or-member-definitions>
    end
```

</td>
</tr>
<tr><td><span data-ttu-id="8eaae-129">name</span><span class="sxs-lookup"><span data-stu-id="8eaae-129">module</span></span></td><td>

```fsharp
module <module-name> =
    ...
```

</td><td>

```fsharp
module <module-name> =
    begin
        ...
    end
```

</td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="8eaae-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="8eaae-130">See also</span></span>

- [<span data-ttu-id="8eaae-131">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="8eaae-131">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="8eaae-132">編譯器指示詞</span><span class="sxs-lookup"><span data-stu-id="8eaae-132">Compiler Directives</span></span>](compiler-directives.md)
- [<span data-ttu-id="8eaae-133">程式碼格式化方針</span><span class="sxs-lookup"><span data-stu-id="8eaae-133">Code Formatting Guidelines</span></span>](../style-guide/formatting.md)
