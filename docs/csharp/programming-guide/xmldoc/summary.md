---
title: <summary> - C# 程式設計指南
ms.date: 07/20/2015
f1_keywords:
- <summary>
- summary
helpviewer_keywords:
- <summary> C# XML tag
- summary C# XML tag
ms.assetid: b4c43d92-2067-4eac-a59a-d32f5248c08b
ms.openlocfilehash: 1ae3c17bef69a52b4d5852e09284929dc328bf8a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789665"
---
# <a name="summary-c-programming-guide"></a><span data-ttu-id="157d7-102">\<摘要>（C# 程式設計指南）</span><span class="sxs-lookup"><span data-stu-id="157d7-102">\<summary> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="157d7-103">語法</span><span class="sxs-lookup"><span data-stu-id="157d7-103">Syntax</span></span>

```xml
<summary>description</summary>
```

## <a name="parameters"></a><span data-ttu-id="157d7-104">參數</span><span class="sxs-lookup"><span data-stu-id="157d7-104">Parameters</span></span>

- `description`

  <span data-ttu-id="157d7-105">物件的摘要。</span><span class="sxs-lookup"><span data-stu-id="157d7-105">A summary of the object.</span></span>

## <a name="remarks"></a><span data-ttu-id="157d7-106">備註</span><span class="sxs-lookup"><span data-stu-id="157d7-106">Remarks</span></span>

<span data-ttu-id="157d7-107">\<summary> 標記應該用來描述類型或類型成員。</span><span class="sxs-lookup"><span data-stu-id="157d7-107">The \<summary> tag should be used to describe a type or a type member.</span></span> <span data-ttu-id="157d7-108">使用[\<備註>](./remarks.md)向類型說明添加補充資訊。</span><span class="sxs-lookup"><span data-stu-id="157d7-108">Use [\<remarks>](./remarks.md) to add supplemental information to a type description.</span></span> <span data-ttu-id="157d7-109">使用 [cref 屬性](./cref-attribute.md)，讓 [DocFX](https://dotnet.github.io/docfx/) 和 [Sandcastle](https://github.com/EWSoftware/SHFB) 這類文件工具為程式碼項目建立文件頁面的內部超連結。</span><span class="sxs-lookup"><span data-stu-id="157d7-109">Use the [cref Attribute](./cref-attribute.md) to enable documentation tools such as [DocFX](https://dotnet.github.io/docfx/) and [Sandcastle](https://github.com/EWSoftware/SHFB) to create internal hyperlinks to documentation pages for code elements.</span></span>

<span data-ttu-id="157d7-110">\<summary> 標記的文字是 IntelliSense 中類型的唯一資訊來源，也會顯示在 [物件瀏覽器] 視窗中。</span><span class="sxs-lookup"><span data-stu-id="157d7-110">The text for the \<summary> tag is the only source of information about the type in IntelliSense, and is also displayed in the Object Browser Window.</span></span>

<span data-ttu-id="157d7-111">使用[-doc](../../language-reference/compiler-options/doc-compiler-option.md)編譯，以處理檔的文檔注釋。</span><span class="sxs-lookup"><span data-stu-id="157d7-111">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span> <span data-ttu-id="157d7-112">要基於編譯器生成的檔創建最終文檔，您可以創建自訂工具，或使用[DocFX](https://dotnet.github.io/docfx/)或[Sandcastle](https://github.com/EWSoftware/SHFB)等工具。</span><span class="sxs-lookup"><span data-stu-id="157d7-112">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [DocFX](https://dotnet.github.io/docfx/) or [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>

## <a name="example"></a><span data-ttu-id="157d7-113">範例</span><span class="sxs-lookup"><span data-stu-id="157d7-113">Example</span></span>

[!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]

<span data-ttu-id="157d7-114">上述範例會產生下列 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="157d7-114">The previous example produces the following XML file.</span></span>

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
            <seealso cref="M:TestClass.Main"/>
            </summary>
        </member>
        <member name="M:TestClass.Main">
            text for Main
        </member>
    </members>
</doc>
```

## <a name="example"></a><span data-ttu-id="157d7-115">範例</span><span class="sxs-lookup"><span data-stu-id="157d7-115">Example</span></span>

<span data-ttu-id="157d7-116">下列範例示範如何設定泛型型別的 `cref` 參考。</span><span class="sxs-lookup"><span data-stu-id="157d7-116">The following example shows how to make a `cref` reference to a generic type.</span></span>

[!code-csharp[csProgGuideDocComments#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#11)]

<span data-ttu-id="157d7-117">上述範例會產生下列 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="157d7-117">The previous example produces the following XML file.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="157d7-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="157d7-118">See also</span></span>

- [<span data-ttu-id="157d7-119">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="157d7-119">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="157d7-120">建議使用的文件註解標籤</span><span class="sxs-lookup"><span data-stu-id="157d7-120">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
