---
title: <typeparam> - C# 程式設計指南
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- typeparam
helpviewer_keywords:
- <typeparam> C# XML tag
- typeparam C# XML tag
ms.assetid: 9b99d400-e911-4e55-99c6-64367c96aa4f
ms.openlocfilehash: 08f9cf42f32c48e5dca09fc1141c55f6ba8af109
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55266269"
---
# <a name="typeparam-c-programming-guide"></a><span data-ttu-id="22d01-102">\<typeparam> (C# 程式設計指南)</span><span class="sxs-lookup"><span data-stu-id="22d01-102">\<typeparam> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="22d01-103">語法</span><span class="sxs-lookup"><span data-stu-id="22d01-103">Syntax</span></span>  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="22d01-104">參數</span><span class="sxs-lookup"><span data-stu-id="22d01-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="22d01-105">型別參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="22d01-105">The name of the type parameter.</span></span> <span data-ttu-id="22d01-106">以雙引號 (" ") 括住名稱。</span><span class="sxs-lookup"><span data-stu-id="22d01-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="22d01-107">型別參數的描述。</span><span class="sxs-lookup"><span data-stu-id="22d01-107">A description for the type parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="22d01-108">備註</span><span class="sxs-lookup"><span data-stu-id="22d01-108">Remarks</span></span>  
 <span data-ttu-id="22d01-109">`<typeparam>` 標記應該用於泛型型別或方法宣告的註解中，以描述型別參數。</span><span class="sxs-lookup"><span data-stu-id="22d01-109">The `<typeparam>` tag should be used in the comment for a generic type or method declaration to describe a type parameter.</span></span> <span data-ttu-id="22d01-110">新增泛型型別或方法之每個型別參數的標記。</span><span class="sxs-lookup"><span data-stu-id="22d01-110">Add a tag for each type parameter of the generic type or method.</span></span>  
  
 <span data-ttu-id="22d01-111">如需詳細資訊，請參閱[泛型](../../../csharp/programming-guide/generics/index.md)。</span><span class="sxs-lookup"><span data-stu-id="22d01-111">For more information, see [Generics](../../../csharp/programming-guide/generics/index.md).</span></span>  
  
 <span data-ttu-id="22d01-112">`<typeparam>` 標記的文字將會顯示於 IntelliSense，即 [Object Browser Window](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser) (物件瀏覽器視窗) 程式碼註解 Web 報告。</span><span class="sxs-lookup"><span data-stu-id="22d01-112">The text for the `<typeparam>` tag will be displayed in IntelliSense, the [Object Browser Window](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser) code comment web report.</span></span>  
  
 <span data-ttu-id="22d01-113">使用 [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) 編譯，可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="22d01-113">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="22d01-114">範例</span><span class="sxs-lookup"><span data-stu-id="22d01-114">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#13](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/typeparam_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="22d01-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="22d01-115">See also</span></span>

- [<span data-ttu-id="22d01-116">C# 參考</span><span class="sxs-lookup"><span data-stu-id="22d01-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="22d01-117">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="22d01-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="22d01-118">建議使用的文件註解標籤</span><span class="sxs-lookup"><span data-stu-id="22d01-118">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
