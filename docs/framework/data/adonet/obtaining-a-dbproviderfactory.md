---
title: "取得 DbProviderFactory | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a16e4a4d-6a5b-45db-8635-19570e4572ae
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# 取得 DbProviderFactory
取得 <xref:System.Data.Common.DbProviderFactory> 的程序包含傳遞資料提供者的相關資訊給 <xref:System.Data.Common.DbProviderFactories> 類別。  根據這項資訊，<xref:System.Data.Common.DbProviderFactories.GetFactory%2A> 方法會建立強型別 \(Strongly Typed\) 提供者 Factory。  例如，若要建立 <xref:System.Data.SqlClient.SqlClientFactory>，您可以將提供者名稱指定為 "System.Data.SqlClient" 的字串傳遞給 `GetFactory`。  `GetFactory` 的其他多載會接受 <xref:System.Data.DataRow>。  一旦您建立了提供者 Factory，之後就可以使用其方法來建立其他物件。  `SqlClientFactory` 的某些方法包括 <xref:System.Data.SqlClient.SqlClientFactory.CreateConnection%2A>、<xref:System.Data.SqlClient.SqlClientFactory.CreateCommand%2A> 和 <xref:System.Data.SqlClient.SqlClientFactory.CreateDataAdapter%2A>。  
  
> [!NOTE]
>  .NET Framework <xref:System.Data.OracleClient.OracleClientFactory>、<xref:System.Data.Odbc.OdbcFactory> 和 <xref:System.Data.OleDb.OleDbFactory> 類別也會提供類似的功能。  
  
## 註冊 DbProviderFactories  
 每個支援以 Factory 為基礎之類別的 .NET Framework 資料提供者會在本機電腦之 **machine.config** 檔的 **DbProviderFactories** 區段中註冊組態資訊。  下列組態檔片段會顯示 <xref:System.Data.SqlClient> 的語法和格式。  
  
```  
<system.data>  
  <DbProviderFactories>  
    <add name="SqlClient Data Provider"  
     invariant="System.Data.SqlClient"   
     description=".Net Framework Data Provider for SqlServer"   
     type="System.Data.SqlClient.SqlClientFactory, System.Data,   
     Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
    />  
  </DbProviderFactories>  
</system.data>  
```  
  
 **invariant** 屬性可識別基礎資料提供者。  這個三部分命名語法也會用於建立新的 Factory 以及在應用程式組態檔中識別提供者，如此您就可以在執行階段擷取提供者名稱及其相關聯的連接字串。  
  
## 擷取提供者資訊  
 您可以使用 <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A> 方法，擷取本機電腦上所安裝之所有資料提供者的相關資訊。  它會傳回名為 **DbProviderFactories** 的 <xref:System.Data.DataTable>，其中包含下表中描述的資料行。  
  
|資料行序數|資料行名稱|範例輸出|描述|  
|-----------|-----------|----------|--------|  
|0|**名稱**|SqlClient Data Provider|資料提供者的可讀取名稱|  
|1|**描述**|.Net Framework Data Provider for SqlServer|資料提供者的可讀取描述|  
|2|**InvariantName**|System.Data.SqlClient|可用程式設計方式用來參考資料提供者的名稱|  
|3|**AssemblyQualifiedName**|System.Data.SqlClient.SqlClientFactory, System.Data, Version\=2.0.0.0, Culture\=neutral, PublicKeyToken\=b77a5c561934e089|Factory 類別的完整名稱，其中包含具現化物件的足夠資訊|  
  
 這個 `DataTable` 可用來讓使用者在執行階段選取 <xref:System.Data.DataRow>。  然後，選取的 `DataRow` 可傳遞給 <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> 方法，以便建立強型別 <xref:System.Data.Common.DbProviderFactory>。  選取的 <xref:System.Data.DataRow> 可傳遞給 `GetFactory` 方法，以便建立所需的 `DbProviderFactory` 物件。  
  
## 列出已安裝的提供者 Factory 類別  
 這個範例將說明如何使用 <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A> 方法來傳回 <xref:System.Data.DataTable>，其中包含已安裝提供者的相關資訊。  此程式碼會逐一查看 `DataTable` 中的每個資料列，並在主控台視窗中顯示每個已安裝提供者的資訊。  
  
 [!code-csharp[DataWorks DbProviderFactories#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories/VB/source.vb#1)]  
  
## 使用應用程式組態檔來儲存 Factory 資訊  
 用於處理 Factory 的設計模式需要將提供者和連接字串資訊儲存在應用程式組態檔中，例如 Windows 應用程式的 **app.config** 和 ASP.NET 應用程式的 **web.config**。  
  
 下列組態檔片段將說明如何儲存兩個具名連接字串："NorthwindSQL" 代表 SQL Server 中 Northwind 資料庫的連接，而 "NorthwindAccess" 代表 Access\/Jet 中 Northwind 資料庫的連接。  **invariant** 名稱用於 **providerName** 屬性。  
  
```  
<configuration>  
  <connectionStrings>  
    <clear/>  
    <add name="NorthwindSQL"   
     providerName="System.Data.SqlClient"   
     connectionString=  
     "Data Source=MSSQL1;Initial Catalog=Northwind;Integrated Security=true"  
    />  
  
    <add name="NorthwindAccess"   
     providerName="System.Data.OleDb"   
     connectionString=  
     "Provider=Microsoft.Jet.OLEDB.4.0;Data Source=C:\Data\Northwind.mdb;"  
    />  
  </connectionStrings>  
</configuration>  
```  
  
### 依提供者名稱擷取連接字串  
 為了建立提供者 Factory，您必須提供連接字串以及提供者名稱。  這則範例將說明如何透過以 "*System.Data.ProviderName*" 非變異格式來傳遞提供者名稱，從應用程式組態檔中擷取連接字串。  此程式碼會逐一查看 <xref:System.Configuration.ConnectionStringSettingsCollection>。  然後，如果成功，它就會傳回 <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A>，否則便傳回 `null` \(在 Visual Basic 中為 `Nothing`\)。  如果某個提供者有多個項目，就會傳回第一個找到的項目。  如需從組態檔中擷取連接字串的詳細資訊和範例，請參閱[連接字串和組態檔](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md)。  
  
> [!NOTE]
>  您必須使用 `System.Configuration.dll` 的參考，才能讓此程式碼執行。  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/VB/source.vb#1)]  
  
## 建立 DbProviderFactory 和 DbConnection  
 這則範例將說明如何透過以 "*System.Data.ProviderName*" 格式來傳遞提供者名稱和連接字串，建立 <xref:System.Data.Common.DbProviderFactory> 和 <xref:System.Data.Common.DbConnection> 物件。  如果成功，它就會傳回 `DbConnection` 物件。如果發生任何錯誤，則會傳回 `null` \(在 Visual Basic 中為 `Nothing`\)。  
  
 此程式碼會透過呼叫 <xref:System.Data.Common.DbProviderFactories.GetFactory%2A>，取得 `DbProviderFactory`。  然後，<xref:System.Data.Common.DbProviderFactory.CreateConnection%2A> 方法會建立 <xref:System.Data.Common.DbConnection> 物件而且 <xref:System.Data.Common.DbConnection.ConnectionString%2A> 屬性會設定為連接字串。  
  
 [!code-csharp[DataWorks DbProviderFactories.GetFactory#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.GetFactory/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.GetFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.GetFactory/VB/source.vb#1)]  
  
## 請參閱  
 [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)   
 [連接字串](../../../../docs/framework/data/adonet/connection-strings.md)   
 [Using the Configuration Classes](../Topic/Using%20the%20Configuration%20Classes.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)