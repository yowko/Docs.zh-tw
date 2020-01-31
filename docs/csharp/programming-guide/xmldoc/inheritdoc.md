---
title: <inheritdoc> - C# 程式設計指南
ms.date: 01/21/2020
f1_keywords:
- inheritdoc
- <inheritdoc>
helpviewer_keywords:
- <inheritdoc> C# XML tag
- inheritdoc C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: d660cb1739733c4e98ae0b7939476fe74e6cf200
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76795158"
---
# <a name="inheritdoc-c-programming-guide"></a><span data-ttu-id="7fb71-102">\<inheritdoc > （C#程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="7fb71-102">\<inheritdoc> (C# Programming Guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="7fb71-103">語法</span><span class="sxs-lookup"><span data-stu-id="7fb71-103">Syntax</span></span>  
  
```xml  
<inheritdoc/> 
```  

## <a name="inheritdoc"></a><span data-ttu-id="7fb71-104">InheritDoc</span><span class="sxs-lookup"><span data-stu-id="7fb71-104">InheritDoc</span></span>

<span data-ttu-id="7fb71-105">從基類、介面和類似的方法繼承 XML 批註。</span><span class="sxs-lookup"><span data-stu-id="7fb71-105">Inherit XML comments from base classes, interfaces, and similar methods.</span></span> <span data-ttu-id="7fb71-106">這可避免不必要的複製和貼上重複的 XML 批註，並自動保持 XML 批註的同步處理。</span><span class="sxs-lookup"><span data-stu-id="7fb71-106">This eliminates unwanted copying and pasting of duplicate XML comments and automatically keeps XML comments synchronized.</span></span> 
  
## <a name="remarks"></a><span data-ttu-id="7fb71-107">備註</span><span class="sxs-lookup"><span data-stu-id="7fb71-107">Remarks</span></span>  
<span data-ttu-id="7fb71-108">在基類或介面中新增您的 XML 批註，並讓 InheritDoc 將批註複製到執行類別。</span><span class="sxs-lookup"><span data-stu-id="7fb71-108">Add your XML comments in base classes or interfaces and let InheritDoc copy the comments to implementing classes.</span></span>

<span data-ttu-id="7fb71-109">將您的 XML 批註新增至您的同步方法，並讓 InheritDoc 將批註複製到相同方法的非同步版本。</span><span class="sxs-lookup"><span data-stu-id="7fb71-109">Add your XML comments to your synchronous methods and let InheritDoc copy the comments to your asynchronous versions of the same methods.</span></span>  

<span data-ttu-id="7fb71-110">如果您想要從特定成員複製批註，您可以使用 `cref` 屬性來指定成員。</span><span class="sxs-lookup"><span data-stu-id="7fb71-110">If you want to copy the comments from a specific member you can use the `cref` attribute to specify the member.</span></span>
  
## <a name="examples"></a><span data-ttu-id="7fb71-111">範例</span><span class="sxs-lookup"><span data-stu-id="7fb71-111">Examples</span></span>
[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#16)]  

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#17)]  

## <a name="see-also"></a><span data-ttu-id="7fb71-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="7fb71-112">See also</span></span>

- [<span data-ttu-id="7fb71-113">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="7fb71-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="7fb71-114">建議使用的文件註解標籤</span><span class="sxs-lookup"><span data-stu-id="7fb71-114">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
