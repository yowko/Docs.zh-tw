---
title: <value> - C# 程式設計指南
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: 7f82008d000bf0316b505bfc5d40e9e64b2685a3
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57465189"
---
# <a name="value-c-programming-guide"></a><span data-ttu-id="db0b7-102">\<value> (C# 程式設計指南)</span><span class="sxs-lookup"><span data-stu-id="db0b7-102">\<value> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="db0b7-103">語法</span><span class="sxs-lookup"><span data-stu-id="db0b7-103">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
## <a name="parameters"></a><span data-ttu-id="db0b7-104">參數</span><span class="sxs-lookup"><span data-stu-id="db0b7-104">Parameters</span></span>  
 `property-description`  
 <span data-ttu-id="db0b7-105">屬性的描述。</span><span class="sxs-lookup"><span data-stu-id="db0b7-105">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="db0b7-106">備註</span><span class="sxs-lookup"><span data-stu-id="db0b7-106">Remarks</span></span>  
 <span data-ttu-id="db0b7-107">\<value> 標記可讓您描述屬性所代表的值。</span><span class="sxs-lookup"><span data-stu-id="db0b7-107">The \<value> tag lets you describe the value that a property represents.</span></span> <span data-ttu-id="db0b7-108">請注意，當您在 Visual Studio .NET 開發環境中透過程式碼精靈新增屬性時，會新增新屬性的 [\<summary>](../../../csharp/programming-guide/xmldoc/summary.md) 標記。</span><span class="sxs-lookup"><span data-stu-id="db0b7-108">Note that when you add a property via code wizard in the Visual Studio .NET development environment, it will add a [\<summary>](../../../csharp/programming-guide/xmldoc/summary.md) tag for the new property.</span></span> <span data-ttu-id="db0b7-109">您接著應該手動新增 \<value> 標記，來描述屬性所代表的值。</span><span class="sxs-lookup"><span data-stu-id="db0b7-109">You should then manually add a \<value> tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="db0b7-110">編譯搭配 [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) 可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="db0b7-110">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="db0b7-111">範例</span><span class="sxs-lookup"><span data-stu-id="db0b7-111">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#14)]  
  
## <a name="see-also"></a><span data-ttu-id="db0b7-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db0b7-112">See also</span></span>

- [<span data-ttu-id="db0b7-113">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="db0b7-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="db0b7-114">建議使用的文件註解標籤</span><span class="sxs-lookup"><span data-stu-id="db0b7-114">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
