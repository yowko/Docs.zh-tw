---
title: "&lt;summary&gt; (C# 程式設計手冊)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- <summary>
- summary
helpviewer_keywords:
- <summary> C# XML tag
- summary C# XML tag
ms.assetid: b4c43d92-2067-4eac-a59a-d32f5248c08b
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5a8aa1f8a07019ff6ccefe90f03b217067ae22c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltsummarygt-c-programming-guide"></a><span data-ttu-id="8912f-102">&lt;summary&gt; (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="8912f-102">&lt;summary&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="8912f-103">語法</span><span class="sxs-lookup"><span data-stu-id="8912f-103">Syntax</span></span>  
  
```xml  
<summary>description</summary>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8912f-104">參數</span><span class="sxs-lookup"><span data-stu-id="8912f-104">Parameters</span></span>  
 `description`  
 <span data-ttu-id="8912f-105">物件的摘要。</span><span class="sxs-lookup"><span data-stu-id="8912f-105">A summary of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8912f-106">備註</span><span class="sxs-lookup"><span data-stu-id="8912f-106">Remarks</span></span>  
 <span data-ttu-id="8912f-107">\<summary> 標記應該用來描述類型或類型成員。</span><span class="sxs-lookup"><span data-stu-id="8912f-107">The \<summary> tag should be used to describe a type or a type member.</span></span> <span data-ttu-id="8912f-108">使用 [\<remarks>](../../../csharp/programming-guide/xmldoc/remarks.md) 新增類型描述的補充資訊。</span><span class="sxs-lookup"><span data-stu-id="8912f-108">Use [\<remarks>](../../../csharp/programming-guide/xmldoc/remarks.md) to add supplemental information to a type description.</span></span> <span data-ttu-id="8912f-109">使用 [cref 屬性](../../../csharp/programming-guide/xmldoc/cref-attribute.md)，讓 [Sandcastle](https://github.com/EWSoftware/SHFB) 這類文件工具建立程式碼項目之文件頁面的內部超連結。</span><span class="sxs-lookup"><span data-stu-id="8912f-109">Use the [cref Attribute](../../../csharp/programming-guide/xmldoc/cref-attribute.md) to enable documentation tools such as [Sandcastle](https://github.com/EWSoftware/SHFB) to create internal hyperlinks to documentation pages for code elements.</span></span>  
  
 <span data-ttu-id="8912f-110">\<summary> 標記的文字是 IntelliSense 中類型的唯一資訊來源，也會顯示在 [物件瀏覽器] 視窗中。</span><span class="sxs-lookup"><span data-stu-id="8912f-110">The text for the \<summary> tag is the only source of information about the type in IntelliSense, and is also displayed in the Object Browser Window.</span></span>  
  
 <span data-ttu-id="8912f-111">使用 [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) 編譯，可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="8912f-111">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span> <span data-ttu-id="8912f-112">若要依據編譯器產生的檔案來建立最終文件，您可以建立自訂工具，或者是使用 [Sandcastle](https://github.com/EWSoftware/SHFB) 這類工具。</span><span class="sxs-lookup"><span data-stu-id="8912f-112">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8912f-113">範例</span><span class="sxs-lookup"><span data-stu-id="8912f-113">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#12](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/summary_1.cs)]  
  
 <span data-ttu-id="8912f-114">上述範例會產生下列 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="8912f-114">The previous example produces the following XML file.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="8912f-115">範例</span><span class="sxs-lookup"><span data-stu-id="8912f-115">Example</span></span>  
 <span data-ttu-id="8912f-116">下列範例示範如何設定泛型型別的 `cref` 參考。</span><span class="sxs-lookup"><span data-stu-id="8912f-116">The following example shows how to make a `cref` reference to a generic type.</span></span>  
  
 [!code-csharp[csProgGuideDocComments#11](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/summary_2.cs)]  
  
 <span data-ttu-id="8912f-117">上述範例會產生下列 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="8912f-117">The previous example produces the following XML file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8912f-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8912f-118">See Also</span></span>  
 [<span data-ttu-id="8912f-119">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="8912f-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="8912f-120">建議使用的文件註解標籤</span><span class="sxs-lookup"><span data-stu-id="8912f-120">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
