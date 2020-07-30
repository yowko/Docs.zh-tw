---
title: '<seealso> -C # 程式設計指南'
description: 瞭解如何使用 XML <seealso> 的相片或視訊。 此標籤可讓您指定您可能想要出現在「另請參閱」一節中的文字。
ms.date: 07/20/2015
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
ms.openlocfilehash: e8618ef352a4fa7f0fd4c88733c6568b0e12e376
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87380640"
---
# <a name="seealso-c-programming-guide"></a><span data-ttu-id="54008-105">\<seealso>（C # 程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="54008-105">\<seealso> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="54008-106">語法</span><span class="sxs-lookup"><span data-stu-id="54008-106">Syntax</span></span>

```xml
<seealso cref="member"/>
```

## <a name="parameters"></a><span data-ttu-id="54008-107">參數</span><span class="sxs-lookup"><span data-stu-id="54008-107">Parameters</span></span>

- <span data-ttu-id="54008-108">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="54008-108">cref = " `member`"</span></span>

  <span data-ttu-id="54008-109">可從目前編譯環境呼叫的成員或欄位參考。</span><span class="sxs-lookup"><span data-stu-id="54008-109">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="54008-110">編譯器會檢查指定的程式碼項目是否存在，並將 `member` 傳遞給輸出 XML 中的項目名稱。`member`</span><span class="sxs-lookup"><span data-stu-id="54008-110">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.`member`</span></span> <span data-ttu-id="54008-111">必須出現在雙引號 (" ") 內。</span><span class="sxs-lookup"><span data-stu-id="54008-111">must appear within double quotation marks (" ").</span></span>

  <span data-ttu-id="54008-112">如需有關如何建立泛型型別之 cref 參考的詳細資訊，請參閱[cref 屬性](./cref-attribute.md)。</span><span class="sxs-lookup"><span data-stu-id="54008-112">For information on how to create a cref reference to a generic type, see [cref attribute](./cref-attribute.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="54008-113">備註</span><span class="sxs-lookup"><span data-stu-id="54008-113">Remarks</span></span>

<span data-ttu-id="54008-114">標籤 `<seealso>` 可讓您指定您可能想要出現在 [另請參閱] 區段中的文字。</span><span class="sxs-lookup"><span data-stu-id="54008-114">The `<seealso>` tag lets you specify the text that you might want to appear in a See Also section.</span></span> <span data-ttu-id="54008-115">用 [\<see>](./see.md) 來指定文字內的連結。</span><span class="sxs-lookup"><span data-stu-id="54008-115">Use [\<see>](./see.md) to specify a link from within text.</span></span>

<span data-ttu-id="54008-116">使用[-doc](../../language-reference/compiler-options/doc-compiler-option.md)進行編譯，以處理檔案的檔批註。</span><span class="sxs-lookup"><span data-stu-id="54008-116">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="54008-117">範例</span><span class="sxs-lookup"><span data-stu-id="54008-117">Example</span></span>

<span data-ttu-id="54008-118">如需使用的範例，請參閱 [\<summary>](./summary.md) \<seealso> 。</span><span class="sxs-lookup"><span data-stu-id="54008-118">See [\<summary>](./summary.md) for an example of using \<seealso>.</span></span>

## <a name="see-also"></a><span data-ttu-id="54008-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="54008-119">See also</span></span>

- [<span data-ttu-id="54008-120">C# 程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="54008-120">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="54008-121">建議使用的文件註解標籤</span><span class="sxs-lookup"><span data-stu-id="54008-121">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
