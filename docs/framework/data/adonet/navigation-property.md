---
title: "導覽屬性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d0bf1a6a-1d84-484c-b7c3-b410fd8dc0b1
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: f5af52532dc534d793e7e8ce72a08c2f7229569b
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="navigation-property"></a>導覽屬性
A*導覽屬性*上是選用屬性[實體類型](../../../../docs/framework/data/adonet/entity-type.md)，可允許從一個導覽[結束](../../../../docs/framework/data/adonet/association-end.md)的[關聯](../../../../docs/framework/data/adonet/association-type.md)至另一端。 不同於其他[屬性](../../../../docs/framework/data/adonet/property.md)，導覽屬性不會包含資料。  
  
 導覽屬性包含下列定義：  
  
-   名稱。 (必要項)  
  
-   巡覽的關聯。 (必要項)  
  
-   巡覽的關聯 End。 (必要項)  
  
 請注意，在關聯各端點的實體類型上，導覽屬性是選擇性的。 如果您在關聯其中一個端點的實體類型上定義導覽屬性，就不必在關聯另一個端點的實體類型上定義導覽屬性。  
  
 導覽屬性的資料類型由[多重性](../../../../docs/framework/data/adonet/association-end-multiplicity.md)其遠端的[關聯 end](../../../../docs/framework/data/adonet/association-end.md)。 例如，假設 `OrdersNavProp` 實體類型上有一個導覽屬性 `Customer`，則該導覽屬性可巡覽 `Customer` 和 `Order` 之間一對多的關聯。 因為導覽屬性的遠端關聯 End 具有「多 (*)」多重性，因此其資料型別是 (`Order` 的) 集合。 同樣地，如果 `CustomerNavProp` 實體類型上有一個導覽屬性 `Order`，其資料類型應為 `Customer`，因為遠端 End 的多重性是「一 (1)」。  
  
## <a name="example"></a>範例  
 下圖顯示包含三種實體類型 (`Book`、`Publisher` 和 `Author`) 的概念模型。 導覽屬性、`Publisher` 和 `Authors` 均在 Book 實體類型上定義。 導覽屬性 `Books` 在 Publisher 實體類型和 `Author` 實體類型上定義。  
  
 ![具有導覽屬性的模型](../../../../docs/framework/data/adonet/media/modelwithnavprops.gif "ModelWithNavProps")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)會使用稱為概念結構定義語言的特定領域語言 (DSL) ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 來定義概念模型。 下列 CSDL 定義上圖所顯示的 `Book` 實體類型：  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
 請注意，XML 屬性用於傳達定義導覽屬性所需的資訊：`Name` 屬性 (attribute) 包含屬性 (property) 的名稱、`Relationship` 包含它所巡覽之關聯的名稱，而 `FromRole` 和 `ToRole` 則包含關聯 End。  
  
## <a name="see-also"></a>請參閱  
 [實體資料模型索引鍵概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [實體資料模型](../../../../docs/framework/data/adonet/entity-data-model.md)
