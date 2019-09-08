---
title: 複雜類型
ms.date: 03/30/2017
ms.assetid: 63efbd23-11d4-4871-bc88-ad01b9837553
ms.openlocfilehash: 0d9b8efd08cc0dfba5b26a70773b614b0d63d74f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786755"
---
# <a name="complex-type"></a>複雜類型
「*複雜類型」（complex type* ）是在[實體類型](entity-type.md)或其他複雜類型上定義豐富結構化屬性的範本。 每個範本包含下列資訊：  
  
- 唯一名稱。 (必要項)  
  
    > [!NOTE]
    > 複雜類型的名稱不可以與同一個命名空間中的實體類型名稱相同。  
  
- 一或多個[屬性](property.md)形式的資料。 (選擇性。)  
  
    > [!NOTE]
    > 複雜類型的屬性可以是另一個複雜類型。  
  
 複雜類型與實體類型相似之處在於，複雜類型可以包含基本型別屬性或其他複雜類型形式的資料承載。 不過，複雜型別和實體類型之間還是有些重大的差異：  
  
- 複雜類型不具有識別，因此無法獨立存在。 複雜類型只能以實體類型或其他複雜類型的屬性形式存在。  
  
- 複雜類型不能參與[關聯](association-type.md)。 關聯的兩端都不可以是複雜類型，因此無法在複雜類型上定義[導覽屬性](navigation-property.md)。  
  
## <a name="example"></a>範例  
 [ADO.NET Entity Framework](./ef/index.md)會使用稱為概念結構定義語言（[CSDL](./ef/language-reference/csdl-specification.md)）的特定領域語言（DSL）來定義概念模型。 下列 CSDL 以基底類型屬性 `StreetAddress`、`City`、`StateOrProvince`、`Country` 和 `PostalCode` 定義複雜類型 Address。  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
 若要將上方的複雜類型 `Address` 定義為實體類型上的屬性，您必須在實體類型定義中宣告屬性型別。 下列 CSDL 會在實體類型 (Publisher) 上將 `Address` 屬性宣告為複雜類型：  
  
 [!code-xml[EDM_Example_Model#EntityWithComplexType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#entitywithcomplextype)]  
  
## <a name="see-also"></a>另請參閱

- [實體資料模型索引鍵概念](entity-data-model-key-concepts.md)
- [實體資料模型](entity-data-model.md)
