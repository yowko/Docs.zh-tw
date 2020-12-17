---
title: 詳細語法
description: '瞭解 F # 程式設計語言中的詳細資訊與輕量語法之間的差異。'
ms.date: 05/16/2016
ms.openlocfilehash: 4e1725b58c8cb67c074ba12fd4ca25ce0c000a1e
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/16/2020
ms.locfileid: "97595173"
---
# <a name="verbose-syntax"></a><span data-ttu-id="c3b20-103">詳細語法</span><span class="sxs-lookup"><span data-stu-id="c3b20-103">Verbose Syntax</span></span>

<span data-ttu-id="c3b20-104">有兩種形式的語法可用於 F # 語言： *詳細語法* 和 *輕量語法* 中的許多結構。</span><span class="sxs-lookup"><span data-stu-id="c3b20-104">There are two forms of syntax available for many constructs in the F# language: *verbose syntax* and *lightweight syntax*.</span></span> <span data-ttu-id="c3b20-105">詳細資訊語法並不常用，但其優點在於縮排較不敏感。</span><span class="sxs-lookup"><span data-stu-id="c3b20-105">The verbose syntax is not as commonly used, but has the advantage of being less sensitive to indentation.</span></span> <span data-ttu-id="c3b20-106">輕量語法較短，而且會使用縮排來表示結構的開頭和結尾，而不是如、、等等的其他關鍵字 `begin` `end` `in` 。</span><span class="sxs-lookup"><span data-stu-id="c3b20-106">The lightweight syntax is shorter and uses indentation to signal the beginning and end of constructs, rather than additional keywords like `begin`, `end`, `in`, and so on.</span></span> <span data-ttu-id="c3b20-107">預設語法是輕量語法。</span><span class="sxs-lookup"><span data-stu-id="c3b20-107">The default syntax is the lightweight syntax.</span></span> <span data-ttu-id="c3b20-108">本主題說明未啟用輕量語法時 F # 結構的語法。</span><span class="sxs-lookup"><span data-stu-id="c3b20-108">This topic describes the syntax for F# constructs when lightweight syntax is not enabled.</span></span> <span data-ttu-id="c3b20-109">詳細語法一律為啟用狀態，因此即使您啟用輕量語法，還是可以針對某些結構使用詳細語法。</span><span class="sxs-lookup"><span data-stu-id="c3b20-109">Verbose syntax is always enabled, so even if you enable lightweight syntax, you can still use verbose syntax for some constructs.</span></span> <span data-ttu-id="c3b20-110">您可以使用指示詞來停用輕量語法 `#light "off"` 。</span><span class="sxs-lookup"><span data-stu-id="c3b20-110">You can disable lightweight syntax by using the `#light "off"` directive.</span></span>

## <a name="table-of-constructs"></a><span data-ttu-id="c3b20-111">結構表</span><span class="sxs-lookup"><span data-stu-id="c3b20-111">Table of Constructs</span></span>

<span data-ttu-id="c3b20-112">下表顯示在這兩種形式之間有差異之 F # 語言結構的輕量和詳細語法。</span><span class="sxs-lookup"><span data-stu-id="c3b20-112">The following table shows the lightweight and verbose syntax for F# language constructs in contexts where there is a difference between the two forms.</span></span> <span data-ttu-id="c3b20-113">在此表格中，角括弧 (&lt; &gt;) 括住使用者提供的語法元素。</span><span class="sxs-lookup"><span data-stu-id="c3b20-113">In this table, angle brackets (&lt;&gt;) enclose user-supplied syntax elements.</span></span> <span data-ttu-id="c3b20-114">如需有關這些結構中所使用之語法的詳細資訊，請參閱每個語言結構的檔。</span><span class="sxs-lookup"><span data-stu-id="c3b20-114">Refer to the documentation for each language construct for more detailed information about the syntax used within these constructs.</span></span>

<table>
<tr>
<th><span data-ttu-id="c3b20-115">語言結構</span><span class="sxs-lookup"><span data-stu-id="c3b20-115">Language construct</span></span></th>
<th><span data-ttu-id="c3b20-116">輕量語法</span><span class="sxs-lookup"><span data-stu-id="c3b20-116">Lightweight syntax</span></span></th>
<th><span data-ttu-id="c3b20-117">詳細語法</span><span class="sxs-lookup"><span data-stu-id="c3b20-117">Verbose syntax</span></span></th>
</tr>
<tr>
<td>
<span data-ttu-id="c3b20-118">複合運算式</span><span class="sxs-lookup"><span data-stu-id="c3b20-118">compound expressions</span></span>
</td>
<td>

```fsharp
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

<span data-ttu-id="c3b20-119">嵌套 `let` 系結</span><span class="sxs-lookup"><span data-stu-id="c3b20-119">nested `let` bindings</span></span>

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
<span data-ttu-id="c3b20-120">程式碼區塊</span><span class="sxs-lookup"><span data-stu-id="c3b20-120">code block</span></span>
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
<tr><td><span data-ttu-id="c3b20-121">記錄 (record)</span><span class="sxs-lookup"><span data-stu-id="c3b20-121">record</span></span>
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
<tr><td><span data-ttu-id="c3b20-122">Class - 類別</span><span class="sxs-lookup"><span data-stu-id="c3b20-122">class</span></span>
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
<tr><td><span data-ttu-id="c3b20-123">structure</span><span class="sxs-lookup"><span data-stu-id="c3b20-123">structure</span></span></td><td>

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
<tr><td><span data-ttu-id="c3b20-124">區分聯集</span><span class="sxs-lookup"><span data-stu-id="c3b20-124">discriminated union</span></span></td><td>

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
<tr><td><span data-ttu-id="c3b20-125">interface</span><span class="sxs-lookup"><span data-stu-id="c3b20-125">interface</span></span></td><td>

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
<tr><td><span data-ttu-id="c3b20-126">物件運算式</span><span class="sxs-lookup"><span data-stu-id="c3b20-126">object expression</span></span></td><td>

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
<tr><td><span data-ttu-id="c3b20-127">介面實作</span><span class="sxs-lookup"><span data-stu-id="c3b20-127">interface implementation</span></span></td><td>

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
<tr><td><span data-ttu-id="c3b20-128">類型延伸模組</span><span class="sxs-lookup"><span data-stu-id="c3b20-128">type extension</span></span></td><td>

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
<tr><td><span data-ttu-id="c3b20-129">name</span><span class="sxs-lookup"><span data-stu-id="c3b20-129">module</span></span></td><td>

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

## <a name="see-also"></a><span data-ttu-id="c3b20-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c3b20-130">See also</span></span>

- [<span data-ttu-id="c3b20-131">F # 語言參考</span><span class="sxs-lookup"><span data-stu-id="c3b20-131">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="c3b20-132">編譯器指示詞</span><span class="sxs-lookup"><span data-stu-id="c3b20-132">Compiler Directives</span></span>](compiler-directives.md)
- [<span data-ttu-id="c3b20-133">程式碼格式化方針</span><span class="sxs-lookup"><span data-stu-id="c3b20-133">Code Formatting Guidelines</span></span>](../style-guide/formatting.md)
