---
title: "詳細語法 (F#)"
description: "了解 F # 程式語言中的詳細資訊和輕量型語法之間的差異。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 0a6792b3-b312-4453-a025-21d9760eee5d
ms.openlocfilehash: 2cef359a879897825733a3186be97b38896f5953
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="verbose-syntax"></a><span data-ttu-id="4ad09-104">詳細語法</span><span class="sxs-lookup"><span data-stu-id="4ad09-104">Verbose Syntax</span></span>

<span data-ttu-id="4ad09-105">有兩種形式的語法適用於在 F # 語言中的許多建構：*詳細語法*和*輕量型語法*。</span><span class="sxs-lookup"><span data-stu-id="4ad09-105">There are two forms of syntax available for many constructs in the F# language: *verbose syntax* and *lightweight syntax*.</span></span> <span data-ttu-id="4ad09-106">詳細語法不常用，但較不容易縮排的優點。</span><span class="sxs-lookup"><span data-stu-id="4ad09-106">The verbose syntax is not as commonly used, but has the advantage of being less sensitive to indentation.</span></span> <span data-ttu-id="4ad09-107">輕量型語法為較短，並使用縮排訊號的開頭和結尾結構，而不是其他關鍵字喜歡`begin`， `end`， `in`，依此類推。</span><span class="sxs-lookup"><span data-stu-id="4ad09-107">The lightweight syntax is shorter and uses indentation to signal the beginning and end of constructs, rather than additional keywords like `begin`, `end`, `in`, and so on.</span></span> <span data-ttu-id="4ad09-108">預設語法是輕量型語法。</span><span class="sxs-lookup"><span data-stu-id="4ad09-108">The default syntax is the lightweight syntax.</span></span> <span data-ttu-id="4ad09-109">本主題描述適用於 F # 建構語法時不會啟用輕量型語法。</span><span class="sxs-lookup"><span data-stu-id="4ad09-109">This topic describes the syntax for F# constructs when lightweight syntax is not enabled.</span></span> <span data-ttu-id="4ad09-110">永遠啟用詳細語法，因此即使您啟用輕量型語法，您仍然可以使用詳細語法的某些建構。</span><span class="sxs-lookup"><span data-stu-id="4ad09-110">Verbose syntax is always enabled, so even if you enable lightweight syntax, you can still use verbose syntax for some constructs.</span></span> <span data-ttu-id="4ad09-111">您可以使用停用輕量型語法`#light "off"`指示詞。</span><span class="sxs-lookup"><span data-stu-id="4ad09-111">You can disable lightweight syntax by using the `#light "off"` directive.</span></span>


## <a name="table-of-constructs"></a><span data-ttu-id="4ad09-112">資料表的建構</span><span class="sxs-lookup"><span data-stu-id="4ad09-112">Table of Constructs</span></span>
<span data-ttu-id="4ad09-113">下表顯示 F # 語言建構的輕量型和冗長語法的內容中沒有兩個形式之間的差異。</span><span class="sxs-lookup"><span data-stu-id="4ad09-113">The following table shows the lightweight and verbose syntax for F# language constructs in contexts where there is a difference between the two forms.</span></span> <span data-ttu-id="4ad09-114">這個資料表，請在角括號 (&lt;&gt;) 括住使用者提供的語法元素。</span><span class="sxs-lookup"><span data-stu-id="4ad09-114">In this table, angle brackets (&lt;&gt;) enclose user-supplied syntax elements.</span></span> <span data-ttu-id="4ad09-115">請參閱每一個語言建構，如需詳細資訊，這些建構函式內使用之語法的詳細文件。</span><span class="sxs-lookup"><span data-stu-id="4ad09-115">Refer to the documentation for each language construct for more detailed information about the syntax used within these constructs.</span></span>



<table>
<tr>
<th><span data-ttu-id="4ad09-116">語言建構</span><span class="sxs-lookup"><span data-stu-id="4ad09-116">Language construct</span></span></th>
<th><span data-ttu-id="4ad09-117">輕量型語法</span><span class="sxs-lookup"><span data-stu-id="4ad09-117">Lightweight syntax</span></span></th>
<th><span data-ttu-id="4ad09-118">詳細語法</span><span class="sxs-lookup"><span data-stu-id="4ad09-118">Verbose syntax</span></span></th>
</tr>
<tr>
<td>
<span data-ttu-id="4ad09-119">複合運算式</span><span class="sxs-lookup"><span data-stu-id="4ad09-119">compound expressions</span></span>
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


<span data-ttu-id="4ad09-120">巢狀`let`繫結</span><span class="sxs-lookup"><span data-stu-id="4ad09-120">nested `let` bindings</span></span>

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
<span data-ttu-id="4ad09-121">程式碼區塊</span><span class="sxs-lookup"><span data-stu-id="4ad09-121">code block</span></span>
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
<tr><td><span data-ttu-id="4ad09-122">資料錄</span><span class="sxs-lookup"><span data-stu-id="4ad09-122">record</span></span>
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
<tr><td><span data-ttu-id="4ad09-123">Class - 類別</span><span class="sxs-lookup"><span data-stu-id="4ad09-123">class</span></span>
</td><td><span data-ttu-id="4ad09-124">
```
type <class-name>(<params>) = ... ```

</span><span class="sxs-lookup"><span data-stu-id="4ad09-124">
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
<tr><td><span data-ttu-id="4ad09-125">結構</span><span class="sxs-lookup"><span data-stu-id="4ad09-125">structure</span></span></td><td>

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
<tr><td><span data-ttu-id="4ad09-126">差別等位</span><span class="sxs-lookup"><span data-stu-id="4ad09-126">discriminated union</span></span></td><td>

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
<tr><td><span data-ttu-id="4ad09-127">interface</span><span class="sxs-lookup"><span data-stu-id="4ad09-127">interface</span></span></td><td>

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
<tr><td><span data-ttu-id="4ad09-128">物件運算式</span><span class="sxs-lookup"><span data-stu-id="4ad09-128">object expression</span></span></td><td>

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
<tr><td><span data-ttu-id="4ad09-129">介面實作</span><span class="sxs-lookup"><span data-stu-id="4ad09-129">interface implementation</span></span></td><td>

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
<tr><td><span data-ttu-id="4ad09-130">類型擴充功能</span><span class="sxs-lookup"><span data-stu-id="4ad09-130">type extension</span></span></td><td>

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
<tr><td><span data-ttu-id="4ad09-131">name</span><span class="sxs-lookup"><span data-stu-id="4ad09-131">module</span></span></td><td>

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



## <a name="see-also"></a><span data-ttu-id="4ad09-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4ad09-132">See Also</span></span>
[<span data-ttu-id="4ad09-133">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="4ad09-133">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="4ad09-134">編譯器指示詞</span><span class="sxs-lookup"><span data-stu-id="4ad09-134">Compiler Directives</span></span>](compiler-directives.md)

[<span data-ttu-id="4ad09-135">程式碼格式化方針</span><span class="sxs-lookup"><span data-stu-id="4ad09-135">Code Formatting Guidelines</span></span>](code-formatting-guidelines.md)
