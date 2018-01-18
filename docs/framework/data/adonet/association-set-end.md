---
title: "關聯集 End"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fe4bf1d3-047a-4a37-98c5-a66e70811346
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 85b4bd732d9de987676bae70f7749a1dd9dc76c5
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="association-set-end"></a>關聯集 End
*關聯集 end*識別[實體類型](../../../../docs/framework/data/adonet/entity-type.md)和[實體集](../../../../docs/framework/data/adonet/entity-set.md)結尾[關聯集](../../../../docs/framework/data/adonet/association-set.md)。 關聯集 End 會定義為關聯集的部分。一個關聯集必須擁有兩個關聯集 End。  
  
 關聯集 End 定義包含下列資訊：  
  
-   關聯集中相關的其中一個屬性類型。 (必要項)  
  
-   關聯集中相關實體類型的實體集。 (必要項)  
  
## <a name="example"></a>範例  
 下圖顯示包含兩個關聯 (`WrittenBy` 和 `PublishedBy`) 的概念模型。  
  
 ![範例模型](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 下圖顯示以前述概念模型為基礎的一個關聯集 (`PublishedBy`) 和兩個實體集 (`Books` 和 `Publishers`)。 關聯集 End 為 `Books` 和 `Publishers` 實體集。 在 bi`Books`實體集表示的執行個體`Book`在執行階段的實體類型。 同樣地，Pj 代表`Publisher`執行個體中`Publishers`實體集。 BiPj 表示的執行個體`PublishedBy`中的關聯`PublishedBy`關聯集。  
  
 ![設定範例](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)會使用稱為概念結構定義語言的 DSL ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 來定義概念模型。 下列 CSDL 定義上圖所示之實體實體容器，每個關聯具有一個關聯集。 請注意，關聯集 End 會定義為每個關聯集定義的一部分。  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a>請參閱  
 [實體資料模型索引鍵概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [實體資料模型](../../../../docs/framework/data/adonet/entity-data-model.md)
