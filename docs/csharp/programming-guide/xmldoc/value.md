---
title: '<value> -C # 程式設計指南'
description: 瞭解 XML <value> 的相片或視訊。 此標記可讓您描述屬性所代表的值。
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: d8294b477d7067653c71d1ec2047a85a0bfe6d02
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87380770"
---
# <a name="value-c-programming-guide"></a><span data-ttu-id="b09d7-105">\<value>（C # 程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="b09d7-105">\<value> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="b09d7-106">語法</span><span class="sxs-lookup"><span data-stu-id="b09d7-106">Syntax</span></span>

```xml
<value>property-description</value>
```

## <a name="parameters"></a><span data-ttu-id="b09d7-107">參數</span><span class="sxs-lookup"><span data-stu-id="b09d7-107">Parameters</span></span>

- `property-description`

  <span data-ttu-id="b09d7-108">屬性的描述。</span><span class="sxs-lookup"><span data-stu-id="b09d7-108">A description for the property.</span></span>

## <a name="remarks"></a><span data-ttu-id="b09d7-109">備註</span><span class="sxs-lookup"><span data-stu-id="b09d7-109">Remarks</span></span>

<span data-ttu-id="b09d7-110">`<value>`標記可讓您描述屬性所代表的值。</span><span class="sxs-lookup"><span data-stu-id="b09d7-110">The `<value>` tag lets you describe the value that a property represents.</span></span> <span data-ttu-id="b09d7-111">當您透過 Visual Studio .NET 開發環境中的程式碼 wizard 加入屬性時，會加入 [\<summary>](./summary.md) 新屬性的標記。</span><span class="sxs-lookup"><span data-stu-id="b09d7-111">When you add a property via code wizard in the Visual Studio .NET development environment, it adds a [\<summary>](./summary.md) tag for the new property.</span></span> <span data-ttu-id="b09d7-112">接著，您應該手動加入 `<value>` 標記來描述屬性所代表的值。</span><span class="sxs-lookup"><span data-stu-id="b09d7-112">You should then manually add a `<value>` tag to describe the value that the property represents.</span></span>

<span data-ttu-id="b09d7-113">使用[-doc](../../language-reference/compiler-options/doc-compiler-option.md)進行編譯，以處理檔案的檔批註。</span><span class="sxs-lookup"><span data-stu-id="b09d7-113">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="b09d7-114">範例</span><span class="sxs-lookup"><span data-stu-id="b09d7-114">Example</span></span>

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#14)]

## <a name="see-also"></a><span data-ttu-id="b09d7-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b09d7-115">See also</span></span>

- [<span data-ttu-id="b09d7-116">C# 程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="b09d7-116">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="b09d7-117">建議使用的文件註解標籤</span><span class="sxs-lookup"><span data-stu-id="b09d7-117">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
