---
title: <param> - C# 程式設計指南
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: d16070a82531519dd276b2ea999623017769d716
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789765"
---
# <a name="param-c-programming-guide"></a><span data-ttu-id="12303-102">\<參數>（C# 程式設計指南）</span><span class="sxs-lookup"><span data-stu-id="12303-102">\<param> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="12303-103">語法</span><span class="sxs-lookup"><span data-stu-id="12303-103">Syntax</span></span>

```xml
<param name="name">description</param>
```

## <a name="parameters"></a><span data-ttu-id="12303-104">參數</span><span class="sxs-lookup"><span data-stu-id="12303-104">Parameters</span></span>

- `name`

  <span data-ttu-id="12303-105">方法參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="12303-105">The name of a method parameter.</span></span> <span data-ttu-id="12303-106">以雙引號 (" ") 將名稱括起來。</span><span class="sxs-lookup"><span data-stu-id="12303-106">Enclose the name in double quotation marks (" ").</span></span>

- `description`

  <span data-ttu-id="12303-107">參數的描述。</span><span class="sxs-lookup"><span data-stu-id="12303-107">A description for the parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="12303-108">備註</span><span class="sxs-lookup"><span data-stu-id="12303-108">Remarks</span></span>

<span data-ttu-id="12303-109">\<param> 標記應該在方法宣告的註解中用來描述參數的其中一個方法。</span><span class="sxs-lookup"><span data-stu-id="12303-109">The \<param> tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span> <span data-ttu-id="12303-110">若要記錄多個參數，請使用多個 \<param > 標記。</span><span class="sxs-lookup"><span data-stu-id="12303-110">To document multiple parameters, use multiple \<param> tags.</span></span>

<span data-ttu-id="12303-111">\<param> 標記的文字將會顯示於 IntelliSense (即物件瀏覽器) 以及程式碼結構 Web 報告中。</span><span class="sxs-lookup"><span data-stu-id="12303-111">The text for the \<param> tag will be displayed in IntelliSense, the Object Browser, and in the Code Comment Web Report.</span></span>

<span data-ttu-id="12303-112">使用[-doc](../../language-reference/compiler-options/doc-compiler-option.md)編譯，以處理檔的文檔注釋。</span><span class="sxs-lookup"><span data-stu-id="12303-112">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="12303-113">範例</span><span class="sxs-lookup"><span data-stu-id="12303-113">Example</span></span>

[!code-csharp[csProgGuideDocComments#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#1)]

## <a name="see-also"></a><span data-ttu-id="12303-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="12303-114">See also</span></span>

- [<span data-ttu-id="12303-115">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="12303-115">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="12303-116">建議使用的文件註解標籤</span><span class="sxs-lookup"><span data-stu-id="12303-116">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
