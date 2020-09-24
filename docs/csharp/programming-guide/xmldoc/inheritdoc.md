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
ms.openlocfilehash: 8c416275254892efdb9f15cd2ae0af5634c82357
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91184088"
---
# <a name="inheritdoc-c-programming-guide"></a><span data-ttu-id="34189-102">\<inheritdoc> (c # 程式設計手冊) </span><span class="sxs-lookup"><span data-stu-id="34189-102">\<inheritdoc> (C# Programming Guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="34189-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="34189-103">Syntax</span></span>  
  
```xml  
<inheritdoc/>
```  

## <a name="inheritdoc"></a><span data-ttu-id="34189-104">InheritDoc</span><span class="sxs-lookup"><span data-stu-id="34189-104">InheritDoc</span></span>

<span data-ttu-id="34189-105">從基底類別、介面和類似的方法繼承 XML 批註。</span><span class="sxs-lookup"><span data-stu-id="34189-105">Inherit XML comments from base classes, interfaces, and similar methods.</span></span> <span data-ttu-id="34189-106">這可避免不必要的複製和貼上重複的 XML 批註，並自動保持 XML 批註的同步。</span><span class="sxs-lookup"><span data-stu-id="34189-106">This eliminates unwanted copying and pasting of duplicate XML comments and automatically keeps XML comments synchronized.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="34189-107">備註</span><span class="sxs-lookup"><span data-stu-id="34189-107">Remarks</span></span>  

<span data-ttu-id="34189-108">在基底類別或介面中新增您的 XML 批註，讓 InheritDoc 將批註複製到執行類別。</span><span class="sxs-lookup"><span data-stu-id="34189-108">Add your XML comments in base classes or interfaces and let InheritDoc copy the comments to implementing classes.</span></span>

<span data-ttu-id="34189-109">將您的 XML 批註新增至同步方法，並讓 InheritDoc 將批註複製到相同方法的非同步版本。</span><span class="sxs-lookup"><span data-stu-id="34189-109">Add your XML comments to your synchronous methods and let InheritDoc copy the comments to your asynchronous versions of the same methods.</span></span>  

<span data-ttu-id="34189-110">如果您想要複製特定成員的批註，您可以使用 `cref` 屬性來指定成員。</span><span class="sxs-lookup"><span data-stu-id="34189-110">If you want to copy the comments from a specific member you can use the `cref` attribute to specify the member.</span></span>
  
## <a name="examples"></a><span data-ttu-id="34189-111">範例</span><span class="sxs-lookup"><span data-stu-id="34189-111">Examples</span></span>

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#16)]  

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#17)]  

## <a name="see-also"></a><span data-ttu-id="34189-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="34189-112">See also</span></span>

- [<span data-ttu-id="34189-113">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="34189-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="34189-114">建議使用的檔註解標記</span><span class="sxs-lookup"><span data-stu-id="34189-114">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
