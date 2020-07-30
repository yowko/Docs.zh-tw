---
title: '<exception>-C # 程式設計指南'
description: 瞭解 XML <exception> 標記。 此標記可讓您指定可以擲回的例外狀況，並可套用至方法、屬性、事件和索引子。
ms.date: 07/20/2015
f1_keywords:
- exception
- <exception>
helpviewer_keywords:
- <exception> C# XML tag
- exception C# XML tag
ms.assetid: dd73aac5-3c74-4fcf-9498-f11bff3a2f3c
ms.openlocfilehash: 22a28f3fe6de5a0db9aea0f1fd7963d4e6fcee05
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381732"
---
# <a name="exception-c-programming-guide"></a><span data-ttu-id="b99f2-104">\<exception>（C # 程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="b99f2-104">\<exception> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="b99f2-105">語法</span><span class="sxs-lookup"><span data-stu-id="b99f2-105">Syntax</span></span>

```xml
<exception cref="member">description</exception>
```

## <a name="parameters"></a><span data-ttu-id="b99f2-106">參數</span><span class="sxs-lookup"><span data-stu-id="b99f2-106">Parameters</span></span>

- <span data-ttu-id="b99f2-107">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="b99f2-107">cref = " `member`"</span></span>

  <span data-ttu-id="b99f2-108">可從目前編譯環境取得之例外狀況的參考。</span><span class="sxs-lookup"><span data-stu-id="b99f2-108">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="b99f2-109">編譯器會檢查指定的例外狀況是否存在，並將 `member` 轉譯為輸出 XML 中的標準項目名稱。</span><span class="sxs-lookup"><span data-stu-id="b99f2-109">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="b99f2-110">`member` 必須出現在雙引號內 (" ")。</span><span class="sxs-lookup"><span data-stu-id="b99f2-110">`member` must appear within double quotation marks (" ").</span></span>

  <span data-ttu-id="b99f2-111">如需有關如何設定 `member` 格式以參考泛型型別的詳細資訊，請參閱[處理 XML 檔案](processing-the-xml-file.md)。</span><span class="sxs-lookup"><span data-stu-id="b99f2-111">For more information on how to format `member` to reference a generic type, see [Processing the XML File](processing-the-xml-file.md).</span></span>

- `description`

  <span data-ttu-id="b99f2-112">例外狀況的描述。</span><span class="sxs-lookup"><span data-stu-id="b99f2-112">A description of the exception.</span></span>

## <a name="remarks"></a><span data-ttu-id="b99f2-113">備註</span><span class="sxs-lookup"><span data-stu-id="b99f2-113">Remarks</span></span>

<span data-ttu-id="b99f2-114">`<exception>`標記可讓您指定可以擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b99f2-114">The `<exception>` tag lets you specify which exceptions can be thrown.</span></span> <span data-ttu-id="b99f2-115">這個標記可以套用至方法、屬性、事件和索引子的定義。</span><span class="sxs-lookup"><span data-stu-id="b99f2-115">This tag can be applied to definitions for methods, properties, events, and indexers.</span></span>

<span data-ttu-id="b99f2-116">使用[-doc](../../language-reference/compiler-options/doc-compiler-option.md)進行編譯，以處理檔案的檔批註。</span><span class="sxs-lookup"><span data-stu-id="b99f2-116">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

<span data-ttu-id="b99f2-117">如需例外狀況處理的詳細資訊，請參閱[例外狀況和例外狀況處理](../exceptions/index.md)。</span><span class="sxs-lookup"><span data-stu-id="b99f2-117">For more information about exception handling, see [Exceptions and Exception Handling](../exceptions/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="b99f2-118">範例</span><span class="sxs-lookup"><span data-stu-id="b99f2-118">Example</span></span>

[!code-csharp[csProgGuideDocComments#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#4)]

## <a name="see-also"></a><span data-ttu-id="b99f2-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b99f2-119">See also</span></span>

- [<span data-ttu-id="b99f2-120">C# 程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="b99f2-120">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="b99f2-121">建議使用的文件註解標籤</span><span class="sxs-lookup"><span data-stu-id="b99f2-121">Recommended tags for documentation comments</span></span>](recommended-tags-for-documentation-comments.md)
