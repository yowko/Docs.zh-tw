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
# <a name="inheritdoc-c-programming-guide"></a>\<繼承>（C# 程式設計指南）

## <a name="syntax"></a>語法  
  
```xml  
<inheritdoc/>
```  

## <a name="inheritdoc"></a>繼承文檔

從基類、介面和類似方法繼承 XML 注釋。 這樣可以消除重複的 XML 注釋的不需要複製和粘貼，並自動保持 XML 注釋同步。
  
## <a name="remarks"></a>備註  
在基本類或介面中添加 XML 注釋，並讓 InheritDoc 將注釋複製到實現類。

將 XML 注釋添加到同步方法，並讓 InheritDoc 將注釋複製到相同方法的非同步版本中。  

如果要從特定成員複製注釋，可以使用 該`cref`屬性指定該成員。
  
## <a name="examples"></a>範例
[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#16)]  

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#17)]  

## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../index.md)
- [文檔注釋的推薦標記](./recommended-tags-for-documentation-comments.md)
