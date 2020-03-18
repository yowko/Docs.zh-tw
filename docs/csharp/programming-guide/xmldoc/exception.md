---
title: <exception>- C# 程式設計指南
ms.date: 07/20/2015
f1_keywords:
- exception
- <exception>
helpviewer_keywords:
- <exception> C# XML tag
- exception C# XML tag
ms.assetid: dd73aac5-3c74-4fcf-9498-f11bff3a2f3c
ms.openlocfilehash: 14318ac0b0cdf781d0488eecaf934879017d91f6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789796"
---
# <a name="exception-c-programming-guide"></a><span data-ttu-id="a10a5-102">\<異常>（C# 程式設計指南）</span><span class="sxs-lookup"><span data-stu-id="a10a5-102">\<exception> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="a10a5-103">語法</span><span class="sxs-lookup"><span data-stu-id="a10a5-103">Syntax</span></span>

```xml
<exception cref="member">description</exception>
```

## <a name="parameters"></a><span data-ttu-id="a10a5-104">參數</span><span class="sxs-lookup"><span data-stu-id="a10a5-104">Parameters</span></span>

- <span data-ttu-id="a10a5-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="a10a5-105">cref = " `member`"</span></span>

  <span data-ttu-id="a10a5-106">可從目前編譯環境取得之例外狀況的參考。</span><span class="sxs-lookup"><span data-stu-id="a10a5-106">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="a10a5-107">編譯器會檢查指定的例外狀況是否存在，並將 `member` 轉譯為輸出 XML 中的標準項目名稱。</span><span class="sxs-lookup"><span data-stu-id="a10a5-107">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="a10a5-108">`member` 必須出現在雙引號內 (" ")。</span><span class="sxs-lookup"><span data-stu-id="a10a5-108">`member` must appear within double quotation marks (" ").</span></span>

  <span data-ttu-id="a10a5-109">如需有關如何設定 `member` 格式以參考泛型型別的詳細資訊，請參閱[處理 XML 檔案](processing-the-xml-file.md)。</span><span class="sxs-lookup"><span data-stu-id="a10a5-109">For more information on how to format `member` to reference a generic type, see [Processing the XML File](processing-the-xml-file.md).</span></span>

- `description`

  <span data-ttu-id="a10a5-110">例外狀況的描述。</span><span class="sxs-lookup"><span data-stu-id="a10a5-110">A description of the exception.</span></span>

## <a name="remarks"></a><span data-ttu-id="a10a5-111">備註</span><span class="sxs-lookup"><span data-stu-id="a10a5-111">Remarks</span></span>

<span data-ttu-id="a10a5-112">\<exception> 標記可讓您指定可以擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a10a5-112">The \<exception> tag lets you specify which exceptions can be thrown.</span></span> <span data-ttu-id="a10a5-113">這個標記可以套用至方法、屬性、事件和索引子的定義。</span><span class="sxs-lookup"><span data-stu-id="a10a5-113">This tag can be applied to definitions for methods, properties, events, and indexers.</span></span>

<span data-ttu-id="a10a5-114">使用[-doc](../../language-reference/compiler-options/doc-compiler-option.md)編譯，以處理檔的文檔注釋。</span><span class="sxs-lookup"><span data-stu-id="a10a5-114">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

<span data-ttu-id="a10a5-115">如需例外狀況處理的詳細資訊，請參閱[例外狀況和例外狀況處理](../exceptions/index.md)。</span><span class="sxs-lookup"><span data-stu-id="a10a5-115">For more information about exception handling, see [Exceptions and Exception Handling](../exceptions/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="a10a5-116">範例</span><span class="sxs-lookup"><span data-stu-id="a10a5-116">Example</span></span>

[!code-csharp[csProgGuideDocComments#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#4)]

## <a name="see-also"></a><span data-ttu-id="a10a5-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a10a5-117">See also</span></span>

- [<span data-ttu-id="a10a5-118">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="a10a5-118">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="a10a5-119">建議使用的文件註解標籤</span><span class="sxs-lookup"><span data-stu-id="a10a5-119">Recommended tags for documentation comments</span></span>](recommended-tags-for-documentation-comments.md)
