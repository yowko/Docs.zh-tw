---
title: 建議用於檔批註的 XML 標記
ms.date: 07/20/2015
f1_keywords:
- vb.XmlDocComment
helpviewer_keywords:
- tags, XML
- XML comments, recommended tags [Visual Basic]
- comments, recommended XML tags
ms.assetid: 294e0736-ff1e-498e-af83-6db71ed41a72
ms.openlocfilehash: 9f877ee3fc9d616dc1e946293489a8aab96ac2e1
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90872789"
---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a><span data-ttu-id="2186d-102">建議可用於文件註解的 XML 標記 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2186d-102">Recommended XML Tags for Documentation Comments (Visual Basic)</span></span>

<span data-ttu-id="2186d-103">Visual Basic 編譯器可以將程式碼中的檔批註處理成 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="2186d-103">The Visual Basic compiler can process documentation comments in your code to an XML file.</span></span> <span data-ttu-id="2186d-104">您可以使用其他工具將 XML 檔案處理成檔。</span><span class="sxs-lookup"><span data-stu-id="2186d-104">You can use additional tools to process the XML file into documentation.</span></span>  
  
 <span data-ttu-id="2186d-105">XML 批註可在程式碼結構（例如類型和類型成員）上使用。</span><span class="sxs-lookup"><span data-stu-id="2186d-105">XML comments are allowed on code constructs such as types and type members.</span></span> <span data-ttu-id="2186d-106">針對部分類型，只有類型的其中一個部分可以有 XML 批註，雖然批註其成員沒有任何限制。</span><span class="sxs-lookup"><span data-stu-id="2186d-106">For partial types, only one part of the type can have XML comments, although there is no restriction on commenting its members.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2186d-107">檔批註無法套用至命名空間。</span><span class="sxs-lookup"><span data-stu-id="2186d-107">Documentation comments cannot be applied to namespaces.</span></span> <span data-ttu-id="2186d-108">原因是某個命名空間可以跨越數個元件，而不是所有的元件都必須同時載入。</span><span class="sxs-lookup"><span data-stu-id="2186d-108">The reason is that one namespace can span several assemblies, and not all assemblies have to be loaded at the same time.</span></span>  
  
 <span data-ttu-id="2186d-109">編譯器會處理任何有效 XML 的標記。</span><span class="sxs-lookup"><span data-stu-id="2186d-109">The compiler processes any tag that is valid XML.</span></span> <span data-ttu-id="2186d-110">下列標記提供使用者檔中常用的功能。</span><span class="sxs-lookup"><span data-stu-id="2186d-110">The following tags provide commonly used functionality in user documentation.</span></span>  
  
||||  
|---|---|---|  
|[\<c>](c.md)|[\<code>](code.md)|[\<example>](example.md)|  
|<span data-ttu-id="2186d-111">[\<exception>](exception.md)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="2186d-111">[\<exception>](exception.md) <sup>1</sup></span></span>|<span data-ttu-id="2186d-112">[\<include>](include.md)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="2186d-112">[\<include>](include.md) <sup>1</sup></span></span>|[\<list>](list.md)|  
|[\<para>](para.md)|<span data-ttu-id="2186d-113">[\<param>](param.md)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="2186d-113">[\<param>](param.md) <sup>1</sup></span></span>|[\<paramref>](paramref.md)|  
|<span data-ttu-id="2186d-114">[\<permission>](permission.md)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="2186d-114">[\<permission>](permission.md) <sup>1</sup></span></span>|[\<remarks>](remarks.md)|[\<returns>](returns.md)|  
|<span data-ttu-id="2186d-115">[\<see>](see.md)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="2186d-115">[\<see>](see.md) <sup>1</sup></span></span>|<span data-ttu-id="2186d-116">[\<seealso>](seealso.md)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="2186d-116">[\<seealso>](seealso.md) <sup>1</sup></span></span>|[\<summary>](summary.md)|  
|<span data-ttu-id="2186d-117">[\<typeparam>](typeparam.md)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="2186d-117">[\<typeparam>](typeparam.md) <sup>1</sup></span></span>|[\<value>](value.md)||  
  
 <span data-ttu-id="2186d-118"> (<sup>1</sup> ：編譯器會驗證語法。 ) </span><span class="sxs-lookup"><span data-stu-id="2186d-118">(<sup>1</sup> The compiler verifies syntax.)</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2186d-119">如果您想要讓角括弧出現在檔批註的文字中，請使用 `&lt;` 和 `&gt;` 。</span><span class="sxs-lookup"><span data-stu-id="2186d-119">If you want angle brackets to appear in the text of a documentation comment, use `&lt;` and `&gt;`.</span></span> <span data-ttu-id="2186d-120">例如，字串將會 `"&lt;text in angle brackets&gt;"` 顯示為 `<text in angle brackets>` 。</span><span class="sxs-lookup"><span data-stu-id="2186d-120">For example, the string `"&lt;text in angle brackets&gt;"` will appear as `<text in angle brackets>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2186d-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2186d-121">See also</span></span>

- [<span data-ttu-id="2186d-122">使用 XML 加入程式碼註解</span><span class="sxs-lookup"><span data-stu-id="2186d-122">Documenting Your Code with XML</span></span>](../../programming-guide/program-structure/documenting-your-code-with-xml.md)
- [<span data-ttu-id="2186d-123">-doc</span><span class="sxs-lookup"><span data-stu-id="2186d-123">-doc</span></span>](../../reference/command-line-compiler/doc.md)
- [<span data-ttu-id="2186d-124">如何：建立 XML 文件</span><span class="sxs-lookup"><span data-stu-id="2186d-124">How to: Create XML Documentation</span></span>](../../programming-guide/program-structure/how-to-create-xml-documentation.md)
