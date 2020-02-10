---
title: <seealso> - C#程式設計指南
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
ms.openlocfilehash: e24d5910ab21f01aebb5a32ce7646cf56886a81a
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2020
ms.locfileid: "77093457"
---
# <a name="seealso-c-programming-guide"></a><span data-ttu-id="16601-102">\<seealso > （C#程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="16601-102">\<seealso> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="16601-103">語法</span><span class="sxs-lookup"><span data-stu-id="16601-103">Syntax</span></span>

```xml
<seealso cref="member"/>
```

## <a name="parameters"></a><span data-ttu-id="16601-104">參數</span><span class="sxs-lookup"><span data-stu-id="16601-104">Parameters</span></span>

- <span data-ttu-id="16601-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="16601-105">cref = " `member`"</span></span>

  <span data-ttu-id="16601-106">可從目前編譯環境呼叫的成員或欄位參考。</span><span class="sxs-lookup"><span data-stu-id="16601-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="16601-107">編譯器會檢查指定的程式碼項目是否存在，並將 `member` 傳遞給輸出 XML 中的項目名稱。`member`</span><span class="sxs-lookup"><span data-stu-id="16601-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.`member`</span></span> <span data-ttu-id="16601-108">必須出現在雙引號 (" ") 內。</span><span class="sxs-lookup"><span data-stu-id="16601-108">must appear within double quotation marks (" ").</span></span>

  <span data-ttu-id="16601-109">如需有關如何建立泛型型別之 cref 參考的詳細資訊，請參閱[cref 屬性](./cref-attribute.md)。</span><span class="sxs-lookup"><span data-stu-id="16601-109">For information on how to create a cref reference to a generic type, see [cref attribute](./cref-attribute.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="16601-110">備註</span><span class="sxs-lookup"><span data-stu-id="16601-110">Remarks</span></span>

<span data-ttu-id="16601-111">\<seealso> 標記可讓您指定要顯示在＜請參閱＞一節中的文字。</span><span class="sxs-lookup"><span data-stu-id="16601-111">The \<seealso> tag lets you specify the text that you might want to appear in a See Also section.</span></span> <span data-ttu-id="16601-112">使用 [\<see>](./see.md)，以在文字內指定連結。</span><span class="sxs-lookup"><span data-stu-id="16601-112">Use [\<see>](./see.md) to specify a link from within text.</span></span>

<span data-ttu-id="16601-113">使用 [-doc](../../language-reference/compiler-options/doc-compiler-option.md) 編譯可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="16601-113">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="16601-114">範例</span><span class="sxs-lookup"><span data-stu-id="16601-114">Example</span></span>

<span data-ttu-id="16601-115">如需使用 [seealso> 的範例，請參閱 \<](./summary.md)summary>\<。</span><span class="sxs-lookup"><span data-stu-id="16601-115">See [\<summary>](./summary.md) for an example of using \<seealso>.</span></span>

## <a name="see-also"></a><span data-ttu-id="16601-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="16601-116">See also</span></span>

- [<span data-ttu-id="16601-117">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="16601-117">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="16601-118">建議使用的檔註解標記</span><span class="sxs-lookup"><span data-stu-id="16601-118">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
