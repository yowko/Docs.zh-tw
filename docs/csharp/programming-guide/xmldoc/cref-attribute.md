---
title: 'cref 屬性-c # 程式設計指南'
description: 瞭解 cref 屬性。 Cref 屬性工作表示「程式碼參考」，而且會指定標記的內部文字是 code 元素。
ms.date: 07/20/2015
helpviewer_keywords:
- cref [C#]
ms.assetid: 66a6b0e5-b961-4504-a461-3a4cf481fc8b
ms.openlocfilehash: 31fa1a3f182d7b72a1dfbe1ce47386f87fbbff75
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381992"
---
# <a name="cref-attribute-c-programming-guide"></a><span data-ttu-id="de3af-104">cref 屬性（c # 程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="de3af-104">cref attribute (C# programming guide)</span></span>

<span data-ttu-id="de3af-105">`cref` 屬性在 XML 文件標記中表示「程式碼參考」。</span><span class="sxs-lookup"><span data-stu-id="de3af-105">The `cref` attribute in an XML documentation tag means "code reference."</span></span> <span data-ttu-id="de3af-106">它會指定標記的內部文字是程式碼項目，例如類型、方法或屬性。</span><span class="sxs-lookup"><span data-stu-id="de3af-106">It specifies that the inner text of the tag is a code element, such as a type, method, or property.</span></span> <span data-ttu-id="de3af-107">[DocFX](https://dotnet.github.io/docfx/) 和 [Sandcastle](https://github.com/EWSoftware/SHFB) 這類文件工具使用 `cref` 屬性自動產生記錄類型或成員的頁面超連結。</span><span class="sxs-lookup"><span data-stu-id="de3af-107">Documentation tools like [DocFX](https://dotnet.github.io/docfx/) and [Sandcastle](https://github.com/EWSoftware/SHFB) use the `cref` attributes to automatically generate hyperlinks to the page where the type or member is documented.</span></span>

## <a name="example"></a><span data-ttu-id="de3af-108">範例</span><span class="sxs-lookup"><span data-stu-id="de3af-108">Example</span></span>

<span data-ttu-id="de3af-109">下列範例顯示 `cref` 標記中使用的 [\<see>](./see.md) 屬性。</span><span class="sxs-lookup"><span data-stu-id="de3af-109">The following example shows `cref` attributes used in [\<see>](./see.md) tags.</span></span>

[!code-csharp[csProgGuideDocComments#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#3)]

<span data-ttu-id="de3af-110">編譯時，此程式會產生下列 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="de3af-110">When compiled, the program produces the following XML file.</span></span> <span data-ttu-id="de3af-111">請注意，以 `GetZero` 方法的 `cref` 屬性為例，已被編譯器轉換成 `"M:TestNamespace.TestClass.GetZero"`。</span><span class="sxs-lookup"><span data-stu-id="de3af-111">Notice that the `cref` attribute for the `GetZero` method, for example, has been transformed by the compiler to `"M:TestNamespace.TestClass.GetZero"`.</span></span> <span data-ttu-id="de3af-112">"M:" 前置詞表示「方法」，而且是能為 DocFX 和 Sandcastle 這類文件工具識別的慣例。</span><span class="sxs-lookup"><span data-stu-id="de3af-112">The "M:" prefix means "method" and is a convention that is recognized by documentation tools such as DocFX and Sandcastle.</span></span> <span data-ttu-id="de3af-113">如需前置詞的完整清單，請參閱[處理 XML 檔案](./processing-the-xml-file.md)。</span><span class="sxs-lookup"><span data-stu-id="de3af-113">For a complete list of prefixes, see [Processing the XML File](./processing-the-xml-file.md).</span></span>

```xml  
<?xml version="1.0"?>
<doc>
    <assembly>
        <name>CRefTest</name>
    </assembly>
    <members>
        <member name="T:TestNamespace.TestClass">
            <summary>
            TestClass contains several cref examples.
            </summary>
        </member>
        <member name="M:TestNamespace.TestClass.#ctor">
            <summary>
            This sample shows how to specify the <see cref="T:TestNamespace.TestClass"/> constructor as a cref attribute.
            </summary>
        </member>
        <member name="M:TestNamespace.TestClass.#ctor(System.Int32)">
            <summary>
            This sample shows how to specify the <see cref="M:TestNamespace.TestClass.#ctor(System.Int32)"/> constructor as a cref attribute.
            </summary>
        </member>
        <member name="M:TestNamespace.TestClass.GetZero">
            <summary>
            The GetZero method.
            </summary>
            <example>
            This sample shows how to call the <see cref="M:TestNamespace.TestClass.GetZero"/> method.
            <code>
            class TestClass
            {
                static int Main()
                {
                    return GetZero();
                }
            }
            </code>
            </example>
        </member>
        <member name="M:TestNamespace.TestClass.GetGenericValue``1(``0)">
            <summary>
            The GetGenericValue method.
            </summary>
            <remarks>
            This sample shows how to specify the <see cref="M:TestNamespace.TestClass.GetGenericValue``1(``0)"/> method as a cref attribute.
            </remarks>
        </member>
        <member name="T:TestNamespace.GenericClass`1">
            <summary>
            GenericClass.
            </summary>
            <remarks>
            This example shows how to specify the <see cref="T:TestNamespace.GenericClass`1"/> type as a cref attribute.
            </remarks>
        </member>
    </members>
</doc>
```

## <a name="see-also"></a><span data-ttu-id="de3af-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="de3af-114">See also</span></span>

- [<span data-ttu-id="de3af-115">XML 文件註解</span><span class="sxs-lookup"><span data-stu-id="de3af-115">XML documentation comments</span></span>](./index.md)
- [<span data-ttu-id="de3af-116">建議使用的文件註解標籤</span><span class="sxs-lookup"><span data-stu-id="de3af-116">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
