---
title: 建議使用的文件註解標籤 - C# 程式設計指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
ms.openlocfilehash: d17ff0b78d8ae40916447e8e12da7948a21e5717
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523364"
---
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a><span data-ttu-id="32480-102">建議使用的文件註解標籤 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="32480-102">Recommended Tags for Documentation Comments (C# Programming Guide)</span></span>
<span data-ttu-id="32480-103">C# 編譯器會處理程式碼中的文件註解，並將其在 **/doc** 命令列選項中指定其名稱的檔案中格式化為 XML。</span><span class="sxs-lookup"><span data-stu-id="32480-103">The C# compiler processes documentation comments in your code and formats them as XML in a file whose name you specify in the **/doc** command-line option.</span></span> <span data-ttu-id="32480-104">若要依據編譯器產生的檔案來建立最終文件，您可以建立自訂工具，或者是使用 [DocFX](https://dotnet.github.io/docfx/) 或 [Sandcastle](https://github.com/EWSoftware/SHFB)這類工具。</span><span class="sxs-lookup"><span data-stu-id="32480-104">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [DocFX](https://dotnet.github.io/docfx/) or [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>  
  
 <span data-ttu-id="32480-105">標記是在類型和類型成員這類程式碼建構上處理。</span><span class="sxs-lookup"><span data-stu-id="32480-105">Tags are processed on code constructs such as types and type members.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="32480-106">文件註解不能套用至命名空間。</span><span class="sxs-lookup"><span data-stu-id="32480-106">Documentation comments cannot be applied to a namespace.</span></span>  
  
 <span data-ttu-id="32480-107">編譯器會處理任何為有效 XML 的標記。</span><span class="sxs-lookup"><span data-stu-id="32480-107">The compiler will process any tag that is valid XML.</span></span> <span data-ttu-id="32480-108">下列標記提供使用者文件中的常用功能。</span><span class="sxs-lookup"><span data-stu-id="32480-108">The following tags provide generally used functionality in user documentation.</span></span>  
  
## <a name="tags"></a><span data-ttu-id="32480-109">Tags</span><span class="sxs-lookup"><span data-stu-id="32480-109">Tags</span></span>  
  
||||  
|---|---|---|  
|[<span data-ttu-id="32480-110">\<c></span><span class="sxs-lookup"><span data-stu-id="32480-110">\<c></span></span>](./code-inline.md)|[<span data-ttu-id="32480-111">\<para></span><span class="sxs-lookup"><span data-stu-id="32480-111">\<para></span></span>](./para.md)|<span data-ttu-id="32480-112">[\<see>](./see.md)\*</span><span class="sxs-lookup"><span data-stu-id="32480-112">[\<see>](./see.md)\*</span></span>|  
|[<span data-ttu-id="32480-113">\<code></span><span class="sxs-lookup"><span data-stu-id="32480-113">\<code></span></span>](./code.md)|<span data-ttu-id="32480-114">[\<param>](./param.md)\*</span><span class="sxs-lookup"><span data-stu-id="32480-114">[\<param>](./param.md)\*</span></span>|<span data-ttu-id="32480-115">[\<seealso>](./seealso.md)\*</span><span class="sxs-lookup"><span data-stu-id="32480-115">[\<seealso>](./seealso.md)\*</span></span>|  
|[<span data-ttu-id="32480-116">\<example></span><span class="sxs-lookup"><span data-stu-id="32480-116">\<example></span></span>](./example.md)|[<span data-ttu-id="32480-117">\<paramref></span><span class="sxs-lookup"><span data-stu-id="32480-117">\<paramref></span></span>](./paramref.md)|[<span data-ttu-id="32480-118">\<summary></span><span class="sxs-lookup"><span data-stu-id="32480-118">\<summary></span></span>](./summary.md)|  
|<span data-ttu-id="32480-119">[\<exception>](./exception.md)\*</span><span class="sxs-lookup"><span data-stu-id="32480-119">[\<exception>](./exception.md)\*</span></span>|<span data-ttu-id="32480-120">[\<permission>](./permission.md)\*</span><span class="sxs-lookup"><span data-stu-id="32480-120">[\<permission>](./permission.md)\*</span></span>|<span data-ttu-id="32480-121">[\<typeparam>](./typeparam.md)\*</span><span class="sxs-lookup"><span data-stu-id="32480-121">[\<typeparam>](./typeparam.md)\*</span></span>|  
|<span data-ttu-id="32480-122">[\<include>](./include.md)\*</span><span class="sxs-lookup"><span data-stu-id="32480-122">[\<include>](./include.md)\*</span></span>|[<span data-ttu-id="32480-123">\<remarks></span><span class="sxs-lookup"><span data-stu-id="32480-123">\<remarks></span></span>](./remarks.md)|[<span data-ttu-id="32480-124">\<typeparamref></span><span class="sxs-lookup"><span data-stu-id="32480-124">\<typeparamref></span></span>](./typeparamref.md)|  
|[<span data-ttu-id="32480-125">\<list></span><span class="sxs-lookup"><span data-stu-id="32480-125">\<list></span></span>](./list.md)|[<span data-ttu-id="32480-126">\<returns></span><span class="sxs-lookup"><span data-stu-id="32480-126">\<returns></span></span>](./returns.md)|[<span data-ttu-id="32480-127">\<value></span><span class="sxs-lookup"><span data-stu-id="32480-127">\<value></span></span>](./value.md)|  
  
 <span data-ttu-id="32480-128">(\* 表示編譯器會驗證語法。)</span><span class="sxs-lookup"><span data-stu-id="32480-128">(\* denotes that the compiler verifies syntax.)</span></span>  
  
 <span data-ttu-id="32480-129">如果您想要讓角括弧出現在文件註解的文字中，請使用 `<` 和 `>` 的 HTML 編碼，其分別為 `&lt;` 和 `&gt;`。</span><span class="sxs-lookup"><span data-stu-id="32480-129">If you want angle brackets to appear in the text of a documentation comment, use the HTML encoding of `<` and `>` which is `&lt;` and `&gt;` respectively.</span></span> <span data-ttu-id="32480-130">此編碼已顯示於下列範例中：</span><span class="sxs-lookup"><span data-stu-id="32480-130">This encoding is shown in the following example:</span></span>
  
```csharp  
/// <summary>
/// This property always returns a value &lt; 1.
/// </summary>
```
  
## <a name="see-also"></a><span data-ttu-id="32480-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="32480-131">See also</span></span>

- [<span data-ttu-id="32480-132">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="32480-132">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="32480-133">-doc (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="32480-133">-doc (C# Compiler Options)</span></span>](../../language-reference/compiler-options/doc-compiler-option.md)
- [<span data-ttu-id="32480-134">XML 文件註解</span><span class="sxs-lookup"><span data-stu-id="32480-134">XML Documentation Comments</span></span>](./index.md)
