---
title: 導覽屬性
ms.date: 03/30/2017
ms.assetid: d0bf1a6a-1d84-484c-b7c3-b410fd8dc0b1
ms.openlocfilehash: eaf22ad4dd24b4bf046f14ccabd435a9ecd1776f
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094380"
---
# <a name="navigation-property"></a>導覽屬性

*導覽屬性*是[實體類型](entity-type.md)上的選擇性屬性，可讓您從[關聯](association-type.md)[的一端導覽](association-end.md)至另一端。 不同于其他[屬性](property.md)，導覽屬性不會包含資料。

導覽屬性包含下列定義：

- 名稱。 (必要)

- 巡覽的關聯。 (必要)

- 巡覽的關聯 End。 (必要)

在關聯的兩端，這兩個實體類型的導覽屬性都是選擇性的。 如果您在關聯其中一個端點的實體類型上定義導覽屬性，就不必在關聯另一個端點的實體類型上定義導覽屬性。

導覽屬性的資料類型取決於其遠端[關聯 end](association-end.md)的[多重性](association-end-multiplicity.md)。 例如，假設 `OrdersNavProp` 實體類型上有一個導覽屬性 `Customer`，則該導覽屬性可巡覽 `Customer` 和 `Order` 之間一對多的關聯。 因為導覽屬性的遠端關聯 end 具有「多（\*）」的多重性，所以其資料型別為集合（屬於 `Order`）。 同樣地，如果 `CustomerNavProp` 實體類型上有一個導覽屬性 `Order`，其資料類型應為 `Customer`，因為遠端 End 的多重性是「一 (1)」。

## <a name="example"></a>範例

下圖顯示包含三種實體類型 (`Book`、`Publisher` 和 `Author`) 的概念模型。 `Publisher` 和 `Authors` 的導覽屬性是在 Book 實體類型上定義。 導覽屬性 `Books` 在 Publisher 實體類型和 `Author` 實體類型上定義。

![顯示具有三個實體類型之概念模型的圖表。](./media/navigation-property/conceptual-model-entity-types-associations.gif)  

[ADO.NET Entity Framework](./ef/index.md)會使用稱為概念結構定義語言（[CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)）的特定領域語言（DSL）來定義概念模型。 下列 CSDL 定義上圖所顯示的 `Book` 實體類型：

[!code-xml[EDM_Example_Model#EntityExample](~/samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]

XML 屬性是用來傳達定義導覽屬性所需的資訊：屬性 `Name` 包含屬性的名稱，`Relationship` 包含它所導覽之關聯的名稱，而 `FromRole` 和 `ToRole` 包含關聯的端點。

## <a name="see-also"></a>另請參閱

- [實體資料模型索引鍵概念](entity-data-model-key-concepts.md)
- [實體資料模型](entity-data-model.md)
- [關聯性、導覽屬性和外鍵](/ef/ef6/fundamentals/relationships)
