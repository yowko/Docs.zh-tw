---
title: "&lt;see&gt; (C# 程式設計手冊)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- <see>
- see
helpviewer_keywords:
- cref [C#], <see> tag
- <see> C# XML tag
- cross-references [C#]
- see C# XML tag
ms.assetid: 0200de01-7e2f-45c4-9094-829d61236383
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 065c85ba411794858c8c4d70de0ac1467da1fe56
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltseegt-c-programming-guide"></a><span data-ttu-id="dfbfd-102">&lt;see&gt; (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="dfbfd-102">&lt;see&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="dfbfd-103">語法</span><span class="sxs-lookup"><span data-stu-id="dfbfd-103">Syntax</span></span>  
  
```xml  
<see cref="member"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dfbfd-104">參數</span><span class="sxs-lookup"><span data-stu-id="dfbfd-104">Parameters</span></span>  
 <span data-ttu-id="dfbfd-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="dfbfd-105">cref = " `member`"</span></span>  
 <span data-ttu-id="dfbfd-106">可從目前編譯環境呼叫的成員或欄位參考。</span><span class="sxs-lookup"><span data-stu-id="dfbfd-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="dfbfd-107">編譯器會檢查指定的程式碼項目是否存在，並將 `member` 傳遞給輸出 XML 中的項目名稱。請將 *member* 放在雙引號 (" ") 內。</span><span class="sxs-lookup"><span data-stu-id="dfbfd-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.Place *member* within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dfbfd-108">備註</span><span class="sxs-lookup"><span data-stu-id="dfbfd-108">Remarks</span></span>  
 <span data-ttu-id="dfbfd-109">\<see> 標記可讓您在文字內指定連結。</span><span class="sxs-lookup"><span data-stu-id="dfbfd-109">The \<see> tag lets you specify a link from within text.</span></span> <span data-ttu-id="dfbfd-110">使用 [\<seealso>](../../../csharp/programming-guide/xmldoc/seealso.md) 指出文字應該放置於＜請參閱＞一節中。</span><span class="sxs-lookup"><span data-stu-id="dfbfd-110">Use [\<seealso>](../../../csharp/programming-guide/xmldoc/seealso.md) to indicate that text should be placed in a See Also section.</span></span> <span data-ttu-id="dfbfd-111">使用 [cref 屬性](../../../csharp/programming-guide/xmldoc/cref-attribute.md)，建立程式碼項目之文件頁面的內部超連結。</span><span class="sxs-lookup"><span data-stu-id="dfbfd-111">Use the [cref Attribute](../../../csharp/programming-guide/xmldoc/cref-attribute.md) to create internal hyperlinks to documentation pages for code elements.</span></span>  
  
 <span data-ttu-id="dfbfd-112">編譯搭配 [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) 可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="dfbfd-112">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
 <span data-ttu-id="dfbfd-113">下列範例示範摘要區段內的 \<see> 標記。</span><span class="sxs-lookup"><span data-stu-id="dfbfd-113">The following example shows a \<see> tag within a summary section.</span></span>  
  
 [!code-csharp[csProgGuideDocComments#12](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/see_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="dfbfd-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dfbfd-114">See Also</span></span>  
 [<span data-ttu-id="dfbfd-115">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="dfbfd-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="dfbfd-116">建議使用的文件註解標籤</span><span class="sxs-lookup"><span data-stu-id="dfbfd-116">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
