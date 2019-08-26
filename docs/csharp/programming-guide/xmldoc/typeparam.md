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
ms.openlocfilehash: ea48cf0cdfc2dc48ad29ab6219449f801739bc8f
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69587590"
---
# <a name="typeparam-c-programming-guide"></a><span data-ttu-id="6b66d-102">\<typeparam> (C# 程式設計指南)</span><span class="sxs-lookup"><span data-stu-id="6b66d-102">\<typeparam> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="6b66d-103">語法</span><span class="sxs-lookup"><span data-stu-id="6b66d-103">Syntax</span></span>  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
## <a name="parameters"></a><span data-ttu-id="6b66d-104">參數</span><span class="sxs-lookup"><span data-stu-id="6b66d-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="6b66d-105">型別參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="6b66d-105">The name of the type parameter.</span></span> <span data-ttu-id="6b66d-106">以雙引號 (" ") 括住名稱。</span><span class="sxs-lookup"><span data-stu-id="6b66d-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="6b66d-107">型別參數的描述。</span><span class="sxs-lookup"><span data-stu-id="6b66d-107">A description for the type parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6b66d-108">備註</span><span class="sxs-lookup"><span data-stu-id="6b66d-108">Remarks</span></span>  
 <span data-ttu-id="6b66d-109">`<typeparam>` 標記應該用於泛型型別或方法宣告的註解中，以描述型別參數。</span><span class="sxs-lookup"><span data-stu-id="6b66d-109">The `<typeparam>` tag should be used in the comment for a generic type or method declaration to describe a type parameter.</span></span> <span data-ttu-id="6b66d-110">新增泛型型別或方法之每個型別參數的標記。</span><span class="sxs-lookup"><span data-stu-id="6b66d-110">Add a tag for each type parameter of the generic type or method.</span></span>  
  
 <span data-ttu-id="6b66d-111">如需詳細資訊，請參閱[泛型](../generics/index.md)。</span><span class="sxs-lookup"><span data-stu-id="6b66d-111">For more information, see [Generics](../generics/index.md).</span></span>  
  
 <span data-ttu-id="6b66d-112">`<typeparam>` 標記的文字將會顯示於 IntelliSense，即 [Object Browser Window](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser) (物件瀏覽器視窗) 程式碼註解 Web 報告。</span><span class="sxs-lookup"><span data-stu-id="6b66d-112">The text for the `<typeparam>` tag will be displayed in IntelliSense, the [Object Browser Window](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser) code comment web report.</span></span>  
  
 <span data-ttu-id="6b66d-113">編譯搭配 [/doc](../../language-reference/compiler-options/doc-compiler-option.md) 可處理檔案的文件註解。</span><span class="sxs-lookup"><span data-stu-id="6b66d-113">Compile with [/doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b66d-114">範例</span><span class="sxs-lookup"><span data-stu-id="6b66d-114">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]  
  
## <a name="see-also"></a><span data-ttu-id="6b66d-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b66d-115">See also</span></span>

- [<span data-ttu-id="6b66d-116">C# 參考</span><span class="sxs-lookup"><span data-stu-id="6b66d-116">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="6b66d-117">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="6b66d-117">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="6b66d-118">建議使用的文件註解標籤</span><span class="sxs-lookup"><span data-stu-id="6b66d-118">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
