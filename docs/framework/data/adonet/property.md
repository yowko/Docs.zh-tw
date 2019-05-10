---
title: 屬性
ms.date: 03/30/2017
ms.assetid: a941c53f-fc97-42c2-8832-0fb9f1d55c06
ms.openlocfilehash: 97bb41305bd9b736fd67b51d77ee15ad9efa3f29
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645238"
---
# <a name="property"></a>屬性
*屬性*是基本建置組塊[實體類型](../../../../docs/framework/data/adonet/entity-type.md)並[複雜型別](../../../../docs/framework/data/adonet/complex-type.md)。 屬性可定義實體類型執行個體或複雜類型執行個體將包含的資料圖案和特性。 概念模型中的屬性類似類別中定義的屬性。 如同類別上的屬性可定義類別的圖形並包含關於物件的資訊，概念模型的屬性可定義實體類別的圖形，並包含關於實體類型執行個體的資訊。  
  
> [!NOTE]
>  如本章所述，屬性與導覽屬性不同。 如需詳細資訊，請參閱 <<c0> [ 導覽屬性](../../../../docs/framework/data/adonet/navigation-property.md)。  
  
 屬性定義包含下列資訊：  
  
- 屬性名稱。 (必要項)  
  
- 屬性型別。 (必要項)  
  
- 一組[facet](../../../../docs/framework/data/adonet/facet.md)。 (選擇項)  
  
 屬性可以包含基底資料 (例如字串、整數或布林值) 或結構化資料 (例如複雜類型)。 屬於基本型別的屬性亦稱為純量屬性。 如需詳細資訊，請參閱[實體資料模型：基本資料型別](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md)。  
  
> [!NOTE]
>  複雜類型本身可以包含複雜類型的屬性。  
  
## <a name="example"></a>範例  
 下圖顯示包含三種實體類型 (`Book`、`Publisher` 和 `Author`) 的概念模型。 雖然圖中並提供每個屬性的型別資訊，但每個實體類型均具有數個屬性。 屬性[實體索引鍵](../../../../docs/framework/data/adonet/entity-key.md)皆加註 （索引鍵）。  
  
 ![具有三種實體類型的範例模型](./media/property/example-model-three-entity-types.gif)  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)會使用稱為概念結構定義語言的特定領域語言 (DSL) ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 來定義概念模型。 下列 CSDL 定義 `Book` 實體類型 (如上圖所示)，並且使用 XML 屬性 (attribute) 指出各個屬性 (property) 的型別和名稱。 `Nullable` (選擇性 Facet) 也是使用 XML 屬性所定義。  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
 圖中顯示的其中一個屬性可能會是複雜類型屬性。 例如，`Address`實體型別上的 `Publisher` 屬性可能是複雜類型屬性，由數個包純量屬性組成，例如 `StreetAddress`、`City`、`StateOrProvince`、`Country` 和 `PostalCode`。 此類複雜類型的 CSDL 表示如下所示：  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
## <a name="see-also"></a>另請參閱

- [實體資料模型索引鍵概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [實體資料模型](../../../../docs/framework/data/adonet/entity-data-model.md)
