---
title: <exception> - C# 程式設計指南
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- exception
- <exception>
helpviewer_keywords:
- <exception> C# XML tag
- exception C# XML tag
ms.assetid: dd73aac5-3c74-4fcf-9498-f11bff3a2f3c
ms.openlocfilehash: fe304b9c6631591cf7a3d62fcecd2ed3ca05db9c
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55257287"
---
# <a name="exception-c-programming-guide"></a><span data-ttu-id="d65ae-102">\<exception> (C# 程式設計指南)</span><span class="sxs-lookup"><span data-stu-id="d65ae-102">\<exception> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="d65ae-103">語法</span><span class="sxs-lookup"><span data-stu-id="d65ae-103">Syntax</span></span>  
  
```xml  
<exception cref="member">description</exception>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d65ae-104">參數</span><span class="sxs-lookup"><span data-stu-id="d65ae-104">Parameters</span></span>  
 <span data-ttu-id="d65ae-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="d65ae-105">cref = " `member`"</span></span>  
 <span data-ttu-id="d65ae-106">可從目前編譯環境取得之例外狀況的參考。</span><span class="sxs-lookup"><span data-stu-id="d65ae-106">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="d65ae-107">編譯器會檢查指定的例外狀況是否存在，並將 `member` 轉譯為輸出 XML 中的標準項目名稱。</span><span class="sxs-lookup"><span data-stu-id="d65ae-107">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="d65ae-108">`member` 必須出現在雙引號內 (" ")。</span><span class="sxs-lookup"><span data-stu-id="d65ae-108">`member` must appear within double quotation marks (" ").</span></span>  
  
 <span data-ttu-id="d65ae-109">如需如何建立泛型型別 cref 參考的詳細資訊，請參閱[\<請參閱>](../../../csharp/programming-guide/xmldoc/see.md)。</span><span class="sxs-lookup"><span data-stu-id="d65ae-109">For more information on how to create a cref reference to a generic type, see [\<see>](../../../csharp/programming-guide/xmldoc/see.md).</span></span>  
  
 `description`  
 <span data-ttu-id="d65ae-110">例外狀況的描述。</span><span class="sxs-lookup"><span data-stu-id="d65ae-110">A description of the exception.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d65ae-111">備註</span><span class="sxs-lookup"><span data-stu-id="d65ae-111">Remarks</span></span>  
 <span data-ttu-id="d65ae-112">\<exception> 標記可讓您指定可以擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d65ae-112">The \<exception> tag lets you specify which exceptions can be thrown.</span></span> <span data-ttu-id="d65ae-113">這個標記可以套用至方法、屬性、事件和索引子的定義。</span><span class="sxs-lookup"><span data-stu-id="d65ae-113">This tag can be applied to definitions for methods, properties, events, and indexers.</span></span>  
  
 <span data-ttu-id="d65ae-114">使用 [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) 編譯，可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="d65ae-114">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
 <span data-ttu-id="d65ae-115">如需例外狀況處理的詳細資訊，請參閱[例外狀況和例外狀況處理](../../../csharp/programming-guide/exceptions/index.md)。</span><span class="sxs-lookup"><span data-stu-id="d65ae-115">For more information about exception handling, see [Exceptions and Exception Handling](../../../csharp/programming-guide/exceptions/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d65ae-116">範例</span><span class="sxs-lookup"><span data-stu-id="d65ae-116">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#4](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/exception_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="d65ae-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d65ae-117">See also</span></span>

- [<span data-ttu-id="d65ae-118">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="d65ae-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="d65ae-119">建議使用的文件註解標籤</span><span class="sxs-lookup"><span data-stu-id="d65ae-119">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
