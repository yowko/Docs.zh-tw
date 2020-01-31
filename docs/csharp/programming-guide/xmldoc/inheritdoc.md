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
# <a name="inheritdoc-c-programming-guide"></a>\<inheritdoc > （C#程式設計手冊）

## <a name="syntax"></a>語法  
  
```xml  
<inheritdoc/> 
```  

## <a name="inheritdoc"></a>InheritDoc

從基類、介面和類似的方法繼承 XML 批註。 這可避免不必要的複製和貼上重複的 XML 批註，並自動保持 XML 批註的同步處理。 
  
## <a name="remarks"></a>備註  
在基類或介面中新增您的 XML 批註，並讓 InheritDoc 將批註複製到執行類別。

將您的 XML 批註新增至您的同步方法，並讓 InheritDoc 將批註複製到相同方法的非同步版本。  

如果您想要從特定成員複製批註，您可以使用 `cref` 屬性來指定成員。
  
## <a name="examples"></a>範例
[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#16)]  

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#17)]  

## <a name="see-also"></a>請參閱

- [C# 程式設計指南](../index.md)
- [建議使用的文件註解標籤](./recommended-tags-for-documentation-comments.md)
