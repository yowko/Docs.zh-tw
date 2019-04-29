---
title: 取得 DbProviderFactory
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a16e4a4d-6a5b-45db-8635-19570e4572ae
ms.openlocfilehash: c84229dc1c32217099eb7ed8b90accc04cc66148
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772188"
---
# <a name="obtaining-a-dbproviderfactory"></a><span data-ttu-id="fe5f8-102">取得 DbProviderFactory</span><span class="sxs-lookup"><span data-stu-id="fe5f8-102">Obtaining a DbProviderFactory</span></span>
<span data-ttu-id="fe5f8-103">取得 <xref:System.Data.Common.DbProviderFactory> 的程序包含傳遞資料提供者的相關資訊給 <xref:System.Data.Common.DbProviderFactories> 類別。</span><span class="sxs-lookup"><span data-stu-id="fe5f8-103">The process of obtaining a <xref:System.Data.Common.DbProviderFactory> involves passing information about a data provider to the <xref:System.Data.Common.DbProviderFactories> class.</span></span> <span data-ttu-id="fe5f8-104">根據這項資訊，<xref:System.Data.Common.DbProviderFactories.GetFactory%2A> 方法會建立強型別 (Strongly Typed) 提供者 Factory。</span><span class="sxs-lookup"><span data-stu-id="fe5f8-104">Based on this information, the <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> method creates a strongly typed provider factory.</span></span> <span data-ttu-id="fe5f8-105">例如，若要建立 <xref:System.Data.SqlClient.SqlClientFactory>，您可以將提供者名稱指定為 "System.Data.SqlClient" 的字串傳遞給 `GetFactory`。</span><span class="sxs-lookup"><span data-stu-id="fe5f8-105">For example, to create a <xref:System.Data.SqlClient.SqlClientFactory>, you can pass `GetFactory` a string with the provider name specified as "System.Data.SqlClient".</span></span> <span data-ttu-id="fe5f8-106">`GetFactory` 的其他多載會接受 <xref:System.Data.DataRow>。</span><span class="sxs-lookup"><span data-stu-id="fe5f8-106">The other overload of `GetFactory` takes a <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="fe5f8-107">一旦您建立了提供者 Factory，之後就可以使用其方法來建立其他物件。</span><span class="sxs-lookup"><span data-stu-id="fe5f8-107">Once you create the provider factory, you can then use its methods to create additional objects.</span></span> <span data-ttu-id="fe5f8-108">`SqlClientFactory` 的某些方法包括 <xref:System.Data.SqlClient.SqlClientFactory.CreateConnection%2A>、<xref:System.Data.SqlClient.SqlClientFactory.CreateCommand%2A> 和 <xref:System.Data.SqlClient.SqlClientFactory.CreateDataAdapter%2A>。</span><span class="sxs-lookup"><span data-stu-id="fe5f8-108">Some of the methods of a `SqlClientFactory` include <xref:System.Data.SqlClient.SqlClientFactory.CreateConnection%2A>, <xref:System.Data.SqlClient.SqlClientFactory.CreateCommand%2A>, and <xref:System.Data.SqlClient.SqlClientFactory.CreateDataAdapter%2A>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fe5f8-109">.NET Framework <xref:System.Data.OracleClient.OracleClientFactory>、<xref:System.Data.Odbc.OdbcFactory> 和 <xref:System.Data.OleDb.OleDbFactory> 類別也會提供類似的功能。</span><span class="sxs-lookup"><span data-stu-id="fe5f8-109">The .NET Framework <xref:System.Data.OracleClient.OracleClientFactory>, <xref:System.Data.Odbc.OdbcFactory>, and <xref:System.Data.OleDb.OleDbFactory> classes also provide similar functionality.</span></span>  
  
