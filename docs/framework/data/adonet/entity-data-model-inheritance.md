---
title: 實體資料模型：繼承
ms.date: 03/30/2017
ms.assetid: 42c7ef24-710a-4af9-8493-cd41c399ecb0
ms.openlocfilehash: 057040eee411988c46adc9c4cabcfe5f5a185e1b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91175456"
---
# <a name="entity-data-model-inheritance"></a>實體資料模型：繼承

實體資料模型 (EDM) 支援 [實體類型](entity-type.md)的繼承。 EDM 中的繼承類似於物件導向程式設計語言中的類別繼承。 就像物件導向語言中的類別一樣，在概念模型中，您可以定義實體類型 (*衍生類型*) 繼承自另一個實體類型，) *基底類型* (。 不過，不同于物件導向程式設計中的類別，在概念模型中，衍生型別一律會繼承基底類型的所有 [屬性](property.md) 和 [導覽屬性](navigation-property.md) 。 您不能覆寫衍生型別中的繼承屬性。  
  
 在概念模型中，您可以組建繼承階層，其中的衍生型別繼承自另一種衍生型別。 階層頂端的型別 (階層中不是衍生型別) 的型別稱為「根型別」（ *root type*）。 在繼承階層中，必須在根型別上定義 [實體索引鍵](entity-key.md) 。  
  
 您不可建置衍生型別繼承自多個型別的繼承階層。 例如，在具有 `Book` 實體類型的概念模型中，您可以定義分別繼承自 `FictionBook` 的衍生型別 `NonFictionBook` 和 `Book`。 不過，您可能無法定義同時繼承自 `FictionBook` 和 `NonFictionBook` 型別的型別。  
  
## <a name="example"></a>範例  

下圖顯示具有四個實體類型的概念模型： `Book` 、 `FictionBook` 、 `Publisher` 和 `Author` 。 `FictionBook` 實體類型為衍生型別，繼承自 `Book` 實體類型。 `FictionBook` 型別繼承自 `ISBN (Key)`、`Title` 和 `Revision` 屬性，並且定義稱為 `Genre` 的額外屬性。  
  
 ![顯示具有四個實體類型之概念模型的圖表。](./media/entity-data-model-inheritance/entity-type-inheritance.gif)  
  
 [ADO.NET Entity Framework](./ef/index.md)會使用 (DSL) 稱為概念結構定義語言 ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) 來定義概念模型的特定領域語言。 下列 CSDL 定義實體類型 `FictionBook`，此實體類型繼承自 `Book` 型別 (如上圖所示)：  
  
 [!code-xml[EDM_Example_Model#DerivedType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books5.edmx#derivedtype)]  
  
## <a name="see-also"></a>另請參閱

- [實體資料模型索引鍵概念](entity-data-model-key-concepts.md)
- [實體資料模型](entity-data-model.md)
