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
ms.openlocfilehash: 6f42462f21d045428577cd2123e2180d866f1e1e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156944"
---
# <a name="inheritdoc-c-programming-guide"></a><span data-ttu-id="e6d0c-102">\<繼承>（C# 程式設計指南）</span><span class="sxs-lookup"><span data-stu-id="e6d0c-102">\<inheritdoc> (C# Programming Guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="e6d0c-103">語法</span><span class="sxs-lookup"><span data-stu-id="e6d0c-103">Syntax</span></span>  
  
```xml  
<inheritdoc/>
```  

## <a name="inheritdoc"></a><span data-ttu-id="e6d0c-104">繼承文檔</span><span class="sxs-lookup"><span data-stu-id="e6d0c-104">InheritDoc</span></span>

<span data-ttu-id="e6d0c-105">從基類、介面和類似方法繼承 XML 注釋。</span><span class="sxs-lookup"><span data-stu-id="e6d0c-105">Inherit XML comments from base classes, interfaces, and similar methods.</span></span> <span data-ttu-id="e6d0c-106">這樣可以消除重複的 XML 注釋的不需要複製和粘貼，並自動保持 XML 注釋同步。</span><span class="sxs-lookup"><span data-stu-id="e6d0c-106">This eliminates unwanted copying and pasting of duplicate XML comments and automatically keeps XML comments synchronized.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="e6d0c-107">備註</span><span class="sxs-lookup"><span data-stu-id="e6d0c-107">Remarks</span></span>  
<span data-ttu-id="e6d0c-108">在基本類或介面中添加 XML 注釋，並讓 InheritDoc 將注釋複製到實現類。</span><span class="sxs-lookup"><span data-stu-id="e6d0c-108">Add your XML comments in base classes or interfaces and let InheritDoc copy the comments to implementing classes.</span></span>

<span data-ttu-id="e6d0c-109">將 XML 注釋添加到同步方法，並讓 InheritDoc 將注釋複製到相同方法的非同步版本中。</span><span class="sxs-lookup"><span data-stu-id="e6d0c-109">Add your XML comments to your synchronous methods and let InheritDoc copy the comments to your asynchronous versions of the same methods.</span></span>  

<span data-ttu-id="e6d0c-110">如果要從特定成員複製注釋，可以使用 該`cref`屬性指定該成員。</span><span class="sxs-lookup"><span data-stu-id="e6d0c-110">If you want to copy the comments from a specific member you can use the `cref` attribute to specify the member.</span></span>
  
## <a name="examples"></a><span data-ttu-id="e6d0c-111">範例</span><span class="sxs-lookup"><span data-stu-id="e6d0c-111">Examples</span></span>
[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#16)]  

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#17)]  

## <a name="see-also"></a><span data-ttu-id="e6d0c-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6d0c-112">See also</span></span>

- [<span data-ttu-id="e6d0c-113">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="e6d0c-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e6d0c-114">文檔注釋的推薦標記</span><span class="sxs-lookup"><span data-stu-id="e6d0c-114">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
