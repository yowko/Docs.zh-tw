---
title: 文檔注釋的推薦標記 - C# 程式設計指南
ms.date: 01/21/2020
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
ms.openlocfilehash: c746615d0d7a7a3058fbe2f8506a7a7c5c4a8779
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789718"
---
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a><span data-ttu-id="a4410-102">文檔注釋的推薦標籤（C# 程式設計指南）</span><span class="sxs-lookup"><span data-stu-id="a4410-102">Recommended tags for documentation comments (C# programming guide)</span></span>

<span data-ttu-id="a4410-103">C# 編譯器會處理程式碼中的文件註解，並將其在 **/doc** 命令列選項中指定其名稱的檔案中格式化為 XML。</span><span class="sxs-lookup"><span data-stu-id="a4410-103">The C# compiler processes documentation comments in your code and formats them as XML in a file whose name you specify in the **/doc** command-line option.</span></span> <span data-ttu-id="a4410-104">要基於編譯器生成的檔創建最終文檔，您可以創建自訂工具，或使用[DocFX](https://dotnet.github.io/docfx/)或[Sandcastle](https://github.com/EWSoftware/SHFB)等工具。</span><span class="sxs-lookup"><span data-stu-id="a4410-104">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [DocFX](https://dotnet.github.io/docfx/) or [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>

<span data-ttu-id="a4410-105">標記是在類型和類型成員這類程式碼建構上處理。</span><span class="sxs-lookup"><span data-stu-id="a4410-105">Tags are processed on code constructs such as types and type members.</span></span>

> [!NOTE]
> <span data-ttu-id="a4410-106">文件註解不能套用至命名空間。</span><span class="sxs-lookup"><span data-stu-id="a4410-106">Documentation comments cannot be applied to a namespace.</span></span>  
  
 <span data-ttu-id="a4410-107">編譯器會處理任何為有效 XML 的標記。</span><span class="sxs-lookup"><span data-stu-id="a4410-107">The compiler will process any tag that is valid XML.</span></span> <span data-ttu-id="a4410-108">下列標記提供使用者文件中的常用功能。</span><span class="sxs-lookup"><span data-stu-id="a4410-108">The following tags provide generally used functionality in user documentation.</span></span>  
  
## <a name="tags"></a><span data-ttu-id="a4410-109">Tags</span><span class="sxs-lookup"><span data-stu-id="a4410-109">Tags</span></span>  
  
|||||  
|---|---|---|---|
|[<span data-ttu-id="a4410-110">\<c></span><span class="sxs-lookup"><span data-stu-id="a4410-110">\<c></span></span>](./code-inline.md)|[<span data-ttu-id="a4410-111">\<第>段</span><span class="sxs-lookup"><span data-stu-id="a4410-111">\<para></span></span>](./para.md)|<span data-ttu-id="a4410-112">[\<見>](./see.md)\*</span><span class="sxs-lookup"><span data-stu-id="a4410-112">[\<see>](./see.md)\*</span></span>|[<span data-ttu-id="a4410-113">\<值></span><span class="sxs-lookup"><span data-stu-id="a4410-113">\<value></span></span>](./value.md)  
|[<span data-ttu-id="a4410-114">\<代碼></span><span class="sxs-lookup"><span data-stu-id="a4410-114">\<code></span></span>](./code.md)|<span data-ttu-id="a4410-115">[\<參數>](./param.md)\*</span><span class="sxs-lookup"><span data-stu-id="a4410-115">[\<param>](./param.md)\*</span></span>|<span data-ttu-id="a4410-116">[\<也看到>](./seealso.md)\*</span><span class="sxs-lookup"><span data-stu-id="a4410-116">[\<seealso>](./seealso.md)\*</span></span>|  
|[<span data-ttu-id="a4410-117">\<示例></span><span class="sxs-lookup"><span data-stu-id="a4410-117">\<example></span></span>](./example.md)|[<span data-ttu-id="a4410-118">\<帕></span><span class="sxs-lookup"><span data-stu-id="a4410-118">\<paramref></span></span>](./paramref.md)|[<span data-ttu-id="a4410-119">\<摘要></span><span class="sxs-lookup"><span data-stu-id="a4410-119">\<summary></span></span>](./summary.md)|  
|<span data-ttu-id="a4410-120">[\<異常>](./exception.md)\*</span><span class="sxs-lookup"><span data-stu-id="a4410-120">[\<exception>](./exception.md)\*</span></span>|<span data-ttu-id="a4410-121">[\<許可權>](./permission.md)\*</span><span class="sxs-lookup"><span data-stu-id="a4410-121">[\<permission>](./permission.md)\*</span></span>|<span data-ttu-id="a4410-122">[\<類型帕拉姆>](./typeparam.md)\*</span><span class="sxs-lookup"><span data-stu-id="a4410-122">[\<typeparam>](./typeparam.md)\*</span></span>|  
|<span data-ttu-id="a4410-123">[\<包括>](./include.md)\*</span><span class="sxs-lookup"><span data-stu-id="a4410-123">[\<include>](./include.md)\*</span></span>|[<span data-ttu-id="a4410-124">\<評論></span><span class="sxs-lookup"><span data-stu-id="a4410-124">\<remarks></span></span>](./remarks.md)|[<span data-ttu-id="a4410-125">\<類型帕阿姆夫></span><span class="sxs-lookup"><span data-stu-id="a4410-125">\<typeparamref></span></span>](./typeparamref.md)|  
|[<span data-ttu-id="a4410-126">\<清單></span><span class="sxs-lookup"><span data-stu-id="a4410-126">\<list></span></span>](./list.md)|[<span data-ttu-id="a4410-127">\<繼承></span><span class="sxs-lookup"><span data-stu-id="a4410-127">\<inheritdoc></span></span>](./inheritdoc.md)|[<span data-ttu-id="a4410-128">\<返回></span><span class="sxs-lookup"><span data-stu-id="a4410-128">\<returns></span></span>](./returns.md)|
  
<span data-ttu-id="a4410-129">（\*表示編譯器驗證語法。</span><span class="sxs-lookup"><span data-stu-id="a4410-129">(\* denotes that the compiler verifies syntax.)</span></span>

<span data-ttu-id="a4410-130">如果您想要讓角括弧出現在文件註解的文字中，請使用 `<` 和 `>` 的 HTML 編碼，其分別為 `&lt;` 和 `&gt;`。</span><span class="sxs-lookup"><span data-stu-id="a4410-130">If you want angle brackets to appear in the text of a documentation comment, use the HTML encoding of `<` and `>` which is `&lt;` and `&gt;` respectively.</span></span> <span data-ttu-id="a4410-131">此編碼顯示在以下示例中。</span><span class="sxs-lookup"><span data-stu-id="a4410-131">This encoding is shown in the following example.</span></span>

```csharp
/// <summary>
/// This property always returns a value &lt; 1.
/// </summary>
```

## <a name="see-also"></a><span data-ttu-id="a4410-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a4410-132">See also</span></span>

- [<span data-ttu-id="a4410-133">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="a4410-133">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="a4410-134">-文檔（C# 編譯器選項）</span><span class="sxs-lookup"><span data-stu-id="a4410-134">-doc (C# compiler options)</span></span>](../../language-reference/compiler-options/doc-compiler-option.md)
- [<span data-ttu-id="a4410-135">XML 文件註解</span><span class="sxs-lookup"><span data-stu-id="a4410-135">XML documentation comments</span></span>](./index.md)
