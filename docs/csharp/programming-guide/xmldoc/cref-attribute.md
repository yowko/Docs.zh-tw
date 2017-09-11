---
title: "cref 屬性 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- cref [C#]
ms.assetid: 66a6b0e5-b961-4504-a461-3a4cf481fc8b
caps.latest.revision: 10
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 7861d6696b7a40b8a665d489b92a3b196a7dd0ce
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="cref-attribute-c-programming-guide"></a><span data-ttu-id="1efaa-102">cref 屬性 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="1efaa-102">cref Attribute (C# Programming Guide)</span></span>
<span data-ttu-id="1efaa-103">`cref` 屬性在 XML 文件標記中表示「程式碼參考」。</span><span class="sxs-lookup"><span data-stu-id="1efaa-103">The `cref` attribute in an XML documentation tag means "code reference."</span></span> <span data-ttu-id="1efaa-104">它會指定標記的內部文字是程式碼項目，例如類型、方法或屬性。</span><span class="sxs-lookup"><span data-stu-id="1efaa-104">It specifies that the inner text of the tag is a code element, such as a type, method, or property.</span></span> <span data-ttu-id="1efaa-105">[Sandcastle](https://github.com/EWSoftware/SHFB) 等文件工具使用 `cref` 屬性自動產生記錄類型或成員的頁面超連結。</span><span class="sxs-lookup"><span data-stu-id="1efaa-105">Documentation tools like [Sandcastle](https://github.com/EWSoftware/SHFB) use the `cref` attributes to automatically generate hyperlinks to the page where the type or member is documented.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1efaa-106">範例</span><span class="sxs-lookup"><span data-stu-id="1efaa-106">Example</span></span>  
 <span data-ttu-id="1efaa-107">下例示範在 [\<see>](../../../csharp/programming-guide/xmldoc/see.md) 標記中使用的 `cref` 屬性。</span><span class="sxs-lookup"><span data-stu-id="1efaa-107">The following example shows `cref` attributes used in [\<see>](../../../csharp/programming-guide/xmldoc/see.md) tags.</span></span>  
  
 <span data-ttu-id="1efaa-108">[!code-cs[csProgGuideDocComments#3](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/cref-attribute_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="1efaa-108">[!code-cs[csProgGuideDocComments#3](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/cref-attribute_1.cs)]</span></span>  
  
 <span data-ttu-id="1efaa-109">編譯時，此程式會產生下列 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="1efaa-109">When compiled, the program produces the following XML file.</span></span> <span data-ttu-id="1efaa-110">請注意，以 `GetZero` 方法的 `cref` 屬性為例，已被編譯器轉換成 `"M:TestNamespace.TestClass.GetZero"`。</span><span class="sxs-lookup"><span data-stu-id="1efaa-110">Notice that the `cref` attribute for the `GetZero` method, for example, has been transformed by the compiler to `"M:TestNamespace.TestClass.GetZero"`.</span></span> <span data-ttu-id="1efaa-111">"M:" 前置詞表示「方法」，而且是能為 Sandcastle 等文件工具識別的慣例。</span><span class="sxs-lookup"><span data-stu-id="1efaa-111">The "M:" prefix means "method" and is a convention that is recognized by documentation tools such as Sandcastle.</span></span> <span data-ttu-id="1efaa-112">如需前置詞的完整清單，請參閱[處理 XML 檔案](../../../csharp/programming-guide/xmldoc/processing-the-xml-file.md)。</span><span class="sxs-lookup"><span data-stu-id="1efaa-112">For a complete list of prefixes, see [Processing the XML File](../../../csharp/programming-guide/xmldoc/processing-the-xml-file.md).</span></span>  
  
```xml  
<?xml version="1.0"?>  
<doc>  
    <assembly>  
        <name>CRefTest</name>  
    </assembly>  
    <members>  
        <member name="T:TestNamespace.TestClass">  
            <summary>  
            TestClass contains cref examples.  
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
    </members>    <members>  
        <member name="T:TestNamespace.TestClass">  
            <summary>  
            TestClass contains two cref examples.  
            </summary>  
        </member>  
        <member name="M:TestNamespace.TestClass.GetZero">  
            <summary>  
            The GetZero method.  
            </summary>  
            <example> This sample shows how to call the <see cref="M:TestNamespace.TestClass.GetZero"/> method.  
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
  
## <a name="see-also"></a><span data-ttu-id="1efaa-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1efaa-113">See Also</span></span>  
 <span data-ttu-id="1efaa-114">[XML 文件註解](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md) </span><span class="sxs-lookup"><span data-stu-id="1efaa-114">[XML Documentation Comments](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md) </span></span>  
 [<span data-ttu-id="1efaa-115">建議使用的文件註解標籤</span><span class="sxs-lookup"><span data-stu-id="1efaa-115">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

