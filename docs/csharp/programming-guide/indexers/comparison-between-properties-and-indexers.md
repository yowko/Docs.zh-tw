---
title: 屬性與索引子之間的比較 - C# 程式設計指南
description: '比較 c # 中的索引子如何與屬性相同。 除了某些差異之外，針對屬性存取子所定義的規則也會套用至索引子存取子。'
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], vs. indexers
- indexers [C#], vs. properties
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
ms.openlocfilehash: fff20ca965e7614d26f7da32321a829d13292389
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91192525"
---
# <a name="comparison-between-properties-and-indexers-c-programming-guide"></a>屬性與索引子之間的比較 (C# 程式設計手冊)

索引子就像是屬性。 除了下表所列的差異外，所有為屬性存取子定義的規則也適用於索引子存取子。  
  
|屬性|索引編製程式|  
|--------------|-------------|  
|允許方法接受呼叫，就像是公用資料成員一樣。|允許使用物件本身的陣列標記法，存取物件的內部集合元素。|  
|透過簡單名稱存取。|透過索引存取。|  
|可以是靜態或執行個體成員。|必須是執行個體成員。|  
|屬性的 [get](../../language-reference/keywords/get.md) 存取子沒有參數。|索引子的 `get` 存取子擁有與索引子相同的型式參數清單。|  
|屬性的 [set](../../language-reference/keywords/set.md) 存取子包含隱含的 `value` 參數。|索引子的 `set` 存取子擁有與索引子相同的型式參數清單，同時也擁有 [value](../../language-reference/keywords/value.md) 參數。|  
|支援縮短的語法與[自動實作的屬性](../classes-and-structs/auto-implemented-properties.md)。|支援針對僅取得索引子使用運算式主體的成員。|  
  
## <a name="see-also"></a>另請參閱

- [C # 程式設計指南](../index.md)
- [索引子](./index.md)
- [屬性](../classes-and-structs/properties.md)