## <a name="registering-dbproviderfactories"></a><span data-ttu-id="fe5f8-110">註冊 DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="fe5f8-110">Registering DbProviderFactories</span></span>  
 <span data-ttu-id="fe5f8-111">支援以 factory 為基礎的類別每個.NET Framework 資料提供者註冊中的組態資訊**DbProviderFactories**一節**machine.config**本機電腦上的檔案。</span><span class="sxs-lookup"><span data-stu-id="fe5f8-111">Each .NET Framework data provider that supports a factory-based class registers configuration information in the **DbProviderFactories** section of the **machine.config** file on the local computer.</span></span> <span data-ttu-id="fe5f8-112">下列組態檔片段會顯示 <xref:System.Data.SqlClient> 的語法和格式。</span><span class="sxs-lookup"><span data-stu-id="fe5f8-112">The following configuration file fragment shows the syntax and format for <xref:System.Data.SqlClient>.</span></span>  
  
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
  
 <span data-ttu-id="fe5f8-113">**非變異**屬性可識別基礎資料提供者。</span><span class="sxs-lookup"><span data-stu-id="fe5f8-113">The **invariant** attribute identifies the underlying data provider.</span></span> <span data-ttu-id="fe5f8-114">這個三部分命名語法也會用於建立新的 Factory 以及在應用程式組態檔中識別提供者，如此您就可以在執行階段擷取提供者名稱及其相關聯的連接字串。</span><span class="sxs-lookup"><span data-stu-id="fe5f8-114">This three-part naming syntax is also used when creating a new factory and for identifying the provider in an application configuration file so that the provider name, along with its associated connection string, can be retrieved at run time.</span></span>  
  
## <a name="retrieving-provider-information"></a><span data-ttu-id="fe5f8-115">擷取提供者資訊</span><span class="sxs-lookup"><span data-stu-id="fe5f8-115">Retrieving Provider Information</span></span>  
 <span data-ttu-id="fe5f8-116">您可以使用 <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A>  方法，擷取本機電腦上所安裝之所有資料提供者的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="fe5f8-116">You can retrieve information about all of the data providers installed on the local computer by using the <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A> method.</span></span> <span data-ttu-id="fe5f8-117">它會傳回<xref:System.Data.DataTable>名為**DbProviderFactories** ，其中包含下表所述的資料行。</span><span class="sxs-lookup"><span data-stu-id="fe5f8-117">It returns a <xref:System.Data.DataTable> named **DbProviderFactories** that contains the columns described in the following table.</span></span>  
  
