---
title: "實體資料模型：繼承 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 42c7ef24-710a-4af9-8493-cd41c399ecb0
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# 實體資料模型：繼承
實體資料模型 \(EDM\) 支援[實體類型](../../../../docs/framework/data/adonet/entity-type.md)的繼承。  EDM 中的繼承類似於物件導向程式設計語言中的類別繼承。  如同物件導向語言中的類別，在概念模型中，您可以定義繼承自另一個實體類型 \(「*基底類型*」\(Base Type\)\) 的實體類型 \(「*衍生型別*」\(Derived Type\)\) 。  不過，不同於物件導向程式設計中的類別，在概念模型中，衍生型別永遠會繼承基底類型的所有[屬性](../../../../docs/framework/data/adonet/property.md)和[導覽屬性](../../../../docs/framework/data/adonet/navigation-property.md)。  您不能覆寫衍生型別中的繼承屬性。  
  
 在概念模型中，您可以組建繼承階層，其中的衍生型別繼承自另一種衍生型別。  階層上層的型別 \(階層中非衍生型別的型別\) 稱為「*根型別*」\(Root Type\)。  在繼承階層中，必須在根型別定義[實體索引鍵](../../../../docs/framework/data/adonet/entity-key.md)。  
  
 您不可建置衍生型別繼承自多個型別的繼承階層。  例如，在具有 `Book` 實體類型的概念模型中，您可以定義分別繼承自 `Book` 的衍生型別 `FictionBook` 和 `NonFictionBook`。  不過，您可能無法定義同時繼承自 `FictionBook` 和 `NonFictionBook` 型別的型別。  
  
## 範例  
 下圖顯示包含四種實體類型 \(`Book`、`FictionBook`、`Publisher` 和 `Author`\) 的概念模型：  `FictionBook` 實體類型為衍生型別，繼承自 `Book` 實體類型。  `FictionBook` 型別繼承自 `ISBN (Key)`、`Title` 和 `Revision` 屬性，並且定義稱為 `Genre` 的額外屬性。  
  
 ![繼承](../../../../docs/framework/data/adonet/media/inheritanceexample.gif "InheritanceExample")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) 會使用稱為概念結構定義語言 \([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)\) 的特定定義域語言 \(DSL\) 來定義概念模型。  下列 CSDL 定義實體類型 `FictionBook`，此實體類型繼承自 `Book` 型別 \(如上圖所示\)：  
  
 [!code-xml[EDM_Example_Model#DerivedType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books5.edmx#derivedtype)]  
  
## 請參閱  
 [實體資料模型索引鍵概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)   
 [實體資料模型](../../../../docs/framework/data/adonet/entity-data-model.md)