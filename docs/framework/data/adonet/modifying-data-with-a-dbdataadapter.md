---
title: "使用 DbDataAdapter 來修改資料 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e35c7f9e-648b-4fcc-9361-d365c3e42c9a
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# 使用 DbDataAdapter 來修改資料
<xref:System.Data.Common.DbProviderFactory> 物件的 <xref:System.Data.Common.DbProviderFactory.CreateDataAdapter%2A> 方法可提供 <xref:System.Data.Common.DbDataAdapter> 物件，而它是建立 Factory 時指定之基礎資料提供者的強型別 \(Strongly Typed\) 物件。  然後，您可以使用 <xref:System.Data.Common.DbCommandBuilder> 來建立命令，以便針對資料來源插入、更新和刪除 <xref:System.Data.DataSet> 的資料。  
  
## 使用 DbDataAdapter 擷取資料  
 這則範例將示範如何根據提供者名稱和連接字串 \(Connection String\) 來建立強型別 `DbDataAdapter`。  此程式碼會使用 <xref:System.Data.Common.DbProviderFactory> 的 <xref:System.Data.Common.DbProviderFactory.CreateConnection%2A> 方法來建立 <xref:System.Data.Common.DbConnection>。  接著，此程式碼會使用 <xref:System.Data.Common.DbProviderFactory.CreateCommand%2A> 方法來建立 <xref:System.Data.Common.DbCommand>，以便透過設定其 `CommandText` 和 `Connection` 屬性來選取資料。  最後，此程式碼會使用 <xref:System.Data.Common.DbProviderFactory.CreateDataAdapter%2A> 方法來建立 <xref:System.Data.Common.DbDataAdapter> 物件並設定其 `SelectCommand` 屬性。  `DbDataAdapter` 的 `Fill` 方法會將資料載入 <xref:System.Data.DataTable> 中。  
  
 [!code-csharp[DataWorks DbProviderFactories.DbDataAdapter#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbDataAdapter/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbDataAdapter#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbDataAdapter/VB/source.vb#1)]  
  
## 使用 DbDataAdapter 修改資料  
 這則範例將示範如何透過 <xref:System.Data.Common.DbCommandBuilder> 來產生更新資料來源之資料所需的命令，並使用 <xref:System.Data.Common.DbDataAdapter> 來修改 `DataTable` 中的資料。  `DbDataAdapter` 的 <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> 會設定為從 Customers 資料表中擷取 CustomerID 和 CompanyName。  <xref:System.Data.Common.DbCommandBuilder.GetInsertCommand%2A> 方法可用來設定 <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> 屬性、<xref:System.Data.Common.DbCommandBuilder.GetUpdateCommand%2A> 方法可用來設定 <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> 屬性，而 <xref:System.Data.Common.DbCommandBuilder.GetDeleteCommand%2A> 方法可用來設定 <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> 屬性。  此程式碼會將新的資料列加入至 Customers 資料表並更新資料來源。  然後，此程式碼會搜尋 CustomerID \(針對 Customers 資料表所定義的主索引鍵\)，藉以找出加入的資料列。  它會變更 CompanyName 並更新資料來源。  最後，此程式碼會刪除該資料列。  
  
 [!code-csharp[DataWorks DbProviderFactories.DbDataAdapterModify#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbDataAdapterModify/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbDataAdapterModify#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbDataAdapterModify/VB/source.vb#1)]  
  
## 處理參數  
 .NET Framework 資料提供者會以不同方式來處理參數和參數預留位置的命名及指定。  此處的語法是針對特定的資料來源而量身訂做，如下表所述。  
  
|資料提供者|參數命名語法|  
|-----------|------------|  
|`SqlClient`|以格式 `@`*parametername* 使用具名參數。|  
|`OracleClient`|以格式 `:`*parmname* \(或 *parmname*\) 使用具名參數。|  
|`OleDb`|使用由問號 \(`?`\) 表示的位置參數標記。|  
|`Odbc`|使用由問號 \(`?`\) 表示的位置參數標記。|  
  
 此 Factory 模型對於建立參數化 `DbCommand` 和 `DbDataAdapter` 物件沒有幫助。  您必須建立程式碼的分支，以便建立針對資料提供者量身訂做的參數。  
  
> [!IMPORTANT]
>  基於安全性考量，我們不建議您使用字串串連來建構直接 SQL 陳述式，藉以完全避免提供者專用的參數。  使用字串串連來取代參數會讓應用程式容易遭受 SQL 插入式攻擊。  
  
## 請參閱  
 [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)   
 [取得 DbProviderFactory](../../../../docs/framework/data/adonet/obtaining-a-dbproviderfactory.md)   
 [DbConnection、DbCommand 和 DbException](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)