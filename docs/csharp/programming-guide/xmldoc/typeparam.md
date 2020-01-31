---
title: <typeparam> - C#程式設計指南
ms.date: 07/20/2015
f1_keywords:
- typeparam
helpviewer_keywords:
- <typeparam> C# XML tag
- typeparam C# XML tag
ms.assetid: 9b99d400-e911-4e55-99c6-64367c96aa4f
ms.openlocfilehash: 867ecacf58f95533395ded203a8f17bc92558ccf
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793358"
---
# <a name="typeparam-c-programming-guide"></a><span data-ttu-id="dbdeb-102">\<typeparam > （C#程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="dbdeb-102">\<typeparam> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="dbdeb-103">語法</span><span class="sxs-lookup"><span data-stu-id="dbdeb-103">Syntax</span></span>

```xml
<typeparam name="name">description</typeparam>
```

## <a name="parameters"></a><span data-ttu-id="dbdeb-104">參數</span><span class="sxs-lookup"><span data-stu-id="dbdeb-104">Parameters</span></span>

- `name`

  <span data-ttu-id="dbdeb-105">型別參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="dbdeb-105">The name of the type parameter.</span></span> <span data-ttu-id="dbdeb-106">以雙引號 (" ") 將名稱括起來。</span><span class="sxs-lookup"><span data-stu-id="dbdeb-106">Enclose the name in double quotation marks (" ").</span></span>

- `description`

  <span data-ttu-id="dbdeb-107">型別參數的描述。</span><span class="sxs-lookup"><span data-stu-id="dbdeb-107">A description for the type parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="dbdeb-108">備註</span><span class="sxs-lookup"><span data-stu-id="dbdeb-108">Remarks</span></span>

<span data-ttu-id="dbdeb-109">`<typeparam>` 標記應該用於泛型型別或方法宣告的註解中，以描述型別參數。</span><span class="sxs-lookup"><span data-stu-id="dbdeb-109">The `<typeparam>` tag should be used in the comment for a generic type or method declaration to describe a type parameter.</span></span> <span data-ttu-id="dbdeb-110">新增泛型型別或方法之每個型別參數的標記。</span><span class="sxs-lookup"><span data-stu-id="dbdeb-110">Add a tag for each type parameter of the generic type or method.</span></span>

<span data-ttu-id="dbdeb-111">如需詳細資訊，請參閱[泛型](../generics/index.md)。</span><span class="sxs-lookup"><span data-stu-id="dbdeb-111">For more information, see [Generics](../generics/index.md).</span></span>

<span data-ttu-id="dbdeb-112">`<typeparam>` 標記的文字將會顯示於 IntelliSense，即 [Object Browser Window](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser) (物件瀏覽器視窗) 程式碼註解 Web 報告。</span><span class="sxs-lookup"><span data-stu-id="dbdeb-112">The text for the `<typeparam>` tag will be displayed in IntelliSense, the [Object Browser Window](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser) code comment web report.</span></span>

<span data-ttu-id="dbdeb-113">使用 [-doc](../../language-reference/compiler-options/doc-compiler-option.md) 編譯可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="dbdeb-113">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="dbdeb-114">範例</span><span class="sxs-lookup"><span data-stu-id="dbdeb-114">Example</span></span>

[!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]

## <a name="see-also"></a><span data-ttu-id="dbdeb-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="dbdeb-115">See also</span></span>

- [<span data-ttu-id="dbdeb-116">C# 參考</span><span class="sxs-lookup"><span data-stu-id="dbdeb-116">C# reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="dbdeb-117">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="dbdeb-117">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="dbdeb-118">建議使用的檔註解標記</span><span class="sxs-lookup"><span data-stu-id="dbdeb-118">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
