---
title: "建立運算式資料行 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0af3bd64-92a2-4b47-ae62-f5df35f131a6
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# 建立運算式資料行
您可以定義資料行的運算式，使其包含從相同資料列的其他資料行值，或從資料表的多重資料列的資料行值來計算所得的值。  若要定義要評估的運算式，請使用目標資料行的 <xref:System.Data.DataColumn.Expression%2A> 屬性，並使用 <xref:System.Data.DataColumn.ColumnName%2A> 屬性來參照運算式中的其他資料行。  運算式資料行的 <xref:System.Data.DataColumn.DataType%2A> 必須適用於運算式傳回的值。  
  
 下表列出數個資料表的運算式資料行可能使用的方法。  
  
|運算式型別|範例|  
|-----------|--------|  
|比較|"Total \>\= 500"|  
|計算|"UnitPrice \* Quantity"|  
|彙總|Sum\(Price\)|  
  
 您可以在現有的 **DataColumn** 物件上設定 **Expression** 屬性，或者包含該屬性做為要傳送至 <xref:System.Data.DataColumn> 建構函式的第三個引數，如下列範例所示。  
  
```vb  
workTable.Columns.Add("Total",Type.GetType("System.Double"))  
workTable.Columns.Add("SalesTax", Type.GetType("System.Double"), _  
  "Total * 0.086")  
  
```  
  
```csharp  
workTable.Columns.Add("Total", typeof(Double));  
workTable.Columns.Add("SalesTax", typeof(Double), "Total * 0.086");  
```  
  
 運算式可參考其他運算式資料行；但循環參考 \(兩個運算式互相參考\) 將產生例外狀況。  如需撰寫運算式的相關規則，請參閱 **DataColumn** 類別的 <xref:System.Data.DataColumn.Expression%2A> 屬性。  
  
## 請參閱  
 <xref:System.Data.DataColumn>   
 <xref:System.Data.DataSet>   
 <xref:System.Data.DataTable>   
 [DataTable 結構描述定義](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)   
 [DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)