|<span data-ttu-id="fe5f8-118">資料行序數</span><span class="sxs-lookup"><span data-stu-id="fe5f8-118">Column ordinal</span></span>|<span data-ttu-id="fe5f8-119">資料行名稱</span><span class="sxs-lookup"><span data-stu-id="fe5f8-119">Column name</span></span>|<span data-ttu-id="fe5f8-120">範例輸出</span><span class="sxs-lookup"><span data-stu-id="fe5f8-120">Example output</span></span>|<span data-ttu-id="fe5f8-121">描述</span><span class="sxs-lookup"><span data-stu-id="fe5f8-121">Description</span></span>|  
|--------------------|-----------------|--------------------|-----------------|  
|<span data-ttu-id="fe5f8-122">0</span><span class="sxs-lookup"><span data-stu-id="fe5f8-122">0</span></span>|<span data-ttu-id="fe5f8-123">**名稱**</span><span class="sxs-lookup"><span data-stu-id="fe5f8-123">**Name**</span></span>|<span data-ttu-id="fe5f8-124">SqlClient Data Provider</span><span class="sxs-lookup"><span data-stu-id="fe5f8-124">SqlClient Data Provider</span></span>|<span data-ttu-id="fe5f8-125">資料提供者的可讀取名稱</span><span class="sxs-lookup"><span data-stu-id="fe5f8-125">Readable name for the data provider</span></span>|  
|<span data-ttu-id="fe5f8-126">1</span><span class="sxs-lookup"><span data-stu-id="fe5f8-126">1</span></span>|<span data-ttu-id="fe5f8-127">**描述**</span><span class="sxs-lookup"><span data-stu-id="fe5f8-127">**Description**</span></span>|<span data-ttu-id="fe5f8-128">.Net Framework Data Provider for SqlServer</span><span class="sxs-lookup"><span data-stu-id="fe5f8-128">.Net Framework Data Provider for SqlServer</span></span>|<span data-ttu-id="fe5f8-129">資料提供者的可讀取描述</span><span class="sxs-lookup"><span data-stu-id="fe5f8-129">Readable description of the data provider</span></span>|  
|<span data-ttu-id="fe5f8-130">2</span><span class="sxs-lookup"><span data-stu-id="fe5f8-130">2</span></span>|<span data-ttu-id="fe5f8-131">**InvariantName**</span><span class="sxs-lookup"><span data-stu-id="fe5f8-131">**InvariantName**</span></span>|<span data-ttu-id="fe5f8-132">System.Data.SqlClient</span><span class="sxs-lookup"><span data-stu-id="fe5f8-132">System.Data.SqlClient</span></span>|<span data-ttu-id="fe5f8-133">可用程式設計方式用來參考資料提供者的名稱</span><span class="sxs-lookup"><span data-stu-id="fe5f8-133">Name that can be used programmatically to refer to the data provider</span></span>|  
|<span data-ttu-id="fe5f8-134">3</span><span class="sxs-lookup"><span data-stu-id="fe5f8-134">3</span></span>|<span data-ttu-id="fe5f8-135">**AssemblyQualifiedName**</span><span class="sxs-lookup"><span data-stu-id="fe5f8-135">**AssemblyQualifiedName**</span></span>|<span data-ttu-id="fe5f8-136">System.Data.SqlClient.SqlClientFactory, System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089</span><span class="sxs-lookup"><span data-stu-id="fe5f8-136">System.Data.SqlClient.SqlClientFactory, System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089</span></span>|<span data-ttu-id="fe5f8-137">Factory 類別的完整名稱，其中包含具現化物件的足夠資訊</span><span class="sxs-lookup"><span data-stu-id="fe5f8-137">Fully qualified name of the factory class, which contains enough information to instantiate the object</span></span>|  
  
 <span data-ttu-id="fe5f8-138">這個 `DataTable` 可用來讓使用者在執行階段選取 <xref:System.Data.DataRow>。</span><span class="sxs-lookup"><span data-stu-id="fe5f8-138">This `DataTable` can be used to enable a user to select a <xref:System.Data.DataRow> at run time.</span></span> <span data-ttu-id="fe5f8-139">然後，選取的 `DataRow` 可傳遞給 <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> 方法，以便建立強型別 <xref:System.Data.Common.DbProviderFactory>。</span><span class="sxs-lookup"><span data-stu-id="fe5f8-139">The selected `DataRow` can then be passed to the <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> method to create a strongly typed <xref:System.Data.Common.DbProviderFactory>.</span></span> <span data-ttu-id="fe5f8-140">選取的 <xref:System.Data.DataRow> 可傳遞給 `GetFactory` 方法，以便建立所需的 `DbProviderFactory` 物件。</span><span class="sxs-lookup"><span data-stu-id="fe5f8-140">A selected <xref:System.Data.DataRow> can be passed to the `GetFactory` method to create the desired `DbProviderFactory` object.</span></span>  
  
