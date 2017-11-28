---
title: "&lt;value&gt; (C# 程式設計手冊)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9ea900c21c2c0477c626be5eff2403312d9e8609
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltvaluegt-c-programming-guide"></a><span data-ttu-id="c341e-102">&lt;value&gt; (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="c341e-102">&lt;value&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="c341e-103">語法</span><span class="sxs-lookup"><span data-stu-id="c341e-103">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c341e-104">參數</span><span class="sxs-lookup"><span data-stu-id="c341e-104">Parameters</span></span>  
 `property-description`  
 <span data-ttu-id="c341e-105">屬性的描述。</span><span class="sxs-lookup"><span data-stu-id="c341e-105">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c341e-106">備註</span><span class="sxs-lookup"><span data-stu-id="c341e-106">Remarks</span></span>  
 <span data-ttu-id="c341e-107">\<value> 標記可讓您描述屬性所代表的值。</span><span class="sxs-lookup"><span data-stu-id="c341e-107">The \<value> tag lets you describe the value that a property represents.</span></span> <span data-ttu-id="c341e-108">請注意，當您在 Visual Studio .NET 開發環境中透過程式碼精靈新增屬性時，會新增新屬性的 [\<summary>](../../../csharp/programming-guide/xmldoc/summary.md) 標記。</span><span class="sxs-lookup"><span data-stu-id="c341e-108">Note that when you add a property via code wizard in the Visual Studio .NET development environment, it will add a [\<summary>](../../../csharp/programming-guide/xmldoc/summary.md) tag for the new property.</span></span> <span data-ttu-id="c341e-109">您接著應該手動新增 \<value> 標記，來描述屬性所代表的值。</span><span class="sxs-lookup"><span data-stu-id="c341e-109">You should then manually add a \<value> tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="c341e-110">編譯搭配 [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) 可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="c341e-110">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c341e-111">範例</span><span class="sxs-lookup"><span data-stu-id="c341e-111">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#14](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/value_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="c341e-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c341e-112">See Also</span></span>  
 [<span data-ttu-id="c341e-113">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="c341e-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c341e-114">建議使用的文件註解標籤</span><span class="sxs-lookup"><span data-stu-id="c341e-114">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
