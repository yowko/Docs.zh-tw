---
title: 詳細語法
description: 瞭解 F# 程式設計語言中詳細語法和輕量級語法之間的區別。
ms.date: 05/16/2016
ms.openlocfilehash: 722807695c56beb0d681b95a78ed8cb8c1df3ddf
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463912"
---
# <a name="verbose-syntax"></a><span data-ttu-id="47c71-103">詳細語法</span><span class="sxs-lookup"><span data-stu-id="47c71-103">Verbose Syntax</span></span>

<span data-ttu-id="47c71-104">F# 語言中的許多建構有兩種形式的語法:*詳細語法*與*輕巧的語法*。</span><span class="sxs-lookup"><span data-stu-id="47c71-104">There are two forms of syntax available for many constructs in the F# language: *verbose syntax* and *lightweight syntax*.</span></span> <span data-ttu-id="47c71-105">詳細語法不常用,但優點是對縮進不太敏感。</span><span class="sxs-lookup"><span data-stu-id="47c71-105">The verbose syntax is not as commonly used, but has the advantage of being less sensitive to indentation.</span></span> <span data-ttu-id="47c71-106">輕量級語法較短,並使用縮進來發出構造的開始和結束信號,而不是其他關鍵字,如`begin`、、、`end``in`等。</span><span class="sxs-lookup"><span data-stu-id="47c71-106">The lightweight syntax is shorter and uses indentation to signal the beginning and end of constructs, rather than additional keywords like `begin`, `end`, `in`, and so on.</span></span> <span data-ttu-id="47c71-107">默認語法是輕量級語法。</span><span class="sxs-lookup"><span data-stu-id="47c71-107">The default syntax is the lightweight syntax.</span></span> <span data-ttu-id="47c71-108">本主題介紹未啟用輕量級語法時 F# 構造的語法。</span><span class="sxs-lookup"><span data-stu-id="47c71-108">This topic describes the syntax for F# constructs when lightweight syntax is not enabled.</span></span> <span data-ttu-id="47c71-109">詳細語法始終啟用,因此即使您啟用輕量級語法,您仍可以為某些構造使用詳細語法。</span><span class="sxs-lookup"><span data-stu-id="47c71-109">Verbose syntax is always enabled, so even if you enable lightweight syntax, you can still use verbose syntax for some constructs.</span></span> <span data-ttu-id="47c71-110">您可以使用`#light "off"`該指令禁用輕量級語法。</span><span class="sxs-lookup"><span data-stu-id="47c71-110">You can disable lightweight syntax by using the `#light "off"` directive.</span></span>

## <a name="table-of-constructs"></a><span data-ttu-id="47c71-111">建構表</span><span class="sxs-lookup"><span data-stu-id="47c71-111">Table of Constructs</span></span>

<span data-ttu-id="47c71-112">下表顯示了 F# 語言構造的輕量級和詳細語法,這些上下文中兩種窗體之間存在差異。</span><span class="sxs-lookup"><span data-stu-id="47c71-112">The following table shows the lightweight and verbose syntax for F# language constructs in contexts where there is a difference between the two forms.</span></span> <span data-ttu-id="47c71-113">在此表中,角括弧&lt;&gt;( ) 括使用者提供的語法元素。</span><span class="sxs-lookup"><span data-stu-id="47c71-113">In this table, angle brackets (&lt;&gt;) enclose user-supplied syntax elements.</span></span> <span data-ttu-id="47c71-114">有關這些構造中使用的語法的詳細資訊,請參閱每個語言構造的文檔。</span><span class="sxs-lookup"><span data-stu-id="47c71-114">Refer to the documentation for each language construct for more detailed information about the syntax used within these constructs.</span></span>

<table>
<tr>
<th><span data-ttu-id="47c71-115">語言建構</span><span class="sxs-lookup"><span data-stu-id="47c71-115">Language construct</span></span></th>
<th><span data-ttu-id="47c71-116">輕巧法</span><span class="sxs-lookup"><span data-stu-id="47c71-116">Lightweight syntax</span></span></th>
<th><span data-ttu-id="47c71-117">詳細語法</span><span class="sxs-lookup"><span data-stu-id="47c71-117">Verbose syntax</span></span></th>
</tr>
<tr>
<td>
<span data-ttu-id="47c71-118">複合運算式</span><span class="sxs-lookup"><span data-stu-id="47c71-118">compound expressions</span></span>
</td>
<td>

```xml
<expression1 />
<expression2 />
```

</td><td>

```fsharp
<expression1>; <expression2>
```

</td>
</tr>
<tr><td>

<span data-ttu-id="47c71-119">巢狀`let`結合</span><span class="sxs-lookup"><span data-stu-id="47c71-119">nested `let` bindings</span></span>

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
<span data-ttu-id="47c71-120">代碼塊</span><span class="sxs-lookup"><span data-stu-id="47c71-120">code block</span></span>
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
<tr><td><span data-ttu-id="47c71-121">記錄 (record)</span><span class="sxs-lookup"><span data-stu-id="47c71-121">record</span></span>
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
<tr><td><span data-ttu-id="47c71-122">Class - 類別</span><span class="sxs-lookup"><span data-stu-id="47c71-122">class</span></span>
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
<tr><td><span data-ttu-id="47c71-123">structure</span><span class="sxs-lookup"><span data-stu-id="47c71-123">structure</span></span></td><td>

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
<tr><td><span data-ttu-id="47c71-124">歧視工會</span><span class="sxs-lookup"><span data-stu-id="47c71-124">discriminated union</span></span></td><td>

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
<tr><td><span data-ttu-id="47c71-125">interface</span><span class="sxs-lookup"><span data-stu-id="47c71-125">interface</span></span></td><td>

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
<tr><td><span data-ttu-id="47c71-126">物件運算式</span><span class="sxs-lookup"><span data-stu-id="47c71-126">object expression</span></span></td><td>

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
<tr><td><span data-ttu-id="47c71-127">介面實作</span><span class="sxs-lookup"><span data-stu-id="47c71-127">interface implementation</span></span></td><td>

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
<tr><td><span data-ttu-id="47c71-128">型態延伸</span><span class="sxs-lookup"><span data-stu-id="47c71-128">type extension</span></span></td><td>

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
<tr><td><span data-ttu-id="47c71-129">module</span><span class="sxs-lookup"><span data-stu-id="47c71-129">module</span></span></td><td>

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

## <a name="see-also"></a><span data-ttu-id="47c71-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="47c71-130">See also</span></span>

- [<span data-ttu-id="47c71-131">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="47c71-131">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="47c71-132">編譯器指示詞</span><span class="sxs-lookup"><span data-stu-id="47c71-132">Compiler Directives</span></span>](compiler-directives.md)
- [<span data-ttu-id="47c71-133">程式碼格式化方針</span><span class="sxs-lookup"><span data-stu-id="47c71-133">Code Formatting Guidelines</span></span>](../style-guide/formatting.md)
