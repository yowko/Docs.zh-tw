---
title: 取得 DbProviderFactory
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a16e4a4d-6a5b-45db-8635-19570e4572ae
ms.openlocfilehash: 1099d8ec8e9d516b2269232857c695f9ff04d99c
ms.sourcegitcommit: c6f69b0cf149f6b54483a6d5c2ece222913f43ce
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55904600"
---
# <a name="obtaining-a-dbproviderfactory"></a>取得 DbProviderFactory
取得 <xref:System.Data.Common.DbProviderFactory> 的程序包含傳遞資料提供者的相關資訊給 <xref:System.Data.Common.DbProviderFactories> 類別。 根據這項資訊，<xref:System.Data.Common.DbProviderFactories.GetFactory%2A> 方法會建立強型別 (Strongly Typed) 提供者 Factory。 例如，若要建立 <xref:System.Data.SqlClient.SqlClientFactory>，您可以將提供者名稱指定為 "System.Data.SqlClient" 的字串傳遞給 `GetFactory`。 `GetFactory` 的其他多載會接受 <xref:System.Data.DataRow>。 一旦您建立了提供者 Factory，之後就可以使用其方法來建立其他物件。 `SqlClientFactory` 的某些方法包括 <xref:System.Data.SqlClient.SqlClientFactory.CreateConnection%2A>、<xref:System.Data.SqlClient.SqlClientFactory.CreateCommand%2A> 和 <xref:System.Data.SqlClient.SqlClientFactory.CreateDataAdapter%2A>。  
  
> [!NOTE]
>  .NET Framework <xref:System.Data.OracleClient.OracleClientFactory>、<xref:System.Data.Odbc.OdbcFactory> 和 <xref:System.Data.OleDb.OleDbFactory> 類別也會提供類似的功能。  
  
## <a name="registering-dbproviderfactories"></a>註冊 DbProviderFactories  
 支援以 factory 為基礎的類別每個.NET Framework 資料提供者註冊中的組態資訊**DbProviderFactories**一節**machine.config**本機電腦上的檔案。 下列組態檔片段會顯示 <xref:System.Data.SqlClient> 的語法和格式。  
  
```xml  
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
  
 **非變異**屬性可識別基礎資料提供者。 這個三部分命名語法也會用於建立新的 Factory 以及在應用程式組態檔中識別提供者，如此您就可以在執行階段擷取提供者名稱及其相關聯的連接字串。  
  
## <a name="retrieving-provider-information"></a>擷取提供者資訊  
 您可以使用 <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A>  方法，擷取本機電腦上所安裝之所有資料提供者的相關資訊。 它會傳回<xref:System.Data.DataTable>名為**DbProviderFactories** ，其中包含下表所述的資料行。  
  
|資料行序數|資料行名稱|範例輸出|描述|  
|--------------------|-----------------|--------------------|-----------------|  
|0|**名稱**|SqlClient Data Provider|資料提供者的可讀取名稱|  
|1|**描述**|.Net Framework Data Provider for SqlServer|資料提供者的可讀取描述|  
|2|**InvariantName**|System.Data.SqlClient|可用程式設計方式用來參考資料提供者的名稱|  
|3|**AssemblyQualifiedName**|System.Data.SqlClient.SqlClientFactory, System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089|Factory 類別的完整名稱，其中包含具現化物件的足夠資訊|  
  
 這個 `DataTable` 可用來讓使用者在執行階段選取 <xref:System.Data.DataRow>。 然後，選取的 `DataRow` 可傳遞給 <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> 方法，以便建立強型別 <xref:System.Data.Common.DbProviderFactory>。 選取的 <xref:System.Data.DataRow> 可傳遞給 `GetFactory` 方法，以便建立所需的 `DbProviderFactory` 物件。  
  
## <a name="listing-the-installed-provider-factory-classes"></a>列出已安裝的提供者 Factory 類別  
 這個範例將說明如何使用 <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A> 方法來傳回 <xref:System.Data.DataTable>，其中包含已安裝提供者的相關資訊。 此程式碼會逐一查看 `DataTable` 中的每個資料列，並在主控台視窗中顯示每個已安裝提供者的資訊。  
  
 [!code-csharp[DataWorks DbProviderFactories#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories/VB/source.vb#1)]  
  
## <a name="using-application-configuration-files-to-store-factory-information"></a>使用應用程式組態檔來儲存 Factory 資訊  
 用於處理 factory 的設計模式可讓您需要提供者和連接字串將資訊儲存在應用程式組態檔，例如**app.config** Windows 應用程式，和**web.config** ASP.NET 應用程式。  
  
 下列組態檔片段將說明如何儲存兩個具名連接字串："NorthwindSQL" 代表 SQL Server 中 Northwind 資料庫的連接，而 "NorthwindAccess" 代表 Access/Jet 中 Northwind 資料庫的連接。 **非變異**名稱會用於**providerName**屬性。  
  
```xml  
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
  
### <a name="retrieving-a-connection-string-by-provider-name"></a>依提供者名稱擷取連接字串  
 為了建立提供者 Factory，您必須提供連接字串以及提供者名稱。 此範例示範如何從應用程式組態檔擷取連接字串，而異的格式傳遞提供者名稱 」*System.Data.ProviderName*"。 此程式碼會逐一查看 <xref:System.Configuration.ConnectionStringSettingsCollection>。 然後，如果成功，它就會傳回 <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A>，否則便傳回 `null` (在 Visual Basic 中為 `Nothing`)。 如果某個提供者有多個項目，就會傳回第一個找到的項目。 如需詳細資訊和從組態檔擷取連接字串的範例，請參閱 <<c0> [ 連接字串和組態檔](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md)。  
  
> [!NOTE]
>  您必須使用 `System.Configuration.dll` 的參考，才能讓此程式碼執行。  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/VB/source.vb#1)]  
  
## <a name="creating-the-dbproviderfactory-and-dbconnection"></a>建立 DbProviderFactory 和 DbConnection  
 此範例示範如何建立<xref:System.Data.Common.DbProviderFactory>並<xref:System.Data.Common.DbConnection>物件，並傳遞它的格式的提供者名稱 」*System.Data.ProviderName*」 和連接字串。 如果成功，它就會傳回 `DbConnection` 物件。如果發生任何錯誤，則會傳回 `null` (在 Visual Basic 中為 `Nothing`)。  
  
 此程式碼會透過呼叫 `DbProviderFactory`，取得 <xref:System.Data.Common.DbProviderFactories.GetFactory%2A>。 然後，<xref:System.Data.Common.DbProviderFactory.CreateConnection%2A> 方法會建立 <xref:System.Data.Common.DbConnection> 物件而且 <xref:System.Data.Common.DbConnection.ConnectionString%2A> 屬性會設定為連接字串。  
  
 [!code-csharp[DataWorks DbProviderFactories.GetFactory#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.GetFactory/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.GetFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.GetFactory/VB/source.vb#1)]  
  
## <a name="see-also"></a>另請參閱
- [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)
- [連接字串](../../../../docs/framework/data/adonet/connection-strings.md)
- [使用組態類別](https://docs.microsoft.com/previous-versions/aspnet/ms228063(v=vs.100))
- [ADO.NET 概觀](ado-net-overview.md)
