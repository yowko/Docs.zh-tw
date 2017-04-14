---
title: "將 XML 結構描述 (XSD) 條件約束對應至 DataSet 條件約束 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3d0d1a4b-9104-434f-ac04-6c01ab5716b5
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# 將 XML 結構描述 (XSD) 條件約束對應至 DataSet 條件約束
XML 結構描述定義語言 \(XSD\) 允許在其定義的項目和屬性上指定條件約束。  將 XML 結構描述對應至 <xref:System.Data.DataSet> 內的關聯式結構描述時，XML 結構描述條件約束會對應至 **DataSet** 內資料表和資料行中的適當關聯式條件約束 \(Constraint\)。  
  
 本節討論下列 XML 結構描述條件約束的對應：  
  
-   使用 **unique** 項目指定的唯一性條件約束。  
  
-   使用 **key** 項目指定的索引鍵條件約束。  
  
-   使用 **keyref** 項目指定的 keyref 條件約束。  
  
 您可以在項目或屬性上使用條件約束，為文件內任何執行個體項目的值指定特定限制。  例如，在結構描述內 **Customer** 項目的 **CustomerID** 項目子系中，索引鍵條件約束會指出 **CustomerID** 項目子系的值在任何文件執行個體中必須是唯一，且不可為 Null 值。  
  
 您也可以在文件的項目和屬性間指定條件約束，以便在文件中建立關係。  結構描述中會使用索引鍵條件約束和 keyref 條件約束在文件內指定條件約束，以建立文件項目和屬性之間的關係。  
  
 對應處理會在 **DataSet** 內建立的資料表上，將這些結構描述條件約束轉換為適當的條件約束。  
  
## 在本節中  
 [將 XML 結構描述 \(XSD\) 的唯一條件約束對應至 DataSet 條件約束](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-unique-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 說明用來在 **DataSet** 內建立唯一的條件約束的 XML 結構描述項目。  
  
 [將 XML 結構描述 \(XSD\) 索引鍵條件約束對應至 DataSet 條件約束](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-key-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 說明用來在 **DataSet** 內建立索引鍵條件約束 \(唯一的條件約束，不允許 Null 值\) 的 XML 結構描述項目。  
  
 [將 XML 結構描述 \(XSD\) keyref 條件約束對應至 DataSet 條件約束](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-keyref-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 說明用來在 **DataSet** 內建立 keyref \(外部索引鍵\) 條件約束的 XML 結構描述項目。  
  
## 相關章節  
 [從 XML 結構描述 \(XSD\) 衍生 DataSet 關聯式結構](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 說明從 XSD 結構描述中建立的 **DataSet** 之關聯式結構 \(或結構描述\)。  
  
 [從 XML 結構描述 \(XSD\) 產生 DataSet 關聯](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 說明用來在 **DataSet** 內的資料表資料行間建立關聯的 XML 結構描述項目。  
  
## 請參閱  
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)