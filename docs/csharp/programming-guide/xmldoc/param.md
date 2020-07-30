---
title: '<param> -C # 程式設計指南'
description: 瞭解 XML <param> 的相片或視訊。 此標記會用於方法宣告的批註中，以描述方法的其中一個參數。
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: a9e3b2e86528afcbe1330788e248f0143efb5c1b
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381550"
---
# <a name="param-c-programming-guide"></a><span data-ttu-id="bb35c-105">\<param>（C # 程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="bb35c-105">\<param> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="bb35c-106">語法</span><span class="sxs-lookup"><span data-stu-id="bb35c-106">Syntax</span></span>

```xml
<param name="name">description</param>
```

## <a name="parameters"></a><span data-ttu-id="bb35c-107">參數</span><span class="sxs-lookup"><span data-stu-id="bb35c-107">Parameters</span></span>

- `name`

  <span data-ttu-id="bb35c-108">方法參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="bb35c-108">The name of a method parameter.</span></span> <span data-ttu-id="bb35c-109">以雙引號 (" ") 將名稱括起來。</span><span class="sxs-lookup"><span data-stu-id="bb35c-109">Enclose the name in double quotation marks (" ").</span></span>

- `description`

  <span data-ttu-id="bb35c-110">參數的描述。</span><span class="sxs-lookup"><span data-stu-id="bb35c-110">A description for the parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="bb35c-111">備註</span><span class="sxs-lookup"><span data-stu-id="bb35c-111">Remarks</span></span>

<span data-ttu-id="bb35c-112">`<param>`標記應該用於方法宣告的批註中，以描述方法的其中一個參數。</span><span class="sxs-lookup"><span data-stu-id="bb35c-112">The `<param>` tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span> <span data-ttu-id="bb35c-113">若要記錄多個參數，請使用多個 `<param>` 標記。</span><span class="sxs-lookup"><span data-stu-id="bb35c-113">To document multiple parameters, use multiple `<param>` tags.</span></span>

<span data-ttu-id="bb35c-114">標記的文字 `<param>` 會顯示在 IntelliSense、物件瀏覽器和程式碼批註 Web 報告中。</span><span class="sxs-lookup"><span data-stu-id="bb35c-114">The text for the `<param>` tag is displayed in IntelliSense, the Object Browser, and the Code Comment Web Report.</span></span>

<span data-ttu-id="bb35c-115">使用[-doc](../../language-reference/compiler-options/doc-compiler-option.md)進行編譯，以處理檔案的檔批註。</span><span class="sxs-lookup"><span data-stu-id="bb35c-115">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="bb35c-116">範例</span><span class="sxs-lookup"><span data-stu-id="bb35c-116">Example</span></span>

[!code-csharp[csProgGuideDocComments#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#1)]

## <a name="see-also"></a><span data-ttu-id="bb35c-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb35c-117">See also</span></span>

- [<span data-ttu-id="bb35c-118">C# 程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="bb35c-118">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="bb35c-119">建議使用的文件註解標籤</span><span class="sxs-lookup"><span data-stu-id="bb35c-119">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
