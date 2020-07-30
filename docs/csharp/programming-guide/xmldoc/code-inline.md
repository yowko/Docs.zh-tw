---
title: '<c>-C # 程式設計指南'
description: 瞭解 XML <c> 標記。 此標記會將描述中的單行文字標記為程式碼，而 <code>indicates multiple lines.
ms.date: 07/20/2015
f1_keywords:
- c
- <c>
helpviewer_keywords:
- text, marking as code [C#]
- code, marking text as [C#]
- c C# XML tag
- <c> C# XML tag
ms.assetid: aad5b16e-a29e-445e-bd0d-eea0b138d7b2
ms.openlocfilehash: 78e59e1df4b096782e0a97b6d12c21c843a1cb21
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87382018"
---
# <a name="c-c-programming-guide"></a><span data-ttu-id="24ec9-104">\<c>（C # 程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="24ec9-104">\<c> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="24ec9-105">語法</span><span class="sxs-lookup"><span data-stu-id="24ec9-105">Syntax</span></span>

```xml
<c>text</c>
```

## <a name="parameters"></a><span data-ttu-id="24ec9-106">參數</span><span class="sxs-lookup"><span data-stu-id="24ec9-106">Parameters</span></span>

- `text`

  <span data-ttu-id="24ec9-107">您要指定為程式碼的文字。</span><span class="sxs-lookup"><span data-stu-id="24ec9-107">The text you would like to indicate as code.</span></span>

## <a name="remarks"></a><span data-ttu-id="24ec9-108">備註</span><span class="sxs-lookup"><span data-stu-id="24ec9-108">Remarks</span></span>

<span data-ttu-id="24ec9-109">`<c>`標記可讓您指定描述中的文字應該標記為程式碼。</span><span class="sxs-lookup"><span data-stu-id="24ec9-109">The `<c>` tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="24ec9-110">用 [\<code>](./code.md) 來指示多行作為程式碼。</span><span class="sxs-lookup"><span data-stu-id="24ec9-110">Use [\<code>](./code.md) to indicate multiple lines as code.</span></span>

<span data-ttu-id="24ec9-111">使用[-doc](../../language-reference/compiler-options/doc-compiler-option.md)進行編譯，以處理檔案的檔批註。</span><span class="sxs-lookup"><span data-stu-id="24ec9-111">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="24ec9-112">範例</span><span class="sxs-lookup"><span data-stu-id="24ec9-112">Example</span></span>

[!code-csharp[csProgGuideDocComments#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#2)]
  
## <a name="see-also"></a><span data-ttu-id="24ec9-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="24ec9-113">See also</span></span>

- [<span data-ttu-id="24ec9-114">C# 程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="24ec9-114">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="24ec9-115">建議使用的文件註解標籤</span><span class="sxs-lookup"><span data-stu-id="24ec9-115">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
