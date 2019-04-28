---
title: 詳細語法
description: 了解的差異詳細資訊和輕量型語法，在F#程式設計語言。
ms.date: 05/16/2016
ms.openlocfilehash: c770f2843276619cb2878198a537dcfb9c054b6b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61902300"
---
# <a name="verbose-syntax"></a><span data-ttu-id="e84c8-103">詳細語法</span><span class="sxs-lookup"><span data-stu-id="e84c8-103">Verbose Syntax</span></span>

<span data-ttu-id="e84c8-104">有兩種形式的語法中的許多建構F#語言：*詳細語法*並*輕量型語法*。</span><span class="sxs-lookup"><span data-stu-id="e84c8-104">There are two forms of syntax available for many constructs in the F# language: *verbose syntax* and *lightweight syntax*.</span></span> <span data-ttu-id="e84c8-105">詳細的語法不常用，但優點是較不容易縮排。</span><span class="sxs-lookup"><span data-stu-id="e84c8-105">The verbose syntax is not as commonly used, but has the advantage of being less sensitive to indentation.</span></span> <span data-ttu-id="e84c8-106">輕量型語法較短，並使用縮排來表示的開頭和結尾的建構，而非其他關鍵字喜歡`begin`， `end`， `in`，依此類推。</span><span class="sxs-lookup"><span data-stu-id="e84c8-106">The lightweight syntax is shorter and uses indentation to signal the beginning and end of constructs, rather than additional keywords like `begin`, `end`, `in`, and so on.</span></span> <span data-ttu-id="e84c8-107">預設語法是輕量型語法。</span><span class="sxs-lookup"><span data-stu-id="e84c8-107">The default syntax is the lightweight syntax.</span></span> <span data-ttu-id="e84c8-108">本主題描述的語法F#建構時不會啟用輕量型語法。</span><span class="sxs-lookup"><span data-stu-id="e84c8-108">This topic describes the syntax for F# constructs when lightweight syntax is not enabled.</span></span> <span data-ttu-id="e84c8-109">永遠啟用詳細語法，因此即使您啟用輕量型語法時，您仍然可以使用詳細語法適用於某些建構。</span><span class="sxs-lookup"><span data-stu-id="e84c8-109">Verbose syntax is always enabled, so even if you enable lightweight syntax, you can still use verbose syntax for some constructs.</span></span> <span data-ttu-id="e84c8-110">您可以使用連線，停用輕量型語法`#light "off"`指示詞。</span><span class="sxs-lookup"><span data-stu-id="e84c8-110">You can disable lightweight syntax by using the `#light "off"` directive.</span></span>

## <a name="table-of-constructs"></a><span data-ttu-id="e84c8-111">資料表的建構</span><span class="sxs-lookup"><span data-stu-id="e84c8-111">Table of Constructs</span></span>

<span data-ttu-id="e84c8-112">下表顯示的輕量級和詳細語法F#語言建構的內容中沒有兩個形式之間的差異。</span><span class="sxs-lookup"><span data-stu-id="e84c8-112">The following table shows the lightweight and verbose syntax for F# language constructs in contexts where there is a difference between the two forms.</span></span> <span data-ttu-id="e84c8-113">下表中角括弧 (&lt;&gt;) 括住使用者提供的語法元素。</span><span class="sxs-lookup"><span data-stu-id="e84c8-113">In this table, angle brackets (&lt;&gt;) enclose user-supplied syntax elements.</span></span> <span data-ttu-id="e84c8-114">文件以取得每個語言建構，這些建構內所使用之語法的詳細資訊，請參閱。</span><span class="sxs-lookup"><span data-stu-id="e84c8-114">Refer to the documentation for each language construct for more detailed information about the syntax used within these constructs.</span></span>

<table>
<tr>
<th><span data-ttu-id="e84c8-115">語言建構</span><span class="sxs-lookup"><span data-stu-id="e84c8-115">Language construct</span></span></th>
<th><span data-ttu-id="e84c8-116">輕量型語法</span><span class="sxs-lookup"><span data-stu-id="e84c8-116">Lightweight syntax</span></span></th>
<th><span data-ttu-id="e84c8-117">詳細語法</span><span class="sxs-lookup"><span data-stu-id="e84c8-117">Verbose syntax</span></span></th>
</tr>
<tr>
<td>
<span data-ttu-id="e84c8-118">複合運算式</span><span class="sxs-lookup"><span data-stu-id="e84c8-118">compound expressions</span></span>
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

<span data-ttu-id="e84c8-119">巢狀`let`繫結</span><span class="sxs-lookup"><span data-stu-id="e84c8-119">nested `let` bindings</span></span>

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
<span data-ttu-id="e84c8-120">程式碼區塊</span><span class="sxs-lookup"><span data-stu-id="e84c8-120">code block</span></span>
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

```
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
<tr><td><span data-ttu-id="e84c8-121">記錄</span><span class="sxs-lookup"><span data-stu-id="e84c8-121">record</span></span>
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
<tr><td><span data-ttu-id="e84c8-122">Class - 類別</span><span class="sxs-lookup"><span data-stu-id="e84c8-122">class</span></span>
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
<tr><td><span data-ttu-id="e84c8-123">結構</span><span class="sxs-lookup"><span data-stu-id="e84c8-123">structure</span></span></td><td>

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
<tr><td><span data-ttu-id="e84c8-124">已區分聯集</span><span class="sxs-lookup"><span data-stu-id="e84c8-124">discriminated union</span></span></td><td>

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
<tr><td><span data-ttu-id="e84c8-125">interface</span><span class="sxs-lookup"><span data-stu-id="e84c8-125">interface</span></span></td><td>

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
<tr><td><span data-ttu-id="e84c8-126">物件運算式</span><span class="sxs-lookup"><span data-stu-id="e84c8-126">object expression</span></span></td><td>

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
<tr><td><span data-ttu-id="e84c8-127">介面實作</span><span class="sxs-lookup"><span data-stu-id="e84c8-127">interface implementation</span></span></td><td>

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
<tr><td><span data-ttu-id="e84c8-128">類型擴充功能</span><span class="sxs-lookup"><span data-stu-id="e84c8-128">type extension</span></span></td><td>

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
<tr><td><span data-ttu-id="e84c8-129">name</span><span class="sxs-lookup"><span data-stu-id="e84c8-129">module</span></span></td><td>

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

## <a name="see-also"></a><span data-ttu-id="e84c8-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e84c8-130">See also</span></span>

- [<span data-ttu-id="e84c8-131">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="e84c8-131">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="e84c8-132">編譯器指示詞</span><span class="sxs-lookup"><span data-stu-id="e84c8-132">Compiler Directives</span></span>](compiler-directives.md)
- [<span data-ttu-id="e84c8-133">程式碼格式化方針</span><span class="sxs-lookup"><span data-stu-id="e84c8-133">Code Formatting Guidelines</span></span>](code-formatting-guidelines.md)