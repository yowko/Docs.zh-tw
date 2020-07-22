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
ms.openlocfilehash: 731e42a6d4d354b043a56dbe150bb03a693a9454
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/21/2020
ms.locfileid: "86863782"
---
# <a name="see-c-programming-guide"></a><span data-ttu-id="34412-102">\<see>（C # 程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="34412-102">\<see> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="34412-103">語法</span><span class="sxs-lookup"><span data-stu-id="34412-103">Syntax</span></span>

```xml
<see cref="member"/>
```

## <a name="parameters"></a><span data-ttu-id="34412-104">參數</span><span class="sxs-lookup"><span data-stu-id="34412-104">Parameters</span></span>

- <span data-ttu-id="34412-105">cref = " `member` "</span><span class="sxs-lookup"><span data-stu-id="34412-105">cref = "`member`"</span></span>

  <span data-ttu-id="34412-106">可從目前編譯環境呼叫的成員或欄位參考。</span><span class="sxs-lookup"><span data-stu-id="34412-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="34412-107">編譯器會檢查指定的程式碼項目是否存在，並將 `member` 傳遞給輸出 XML 中的項目名稱。</span><span class="sxs-lookup"><span data-stu-id="34412-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="34412-108">將 *member* 置於雙引號 (" ") 內。</span><span class="sxs-lookup"><span data-stu-id="34412-108">Place *member* within double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="34412-109">備註</span><span class="sxs-lookup"><span data-stu-id="34412-109">Remarks</span></span>

<span data-ttu-id="34412-110">`<see>`標記可讓您指定文字中的連結。</span><span class="sxs-lookup"><span data-stu-id="34412-110">The `<see>` tag lets you specify a link from within text.</span></span> <span data-ttu-id="34412-111">用 [\<seealso>](./seealso.md) 來指示文字應該放在 [另請參閱] 區段中。</span><span class="sxs-lookup"><span data-stu-id="34412-111">Use [\<seealso>](./seealso.md) to indicate that text should be placed in a See Also section.</span></span> <span data-ttu-id="34412-112">使用 [cref 屬性](./cref-attribute.md)，建立程式碼項目之文件頁面的內部超連結。</span><span class="sxs-lookup"><span data-stu-id="34412-112">Use the [cref Attribute](./cref-attribute.md) to create internal hyperlinks to documentation pages for code elements.</span></span> <span data-ttu-id="34412-113">此外， ``href`` 是有效的屬性，可做為超連結。</span><span class="sxs-lookup"><span data-stu-id="34412-113">Also, ``href`` is a valid Attribute that will function as a hyperlink.</span></span>

<span data-ttu-id="34412-114">使用[-doc](../../language-reference/compiler-options/doc-compiler-option.md)進行編譯，以處理檔案的檔批註。</span><span class="sxs-lookup"><span data-stu-id="34412-114">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

<span data-ttu-id="34412-115">下列範例會顯示 `<see>` 摘要區段內的標記。</span><span class="sxs-lookup"><span data-stu-id="34412-115">The following example shows a `<see>` tag within a summary section.</span></span>

[!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]

## <a name="see-also"></a><span data-ttu-id="34412-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="34412-116">See also</span></span>

- [<span data-ttu-id="34412-117">C# 程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="34412-117">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="34412-118">建議使用的文件註解標籤</span><span class="sxs-lookup"><span data-stu-id="34412-118">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
