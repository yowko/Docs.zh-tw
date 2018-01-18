---
title: "實體索引鍵"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d447a6d-fa7a-4db0-8e7a-fd45e385fca0
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 1f2f50f5306904a2a1b42a3abbe9071c33847c66
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="entity-key"></a>實體索引鍵
*實體索引鍵*是[屬性](../../../../docs/framework/data/adonet/property.md)或一組屬性的[實體類型](../../../../docs/framework/data/adonet/entity-type.md)，用於判斷識別。 構成實體索引鍵的屬性是在設計階段選取的。 實體索引鍵屬性的值必須唯一識別實體類型執行個體中的[實體集](../../../../docs/framework/data/adonet/entity-set.md)在執行階段。 您應選取構成實體索引鍵的屬性，以保證執行個體在實體集中的唯一性。  
  
 屬性集若要成為實體索引鍵，需求如下：  
  
-   實體集中的任兩個實體索引鍵均不可完全相同。 也就是說，以實體集中任兩個實體來說，構成索引鍵的所有屬性的值不可完全相同。 不過，構成實體索引鍵的部分 (非所有) 值可以相同。  
  
-   實體索引鍵必須包含一組不可為 null、 不可變的[基本型別屬性](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md)。  
  
-   構成指定實體類型之實體索引鍵的屬性不可變更。 您不能允許指定的實體類型擁有多個可能的實體索引鍵，不支援 Surrogate 索引鍵。  
  
-   實體與繼承階層相關時，根實體必須包含構成實體索引鍵的所有屬性，而且必須在根實體類型定義該實體索引鍵。 如需詳細資訊，請參閱[實體資料模型： 繼承](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md)。  
  
## <a name="example"></a>範例  
 下圖顯示包含三種實體類型 (`Book`、`Publisher` 和 `Author`) 的概念模型。 構成實體索引鍵之每個實體類型的屬性皆加註「(索引鍵)」。 請注意，`Author` 實體類型的實體索引鍵包含兩個屬性：`Name` 和 `Address`。  
  
 ![範例模型](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)會使用稱為概念結構定義語言的特定領域語言 (DSL) ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 來定義概念模型。 下列的 CSDL 會定義上圖顯示的 `Book` 實體類型。 請注意，實體索引鍵是藉由參考實體類型的 `ISBN` 屬性而定義的。  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
 `ISBN` 屬性是實體索引鍵的最佳選擇，因為國際標準書號 (International Standard Book Number，ISBN) 可明確識別一本書。  
  
 下列的 CSDL 會定義上圖顯示的 `Author` 實體類型。 請注意，實體索引鍵包含兩個屬性：`Name` 和 `Address`。  
  
 [!code-xml[EDM_Example_Model#CompositeKeyExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#compositekeyexample)]  
  
 針對實體索引鍵使用 `Name` 和 `Address` 是合理的選擇，因為相同名稱的兩位作者不太可能住在同一個地址。 不過，針對實體索引鍵所做的這個選擇不能絕對保證實體集中的唯一實體索引鍵。 在這種情況下，建議您加入一個屬性，例如 `AuthorId`，可用於明確識別作者。  
  
## <a name="see-also"></a>請參閱  
 [實體資料模型索引鍵概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [實體資料模型](../../../../docs/framework/data/adonet/entity-data-model.md)
