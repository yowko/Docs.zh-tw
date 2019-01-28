---
title: '&lt;see&gt; - C# 程式設計指南'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- <see>
- see
helpviewer_keywords:
- cref [C#], <see> tag
- <see> C# XML tag
- cross-references [C#]
- see C# XML tag
ms.assetid: 0200de01-7e2f-45c4-9094-829d61236383
ms.openlocfilehash: fb8b7dd0f1620895ff95917977745ac391dadf61
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54718594"
---
# <a name="ltseegt-c-programming-guide"></a><span data-ttu-id="9fd35-102">&lt;see&gt; (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="9fd35-102">&lt;see&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="9fd35-103">語法</span><span class="sxs-lookup"><span data-stu-id="9fd35-103">Syntax</span></span>  
  
```xml  
<see cref="member"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9fd35-104">參數</span><span class="sxs-lookup"><span data-stu-id="9fd35-104">Parameters</span></span>  
 <span data-ttu-id="9fd35-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="9fd35-105">cref = " `member`"</span></span>  
 <span data-ttu-id="9fd35-106">可從目前編譯環境呼叫的成員或欄位參考。</span><span class="sxs-lookup"><span data-stu-id="9fd35-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="9fd35-107">編譯器會檢查指定的程式碼項目是否存在，並將 `member` 傳遞給輸出 XML 中的項目名稱。</span><span class="sxs-lookup"><span data-stu-id="9fd35-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="9fd35-108">將 *member* 置於雙引號 (" ") 內。</span><span class="sxs-lookup"><span data-stu-id="9fd35-108">Place *member* within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9fd35-109">備註</span><span class="sxs-lookup"><span data-stu-id="9fd35-109">Remarks</span></span>  
 <span data-ttu-id="9fd35-110">\<see> 標記可讓您在文字內指定連結。</span><span class="sxs-lookup"><span data-stu-id="9fd35-110">The \<see> tag lets you specify a link from within text.</span></span> <span data-ttu-id="9fd35-111">使用 [\<seealso>](../../../csharp/programming-guide/xmldoc/seealso.md) 指出文字應該放置於＜請參閱＞一節中。</span><span class="sxs-lookup"><span data-stu-id="9fd35-111">Use [\<seealso>](../../../csharp/programming-guide/xmldoc/seealso.md) to indicate that text should be placed in a See Also section.</span></span> <span data-ttu-id="9fd35-112">使用 [cref 屬性](../../../csharp/programming-guide/xmldoc/cref-attribute.md)，建立程式碼項目之文件頁面的內部超連結。</span><span class="sxs-lookup"><span data-stu-id="9fd35-112">Use the [cref Attribute](../../../csharp/programming-guide/xmldoc/cref-attribute.md) to create internal hyperlinks to documentation pages for code elements.</span></span>  
  
 <span data-ttu-id="9fd35-113">使用 [-doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) 編譯可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="9fd35-113">Compile with [-doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
 <span data-ttu-id="9fd35-114">下列範例示範摘要區段內的 \<see> 標記。</span><span class="sxs-lookup"><span data-stu-id="9fd35-114">The following example shows a \<see> tag within a summary section.</span></span>  
  
 [!code-csharp[csProgGuideDocComments#12](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/see_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="9fd35-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9fd35-115">See also</span></span>

- [<span data-ttu-id="9fd35-116">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="9fd35-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="9fd35-117">建議使用的文件註解標籤</span><span class="sxs-lookup"><span data-stu-id="9fd35-117">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