## <a name="listing-the-installed-provider-factory-classes"></a><span data-ttu-id="fe5f8-141">列出已安裝的提供者 Factory 類別</span><span class="sxs-lookup"><span data-stu-id="fe5f8-141">Listing the Installed Provider Factory Classes</span></span>  
 <span data-ttu-id="fe5f8-142">這個範例將說明如何使用 <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A> 方法來傳回 <xref:System.Data.DataTable>，其中包含已安裝提供者的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="fe5f8-142">This example demonstrates how to use the <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A> method to return a <xref:System.Data.DataTable> containing information about the installed providers.</span></span> <span data-ttu-id="fe5f8-143">此程式碼會逐一查看 `DataTable` 中的每個資料列，並在主控台視窗中顯示每個已安裝提供者的資訊。</span><span class="sxs-lookup"><span data-stu-id="fe5f8-143">The code iterates through each row in the `DataTable`, displaying information for each installed provider in the console window.</span></span>  
  
 [!code-csharp[DataWorks DbProviderFactories#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories/VB/source.vb#1)]  
  
## <a name="using-application-configuration-files-to-store-factory-information"></a><span data-ttu-id="fe5f8-144">使用應用程式組態檔來儲存 Factory 資訊</span><span class="sxs-lookup"><span data-stu-id="fe5f8-144">Using Application Configuration Files to Store Factory Information</span></span>  
 <span data-ttu-id="fe5f8-145">用於處理 factory 的設計模式可讓您需要提供者和連接字串將資訊儲存在應用程式組態檔，例如**app.config** Windows 應用程式，和**web.config** ASP.NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="fe5f8-145">The design pattern used for working with factories entails storing provider and connection string information in an application configuration file, such as **app.config** for a Windows application, and **web.config** for an ASP.NET application.</span></span>  
  
 <span data-ttu-id="fe5f8-146">下列組態檔片段將說明如何儲存兩個具名連接字串："NorthwindSQL" 代表 SQL Server 中 Northwind 資料庫的連接，而 "NorthwindAccess" 代表 Access/Jet 中 Northwind 資料庫的連接。</span><span class="sxs-lookup"><span data-stu-id="fe5f8-146">The following configuration file fragment demonstrates how to save two named connection strings, "NorthwindSQL" for a connection to the Northwind database in SQL Server, and "NorthwindAccess" for a connection to the Northwind database in Access/Jet.</span></span> <span data-ttu-id="fe5f8-147">**非變異**名稱會用於**providerName**屬性。</span><span class="sxs-lookup"><span data-stu-id="fe5f8-147">The **invariant** name is used for the **providerName** attribute.</span></span>  
  
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
  
### <a name="retrieving-a-connection-string-by-provider-name"></a><span data-ttu-id="fe5f8-148">依提供者名稱擷取連接字串</span><span class="sxs-lookup"><span data-stu-id="fe5f8-148">Retrieving a Connection String by Provider Name</span></span>  
 <span data-ttu-id="fe5f8-149">為了建立提供者 Factory，您必須提供連接字串以及提供者名稱。</span><span class="sxs-lookup"><span data-stu-id="fe5f8-149">In order to create a provider factory, you must supply a connection string as well as the provider name.</span></span> <span data-ttu-id="fe5f8-150">此範例示範如何從應用程式組態檔擷取連接字串，而異的格式傳遞提供者名稱 」*System.Data.ProviderName*"。</span><span class="sxs-lookup"><span data-stu-id="fe5f8-150">This example demonstrates how to retrieve a connection string from an application configuration file by passing the provider name in the invariant format "*System.Data.ProviderName*".</span></span> <span data-ttu-id="fe5f8-151">此程式碼會逐一查看 <xref:System.Configuration.ConnectionStringSettingsCollection>。</span><span class="sxs-lookup"><span data-stu-id="fe5f8-151">The code iterates through the <xref:System.Configuration.ConnectionStringSettingsCollection>.</span></span> <span data-ttu-id="fe5f8-152">然後，如果成功，它就會傳回 <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A>，否則便傳回 `null` (在 Visual Basic 中為 `Nothing`)。</span><span class="sxs-lookup"><span data-stu-id="fe5f8-152">It returns the <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A> on success; otherwise `null` (`Nothing` in Visual Basic).</span></span> <span data-ttu-id="fe5f8-153">如果某個提供者有多個項目，就會傳回第一個找到的項目。</span><span class="sxs-lookup"><span data-stu-id="fe5f8-153">If there are multiple entries for a provider, the first one found is returned.</span></span> <span data-ttu-id="fe5f8-154">如需詳細資訊和從組態檔擷取連接字串的範例，請參閱 <<c0> [ 連接字串和組態檔](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md)。</span><span class="sxs-lookup"><span data-stu-id="fe5f8-154">For more information and examples of retrieving connection strings from configuration files, see [Connection Strings and Configuration Files](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fe5f8-155">您必須使用 `System.Configuration.dll` 的參考，才能讓此程式碼執行。</span><span class="sxs-lookup"><span data-stu-id="fe5f8-155">A reference to `System.Configuration.dll` is required in order for the code to run.</span></span>  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/VB/source.vb#1)]  
  
## <a name="creating-the-dbproviderfactory-and-dbconnection"></a><span data-ttu-id="fe5f8-156">建立 DbProviderFactory 和 DbConnection</span><span class="sxs-lookup"><span data-stu-id="fe5f8-156">Creating the DbProviderFactory and DbConnection</span></span>  
 <span data-ttu-id="fe5f8-157">此範例示範如何建立<xref:System.Data.Common.DbProviderFactory>並<xref:System.Data.Common.DbConnection>物件，並傳遞它的格式的提供者名稱 」*System.Data.ProviderName*」 和連接字串。</span><span class="sxs-lookup"><span data-stu-id="fe5f8-157">This example demonstrates how to create a <xref:System.Data.Common.DbProviderFactory> and <xref:System.Data.Common.DbConnection> object by passing it the provider name in the format "*System.Data.ProviderName*" and a connection string.</span></span> <span data-ttu-id="fe5f8-158">如果成功，它就會傳回 `DbConnection` 物件。如果發生任何錯誤，則會傳回 `null` (在 Visual Basic 中為 `Nothing`)。</span><span class="sxs-lookup"><span data-stu-id="fe5f8-158">A `DbConnection` object is returned on success; `null` (`Nothing` in Visual Basic) on any error.</span></span>  
  
 <span data-ttu-id="fe5f8-159">此程式碼會透過呼叫 `DbProviderFactory`，取得 <xref:System.Data.Common.DbProviderFactories.GetFactory%2A>。</span><span class="sxs-lookup"><span data-stu-id="fe5f8-159">The code obtains the `DbProviderFactory` by calling <xref:System.Data.Common.DbProviderFactories.GetFactory%2A>.</span></span> <span data-ttu-id="fe5f8-160">然後，<xref:System.Data.Common.DbProviderFactory.CreateConnection%2A> 方法會建立 <xref:System.Data.Common.DbConnection> 物件而且 <xref:System.Data.Common.DbConnection.ConnectionString%2A> 屬性會設定為連接字串。</span><span class="sxs-lookup"><span data-stu-id="fe5f8-160">Then the <xref:System.Data.Common.DbProviderFactory.CreateConnection%2A> method creates the <xref:System.Data.Common.DbConnection> object and the <xref:System.Data.Common.DbConnection.ConnectionString%2A> property is set to the connection string.</span></span>  
  
 [!code-csharp[DataWorks DbProviderFactories.GetFactory#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.GetFactory/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.GetFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.GetFactory/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="fe5f8-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fe5f8-161">See also</span></span>

- [<span data-ttu-id="fe5f8-162">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="fe5f8-162">DbProviderFactories</span></span>](../../../../docs/framework/data/adonet/dbproviderfactories.md)
- [<span data-ttu-id="fe5f8-163">連接字串</span><span class="sxs-lookup"><span data-stu-id="fe5f8-163">Connection Strings</span></span>](../../../../docs/framework/data/adonet/connection-strings.md)
- <span data-ttu-id="fe5f8-164">[使用組態類別](https://docs.microsoft.com/previous-versions/aspnet/ms228063(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="fe5f8-164">[Using the Configuration Classes](https://docs.microsoft.com/previous-versions/aspnet/ms228063(v=vs.100))</span></span>
- [<span data-ttu-id="fe5f8-165">ADO.NET 概觀</span><span class="sxs-lookup"><span data-stu-id="fe5f8-165">ADO.NET Overview</span></span>](ado-net-overview.md)
