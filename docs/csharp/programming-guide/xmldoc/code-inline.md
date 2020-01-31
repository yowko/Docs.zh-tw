---
title: <c> 程式C#設計指南
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
ms.openlocfilehash: d5b28ee6db52d191f8454592d792ac0a1e1dc73b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793459"
---
# <a name="c-c-programming-guide"></a><span data-ttu-id="bcd17-102">\<c > （C#程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="bcd17-102">\<c> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="bcd17-103">語法</span><span class="sxs-lookup"><span data-stu-id="bcd17-103">Syntax</span></span>

```xml
<c>text</c>
```

## <a name="parameters"></a><span data-ttu-id="bcd17-104">參數</span><span class="sxs-lookup"><span data-stu-id="bcd17-104">Parameters</span></span>

- `text`

  <span data-ttu-id="bcd17-105">您要指定為程式碼的文字。</span><span class="sxs-lookup"><span data-stu-id="bcd17-105">The text you would like to indicate as code.</span></span>

## <a name="remarks"></a><span data-ttu-id="bcd17-106">備註</span><span class="sxs-lookup"><span data-stu-id="bcd17-106">Remarks</span></span>

<span data-ttu-id="bcd17-107">\<c> 標記可讓您在一段描述中指出應該標記為程式碼的文字。</span><span class="sxs-lookup"><span data-stu-id="bcd17-107">The \<c> tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="bcd17-108">請使用 [\<code>](./code.md) 將多行指定為程式碼。</span><span class="sxs-lookup"><span data-stu-id="bcd17-108">Use [\<code>](./code.md) to indicate multiple lines as code.</span></span>

<span data-ttu-id="bcd17-109">使用 [-doc](../../language-reference/compiler-options/doc-compiler-option.md) 編譯可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="bcd17-109">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="bcd17-110">範例</span><span class="sxs-lookup"><span data-stu-id="bcd17-110">Example</span></span>

[!code-csharp[csProgGuideDocComments#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#2)]
  
## <a name="see-also"></a><span data-ttu-id="bcd17-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="bcd17-111">See also</span></span>

- [<span data-ttu-id="bcd17-112">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="bcd17-112">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="bcd17-113">建議使用的檔註解標記</span><span class="sxs-lookup"><span data-stu-id="bcd17-113">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
