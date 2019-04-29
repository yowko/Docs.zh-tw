---
title: 導覽屬性-ADO.NET
ms.date: 03/30/2017
ms.assetid: d0bf1a6a-1d84-484c-b7c3-b410fd8dc0b1
ms.openlocfilehash: b57ecf9329aa9ea8afc07507613c9e3961bfd0a9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772235"
---
# <a name="navigation-property"></a>導覽屬性

A*導覽屬性*上為選擇性屬性[實體型別](entity-type.md)，可讓不同的瀏覽[結束](association-end.md)的[關聯](association-type.md)至另一端。 不同於其他[屬性](property.md)，導覽屬性不會包含資料。

導覽屬性包含下列定義：

- 名稱。 (必要項)

- 巡覽的關聯。 (必要項)

- 巡覽的關聯 End。 (必要項)

請注意，在關聯各端點的實體類型上，導覽屬性是選擇性的。 如果您在關聯其中一個端點的實體類型上定義導覽屬性，就不必在關聯另一個端點的實體類型上定義導覽屬性。

導覽屬性的資料類型由[多重性](association-end-multiplicity.md)的其遠端[關聯 end](association-end.md)。 例如，假設 `OrdersNavProp` 實體類型上有一個導覽屬性 `Customer`，則該導覽屬性可巡覽 `Customer` 和 `Order` 之間一對多的關聯。 因為導覽屬性的遠端關聯 end 具有多重性為許多 (\*)，其資料型別是集合 (的`Order`)。 同樣地，如果 `CustomerNavProp` 實體類型上有一個導覽屬性 `Order`，其資料類型應為 `Customer`，因為遠端 End 的多重性是「一 (1)」。

## <a name="example"></a>範例

下圖顯示包含三種實體類型 (`Book`、`Publisher` 和 `Author`) 的概念模型。 導覽屬性、`Publisher` 和 `Authors` 均在 Book 實體類型上定義。 導覽屬性 `Books` 在 Publisher 實體類型和 `Author` 實體類型上定義。

 ![顯示具有三種實體類型的概念模型的圖表。](./media/navigation-property/conceptual-model-entity-types-associations.gif)  

[ADO.NET Entity Framework](./ef/index.md)會使用稱為概念結構定義語言的特定領域語言 (DSL) ([CSDL](./ef/language-reference/csdl-specification.md)) 來定義概念模型。 下列 CSDL 定義上圖所顯示的 `Book` 實體類型：

[!code-xml[EDM_Example_Model#EntityExample](~/samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]

請注意，XML 屬性用來傳達定義導覽屬性所需的資訊：屬性`Name`包含屬性的名稱`Relationship`包含巡覽的關聯的名稱並`FromRole`和`ToRole`包含關聯的兩端。

## <a name="see-also"></a>另請參閱

- [實體資料模型索引鍵概念](entity-data-model-key-concepts.md)
- [實體資料模型](entity-data-model.md)
- [關聯性、 導覽屬性和外部索引鍵](/ef/ef6/fundamentals/relationships)
