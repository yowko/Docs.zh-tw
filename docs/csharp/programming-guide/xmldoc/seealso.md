---
title: '&lt;seealso&gt; - C# 程式設計指南'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- cref
- <seealso>
- seealso
helpviewer_keywords:
- cref [C#], see also
- seealso C# XML tag
- cref [C#]
- cross-references [C#], tags
- <seealso> C# XML tag
ms.assetid: 8e157f3f-f220-4fcf-9010-88905b080b18
ms.openlocfilehash: e75480db9aebdeb2199694168abf4f774773b9c8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54543544"
---
# <a name="ltseealsogt-c-programming-guide"></a><span data-ttu-id="d7cd4-102">&lt;seealso&gt; (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="d7cd4-102">&lt;seealso&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="d7cd4-103">語法</span><span class="sxs-lookup"><span data-stu-id="d7cd4-103">Syntax</span></span>  
  
```xml  
<seealso cref="member"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d7cd4-104">參數</span><span class="sxs-lookup"><span data-stu-id="d7cd4-104">Parameters</span></span>  
 <span data-ttu-id="d7cd4-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="d7cd4-105">cref = " `member`"</span></span>  
 <span data-ttu-id="d7cd4-106">可從目前編譯環境呼叫的成員或欄位參考。</span><span class="sxs-lookup"><span data-stu-id="d7cd4-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="d7cd4-107">編譯器會檢查指定的程式碼項目是否存在，並將 `member` 傳遞給輸出 XML 中的項目名稱。`member`</span><span class="sxs-lookup"><span data-stu-id="d7cd4-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.`member`</span></span> <span data-ttu-id="d7cd4-108">必須出現在雙引號 (" ") 內。</span><span class="sxs-lookup"><span data-stu-id="d7cd4-108">must appear within double quotation marks (" ").</span></span>  
  
 <span data-ttu-id="d7cd4-109">如需如何建立泛型型別 cref 參考的資訊，請參閱[\<see>](../../../csharp/programming-guide/xmldoc/see.md)。</span><span class="sxs-lookup"><span data-stu-id="d7cd4-109">For information on how to create a cref reference to a generic type, see [\<see>](../../../csharp/programming-guide/xmldoc/see.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d7cd4-110">備註</span><span class="sxs-lookup"><span data-stu-id="d7cd4-110">Remarks</span></span>  
 <span data-ttu-id="d7cd4-111">\<seealso> 標記可讓您指定要顯示在＜請參閱＞一節中的文字。</span><span class="sxs-lookup"><span data-stu-id="d7cd4-111">The \<seealso> tag lets you specify the text that you might want to appear in a See Also section.</span></span> <span data-ttu-id="d7cd4-112">使用 [\<see>](../../../csharp/programming-guide/xmldoc/see.md)，以在文字內指定連結。</span><span class="sxs-lookup"><span data-stu-id="d7cd4-112">Use [\<see>](../../../csharp/programming-guide/xmldoc/see.md) to specify a link from within text.</span></span>  
  
 <span data-ttu-id="d7cd4-113">編譯搭配 [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) 可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="d7cd4-113">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7cd4-114">範例</span><span class="sxs-lookup"><span data-stu-id="d7cd4-114">Example</span></span>  
 <span data-ttu-id="d7cd4-115">如需使用 \<seealso> 的範例，請參閱 [\<summary>](../../../csharp/programming-guide/xmldoc/summary.md)。</span><span class="sxs-lookup"><span data-stu-id="d7cd4-115">See [\<summary>](../../../csharp/programming-guide/xmldoc/summary.md) for an example of using \<seealso>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7cd4-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7cd4-116">See also</span></span>

- [<span data-ttu-id="d7cd4-117">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="d7cd4-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="d7cd4-118">建議使用的文件註解標籤</span><span class="sxs-lookup"><span data-stu-id="d7cd4-118">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
