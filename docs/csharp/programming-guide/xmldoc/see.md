---
title: <see> - C# 程式設計指南
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
ms.openlocfilehash: 31806ad06cc97fa27f1944f2500f0f9cbb29f561
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55262097"
---
# <a name="see-c-programming-guide"></a><span data-ttu-id="a98b8-102">\<see> (C# 程式設計指南)</span><span class="sxs-lookup"><span data-stu-id="a98b8-102">\<see> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="a98b8-103">語法</span><span class="sxs-lookup"><span data-stu-id="a98b8-103">Syntax</span></span>  
  
```xml  
<see cref="member"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a98b8-104">參數</span><span class="sxs-lookup"><span data-stu-id="a98b8-104">Parameters</span></span>  
 <span data-ttu-id="a98b8-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="a98b8-105">cref = " `member`"</span></span>  
 <span data-ttu-id="a98b8-106">可從目前編譯環境呼叫的成員或欄位參考。</span><span class="sxs-lookup"><span data-stu-id="a98b8-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="a98b8-107">編譯器會檢查指定的程式碼項目是否存在，並將 `member` 傳遞給輸出 XML 中的項目名稱。</span><span class="sxs-lookup"><span data-stu-id="a98b8-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="a98b8-108">將 *member* 置於雙引號 (" ") 內。</span><span class="sxs-lookup"><span data-stu-id="a98b8-108">Place *member* within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a98b8-109">備註</span><span class="sxs-lookup"><span data-stu-id="a98b8-109">Remarks</span></span>  
 <span data-ttu-id="a98b8-110">\<see> 標記可讓您在文字內指定連結。</span><span class="sxs-lookup"><span data-stu-id="a98b8-110">The \<see> tag lets you specify a link from within text.</span></span> <span data-ttu-id="a98b8-111">使用 [\<seealso>](../../../csharp/programming-guide/xmldoc/seealso.md) 指出文字應該放置於＜請參閱＞一節中。</span><span class="sxs-lookup"><span data-stu-id="a98b8-111">Use [\<seealso>](../../../csharp/programming-guide/xmldoc/seealso.md) to indicate that text should be placed in a See Also section.</span></span> <span data-ttu-id="a98b8-112">使用 [cref 屬性](../../../csharp/programming-guide/xmldoc/cref-attribute.md)，建立程式碼項目之文件頁面的內部超連結。</span><span class="sxs-lookup"><span data-stu-id="a98b8-112">Use the [cref Attribute](../../../csharp/programming-guide/xmldoc/cref-attribute.md) to create internal hyperlinks to documentation pages for code elements.</span></span>  
  
 <span data-ttu-id="a98b8-113">使用 [-doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) 編譯，可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="a98b8-113">Compile with [-doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
 <span data-ttu-id="a98b8-114">下列範例示範摘要區段內的 \<see> 標記。</span><span class="sxs-lookup"><span data-stu-id="a98b8-114">The following example shows a \<see> tag within a summary section.</span></span>  
  
 [!code-csharp[csProgGuideDocComments#12](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/see_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="a98b8-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a98b8-115">See also</span></span>

- [<span data-ttu-id="a98b8-116">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="a98b8-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="a98b8-117">建議使用的文件註解標籤</span><span class="sxs-lookup"><span data-stu-id="a98b8-117">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
