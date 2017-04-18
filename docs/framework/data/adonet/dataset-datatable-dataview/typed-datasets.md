---
title: "具型別的 DataSet | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 033d2548-cf24-4c05-8179-67d8b009c048
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# 具型別的 DataSet
<xref:System.Data.DataSet> 可透過弱型別變數，使用晚期繫結存取值，也可透過強型別變數存取資料。  您可以使用好記名稱和強型別變數，存取 **DataSet** 內的資料表和資料行。  
  
 具型別的 **DataSet** 是衍生自 **DataSet** 的類別。  因此，它繼承了 **DataSet** 所有的方法、事件和屬性。  而且，具型別的 **DataSet** 提供強型別方法、事件和屬性。  換句話說，您可以依照名稱存取資料表和資料行，而不需要使用集合架構的方法。  具型別的 **DataSet** 不但能使程式碼更容易閱讀，還能使 Visual Studio .NET 程式碼編輯器在您輸入時自動完成輸入行。  
  
 此外，強型別的 **DataSet** 能夠在編譯時間以正確型別存取值。  有了強型別的 **DataSet**，您就能在編譯程式碼時擷取型別不符的錯誤，而不必等到執行階段。  
  
## 在本節中  
 [產生強型別的 DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-strongly-typed-datasets.md)  
 說明如何建立和使用強型別 **DataSet**。  
  
 [為具型別的 DataSet 加上附註](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/annotating-typed-datasets.md)  
 說明如何在不改變基礎結構描述的情況下，為用來產生強型別 **DataSet** 的 XML 結構描述定義語言 \(XSD\) 結構描述加上註釋，以提供 **DataSet** 項目好記名稱。  
  
## 請參閱  
 [DataSet、DataTable 及 DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)