---
title: '<value> -C # 程式設計指南'
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: bd6630a8d5894fda39ad289c8dd584f6d84e5490
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287190"
---
# <a name="value-c-programming-guide"></a><span data-ttu-id="b933f-102">\<value>（C # 程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="b933f-102">\<value> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="b933f-103">語法</span><span class="sxs-lookup"><span data-stu-id="b933f-103">Syntax</span></span>

```xml
<value>property-description</value>
```

## <a name="parameters"></a><span data-ttu-id="b933f-104">參數</span><span class="sxs-lookup"><span data-stu-id="b933f-104">Parameters</span></span>

- `property-description`

  <span data-ttu-id="b933f-105">屬性的描述。</span><span class="sxs-lookup"><span data-stu-id="b933f-105">A description for the property.</span></span>

## <a name="remarks"></a><span data-ttu-id="b933f-106">備註</span><span class="sxs-lookup"><span data-stu-id="b933f-106">Remarks</span></span>

<span data-ttu-id="b933f-107">`<value>`標記可讓您描述屬性所代表的值。</span><span class="sxs-lookup"><span data-stu-id="b933f-107">The `<value>` tag lets you describe the value that a property represents.</span></span> <span data-ttu-id="b933f-108">當您透過 Visual Studio .NET 開發環境中的程式碼 wizard 加入屬性時，會加入 [\<summary>](./summary.md) 新屬性的標記。</span><span class="sxs-lookup"><span data-stu-id="b933f-108">When you add a property via code wizard in the Visual Studio .NET development environment, it adds a [\<summary>](./summary.md) tag for the new property.</span></span> <span data-ttu-id="b933f-109">接著，您應該手動加入 `<value>` 標記來描述屬性所代表的值。</span><span class="sxs-lookup"><span data-stu-id="b933f-109">You should then manually add a `<value>` tag to describe the value that the property represents.</span></span>

<span data-ttu-id="b933f-110">使用[-doc](../../language-reference/compiler-options/doc-compiler-option.md)進行編譯，以處理檔案的檔批註。</span><span class="sxs-lookup"><span data-stu-id="b933f-110">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="b933f-111">範例</span><span class="sxs-lookup"><span data-stu-id="b933f-111">Example</span></span>

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#14)]

## <a name="see-also"></a><span data-ttu-id="b933f-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b933f-112">See also</span></span>

- [<span data-ttu-id="b933f-113">C# 程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="b933f-113">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="b933f-114">建議使用的文件註解標籤</span><span class="sxs-lookup"><span data-stu-id="b933f-114">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
