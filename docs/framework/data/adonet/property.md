---
title: 屬性
ms.date: 03/30/2017
ms.assetid: a941c53f-fc97-42c2-8832-0fb9f1d55c06
ms.openlocfilehash: 6aeb29c5aa608987466ec858416a4ac141ff1da3
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91180916"
---
# <a name="property"></a>屬性

*屬性* 是 [實體類型](entity-type.md) 和 [複雜類型](complex-type.md)的基本組建區塊。 屬性可定義實體類型執行個體或複雜類型執行個體將包含的資料圖案和特性。 概念模型中的屬性類似類別中定義的屬性。 如同類別上的屬性可定義類別的圖形並包含關於物件的資訊，概念模型的屬性可定義實體類別的圖形，並包含關於實體類型執行個體的資訊。  
  
> [!NOTE]
> 如本章所述，屬性與導覽屬性不同。 如需詳細資訊，請參閱 [導覽屬性](navigation-property.md)。  
  
 屬性定義包含下列資訊：  
  
- 屬性名稱。 (必要)  
  
- 屬性型別。 (必要)  
  
- 一組 [facet](facet.md)。 (選用)  
  
 屬性可以包含基底資料 (例如字串、整數或布林值) 或結構化資料 (例如複雜類型)。 屬於基本型別的屬性亦稱為純量屬性。 如需詳細資訊，請參閱 [實體資料模型：基本資料類型](entity-data-model-primitive-data-types.md)。  
  
> [!NOTE]
> 複雜類型本身可以包含複雜類型的屬性。  
  
## <a name="example"></a>範例  

 下圖顯示包含三種實體類型 (`Book`、`Publisher` 和 `Author`) 的概念模型。 雖然圖中並提供每個屬性的型別資訊，但每個實體類型均具有數個屬性。 [實體索引鍵](entity-key.md)的屬性會以 (索引鍵) 表示。  
  
 ![包含三種實體類型的範例模型](./media/property/example-model-three-entity-types.gif)  
  
 [ADO.NET Entity Framework](./ef/index.md)會使用 (DSL) 稱為概念結構定義語言 ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) 來定義概念模型的特定領域語言。 下列 CSDL 定義 `Book` 實體類型 (如上圖所示)，並且使用 XML 屬性 (attribute) 指出各個屬性 (property) 的型別和名稱。 `Nullable` (選擇性 Facet) 也是使用 XML 屬性所定義。  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
 圖中顯示的其中一個屬性可能會是複雜類型屬性。 例如，`Address`實體型別上的 `Publisher` 屬性可能是複雜類型屬性，由數個包純量屬性組成，例如 `StreetAddress`、`City`、`StateOrProvince`、`Country` 和 `PostalCode`。 此類複雜類型的 CSDL 表示如下所示：  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
## <a name="see-also"></a>另請參閱

- [實體資料模型索引鍵概念](entity-data-model-key-concepts.md)
- [實體資料模型](entity-data-model.md)
