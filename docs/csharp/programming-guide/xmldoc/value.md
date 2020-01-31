---
title: <value> - C#程式設計指南
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: 120805346672738e614743ab8c98388b8dbac0f7
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793356"
---
# <a name="value-c-programming-guide"></a><span data-ttu-id="5c6ea-102">\<值 > （C#程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="5c6ea-102">\<value> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="5c6ea-103">語法</span><span class="sxs-lookup"><span data-stu-id="5c6ea-103">Syntax</span></span>

```xml
<value>property-description</value>
```

## <a name="parameters"></a><span data-ttu-id="5c6ea-104">參數</span><span class="sxs-lookup"><span data-stu-id="5c6ea-104">Parameters</span></span>

- `property-description`

  <span data-ttu-id="5c6ea-105">屬性的描述。</span><span class="sxs-lookup"><span data-stu-id="5c6ea-105">A description for the property.</span></span>

## <a name="remarks"></a><span data-ttu-id="5c6ea-106">備註</span><span class="sxs-lookup"><span data-stu-id="5c6ea-106">Remarks</span></span>

<span data-ttu-id="5c6ea-107">\<value> 標記可讓您描述屬性所代表的值。</span><span class="sxs-lookup"><span data-stu-id="5c6ea-107">The \<value> tag lets you describe the value that a property represents.</span></span> <span data-ttu-id="5c6ea-108">請注意，當您在 Visual Studio .NET 開發環境中透過程式碼精靈新增屬性時，會新增新屬性的 [\<summary>](./summary.md) 標記。</span><span class="sxs-lookup"><span data-stu-id="5c6ea-108">Note that when you add a property via code wizard in the Visual Studio .NET development environment, it will add a [\<summary>](./summary.md) tag for the new property.</span></span> <span data-ttu-id="5c6ea-109">您接著應該手動新增 \<value> 標記，來描述屬性所代表的值。</span><span class="sxs-lookup"><span data-stu-id="5c6ea-109">You should then manually add a \<value> tag to describe the value that the property represents.</span></span>

<span data-ttu-id="5c6ea-110">使用 [-doc](../../language-reference/compiler-options/doc-compiler-option.md) 編譯可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="5c6ea-110">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="5c6ea-111">範例</span><span class="sxs-lookup"><span data-stu-id="5c6ea-111">Example</span></span>

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#14)]

## <a name="see-also"></a><span data-ttu-id="5c6ea-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="5c6ea-112">See also</span></span>

- [<span data-ttu-id="5c6ea-113">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="5c6ea-113">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="5c6ea-114">建議使用的檔註解標記</span><span class="sxs-lookup"><span data-stu-id="5c6ea-114">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
