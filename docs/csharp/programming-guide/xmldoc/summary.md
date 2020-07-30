---
title: '<summary> -C # 程式設計指南'
description: 瞭解 XML <summary> 用來描述型別或型別成員的標記。 請參閱程式碼範例，並查看其他可用的資源。
ms.date: 07/20/2015
f1_keywords:
- <summary>
- summary
helpviewer_keywords:
- <summary> C# XML tag
- summary C# XML tag
ms.assetid: b4c43d92-2067-4eac-a59a-d32f5248c08b
ms.openlocfilehash: f9243e598aaf0c12dd48b48045f461b4b307c18f
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87380601"
---
# <a name="summary-c-programming-guide"></a><span data-ttu-id="612d1-105">\<summary>（C # 程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="612d1-105">\<summary> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="612d1-106">語法</span><span class="sxs-lookup"><span data-stu-id="612d1-106">Syntax</span></span>

```xml
<summary>description</summary>
```

## <a name="parameters"></a><span data-ttu-id="612d1-107">參數</span><span class="sxs-lookup"><span data-stu-id="612d1-107">Parameters</span></span>

- `description`

  <span data-ttu-id="612d1-108">物件的摘要。</span><span class="sxs-lookup"><span data-stu-id="612d1-108">A summary of the object.</span></span>

## <a name="remarks"></a><span data-ttu-id="612d1-109">備註</span><span class="sxs-lookup"><span data-stu-id="612d1-109">Remarks</span></span>

<span data-ttu-id="612d1-110">`<summary>`標記應該用來描述類型或類型成員。</span><span class="sxs-lookup"><span data-stu-id="612d1-110">The `<summary>` tag should be used to describe a type or a type member.</span></span> <span data-ttu-id="612d1-111">使用將 [\<remarks>](./remarks.md) 補充資訊加入至類型描述。</span><span class="sxs-lookup"><span data-stu-id="612d1-111">Use [\<remarks>](./remarks.md) to add supplemental information to a type description.</span></span> <span data-ttu-id="612d1-112">使用 [cref 屬性](./cref-attribute.md)，讓 [DocFX](https://dotnet.github.io/docfx/) 和 [Sandcastle](https://github.com/EWSoftware/SHFB) 這類文件工具為程式碼項目建立文件頁面的內部超連結。</span><span class="sxs-lookup"><span data-stu-id="612d1-112">Use the [cref Attribute](./cref-attribute.md) to enable documentation tools such as [DocFX](https://dotnet.github.io/docfx/) and [Sandcastle](https://github.com/EWSoftware/SHFB) to create internal hyperlinks to documentation pages for code elements.</span></span>

<span data-ttu-id="612d1-113">標記的文字 `<summary>` 是 IntelliSense 中類型的唯一資訊來源，也會顯示在 [物件瀏覽器] 視窗中。</span><span class="sxs-lookup"><span data-stu-id="612d1-113">The text for the `<summary>` tag is the only source of information about the type in IntelliSense, and is also displayed in the Object Browser Window.</span></span>

<span data-ttu-id="612d1-114">使用[-doc](../../language-reference/compiler-options/doc-compiler-option.md)進行編譯，以處理檔案的檔批註。</span><span class="sxs-lookup"><span data-stu-id="612d1-114">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span> <span data-ttu-id="612d1-115">若要根據編譯器產生的檔案建立最終檔集，您可以建立自訂工具，或使用[DocFX](https://dotnet.github.io/docfx/)或[sandcastle 這類](https://github.com/EWSoftware/SHFB)等工具。</span><span class="sxs-lookup"><span data-stu-id="612d1-115">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [DocFX](https://dotnet.github.io/docfx/) or [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>

## <a name="example"></a><span data-ttu-id="612d1-116">範例</span><span class="sxs-lookup"><span data-stu-id="612d1-116">Example</span></span>

[!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]

<span data-ttu-id="612d1-117">上述範例會產生下列 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="612d1-117">The previous example produces the following XML file.</span></span>

```xml
<?xml version="1.0"?>
<doc>
    <assembly>
        <name>YourNamespace</name>
    </assembly>
    <members>
        <member name="T:TestClass">
            text for class TestClass
        </member>
        <member name="M:TestClass.DoWork(System.Int32)">
            <summary>DoWork is a method in the TestClass class.
            <para>Here's how you could make a second paragraph in a description. <see cref="M:System.Console.WriteLine(System.String)"/> for information about output statements.</para>
            </summary>
            <seealso cref="M:TestClass.Main"/>
        </member>
        <member name="M:TestClass.Main">
            text for Main
        </member>
    </members>
</doc>
```

## <a name="example"></a><span data-ttu-id="612d1-118">範例</span><span class="sxs-lookup"><span data-stu-id="612d1-118">Example</span></span>

<span data-ttu-id="612d1-119">下列範例示範如何設定泛型型別的 `cref` 參考。</span><span class="sxs-lookup"><span data-stu-id="612d1-119">The following example shows how to make a `cref` reference to a generic type.</span></span>

[!code-csharp[csProgGuideDocComments#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#11)]

<span data-ttu-id="612d1-120">上述範例會產生下列 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="612d1-120">The previous example produces the following XML file.</span></span>

```xml
<?xml version="1.0"?>
<doc>
    <assembly>
        <name>CRefTest</name>
    </assembly>
    <members>
        <member name="T:A">
            <summary cref="T:C`1">
            </summary>
        </member>
        <member name="T:B">
            <summary cref="T:C`1">
            </summary>
        </member>
        <member name="T:C`1">
            <summary cref="T:A">
            </summary>
            <typeparam name="T"></typeparam>
        </member>
    </members>
</doc>
```

## <a name="see-also"></a><span data-ttu-id="612d1-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="612d1-121">See also</span></span>

- [<span data-ttu-id="612d1-122">C# 程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="612d1-122">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="612d1-123">建議使用的文件註解標籤</span><span class="sxs-lookup"><span data-stu-id="612d1-123">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
