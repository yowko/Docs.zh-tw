---
title: '<see>-C # 程式設計指南'
description: 瞭解 XML <see> 標記。 此標記可讓您指定文字內的連結，例如使用 cref 屬性。
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
ms.openlocfilehash: 1cc4982d1ebe9d6896404218a6d200b10cc6503f
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381927"
---
# <a name="see-c-programming-guide"></a><span data-ttu-id="d3631-104">\<see>（C # 程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="d3631-104">\<see> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="d3631-105">語法</span><span class="sxs-lookup"><span data-stu-id="d3631-105">Syntax</span></span>

```xml
<see cref="member"/>
```

## <a name="parameters"></a><span data-ttu-id="d3631-106">參數</span><span class="sxs-lookup"><span data-stu-id="d3631-106">Parameters</span></span>

- <span data-ttu-id="d3631-107">cref = " `member` "</span><span class="sxs-lookup"><span data-stu-id="d3631-107">cref = "`member`"</span></span>

  <span data-ttu-id="d3631-108">可從目前編譯環境呼叫的成員或欄位參考。</span><span class="sxs-lookup"><span data-stu-id="d3631-108">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="d3631-109">編譯器會檢查指定的程式碼項目是否存在，並將 `member` 傳遞給輸出 XML 中的項目名稱。</span><span class="sxs-lookup"><span data-stu-id="d3631-109">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="d3631-110">將 *member* 置於雙引號 (" ") 內。</span><span class="sxs-lookup"><span data-stu-id="d3631-110">Place *member* within double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="d3631-111">備註</span><span class="sxs-lookup"><span data-stu-id="d3631-111">Remarks</span></span>

<span data-ttu-id="d3631-112">`<see>`標記可讓您指定文字中的連結。</span><span class="sxs-lookup"><span data-stu-id="d3631-112">The `<see>` tag lets you specify a link from within text.</span></span> <span data-ttu-id="d3631-113">用 [\<seealso>](./seealso.md) 來指示文字應該放在 [另請參閱] 區段中。</span><span class="sxs-lookup"><span data-stu-id="d3631-113">Use [\<seealso>](./seealso.md) to indicate that text should be placed in a See Also section.</span></span> <span data-ttu-id="d3631-114">使用 [cref 屬性](./cref-attribute.md)，建立程式碼項目之文件頁面的內部超連結。</span><span class="sxs-lookup"><span data-stu-id="d3631-114">Use the [cref Attribute](./cref-attribute.md) to create internal hyperlinks to documentation pages for code elements.</span></span> <span data-ttu-id="d3631-115">此外， ``href`` 是有效的屬性，可做為超連結。</span><span class="sxs-lookup"><span data-stu-id="d3631-115">Also, ``href`` is a valid Attribute that will function as a hyperlink.</span></span>

<span data-ttu-id="d3631-116">使用[-doc](../../language-reference/compiler-options/doc-compiler-option.md)進行編譯，以處理檔案的檔批註。</span><span class="sxs-lookup"><span data-stu-id="d3631-116">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

<span data-ttu-id="d3631-117">下列範例會顯示 `<see>` 摘要區段內的標記。</span><span class="sxs-lookup"><span data-stu-id="d3631-117">The following example shows a `<see>` tag within a summary section.</span></span>

[!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]

## <a name="see-also"></a><span data-ttu-id="d3631-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3631-118">See also</span></span>

- [<span data-ttu-id="d3631-119">C# 程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="d3631-119">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="d3631-120">建議使用的文件註解標籤</span><span class="sxs-lookup"><span data-stu-id="d3631-120">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
