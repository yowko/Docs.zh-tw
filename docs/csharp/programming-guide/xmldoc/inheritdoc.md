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
# <a name="inheritdoc-c-programming-guide"></a>\<inheritdoc> (c # 程式設計手冊) 

## <a name="syntax"></a>Syntax  
  
```xml  
<inheritdoc/>
```  

## <a name="inheritdoc"></a>InheritDoc

從基底類別、介面和類似的方法繼承 XML 批註。 這可避免不必要的複製和貼上重複的 XML 批註，並自動保持 XML 批註的同步。
  
## <a name="remarks"></a>備註  

在基底類別或介面中新增您的 XML 批註，讓 InheritDoc 將批註複製到執行類別。

將您的 XML 批註新增至同步方法，並讓 InheritDoc 將批註複製到相同方法的非同步版本。  

如果您想要複製特定成員的批註，您可以使用 `cref` 屬性來指定成員。
  
## <a name="examples"></a>範例

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#16)]  

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#17)]  

## <a name="see-also"></a>另請參閱

- [C # 程式設計指南](../index.md)
- [建議使用的檔註解標記](./recommended-tags-for-documentation-comments.md)
