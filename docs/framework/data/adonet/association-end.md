---
title: "關聯 End"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2c345213-0296-4d90-ac6d-cef179798a75
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 7ceb6d40a47c73c4580a8fc33acc3c395a2c5a06
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="association-end"></a>關聯 End
*關聯 end*識別[實體類型](../../../../docs/framework/data/adonet/entity-type.md)的一個 end 上[關聯](../../../../docs/framework/data/adonet/association-type.md)以及關聯的結尾處，輸入可以存在的執行個體的實體數目。 關聯 End 會定義為關聯的部分。關聯必須具有兩個關聯 End。 [導覽屬性](../../../../docs/framework/data/adonet/navigation-property.md)允許從一個關聯 end 導覽至其他。  
  
 關聯 End 定義包含下列資訊：  
  
-   關聯中相關的其中一個屬性類型。 (必要項)  
  
    > [!NOTE]
    >  若為指定關聯，各關聯的指定實體類型可以相同。 這樣會建立自我關聯。  
  
-   [關聯 end 多重性](../../../../docs/framework/data/adonet/association-end-multiplicity.md)表示可以是位於關聯某一端的實體類型執行個體數目。 關聯 End 多重性的值可以是一 (0)、零或一 (0..1)，或許多 (*)。  
  
-   關聯 End 的名稱。 (選擇項)  
  
-   在關聯 End 中所執行的作業相關資訊，例如刪除時的重疊顯示。 (選擇項)  
  
## <a name="example"></a>範例  
 下圖顯示包含兩個關聯 (`PublishedBy` 和 `WrittenBy`) 的概念模型。 `PublishedBy` 關聯的關聯 End 為 `Book` 和 `Publisher` 實體類型。 `Publisher` End 的多重性是 (1)，而 `Book` End 的多重性是許多 (*)，表示一個發行者發行許多書籍，而一本書籍由一個發行者發行。  
  
 ![範例模型](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 ADO.NET Entity Framework 會使用稱為概念結構定義語言的特定領域語言 (DSL) ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 來定義概念模型。 下列的 CSDL 會定義上圖顯示的 `PublishedBy` 關聯。 請注意，各個關聯 End 的類型、名稱和多重性是由 XML 屬性 (分別為 `Type`、`Role` 和 `Multiplicity` 屬性) 指定的。 關於針對其中一端執行之作業的選擇性資訊會在 XML 項目 (`OnDelete` 項目) 中指定。 在此情況中，如果刪除發行者，也會刪除所有相關的書籍。  
  
 [!code-xml[EDM_Example_Model#AssociationEnd](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#associationend)]  
  
## <a name="see-also"></a>另請參閱  
 [實體資料模型的重要概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [實體資料模型](../../../../docs/framework/data/adonet/entity-data-model.md)
