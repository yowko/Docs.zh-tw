---
title: 建議使用的文件註解標籤 - C# 程式設計指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
ms.openlocfilehash: 963be5273389ebbdb3458d41b0658de0d94bb2cd
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634802"
---
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a><span data-ttu-id="47631-102">建議使用的文件註解標籤 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="47631-102">Recommended Tags for Documentation Comments (C# Programming Guide)</span></span>
<span data-ttu-id="47631-103">C# 編譯器會處理程式碼中的文件註解，並將其在 **/doc** 命令列選項中指定其名稱的檔案中格式化為 XML。</span><span class="sxs-lookup"><span data-stu-id="47631-103">The C# compiler processes documentation comments in your code and formats them as XML in a file whose name you specify in the **/doc** command-line option.</span></span> <span data-ttu-id="47631-104">若要依據編譯器產生的檔案來建立最終文件，您可以建立自訂工具，或者是使用 [DocFX](https://dotnet.github.io/docfx/) 或 [Sandcastle](https://github.com/EWSoftware/SHFB)這類工具。</span><span class="sxs-lookup"><span data-stu-id="47631-104">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [DocFX](https://dotnet.github.io/docfx/) or [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>  
  
 <span data-ttu-id="47631-105">標記是在類型和類型成員這類程式碼建構上處理。</span><span class="sxs-lookup"><span data-stu-id="47631-105">Tags are processed on code constructs such as types and type members.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="47631-106">文件註解不能套用至命名空間。</span><span class="sxs-lookup"><span data-stu-id="47631-106">Documentation comments cannot be applied to a namespace.</span></span>  
  
 <span data-ttu-id="47631-107">編譯器會處理任何為有效 XML 的標記。</span><span class="sxs-lookup"><span data-stu-id="47631-107">The compiler will process any tag that is valid XML.</span></span> <span data-ttu-id="47631-108">下列標記提供使用者文件中的常用功能。</span><span class="sxs-lookup"><span data-stu-id="47631-108">The following tags provide generally used functionality in user documentation.</span></span>  
  
## <a name="tags"></a><span data-ttu-id="47631-109">Tags</span><span class="sxs-lookup"><span data-stu-id="47631-109">Tags</span></span>  
  
||||  
|---|---|---|  
|[<span data-ttu-id="47631-110">\<c></span><span class="sxs-lookup"><span data-stu-id="47631-110">\<c></span></span>](../../../csharp/programming-guide/xmldoc/code-inline.md)|[<span data-ttu-id="47631-111">\<para></span><span class="sxs-lookup"><span data-stu-id="47631-111">\<para></span></span>](../../../csharp/programming-guide/xmldoc/para.md)|<span data-ttu-id="47631-112">[\<see>](../../../csharp/programming-guide/xmldoc/see.md)\*</span><span class="sxs-lookup"><span data-stu-id="47631-112">[\<see>](../../../csharp/programming-guide/xmldoc/see.md)\*</span></span>|  
|[<span data-ttu-id="47631-113">\<code></span><span class="sxs-lookup"><span data-stu-id="47631-113">\<code></span></span>](../../../csharp/programming-guide/xmldoc/code.md)|<span data-ttu-id="47631-114">[\<param>](../../../csharp/programming-guide/xmldoc/param.md)\*</span><span class="sxs-lookup"><span data-stu-id="47631-114">[\<param>](../../../csharp/programming-guide/xmldoc/param.md)\*</span></span>|<span data-ttu-id="47631-115">[\<seealso>](../../../csharp/programming-guide/xmldoc/seealso.md)\*</span><span class="sxs-lookup"><span data-stu-id="47631-115">[\<seealso>](../../../csharp/programming-guide/xmldoc/seealso.md)\*</span></span>|  
|[<span data-ttu-id="47631-116">\<example></span><span class="sxs-lookup"><span data-stu-id="47631-116">\<example></span></span>](../../../csharp/programming-guide/xmldoc/example.md)|[<span data-ttu-id="47631-117">\<paramref></span><span class="sxs-lookup"><span data-stu-id="47631-117">\<paramref></span></span>](../../../csharp/programming-guide/xmldoc/paramref.md)|[<span data-ttu-id="47631-118">\<summary></span><span class="sxs-lookup"><span data-stu-id="47631-118">\<summary></span></span>](../../../csharp/programming-guide/xmldoc/summary.md)|  
|<span data-ttu-id="47631-119">[\<exception>](../../../csharp/programming-guide/xmldoc/exception.md)\*</span><span class="sxs-lookup"><span data-stu-id="47631-119">[\<exception>](../../../csharp/programming-guide/xmldoc/exception.md)\*</span></span>|<span data-ttu-id="47631-120">[\<permission>](../../../csharp/programming-guide/xmldoc/permission.md)\*</span><span class="sxs-lookup"><span data-stu-id="47631-120">[\<permission>](../../../csharp/programming-guide/xmldoc/permission.md)\*</span></span>|<span data-ttu-id="47631-121">[\<typeparam>](../../../csharp/programming-guide/xmldoc/typeparam.md)\*</span><span class="sxs-lookup"><span data-stu-id="47631-121">[\<typeparam>](../../../csharp/programming-guide/xmldoc/typeparam.md)\*</span></span>|  
|<span data-ttu-id="47631-122">[\<include>](../../../csharp/programming-guide/xmldoc/include.md)\*</span><span class="sxs-lookup"><span data-stu-id="47631-122">[\<include>](../../../csharp/programming-guide/xmldoc/include.md)\*</span></span>|[<span data-ttu-id="47631-123">\<remarks></span><span class="sxs-lookup"><span data-stu-id="47631-123">\<remarks></span></span>](../../../csharp/programming-guide/xmldoc/remarks.md)|[<span data-ttu-id="47631-124">\<typeparamref></span><span class="sxs-lookup"><span data-stu-id="47631-124">\<typeparamref></span></span>](../../../csharp/programming-guide/xmldoc/typeparamref.md)|  
|[<span data-ttu-id="47631-125">\<list></span><span class="sxs-lookup"><span data-stu-id="47631-125">\<list></span></span>](../../../csharp/programming-guide/xmldoc/list.md)|[<span data-ttu-id="47631-126">\<returns></span><span class="sxs-lookup"><span data-stu-id="47631-126">\<returns></span></span>](../../../csharp/programming-guide/xmldoc/returns.md)|[<span data-ttu-id="47631-127">\<value></span><span class="sxs-lookup"><span data-stu-id="47631-127">\<value></span></span>](../../../csharp/programming-guide/xmldoc/value.md)|  
  
 <span data-ttu-id="47631-128">(\* 表示編譯器會驗證語法。)</span><span class="sxs-lookup"><span data-stu-id="47631-128">(\* denotes that the compiler verifies syntax.)</span></span>  
  
 <span data-ttu-id="47631-129">如果您想要括弧出現在文件註解文字中，請使用 `<` 和 `>`，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="47631-129">If you want angle brackets to appear in the text of a documentation comment, use `<` and `>`, as shown in the following example.</span></span>  
  
```csharp  
/// <summary cref="C < T >">  
/// </summary>  
```  
  
## <a name="see-also"></a><span data-ttu-id="47631-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="47631-130">See also</span></span>

- [<span data-ttu-id="47631-131">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="47631-131">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="47631-132">/doc (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="47631-132">/doc (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)
- [<span data-ttu-id="47631-133">XML 文件註解</span><span class="sxs-lookup"><span data-stu-id="47631-133">XML Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/index.md)
