---
title: <include> - C#程式設計指南
ms.date: 07/20/2015
f1_keywords:
- include
- <include>
helpviewer_keywords:
- <include> C# XML tag
- include C# XML tag
ms.assetid: a8a70302-6196-4643-bd09-ef33f411f18f
ms.openlocfilehash: 1e3722cbed02775d0ad4f392840ea10275c96be1
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793422"
---
# <a name="include-c-programming-guide"></a><span data-ttu-id="61d7c-102">\<包含 > （C#程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="61d7c-102">\<include> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="61d7c-103">語法</span><span class="sxs-lookup"><span data-stu-id="61d7c-103">Syntax</span></span>

```xml
<include file='filename' path='tagpath[@name="id"]' />
```

## <a name="parameters"></a><span data-ttu-id="61d7c-104">參數</span><span class="sxs-lookup"><span data-stu-id="61d7c-104">Parameters</span></span>

- `filename`

  <span data-ttu-id="61d7c-105">包含文件的 XML 檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="61d7c-105">The name of the XML file containing the documentation.</span></span> <span data-ttu-id="61d7c-106">檔案名稱可以採用的原始程式碼檔的相對路徑。</span><span class="sxs-lookup"><span data-stu-id="61d7c-106">The file name can be qualified with a path relative to the source code file.</span></span> <span data-ttu-id="61d7c-107">請將 `filename` 括在單引號 (' ') 內。</span><span class="sxs-lookup"><span data-stu-id="61d7c-107">Enclose `filename` in single quotation marks (' ').</span></span>

- `tagpath`

  <span data-ttu-id="61d7c-108">`filename` 中導致 `name` 標記的標記路徑。</span><span class="sxs-lookup"><span data-stu-id="61d7c-108">The path of the tags in `filename` that leads to the tag `name`.</span></span> <span data-ttu-id="61d7c-109">請將路徑括在單引號 (' ') 內。</span><span class="sxs-lookup"><span data-stu-id="61d7c-109">Enclose the path in single quotation marks (' ').</span></span>

- `name`

  <span data-ttu-id="61d7c-110">標記中位在註解前面的名稱規範；`name` 會有 `id`。</span><span class="sxs-lookup"><span data-stu-id="61d7c-110">The name specifier in the tag that precedes the comments; `name` will have an `id`.</span></span>

- `id`

<span data-ttu-id="61d7c-111">位在註解前面的標記識別碼。</span><span class="sxs-lookup"><span data-stu-id="61d7c-111">The ID for the tag that precedes the comments.</span></span> <span data-ttu-id="61d7c-112">請將識別碼括在雙引號 (" ") 內。</span><span class="sxs-lookup"><span data-stu-id="61d7c-112">Enclose the ID in double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="61d7c-113">備註</span><span class="sxs-lookup"><span data-stu-id="61d7c-113">Remarks</span></span>

<span data-ttu-id="61d7c-114">\<include> 標記可讓您參考另一個檔案中描述原始程式碼中類型和成員的註解。</span><span class="sxs-lookup"><span data-stu-id="61d7c-114">The \<include> tag lets you refer to comments in another file that describe the types and members in your source code.</span></span> <span data-ttu-id="61d7c-115">這是將文件註解直接放在原始程式碼檔中的替代方案。</span><span class="sxs-lookup"><span data-stu-id="61d7c-115">This is an alternative to placing documentation comments directly in your source code file.</span></span> <span data-ttu-id="61d7c-116">將文件放入個別檔案，即可將原始檔控制套用至與原始程式碼不同的文件。</span><span class="sxs-lookup"><span data-stu-id="61d7c-116">By putting the documentation in a separate file, you can apply source control to the documentation separately from the source code.</span></span> <span data-ttu-id="61d7c-117">一個人可以簽出原始程式碼檔，而且其他人可以簽出文件檔。</span><span class="sxs-lookup"><span data-stu-id="61d7c-117">One person can have the source code file checked out and someone else can have the documentation file checked out.</span></span>

