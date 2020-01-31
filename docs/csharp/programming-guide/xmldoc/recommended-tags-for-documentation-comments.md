---
title: 建議使用的檔註解標記C# -程式設計指南
ms.date: 01/21/2020
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
ms.openlocfilehash: c746615d0d7a7a3058fbe2f8506a7a7c5c4a8779
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789718"
---
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a><span data-ttu-id="288d4-102">建議使用的檔註解標記C# （程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="288d4-102">Recommended tags for documentation comments (C# programming guide)</span></span>

<span data-ttu-id="288d4-103">C# 編譯器會處理程式碼中的文件註解，並將其在 **/doc** 命令列選項中指定其名稱的檔案中格式化為 XML。</span><span class="sxs-lookup"><span data-stu-id="288d4-103">The C# compiler processes documentation comments in your code and formats them as XML in a file whose name you specify in the **/doc** command-line option.</span></span> <span data-ttu-id="288d4-104">若要依據編譯器產生的檔案來建立最終文件，您可以建立自訂工具，或者是使用 [DocFX](https://dotnet.github.io/docfx/) 或 [Sandcastle](https://github.com/EWSoftware/SHFB)這類工具。</span><span class="sxs-lookup"><span data-stu-id="288d4-104">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [DocFX](https://dotnet.github.io/docfx/) or [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>

<span data-ttu-id="288d4-105">標記是在類型和類型成員這類程式碼建構上處理。</span><span class="sxs-lookup"><span data-stu-id="288d4-105">Tags are processed on code constructs such as types and type members.</span></span>

> [!NOTE]
> <span data-ttu-id="288d4-106">文件註解不能套用至命名空間。</span><span class="sxs-lookup"><span data-stu-id="288d4-106">Documentation comments cannot be applied to a namespace.</span></span>  
  
 <span data-ttu-id="288d4-107">編譯器會處理任何為有效 XML 的標記。</span><span class="sxs-lookup"><span data-stu-id="288d4-107">The compiler will process any tag that is valid XML.</span></span> <span data-ttu-id="288d4-108">下列標記提供使用者文件中的常用功能。</span><span class="sxs-lookup"><span data-stu-id="288d4-108">The following tags provide generally used functionality in user documentation.</span></span>  
  
## <a name="tags"></a><span data-ttu-id="288d4-109">Tags</span><span class="sxs-lookup"><span data-stu-id="288d4-109">Tags</span></span>  
  
|||||  
|---|---|---|---|
|[<span data-ttu-id="288d4-110">\<c></span><span class="sxs-lookup"><span data-stu-id="288d4-110">\<c></span></span>](./code-inline.md)|[<span data-ttu-id="288d4-111">\<para></span><span class="sxs-lookup"><span data-stu-id="288d4-111">\<para></span></span>](./para.md)|<span data-ttu-id="288d4-112">[\<see>](./see.md)\*</span><span class="sxs-lookup"><span data-stu-id="288d4-112">[\<see>](./see.md)\*</span></span>|[<span data-ttu-id="288d4-113">\<value></span><span class="sxs-lookup"><span data-stu-id="288d4-113">\<value></span></span>](./value.md)  
|[<span data-ttu-id="288d4-114">\<code></span><span class="sxs-lookup"><span data-stu-id="288d4-114">\<code></span></span>](./code.md)|<span data-ttu-id="288d4-115">[\<param>](./param.md)\*</span><span class="sxs-lookup"><span data-stu-id="288d4-115">[\<param>](./param.md)\*</span></span>|<span data-ttu-id="288d4-116">[\<seealso>](./seealso.md)\*</span><span class="sxs-lookup"><span data-stu-id="288d4-116">[\<seealso>](./seealso.md)\*</span></span>|  
|[<span data-ttu-id="288d4-117">\<example></span><span class="sxs-lookup"><span data-stu-id="288d4-117">\<example></span></span>](./example.md)|[<span data-ttu-id="288d4-118">\<paramref></span><span class="sxs-lookup"><span data-stu-id="288d4-118">\<paramref></span></span>](./paramref.md)|[<span data-ttu-id="288d4-119">\<summary></span><span class="sxs-lookup"><span data-stu-id="288d4-119">\<summary></span></span>](./summary.md)|  
|<span data-ttu-id="288d4-120">[\<exception>](./exception.md)\*</span><span class="sxs-lookup"><span data-stu-id="288d4-120">[\<exception>](./exception.md)\*</span></span>|<span data-ttu-id="288d4-121">[\<permission>](./permission.md)\*</span><span class="sxs-lookup"><span data-stu-id="288d4-121">[\<permission>](./permission.md)\*</span></span>|<span data-ttu-id="288d4-122">[\<typeparam>](./typeparam.md)\*</span><span class="sxs-lookup"><span data-stu-id="288d4-122">[\<typeparam>](./typeparam.md)\*</span></span>|  
|<span data-ttu-id="288d4-123">[\<include>](./include.md)\*</span><span class="sxs-lookup"><span data-stu-id="288d4-123">[\<include>](./include.md)\*</span></span>|[<span data-ttu-id="288d4-124">\<remarks></span><span class="sxs-lookup"><span data-stu-id="288d4-124">\<remarks></span></span>](./remarks.md)|[<span data-ttu-id="288d4-125">\<typeparamref></span><span class="sxs-lookup"><span data-stu-id="288d4-125">\<typeparamref></span></span>](./typeparamref.md)|  
|[<span data-ttu-id="288d4-126">\<list></span><span class="sxs-lookup"><span data-stu-id="288d4-126">\<list></span></span>](./list.md)|[<span data-ttu-id="288d4-127">\<inheritdoc ></span><span class="sxs-lookup"><span data-stu-id="288d4-127">\<inheritdoc></span></span>](./inheritdoc.md)|[<span data-ttu-id="288d4-128">\<returns></span><span class="sxs-lookup"><span data-stu-id="288d4-128">\<returns></span></span>](./returns.md)|
  
<span data-ttu-id="288d4-129">（\* 表示編譯器會驗證語法）。</span><span class="sxs-lookup"><span data-stu-id="288d4-129">(\* denotes that the compiler verifies syntax.)</span></span>

<span data-ttu-id="288d4-130">如果您想要讓角括弧出現在文件註解的文字中，請使用 `<` 和 `>` 的 HTML 編碼，其分別為 `&lt;` 和 `&gt;`。</span><span class="sxs-lookup"><span data-stu-id="288d4-130">If you want angle brackets to appear in the text of a documentation comment, use the HTML encoding of `<` and `>` which is `&lt;` and `&gt;` respectively.</span></span> <span data-ttu-id="288d4-131">此編碼方式如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="288d4-131">This encoding is shown in the following example.</span></span>

```csharp
/// <summary>
/// This property always returns a value &lt; 1.
/// </summary>
```

## <a name="see-also"></a><span data-ttu-id="288d4-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="288d4-132">See also</span></span>

- [<span data-ttu-id="288d4-133">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="288d4-133">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="288d4-134">-doc （C#編譯器選項）</span><span class="sxs-lookup"><span data-stu-id="288d4-134">-doc (C# compiler options)</span></span>](../../language-reference/compiler-options/doc-compiler-option.md)
- [<span data-ttu-id="288d4-135">XML 檔批註</span><span class="sxs-lookup"><span data-stu-id="288d4-135">XML documentation comments</span></span>](./index.md)
