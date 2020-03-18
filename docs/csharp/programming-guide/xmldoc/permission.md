---
title: <permission> - C# 程式設計指南
ms.date: 07/20/2015
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C# XML tag
- permission C# XML tag
ms.assetid: 769e93fe-8404-443f-bf99-577aa42b6a49
ms.openlocfilehash: 4f76d28d5531c1b9f01fa950589407934cc1244a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "77093470"
---
# <a name="permission-c-programming-guide"></a><span data-ttu-id="655a0-102">\<許可權>（C# 程式設計指南）</span><span class="sxs-lookup"><span data-stu-id="655a0-102">\<permission> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="655a0-103">語法</span><span class="sxs-lookup"><span data-stu-id="655a0-103">Syntax</span></span>

```xml
<permission cref="member">description</permission>
```

## <a name="parameters"></a><span data-ttu-id="655a0-104">參數</span><span class="sxs-lookup"><span data-stu-id="655a0-104">Parameters</span></span>

- <span data-ttu-id="655a0-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="655a0-105">cref = " `member`"</span></span>

  <span data-ttu-id="655a0-106">可從目前編譯環境呼叫的成員或欄位參考。</span><span class="sxs-lookup"><span data-stu-id="655a0-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="655a0-107">編譯器會檢查指定的程式碼項目是否存在，並將 `member` 轉譯為輸出 XML 中的標準項目名稱。</span><span class="sxs-lookup"><span data-stu-id="655a0-107">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="655a0-108">member\*\* 必須出現在雙引號 (" ") 內。</span><span class="sxs-lookup"><span data-stu-id="655a0-108">*member* must appear within double quotation marks (" ").</span></span>

  <span data-ttu-id="655a0-109">有關如何創建對泛型型別的 cref 引用的資訊，請參閱[cref 屬性](./cref-attribute.md)。</span><span class="sxs-lookup"><span data-stu-id="655a0-109">For information on how to create a cref reference to a generic type, see [cref attribute](./cref-attribute.md).</span></span>

- `description`

  <span data-ttu-id="655a0-110">成員存取權的描述。</span><span class="sxs-lookup"><span data-stu-id="655a0-110">A description of the access to the member.</span></span>

## <a name="remarks"></a><span data-ttu-id="655a0-111">備註</span><span class="sxs-lookup"><span data-stu-id="655a0-111">Remarks</span></span>

<span data-ttu-id="655a0-112">\<permission> 標記可讓您記載成員存取權。</span><span class="sxs-lookup"><span data-stu-id="655a0-112">The \<permission> tag lets you document the access of a member.</span></span> <span data-ttu-id="655a0-113"><xref:System.Security.PermissionSet> 類別可讓您指定成員存取權。</span><span class="sxs-lookup"><span data-stu-id="655a0-113">The <xref:System.Security.PermissionSet> class lets you specify access to a member.</span></span>

<span data-ttu-id="655a0-114">使用[-doc](../../language-reference/compiler-options/doc-compiler-option.md)編譯，以處理檔的文檔注釋。</span><span class="sxs-lookup"><span data-stu-id="655a0-114">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="655a0-115">範例</span><span class="sxs-lookup"><span data-stu-id="655a0-115">Example</span></span>

[!code-csharp[csProgGuideDocComments#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#8)]

## <a name="see-also"></a><span data-ttu-id="655a0-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="655a0-116">See also</span></span>

- [<span data-ttu-id="655a0-117">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="655a0-117">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="655a0-118">建議使用的文件註解標籤</span><span class="sxs-lookup"><span data-stu-id="655a0-118">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
