---
title: 屬性與索引子之間的比較 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], vs. indexers
- indexers [C#], vs. properties
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
ms.openlocfilehash: a8b347be33ea6acbdf8a78a7af45fd3d0c27f8fb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33330368"
---
# <a name="comparison-between-properties-and-indexers-c-programming-guide"></a>屬性與索引子之間的比較 (C# 程式設計手冊)
索引子就像是屬性。 除了下表所列的差異外，所有為屬性存取子定義的規則也適用於索引子存取子。  
  
|屬性|索引子|  
|--------------|-------------|  
|允許方法接受呼叫，就像是公用資料成員一樣。|允許使用物件本身的陣列標記法，存取物件的內部集合元素。|  
|透過簡單名稱存取。|透過索引存取。|  
|可以是靜態或執行個體成員。|必須是執行個體成員。|  
|屬性的 [get](../../../csharp/language-reference/keywords/get.md) 存取子沒有參數。|索引子的 `get` 存取子擁有與索引子相同的型式參數清單。|  
|屬性的 [set](../../../csharp/language-reference/keywords/set.md) 存取子包含隱含的 `value` 參數。|索引子的 `set` 存取子擁有與索引子相同的型式參數清單，同時也擁有 [value](../../../csharp/language-reference/keywords/value.md) 參數。|  
|支援縮短的語法與[自動實作的屬性](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)。|不支援縮短的語法。|  
  
## <a name="see-also"></a>請參閱  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [索引子](../../../csharp/programming-guide/indexers/index.md)  
 [屬性](../../../csharp/programming-guide/classes-and-structs/properties.md)