<span data-ttu-id="61d7c-118">\<include> 標記使用 XML XPath 語法。</span><span class="sxs-lookup"><span data-stu-id="61d7c-118">The \<include> tag uses the XML XPath syntax.</span></span> <span data-ttu-id="61d7c-119">如需自訂 \<include> 用法的方式，請參閱 XPath 文件。</span><span class="sxs-lookup"><span data-stu-id="61d7c-119">Refer to XPath documentation for ways to customize your \<include> use.</span></span>

## <a name="example"></a><span data-ttu-id="61d7c-120">範例</span><span class="sxs-lookup"><span data-stu-id="61d7c-120">Example</span></span>

<span data-ttu-id="61d7c-121">這是多檔案範例。</span><span class="sxs-lookup"><span data-stu-id="61d7c-121">This is a multifile example.</span></span> <span data-ttu-id="61d7c-122">以下是第一個使用 \<包含 > 的檔案。</span><span class="sxs-lookup"><span data-stu-id="61d7c-122">The following is the first file, which uses \<include>.</span></span>

[!code-csharp[csProgGuideDocComments#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#5)]

<span data-ttu-id="61d7c-123">第二個檔案（ *xml_include_tag .doc*）包含下列檔批註。</span><span class="sxs-lookup"><span data-stu-id="61d7c-123">The second file, *xml_include_tag.doc*, contains the following documentation comments.</span></span>

```xml
<MyDocs>

<MyMembers name="test">
<summary>
The summary for this type.
</summary>
</MyMembers>

<MyMembers name="test2">
<summary>
The summary for this other type.
</summary>
</MyMembers>

</MyDocs>
```

## <a name="program-output"></a><span data-ttu-id="61d7c-124">程式輸出</span><span class="sxs-lookup"><span data-stu-id="61d7c-124">Program output</span></span>

<span data-ttu-id="61d7c-125">當您使用下列命令列編譯 Test 和 Test2 類別時，會產生下列輸出：`-doc:DocFileName.xml.`。在 Visual Studio 中，您可以在專案設計工具的 [建置] 窗格中指定 XML 文件註解選項。</span><span class="sxs-lookup"><span data-stu-id="61d7c-125">The following output is generated when you compile the Test and Test2 classes with the following command line: `-doc:DocFileName.xml.` In Visual Studio, you specify the XML doc comments option in the Build pane of the Project Designer.</span></span> <span data-ttu-id="61d7c-126">當 C# 編譯器看到 \<include> 標記時，會搜尋 xml_include_tag.doc 中的文件註解，而不是目前的原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="61d7c-126">When the C# compiler sees the \<include> tag, it will search for documentation comments in xml_include_tag.doc instead of the current source file.</span></span> <span data-ttu-id="61d7c-127">編譯器接著會產生 DocFileName.xml，這是 [DocFX](https://dotnet.github.io/docfx/) 和 [Sandcastle](https://github.com/EWSoftware/SHFB) 這類文件工具用來產生最終文件的檔案。</span><span class="sxs-lookup"><span data-stu-id="61d7c-127">The compiler then generates DocFileName.xml, and this is the file that is consumed by documentation tools such as [DocFX](https://dotnet.github.io/docfx/) and [Sandcastle](https://github.com/EWSoftware/SHFB) to produce the final documentation.</span></span>  
  
```xml
<?xml version="1.0"?>
<doc>
    <assembly>
        <name>xml_include_tag</name>
    </assembly>
    <members>
        <member name="T:Test">
            <summary>
The summary for this type.   
</summary>   
        </member>   
        <member name="T:Test2">   
            <summary>   
The summary for this other type.   
</summary>   
        </member>   
    </members>   
</doc>   
```  
  
## <a name="see-also"></a><span data-ttu-id="61d7c-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="61d7c-128">See also</span></span>

- [<span data-ttu-id="61d7c-129">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="61d7c-129">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="61d7c-130">建議使用的文件註解標籤</span><span class="sxs-lookup"><span data-stu-id="61d7c-130">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
