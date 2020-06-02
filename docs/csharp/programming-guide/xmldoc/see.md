---
title: '<see>-C # 程式設計指南'
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
ms.openlocfilehash: 0f10feb0931c6d38c817fdecb925f68d439abb59
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287242"
---
# <a name="see-c-programming-guide"></a><span data-ttu-id="bed5f-102">\<see>（C # 程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="bed5f-102">\<see> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="bed5f-103">語法</span><span class="sxs-lookup"><span data-stu-id="bed5f-103">Syntax</span></span>

```xml
<see cref="member"/>
```

## <a name="parameters"></a><span data-ttu-id="bed5f-104">參數</span><span class="sxs-lookup"><span data-stu-id="bed5f-104">Parameters</span></span>

- <span data-ttu-id="bed5f-105">cref = " `member` "</span><span class="sxs-lookup"><span data-stu-id="bed5f-105">cref = "`member`"</span></span>

  <span data-ttu-id="bed5f-106">可從目前編譯環境呼叫的成員或欄位參考。</span><span class="sxs-lookup"><span data-stu-id="bed5f-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="bed5f-107">編譯器會檢查指定的程式碼項目是否存在，並將 `member` 傳遞給輸出 XML 中的項目名稱。</span><span class="sxs-lookup"><span data-stu-id="bed5f-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="bed5f-108">將 *member* 置於雙引號 (" ") 內。</span><span class="sxs-lookup"><span data-stu-id="bed5f-108">Place *member* within double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="bed5f-109">備註</span><span class="sxs-lookup"><span data-stu-id="bed5f-109">Remarks</span></span>

<span data-ttu-id="bed5f-110">`<see>`標記可讓您指定文字中的連結。</span><span class="sxs-lookup"><span data-stu-id="bed5f-110">The `<see>` tag lets you specify a link from within text.</span></span> <span data-ttu-id="bed5f-111">用 [\<seealso>](./seealso.md) 來指示文字應該放在 [另請參閱] 區段中。</span><span class="sxs-lookup"><span data-stu-id="bed5f-111">Use [\<seealso>](./seealso.md) to indicate that text should be placed in a See Also section.</span></span> <span data-ttu-id="bed5f-112">使用 [cref 屬性](./cref-attribute.md)，建立程式碼項目之文件頁面的內部超連結。</span><span class="sxs-lookup"><span data-stu-id="bed5f-112">Use the [cref Attribute](./cref-attribute.md) to create internal hyperlinks to documentation pages for code elements.</span></span>

<span data-ttu-id="bed5f-113">使用[-doc](../../language-reference/compiler-options/doc-compiler-option.md)進行編譯，以處理檔案的檔批註。</span><span class="sxs-lookup"><span data-stu-id="bed5f-113">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

<span data-ttu-id="bed5f-114">下列範例會顯示 `<see>` 摘要區段內的標記。</span><span class="sxs-lookup"><span data-stu-id="bed5f-114">The following example shows a `<see>` tag within a summary section.</span></span>

[!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]

## <a name="see-also"></a><span data-ttu-id="bed5f-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bed5f-115">See also</span></span>

- [<span data-ttu-id="bed5f-116">C# 程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="bed5f-116">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="bed5f-117">建議使用的文件註解標籤</span><span class="sxs-lookup"><span data-stu-id="bed5f-117">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
