---
title: '&lt;summary&gt; - C# 程式設計指南'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- <summary>
- summary
helpviewer_keywords:
- <summary> C# XML tag
- summary C# XML tag
ms.assetid: b4c43d92-2067-4eac-a59a-d32f5248c08b
ms.openlocfilehash: 5447b9ea129c26fdbb9effe1a3aeac6d7290764a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54740030"
---
# <a name="ltsummarygt-c-programming-guide"></a><span data-ttu-id="51a9c-102">&lt;summary&gt; (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="51a9c-102">&lt;summary&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="51a9c-103">語法</span><span class="sxs-lookup"><span data-stu-id="51a9c-103">Syntax</span></span>  
  
```xml  
<summary>description</summary>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="51a9c-104">參數</span><span class="sxs-lookup"><span data-stu-id="51a9c-104">Parameters</span></span>  
 `description`  
 <span data-ttu-id="51a9c-105">物件的摘要。</span><span class="sxs-lookup"><span data-stu-id="51a9c-105">A summary of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="51a9c-106">備註</span><span class="sxs-lookup"><span data-stu-id="51a9c-106">Remarks</span></span>  
 <span data-ttu-id="51a9c-107">\<summary> 標記應該用來描述類型或類型成員。</span><span class="sxs-lookup"><span data-stu-id="51a9c-107">The \<summary> tag should be used to describe a type or a type member.</span></span> <span data-ttu-id="51a9c-108">使用 [\<remarks>](../../../csharp/programming-guide/xmldoc/remarks.md) 新增類型描述的補充資訊。</span><span class="sxs-lookup"><span data-stu-id="51a9c-108">Use [\<remarks>](../../../csharp/programming-guide/xmldoc/remarks.md) to add supplemental information to a type description.</span></span> <span data-ttu-id="51a9c-109">使用 [cref 屬性](../../../csharp/programming-guide/xmldoc/cref-attribute.md)，讓 [Sandcastle](https://github.com/EWSoftware/SHFB) 這類文件工具建立程式碼項目之文件頁面的內部超連結。</span><span class="sxs-lookup"><span data-stu-id="51a9c-109">Use the [cref Attribute](../../../csharp/programming-guide/xmldoc/cref-attribute.md) to enable documentation tools such as [Sandcastle](https://github.com/EWSoftware/SHFB) to create internal hyperlinks to documentation pages for code elements.</span></span>  
  
 <span data-ttu-id="51a9c-110">\<summary> 標記的文字是 IntelliSense 中類型的唯一資訊來源，也會顯示在 [物件瀏覽器] 視窗中。</span><span class="sxs-lookup"><span data-stu-id="51a9c-110">The text for the \<summary> tag is the only source of information about the type in IntelliSense, and is also displayed in the Object Browser Window.</span></span>  
  
 <span data-ttu-id="51a9c-111">編譯搭配 [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) 可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="51a9c-111">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span> <span data-ttu-id="51a9c-112">若要依據編譯器產生的檔案來建立最終文件，您可以建立自訂工具，或者是使用 [Sandcastle](https://github.com/EWSoftware/SHFB) 這類工具。</span><span class="sxs-lookup"><span data-stu-id="51a9c-112">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>  
  
## <a name="example"></a><span data-ttu-id="51a9c-113">範例</span><span class="sxs-lookup"><span data-stu-id="51a9c-113">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#12](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/summary_1.cs)]  
  
 <span data-ttu-id="51a9c-114">上述範例會產生下列 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="51a9c-114">The previous example produces the following XML file.</span></span>  
  
```xml  
<?xml version="1.0"?>  
<doc>  
    <assembly>  
        <name>YourNamespace</name>  
    </assembly>  
    <members>  
        <member name="T:DotNetEvents.TestClass">  
            text for class TestClass  
        </member>  
        <member name="M:DotNetEvents.TestClass.DoWork(System.Int32)">  
            <summary>DoWork is a method in the TestClass class.  
            <para>Here's how you could make a second paragraph in a description. <see cref="M:System.Console.WriteLine(System.String)"/> for information about output statements.</para>  
            <seealso cref="M:DotNetEvents.TestClass.Main"/>  
            </summary>  
        </member>  
        <member name="M:DotNetEvents.TestClass.Main">  
            text for Main  
        </member>  
    </members>  
</doc>  
```  
  
## <a name="example"></a><span data-ttu-id="51a9c-115">範例</span><span class="sxs-lookup"><span data-stu-id="51a9c-115">Example</span></span>  
 <span data-ttu-id="51a9c-116">下列範例示範如何設定泛型型別的 `cref` 參考。</span><span class="sxs-lookup"><span data-stu-id="51a9c-116">The following example shows how to make a `cref` reference to a generic type.</span></span>  
  
 [!code-csharp[csProgGuideDocComments#11](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/summary_2.cs)]  
  
 <span data-ttu-id="51a9c-117">上述範例會產生下列 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="51a9c-117">The previous example produces the following XML file.</span></span>  
  
```xml  
<?xml version="1.0"?>  
<doc>  
    <assembly>  
        <name>YourNamespace</name>  
    </assembly>  
    <members>  
        <member name="T:ExtensionMethodsDemo1.A">  
            <summary cref="T:ExtensionMethodsDemo1.C`1">  
            </summary>  
        </member>  
        <member name="T:ExtensionMethodsDemo1.B">  
            <summary cref="T:C`1">  
            </summary>  
        </member>  
        <member name="T:ExtensionMethodsDemo1.C`1">  
            <summary cref="T:ExtensionMethodsDemo1.A">  
            </summary>  
            <typeparam name="T"></typeparam>  
        </member>  
    </members>  
</doc>  
```  
  
## <a name="see-also"></a><span data-ttu-id="51a9c-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="51a9c-118">See also</span></span>

- [<span data-ttu-id="51a9c-119">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="51a9c-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="51a9c-120">建議使用的文件註解標籤</span><span class="sxs-lookup"><span data-stu-id="51a9c-120">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
