---
title: "屬性與索引子之間的比較 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- properties [C#], vs. indexers
- indexers [C#], vs. properties
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 4bb2de1cfdcf4a8a7c847dfabe8d69124a4adf90
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

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
  
## <a name="see-also"></a>另請參閱  
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [索引子](../../../csharp/programming-guide/indexers/index.md)   
 [屬性](../../../csharp/programming-guide/classes-and-structs/properties.md)

