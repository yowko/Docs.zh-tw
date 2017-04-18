---
title: "使用命令來修改資料 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f4160389-b9ff-4b74-b655-437c76dcd586
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# 使用命令來修改資料
您可以使用 .NET Framework 資料提供者來執行預存程序或資料定義語言陳述式 \(例如 CREATE TABLE 和 ALTER COLUMN\)，以執行資料庫或目錄的結構描述管理。  這些命令不會像查詢一樣傳回資料列，因此 **Command** 物件會提供 **ExecuteNonQuery** 來處理這些命令。  
  
 除了使用 **ExecuteNonQuery** 修改結構描述，您也可使用這個方法處理能修改資料但不傳回資料列的 SQL 陳述式，例如 INSERT、UPDATE 和 DELETE。  
  
 雖然 **ExecuteNonQuery** 方法不會傳回資料列，但輸入參數、輸出參數和傳回值可透過 **Command** 物件的 **Parameters** 集合來傳遞和傳回。  
  
## 在本節中  
 [更新資料來源中的資料](../../../../docs/framework/data/adonet/updating-data-in-a-data-source.md)  
 說明如何執行修改資料庫資料的命令或預存程序。  
  
 [執行資料庫目錄作業](../../../../docs/framework/data/adonet/performing-catalog-operations.md)  
 說明如何執行修改資料庫結構描述的命令。  
  
## 請參閱  
 [擷取和修改 ADO.NET 中的資料](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)   
 [命令和參數](../../../../docs/framework/data/adonet/commands-and-parameters.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)