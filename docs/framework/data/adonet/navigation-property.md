---
title: 導覽屬性-ADO.NET
ms.date: 03/30/2017
ms.assetid: d0bf1a6a-1d84-484c-b7c3-b410fd8dc0b1
ms.openlocfilehash: afb2043abf70fa92ea7cdf8d1e8246d5cdfdba74
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738381"
---
# <a name="navigation-property"></a>導覽屬性

*導覽屬性*是[實體類型](entity-type.md)上的選擇性屬性，可讓您從[關聯](association-type.md)[的一端導覽](association-end.md)至另一端。 不同于其他[屬性](property.md)，導覽屬性不會包含資料。

導覽屬性包含下列定義：

- 名稱。 (必要項)

- 巡覽的關聯。 (必要項)

- 巡覽的關聯 End。 (必要項)

請注意，在關聯各端點的實體類型上，導覽屬性是選擇性的。 如果您在關聯其中一個端點的實體類型上定義導覽屬性，就不必在關聯另一個端點的實體類型上定義導覽屬性。

導覽屬性的資料類型取決於其遠端[關聯 end](association-end.md)的[多重性](association-end-multiplicity.md)。 例如，假設 `OrdersNavProp` 實體類型上有一個導覽屬性 `Customer`，則該導覽屬性可巡覽 `Customer` 和 `Order` 之間一對多的關聯。 因為導覽屬性的遠端關聯 end 具有「多（\*）」的多重性，所以其資料型別為集合（屬於 `Order`）。 同樣地，如果 `CustomerNavProp` 實體類型上有一個導覽屬性 `Order`，其資料類型應為 `Customer`，因為遠端 End 的多重性是「一 (1)」。

## <a name="example"></a>範例

下圖顯示包含三種實體類型 (`Book`、`Publisher` 和 `Author`) 的概念模型。 導覽屬性、`Publisher` 和 `Authors` 均在 Book 實體類型上定義。 導覽屬性 `Books` 在 Publisher 實體類型和 `Author` 實體類型上定義。

 ![顯示具有三個實體類型之概念模型的圖表。](./media/navigation-property/conceptual-model-entity-types-associations.gif)  

[ADO.NET Entity Framework](./ef/index.md)會使用稱為概念結構定義語言（[CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)）的特定領域語言（DSL）來定義概念模型。 下列 CSDL 定義上圖所顯示的 `Book` 實體類型：

[!code-xml[EDM_Example_Model#EntityExample](~/samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]

請注意，XML 屬性用於傳達定義導覽屬性所需的資訊：`Name` 屬性 (attribute) 包含屬性 (property) 的名稱、`Relationship` 包含它所巡覽之關聯的名稱，而 `FromRole` 和 `ToRole` 則包含關聯 End。

## <a name="see-also"></a>請參閱

- [實體資料模型索引鍵概念](entity-data-model-key-concepts.md)
- [實體資料模型](entity-data-model.md)
- [關聯性、導覽屬性和外鍵](/ef/ef6/fundamentals/relationships)
