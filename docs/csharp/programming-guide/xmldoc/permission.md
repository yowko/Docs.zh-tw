---
title: '<permission> -C # 程式設計指南'
description: 瞭解 XML <permission> 的相片或視訊。 此標記可讓您記錄成員的存取權，而 PermissionSet 類別可讓您指定成員的存取權。
ms.date: 07/20/2015
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C# XML tag
- permission C# XML tag
ms.assetid: 769e93fe-8404-443f-bf99-577aa42b6a49
ms.openlocfilehash: 38c87505b8b2973875e474ffd296dc02b7fb9de6
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381719"
---
# <a name="permission-c-programming-guide"></a><span data-ttu-id="75164-105">\<permission>（C # 程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="75164-105">\<permission> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="75164-106">語法</span><span class="sxs-lookup"><span data-stu-id="75164-106">Syntax</span></span>

```xml
<permission cref="member">description</permission>
```

## <a name="parameters"></a><span data-ttu-id="75164-107">參數</span><span class="sxs-lookup"><span data-stu-id="75164-107">Parameters</span></span>

- <span data-ttu-id="75164-108">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="75164-108">cref = " `member`"</span></span>

  <span data-ttu-id="75164-109">可從目前編譯環境呼叫的成員或欄位參考。</span><span class="sxs-lookup"><span data-stu-id="75164-109">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="75164-110">編譯器會檢查指定的程式碼項目是否存在，並將 `member` 轉譯為輸出 XML 中的標準項目名稱。</span><span class="sxs-lookup"><span data-stu-id="75164-110">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="75164-111">member\*\* 必須出現在雙引號 (" ") 內。</span><span class="sxs-lookup"><span data-stu-id="75164-111">*member* must appear within double quotation marks (" ").</span></span>

  <span data-ttu-id="75164-112">如需有關如何建立泛型型別之 cref 參考的詳細資訊，請參閱[cref 屬性](./cref-attribute.md)。</span><span class="sxs-lookup"><span data-stu-id="75164-112">For information on how to create a cref reference to a generic type, see [cref attribute](./cref-attribute.md).</span></span>

- `description`

  <span data-ttu-id="75164-113">成員存取權的描述。</span><span class="sxs-lookup"><span data-stu-id="75164-113">A description of the access to the member.</span></span>

## <a name="remarks"></a><span data-ttu-id="75164-114">備註</span><span class="sxs-lookup"><span data-stu-id="75164-114">Remarks</span></span>

<span data-ttu-id="75164-115">`<permission>`標記可讓您記錄成員的存取權。</span><span class="sxs-lookup"><span data-stu-id="75164-115">The `<permission>` tag lets you document the access of a member.</span></span> <span data-ttu-id="75164-116"><xref:System.Security.PermissionSet> 類別可讓您指定成員存取權。</span><span class="sxs-lookup"><span data-stu-id="75164-116">The <xref:System.Security.PermissionSet> class lets you specify access to a member.</span></span>

<span data-ttu-id="75164-117">使用[-doc](../../language-reference/compiler-options/doc-compiler-option.md)進行編譯，以處理檔案的檔批註。</span><span class="sxs-lookup"><span data-stu-id="75164-117">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="75164-118">範例</span><span class="sxs-lookup"><span data-stu-id="75164-118">Example</span></span>

[!code-csharp[csProgGuideDocComments#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#8)]

## <a name="see-also"></a><span data-ttu-id="75164-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="75164-119">See also</span></span>

- [<span data-ttu-id="75164-120">C# 程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="75164-120">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="75164-121">建議使用的文件註解標籤</span><span class="sxs-lookup"><span data-stu-id="75164-121">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
