---
title: '<param> -C # 程式設計指南'
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: 396ed716c246091a674268020261069f36dd2be8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287320"
---
# <a name="param-c-programming-guide"></a><span data-ttu-id="eec5e-102">\<param>（C # 程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="eec5e-102">\<param> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="eec5e-103">語法</span><span class="sxs-lookup"><span data-stu-id="eec5e-103">Syntax</span></span>

```xml
<param name="name">description</param>
```

## <a name="parameters"></a><span data-ttu-id="eec5e-104">參數</span><span class="sxs-lookup"><span data-stu-id="eec5e-104">Parameters</span></span>

- `name`

  <span data-ttu-id="eec5e-105">方法參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="eec5e-105">The name of a method parameter.</span></span> <span data-ttu-id="eec5e-106">以雙引號 (" ") 將名稱括起來。</span><span class="sxs-lookup"><span data-stu-id="eec5e-106">Enclose the name in double quotation marks (" ").</span></span>

- `description`

  <span data-ttu-id="eec5e-107">參數的描述。</span><span class="sxs-lookup"><span data-stu-id="eec5e-107">A description for the parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="eec5e-108">備註</span><span class="sxs-lookup"><span data-stu-id="eec5e-108">Remarks</span></span>

<span data-ttu-id="eec5e-109">`<param>`標記應該用於方法宣告的批註中，以描述方法的其中一個參數。</span><span class="sxs-lookup"><span data-stu-id="eec5e-109">The `<param>` tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span> <span data-ttu-id="eec5e-110">若要記錄多個參數，請使用多個 `<param>` 標記。</span><span class="sxs-lookup"><span data-stu-id="eec5e-110">To document multiple parameters, use multiple `<param>` tags.</span></span>

<span data-ttu-id="eec5e-111">標記的文字 `<param>` 會顯示在 IntelliSense、物件瀏覽器和程式碼批註 Web 報告中。</span><span class="sxs-lookup"><span data-stu-id="eec5e-111">The text for the `<param>` tag is displayed in IntelliSense, the Object Browser, and the Code Comment Web Report.</span></span>

<span data-ttu-id="eec5e-112">使用[-doc](../../language-reference/compiler-options/doc-compiler-option.md)進行編譯，以處理檔案的檔批註。</span><span class="sxs-lookup"><span data-stu-id="eec5e-112">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="eec5e-113">範例</span><span class="sxs-lookup"><span data-stu-id="eec5e-113">Example</span></span>

[!code-csharp[csProgGuideDocComments#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#1)]

## <a name="see-also"></a><span data-ttu-id="eec5e-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eec5e-114">See also</span></span>

- [<span data-ttu-id="eec5e-115">C# 程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="eec5e-115">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="eec5e-116">建議使用的文件註解標籤</span><span class="sxs-lookup"><span data-stu-id="eec5e-116">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
