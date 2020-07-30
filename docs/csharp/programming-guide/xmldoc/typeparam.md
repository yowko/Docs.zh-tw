---
title: '<typeparam> -C # 程式設計指南'
description: 瞭解 XML <typeparam> 的相片或視訊。 這個標記用於泛型型別或方法宣告的批註中，以描述型別參數。
ms.date: 07/20/2015
f1_keywords:
- typeparam
helpviewer_keywords:
- <typeparam> C# XML tag
- typeparam C# XML tag
ms.assetid: 9b99d400-e911-4e55-99c6-64367c96aa4f
ms.openlocfilehash: 5e5333e384e8c77b500f74ab7c6038146df6e2c0
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87380783"
---
# <a name="typeparam-c-programming-guide"></a><span data-ttu-id="9893c-105">\<typeparam>（C # 程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="9893c-105">\<typeparam> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="9893c-106">語法</span><span class="sxs-lookup"><span data-stu-id="9893c-106">Syntax</span></span>

```xml
<typeparam name="name">description</typeparam>
```

## <a name="parameters"></a><span data-ttu-id="9893c-107">參數</span><span class="sxs-lookup"><span data-stu-id="9893c-107">Parameters</span></span>

- `name`

  <span data-ttu-id="9893c-108">型別參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="9893c-108">The name of the type parameter.</span></span> <span data-ttu-id="9893c-109">以雙引號 (" ") 將名稱括起來。</span><span class="sxs-lookup"><span data-stu-id="9893c-109">Enclose the name in double quotation marks (" ").</span></span>

- `description`

  <span data-ttu-id="9893c-110">型別參數的描述。</span><span class="sxs-lookup"><span data-stu-id="9893c-110">A description for the type parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="9893c-111">備註</span><span class="sxs-lookup"><span data-stu-id="9893c-111">Remarks</span></span>

<span data-ttu-id="9893c-112">`<typeparam>` 標記應該用於泛型型別或方法宣告的註解中，以描述型別參數。</span><span class="sxs-lookup"><span data-stu-id="9893c-112">The `<typeparam>` tag should be used in the comment for a generic type or method declaration to describe a type parameter.</span></span> <span data-ttu-id="9893c-113">新增泛型型別或方法之每個型別參數的標記。</span><span class="sxs-lookup"><span data-stu-id="9893c-113">Add a tag for each type parameter of the generic type or method.</span></span>

<span data-ttu-id="9893c-114">如需詳細資訊，請參閱[泛型](../generics/index.md)。</span><span class="sxs-lookup"><span data-stu-id="9893c-114">For more information, see [Generics](../generics/index.md).</span></span>

<span data-ttu-id="9893c-115">`<typeparam>` 標記的文字將會顯示於 IntelliSense，即 [Object Browser Window](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser) (物件瀏覽器視窗) 程式碼註解 Web 報告。</span><span class="sxs-lookup"><span data-stu-id="9893c-115">The text for the `<typeparam>` tag will be displayed in IntelliSense, the [Object Browser Window](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser) code comment web report.</span></span>

<span data-ttu-id="9893c-116">使用[-doc](../../language-reference/compiler-options/doc-compiler-option.md)進行編譯，以處理檔案的檔批註。</span><span class="sxs-lookup"><span data-stu-id="9893c-116">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="9893c-117">範例</span><span class="sxs-lookup"><span data-stu-id="9893c-117">Example</span></span>

[!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]

## <a name="see-also"></a><span data-ttu-id="9893c-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9893c-118">See also</span></span>

- [<span data-ttu-id="9893c-119">C# 參考資料</span><span class="sxs-lookup"><span data-stu-id="9893c-119">C# reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="9893c-120">C# 程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="9893c-120">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="9893c-121">建議使用的文件註解標籤</span><span class="sxs-lookup"><span data-stu-id="9893c-121">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
