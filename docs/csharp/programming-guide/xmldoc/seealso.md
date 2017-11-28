---
title: "&lt;seealso&gt; (C# 程式設計手冊)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
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
caps.latest.revision: "11"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 088445680375e1c1805f9fb4356fe98c730178e7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltseealsogt-c-programming-guide"></a><span data-ttu-id="2ca6e-102">&lt;seealso&gt; (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="2ca6e-102">&lt;seealso&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="2ca6e-103">語法</span><span class="sxs-lookup"><span data-stu-id="2ca6e-103">Syntax</span></span>  
  
```xml  
<seealso cref="member"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2ca6e-104">參數</span><span class="sxs-lookup"><span data-stu-id="2ca6e-104">Parameters</span></span>  
 <span data-ttu-id="2ca6e-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="2ca6e-105">cref = " `member`"</span></span>  
 <span data-ttu-id="2ca6e-106">可從目前編譯環境呼叫的成員或欄位參考。</span><span class="sxs-lookup"><span data-stu-id="2ca6e-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="2ca6e-107">編譯器會檢查指定的程式碼項目是否存在，並將 `member` 傳遞給輸出 XML 中的項目名稱。`member`</span><span class="sxs-lookup"><span data-stu-id="2ca6e-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.`member`</span></span> <span data-ttu-id="2ca6e-108">必須出現在雙引號 (" ") 內。</span><span class="sxs-lookup"><span data-stu-id="2ca6e-108">must appear within double quotation marks (" ").</span></span>  
  
 <span data-ttu-id="2ca6e-109">如需如何建立泛型型別 cref 參考的資訊，請參閱[\<see>](../../../csharp/programming-guide/xmldoc/see.md)。</span><span class="sxs-lookup"><span data-stu-id="2ca6e-109">For information on how to create a cref reference to a generic type, see [\<see>](../../../csharp/programming-guide/xmldoc/see.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ca6e-110">備註</span><span class="sxs-lookup"><span data-stu-id="2ca6e-110">Remarks</span></span>  
 <span data-ttu-id="2ca6e-111">\<seealso> 標記可讓您指定要顯示在＜請參閱＞一節中的文字。</span><span class="sxs-lookup"><span data-stu-id="2ca6e-111">The \<seealso> tag lets you specify the text that you might want to appear in a See Also section.</span></span> <span data-ttu-id="2ca6e-112">使用 [\<see>](../../../csharp/programming-guide/xmldoc/see.md)，以在文字內指定連結。</span><span class="sxs-lookup"><span data-stu-id="2ca6e-112">Use [\<see>](../../../csharp/programming-guide/xmldoc/see.md) to specify a link from within text.</span></span>  
  
 <span data-ttu-id="2ca6e-113">編譯搭配 [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) 可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="2ca6e-113">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ca6e-114">範例</span><span class="sxs-lookup"><span data-stu-id="2ca6e-114">Example</span></span>  
 <span data-ttu-id="2ca6e-115">如需使用 \<seealso> 的範例，請參閱 [\<summary>](../../../csharp/programming-guide/xmldoc/summary.md)。</span><span class="sxs-lookup"><span data-stu-id="2ca6e-115">See [\<summary>](../../../csharp/programming-guide/xmldoc/summary.md) for an example of using \<seealso>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ca6e-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2ca6e-116">See Also</span></span>  
 [<span data-ttu-id="2ca6e-117">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="2ca6e-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="2ca6e-118">建議使用的文件註解標籤</span><span class="sxs-lookup"><span data-stu-id="2ca6e-118">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
