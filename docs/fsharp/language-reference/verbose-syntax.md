---
title: 詳細語法 (F#)
description: '了解 F # 程式設計語言中的詳細資訊和輕量型語法之間的差異。'
ms.date: 05/16/2016
ms.openlocfilehash: b4f2354738da4692cb444e5e7dd9531d80d26664
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2018
ms.locfileid: "45647130"
---
# <a name="verbose-syntax"></a><span data-ttu-id="37003-103">詳細語法</span><span class="sxs-lookup"><span data-stu-id="37003-103">Verbose Syntax</span></span>

<span data-ttu-id="37003-104">有可供在 F # 語言中的許多建構的兩種形式的語法：*詳細語法*並*輕量型語法*。</span><span class="sxs-lookup"><span data-stu-id="37003-104">There are two forms of syntax available for many constructs in the F# language: *verbose syntax* and *lightweight syntax*.</span></span> <span data-ttu-id="37003-105">詳細的語法不常用，但優點是較不容易縮排。</span><span class="sxs-lookup"><span data-stu-id="37003-105">The verbose syntax is not as commonly used, but has the advantage of being less sensitive to indentation.</span></span> <span data-ttu-id="37003-106">輕量型語法較短，並使用縮排來表示的開頭和結尾的建構，而非其他關鍵字喜歡`begin`， `end`， `in`，依此類推。</span><span class="sxs-lookup"><span data-stu-id="37003-106">The lightweight syntax is shorter and uses indentation to signal the beginning and end of constructs, rather than additional keywords like `begin`, `end`, `in`, and so on.</span></span> <span data-ttu-id="37003-107">預設語法是輕量型語法。</span><span class="sxs-lookup"><span data-stu-id="37003-107">The default syntax is the lightweight syntax.</span></span> <span data-ttu-id="37003-108">未啟用輕量型語法時，本主題將描述適用於 F # 建構語法。</span><span class="sxs-lookup"><span data-stu-id="37003-108">This topic describes the syntax for F# constructs when lightweight syntax is not enabled.</span></span> <span data-ttu-id="37003-109">永遠啟用詳細語法，因此即使您啟用輕量型語法時，您仍然可以使用詳細語法適用於某些建構。</span><span class="sxs-lookup"><span data-stu-id="37003-109">Verbose syntax is always enabled, so even if you enable lightweight syntax, you can still use verbose syntax for some constructs.</span></span> <span data-ttu-id="37003-110">您可以使用連線，停用輕量型語法`#light "off"`指示詞。</span><span class="sxs-lookup"><span data-stu-id="37003-110">You can disable lightweight syntax by using the `#light "off"` directive.</span></span>

## <a name="table-of-constructs"></a><span data-ttu-id="37003-111">資料表的建構</span><span class="sxs-lookup"><span data-stu-id="37003-111">Table of Constructs</span></span>

<span data-ttu-id="37003-112">下表顯示 F # 語言建構的輕量級和詳細語法在內容中沒有兩個形式之間的差異。</span><span class="sxs-lookup"><span data-stu-id="37003-112">The following table shows the lightweight and verbose syntax for F# language constructs in contexts where there is a difference between the two forms.</span></span> <span data-ttu-id="37003-113">下表中角括弧 (&lt;&gt;) 括住使用者提供的語法元素。</span><span class="sxs-lookup"><span data-stu-id="37003-113">In this table, angle brackets (&lt;&gt;) enclose user-supplied syntax elements.</span></span> <span data-ttu-id="37003-114">文件以取得每個語言建構，這些建構內所使用之語法的詳細資訊，請參閱。</span><span class="sxs-lookup"><span data-stu-id="37003-114">Refer to the documentation for each language construct for more detailed information about the syntax used within these constructs.</span></span>

<table>
<tr>
<th><span data-ttu-id="37003-115">語言建構</span><span class="sxs-lookup"><span data-stu-id="37003-115">Language construct</span></span></th>
<th><span data-ttu-id="37003-116">輕量型語法</span><span class="sxs-lookup"><span data-stu-id="37003-116">Lightweight syntax</span></span></th>
<th><span data-ttu-id="37003-117">詳細語法</span><span class="sxs-lookup"><span data-stu-id="37003-117">Verbose syntax</span></span></th>
</tr>
<tr>
<td>
<span data-ttu-id="37003-118">複合運算式</span><span class="sxs-lookup"><span data-stu-id="37003-118">compound expressions</span></span>
</td>
<td>

```xml
<expression1>
<expression2>
```
</td><td>

```
<expression1>; <expression2>
```

</td>
</tr>
<tr><td>


<span data-ttu-id="37003-119">巢狀`let`繫結</span><span class="sxs-lookup"><span data-stu-id="37003-119">nested `let` bindings</span></span>

</td><td>
```
let f x =
    let a = 1
    let b = 2
    x + a + b
```

</td><td>

```
let f x =
    let a = 1 in
    let b = 2 in
    x + a + b
```

</td>
</tr>
<tr><td>
<span data-ttu-id="37003-120">程式碼區塊</span><span class="sxs-lookup"><span data-stu-id="37003-120">code block</span></span>
</td><td>

```
(
    <expression1>
    <expression2>
)
```

</td><td>

```
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

```
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

```
while <condition> do
    ...
```

</td><td>

```
while <condition> do
    ...
done
```

</td>
</tr>
<tr><td>
`for...in`
</td><td>

```
for var in start .. finish do
    ...
```

</td><td>

```
for var in start .. finish do
    ...
done
```

</td>
</tr>
<tr><td>
`do`
</td><td>

```
do
    ...
```

</td><td>

```
do
    ...
in
```

</td>
</tr>
<tr><td><span data-ttu-id="37003-121">記錄</span><span class="sxs-lookup"><span data-stu-id="37003-121">record</span></span>
</td><td>

```
type <record-name> =
    {
        <field-declarations>
    }
    <value-or-member-definitions>
```

</td><td>

```
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
<tr><td><span data-ttu-id="37003-122">Class - 類別</span><span class="sxs-lookup"><span data-stu-id="37003-122">class</span></span>
</td><td><span data-ttu-id="37003-123">
```
type <class-name>(<params>) = ... ```

</span><span class="sxs-lookup"><span data-stu-id="37003-123">
```
type <class-name>(<params>) = ... ```

</span></span></td><td>

```
type <class-name>(<params>) =
    class
        ...
    end
```
</td>
</tr>
<tr><td><span data-ttu-id="37003-124">結構</span><span class="sxs-lookup"><span data-stu-id="37003-124">structure</span></span></td><td>

```
[<StructAttribute>]
type <structure-name> =
    ...
```
</td><td>

```
type <structure-name> =
    struct
        ...
    end
```

</td>
</tr>
<tr><td><span data-ttu-id="37003-125">已區分聯集</span><span class="sxs-lookup"><span data-stu-id="37003-125">discriminated union</span></span></td><td>

```
type <union-name> =
    | ...
    | ...
    ...
    <value-or-member definitions>
```
</td><td>

```
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
<tr><td><span data-ttu-id="37003-126">interface</span><span class="sxs-lookup"><span data-stu-id="37003-126">interface</span></span></td><td>

```
type <interface-name> =
    ...
```
</td><td>

```
type <interface-name> =
    interface
        ...
    end
```

</td>
</tr>
<tr><td><span data-ttu-id="37003-127">物件運算式</span><span class="sxs-lookup"><span data-stu-id="37003-127">object expression</span></span></td><td>

```
{ new <type-name>
    with
        <value-or-member-definitions>
        <interface-implementations>
}
```

</td><td>

```
{ new <type-name>
    with
        <value-or-member-definitions>
    end
    <interface-implementations>
}
```

</td>
</tr>
<tr><td><span data-ttu-id="37003-128">介面實作</span><span class="sxs-lookup"><span data-stu-id="37003-128">interface implementation</span></span></td><td>

```
interface <interface-name>
    with
        <value-or-member-definitions>
```

</td><td>

```
interface <interface-name>
    with
        <value-or-member-definitions>
    end
```

</td>
</tr>
<tr><td><span data-ttu-id="37003-129">類型擴充功能</span><span class="sxs-lookup"><span data-stu-id="37003-129">type extension</span></span></td><td>

```
type <type-name>
    with
        <value-or-member-definitions>
```

</td><td>

```
type <type-name>
    with
        <value-or-member-definitions>
    end
```

</td>
</tr>
<tr><td><span data-ttu-id="37003-130">name</span><span class="sxs-lookup"><span data-stu-id="37003-130">module</span></span></td><td>

```
module <module-name> =
    ...
```

</td><td>

```
module <module-name> =
    begin
        ...
    end
```

</td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="37003-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="37003-131">See also</span></span>

- [<span data-ttu-id="37003-132">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="37003-132">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="37003-133">編譯器指示詞</span><span class="sxs-lookup"><span data-stu-id="37003-133">Compiler Directives</span></span>](compiler-directives.md)
- [<span data-ttu-id="37003-134">程式碼格式化方針</span><span class="sxs-lookup"><span data-stu-id="37003-134">Code Formatting Guidelines</span></span>](code-formatting-guidelines.md)
