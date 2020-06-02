---
title: 取得 DbProviderFactory
description: 瞭解如何從 DbProviderFactories 類別取得 DbProviderFactory，以便在 .NET Framework 中使用特定的資料來源。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a16e4a4d-6a5b-45db-8635-19570e4572ae
ms.openlocfilehash: b790c87cc3ec293c18bf730567f92b490c7c6594
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286711"
---
# <a name="obtaining-a-dbproviderfactory"></a><span data-ttu-id="2f8d2-103">取得 DbProviderFactory</span><span class="sxs-lookup"><span data-stu-id="2f8d2-103">Obtaining a DbProviderFactory</span></span>
<span data-ttu-id="2f8d2-104">取得 <xref:System.Data.Common.DbProviderFactory> 的程序包含傳遞資料提供者的相關資訊給 <xref:System.Data.Common.DbProviderFactories> 類別。</span><span class="sxs-lookup"><span data-stu-id="2f8d2-104">The process of obtaining a <xref:System.Data.Common.DbProviderFactory> involves passing information about a data provider to the <xref:System.Data.Common.DbProviderFactories> class.</span></span> <span data-ttu-id="2f8d2-105">根據這項資訊，<xref:System.Data.Common.DbProviderFactories.GetFactory%2A> 方法會建立強型別 (Strongly Typed) 提供者 Factory。</span><span class="sxs-lookup"><span data-stu-id="2f8d2-105">Based on this information, the <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> method creates a strongly typed provider factory.</span></span> <span data-ttu-id="2f8d2-106">例如，若要建立 <xref:System.Data.SqlClient.SqlClientFactory>，您可以將提供者名稱指定為 "System.Data.SqlClient" 的字串傳遞給 `GetFactory`。</span><span class="sxs-lookup"><span data-stu-id="2f8d2-106">For example, to create a <xref:System.Data.SqlClient.SqlClientFactory>, you can pass `GetFactory` a string with the provider name specified as "System.Data.SqlClient".</span></span> <span data-ttu-id="2f8d2-107">`GetFactory` 的其他多載會接受 <xref:System.Data.DataRow>。</span><span class="sxs-lookup"><span data-stu-id="2f8d2-107">The other overload of `GetFactory` takes a <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="2f8d2-108">一旦您建立了提供者 Factory，之後就可以使用其方法來建立其他物件。</span><span class="sxs-lookup"><span data-stu-id="2f8d2-108">Once you create the provider factory, you can then use its methods to create additional objects.</span></span> <span data-ttu-id="2f8d2-109">`SqlClientFactory` 的某些方法包括 <xref:System.Data.SqlClient.SqlClientFactory.CreateConnection%2A>、<xref:System.Data.SqlClient.SqlClientFactory.CreateCommand%2A> 和 <xref:System.Data.SqlClient.SqlClientFactory.CreateDataAdapter%2A>。</span><span class="sxs-lookup"><span data-stu-id="2f8d2-109">Some of the methods of a `SqlClientFactory` include <xref:System.Data.SqlClient.SqlClientFactory.CreateConnection%2A>, <xref:System.Data.SqlClient.SqlClientFactory.CreateCommand%2A>, and <xref:System.Data.SqlClient.SqlClientFactory.CreateDataAdapter%2A>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2f8d2-110">.NET Framework <xref:System.Data.OracleClient.OracleClientFactory>、<xref:System.Data.Odbc.OdbcFactory> 和 <xref:System.Data.OleDb.OleDbFactory> 類別也會提供類似的功能。</span><span class="sxs-lookup"><span data-stu-id="2f8d2-110">The .NET Framework <xref:System.Data.OracleClient.OracleClientFactory>, <xref:System.Data.Odbc.OdbcFactory>, and <xref:System.Data.OleDb.OleDbFactory> classes also provide similar functionality.</span></span>  
  
## <a name="registering-dbproviderfactories"></a><span data-ttu-id="2f8d2-111">註冊 DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="2f8d2-111">Registering DbProviderFactories</span></span>  
 <span data-ttu-id="2f8d2-112">支援以 factory 為基礎之類別的每個 .NET Framework Data Provider 都會在本機電腦**上 machine.config 檔案**的**DbProviderFactories**區段中註冊設定資訊。</span><span class="sxs-lookup"><span data-stu-id="2f8d2-112">Each .NET Framework data provider that supports a factory-based class registers configuration information in the **DbProviderFactories** section of the **machine.config** file on the local computer.</span></span> <span data-ttu-id="2f8d2-113">下列組態檔片段會顯示 <xref:System.Data.SqlClient> 的語法和格式。</span><span class="sxs-lookup"><span data-stu-id="2f8d2-113">The following configuration file fragment shows the syntax and format for <xref:System.Data.SqlClient>.</span></span>  
  
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
  
 <span data-ttu-id="2f8d2-114">不**變**屬性會識別基礎資料提供者。</span><span class="sxs-lookup"><span data-stu-id="2f8d2-114">The **invariant** attribute identifies the underlying data provider.</span></span> <span data-ttu-id="2f8d2-115">這個三部分命名語法也會用於建立新的 Factory 以及在應用程式組態檔中識別提供者，如此您就可以在執行階段擷取提供者名稱及其相關聯的連接字串。</span><span class="sxs-lookup"><span data-stu-id="2f8d2-115">This three-part naming syntax is also used when creating a new factory and for identifying the provider in an application configuration file so that the provider name, along with its associated connection string, can be retrieved at run time.</span></span>  
  
## <a name="retrieving-provider-information"></a><span data-ttu-id="2f8d2-116">擷取提供者資訊</span><span class="sxs-lookup"><span data-stu-id="2f8d2-116">Retrieving Provider Information</span></span>  
 <span data-ttu-id="2f8d2-117">您可以使用 <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A>  方法，擷取本機電腦上所安裝之所有資料提供者的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="2f8d2-117">You can retrieve information about all of the data providers installed on the local computer by using the <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A> method.</span></span> <span data-ttu-id="2f8d2-118">它會傳回 <xref:System.Data.DataTable> 名為**DbProviderFactories**的，其中包含下表中所述的資料行。</span><span class="sxs-lookup"><span data-stu-id="2f8d2-118">It returns a <xref:System.Data.DataTable> named **DbProviderFactories** that contains the columns described in the following table.</span></span>  
  
|<span data-ttu-id="2f8d2-119">資料行序數</span><span class="sxs-lookup"><span data-stu-id="2f8d2-119">Column ordinal</span></span>|<span data-ttu-id="2f8d2-120">資料行名稱</span><span class="sxs-lookup"><span data-stu-id="2f8d2-120">Column name</span></span>|<span data-ttu-id="2f8d2-121">範例輸出</span><span class="sxs-lookup"><span data-stu-id="2f8d2-121">Example output</span></span>|<span data-ttu-id="2f8d2-122">描述</span><span class="sxs-lookup"><span data-stu-id="2f8d2-122">Description</span></span>|  
|--------------------|-----------------|--------------------|-----------------|  
|<span data-ttu-id="2f8d2-123">0</span><span class="sxs-lookup"><span data-stu-id="2f8d2-123">0</span></span>|<span data-ttu-id="2f8d2-124">**名稱**</span><span class="sxs-lookup"><span data-stu-id="2f8d2-124">**Name**</span></span>|<span data-ttu-id="2f8d2-125">SqlClient Data Provider</span><span class="sxs-lookup"><span data-stu-id="2f8d2-125">SqlClient Data Provider</span></span>|<span data-ttu-id="2f8d2-126">資料提供者的可讀取名稱</span><span class="sxs-lookup"><span data-stu-id="2f8d2-126">Readable name for the data provider</span></span>|  
|<span data-ttu-id="2f8d2-127">1</span><span class="sxs-lookup"><span data-stu-id="2f8d2-127">1</span></span>|<span data-ttu-id="2f8d2-128">**說明**</span><span class="sxs-lookup"><span data-stu-id="2f8d2-128">**Description**</span></span>|<span data-ttu-id="2f8d2-129">.Net Framework Data Provider for SqlServer</span><span class="sxs-lookup"><span data-stu-id="2f8d2-129">.Net Framework Data Provider for SqlServer</span></span>|<span data-ttu-id="2f8d2-130">資料提供者的可讀取描述</span><span class="sxs-lookup"><span data-stu-id="2f8d2-130">Readable description of the data provider</span></span>|  
|<span data-ttu-id="2f8d2-131">2</span><span class="sxs-lookup"><span data-stu-id="2f8d2-131">2</span></span>|<span data-ttu-id="2f8d2-132">**InvariantName**</span><span class="sxs-lookup"><span data-stu-id="2f8d2-132">**InvariantName**</span></span>|<span data-ttu-id="2f8d2-133">System.Data.SqlClient</span><span class="sxs-lookup"><span data-stu-id="2f8d2-133">System.Data.SqlClient</span></span>|<span data-ttu-id="2f8d2-134">可用程式設計方式用來參考資料提供者的名稱</span><span class="sxs-lookup"><span data-stu-id="2f8d2-134">Name that can be used programmatically to refer to the data provider</span></span>|  
|<span data-ttu-id="2f8d2-135">3</span><span class="sxs-lookup"><span data-stu-id="2f8d2-135">3</span></span>|<span data-ttu-id="2f8d2-136">**AssemblyQualifiedName**</span><span class="sxs-lookup"><span data-stu-id="2f8d2-136">**AssemblyQualifiedName**</span></span>|<span data-ttu-id="2f8d2-137">System.Data.SqlClient.SqlClientFactory, System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089</span><span class="sxs-lookup"><span data-stu-id="2f8d2-137">System.Data.SqlClient.SqlClientFactory, System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089</span></span>|<span data-ttu-id="2f8d2-138">Factory 類別的完整名稱，其中包含具現化物件的足夠資訊</span><span class="sxs-lookup"><span data-stu-id="2f8d2-138">Fully qualified name of the factory class, which contains enough information to instantiate the object</span></span>|  
  
 <span data-ttu-id="2f8d2-139">這個 `DataTable` 可用來讓使用者在執行階段選取 <xref:System.Data.DataRow>。</span><span class="sxs-lookup"><span data-stu-id="2f8d2-139">This `DataTable` can be used to enable a user to select a <xref:System.Data.DataRow> at run time.</span></span> <span data-ttu-id="2f8d2-140">然後，選取的 `DataRow` 可傳遞給 <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> 方法，以便建立強型別 <xref:System.Data.Common.DbProviderFactory>。</span><span class="sxs-lookup"><span data-stu-id="2f8d2-140">The selected `DataRow` can then be passed to the <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> method to create a strongly typed <xref:System.Data.Common.DbProviderFactory>.</span></span> <span data-ttu-id="2f8d2-141">選取的 <xref:System.Data.DataRow> 可傳遞給 `GetFactory` 方法，以便建立所需的 `DbProviderFactory` 物件。</span><span class="sxs-lookup"><span data-stu-id="2f8d2-141">A selected <xref:System.Data.DataRow> can be passed to the `GetFactory` method to create the desired `DbProviderFactory` object.</span></span>  
  
## <a name="listing-the-installed-provider-factory-classes"></a><span data-ttu-id="2f8d2-142">列出已安裝的提供者 Factory 類別</span><span class="sxs-lookup"><span data-stu-id="2f8d2-142">Listing the Installed Provider Factory Classes</span></span>  
 <span data-ttu-id="2f8d2-143">這個範例將說明如何使用 <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A> 方法來傳回 <xref:System.Data.DataTable>，其中包含已安裝提供者的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="2f8d2-143">This example demonstrates how to use the <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A> method to return a <xref:System.Data.DataTable> containing information about the installed providers.</span></span> <span data-ttu-id="2f8d2-144">此程式碼會逐一查看 `DataTable` 中的每個資料列，並在主控台視窗中顯示每個已安裝提供者的資訊。</span><span class="sxs-lookup"><span data-stu-id="2f8d2-144">The code iterates through each row in the `DataTable`, displaying information for each installed provider in the console window.</span></span>  
  
 [!code-csharp[DataWorks DbProviderFactories#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories/VB/source.vb#1)]  
  
## <a name="using-application-configuration-files-to-store-factory-information"></a><span data-ttu-id="2f8d2-145">使用應用程式組態檔來儲存 Factory 資訊</span><span class="sxs-lookup"><span data-stu-id="2f8d2-145">Using Application Configuration Files to Store Factory Information</span></span>  
 <span data-ttu-id="2f8d2-146">用於處理 factory 的設計模式需要將提供者和連接字串資訊儲存在應用程式佈建檔中，例如 Windows 應用程式**的 app.config，** 以及 ASP.NET 應用**程式的 web.config** 。</span><span class="sxs-lookup"><span data-stu-id="2f8d2-146">The design pattern used for working with factories entails storing provider and connection string information in an application configuration file, such as **app.config** for a Windows application, and **web.config** for an ASP.NET application.</span></span>  
  
 <span data-ttu-id="2f8d2-147">下列組態檔片段將說明如何儲存兩個具名連接字串："NorthwindSQL" 代表 SQL Server 中 Northwind 資料庫的連接，而 "NorthwindAccess" 代表 Access/Jet 中 Northwind 資料庫的連接。</span><span class="sxs-lookup"><span data-stu-id="2f8d2-147">The following configuration file fragment demonstrates how to save two named connection strings, "NorthwindSQL" for a connection to the Northwind database in SQL Server, and "NorthwindAccess" for a connection to the Northwind database in Access/Jet.</span></span> <span data-ttu-id="2f8d2-148">不**變**名稱會用於**providerName**屬性。</span><span class="sxs-lookup"><span data-stu-id="2f8d2-148">The **invariant** name is used for the **providerName** attribute.</span></span>  
  
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
  
### <a name="retrieving-a-connection-string-by-provider-name"></a><span data-ttu-id="2f8d2-149">依提供者名稱擷取連接字串</span><span class="sxs-lookup"><span data-stu-id="2f8d2-149">Retrieving a Connection String by Provider Name</span></span>  
 <span data-ttu-id="2f8d2-150">為了建立提供者 Factory，您必須提供連接字串以及提供者名稱。</span><span class="sxs-lookup"><span data-stu-id="2f8d2-150">In order to create a provider factory, you must supply a connection string as well as the provider name.</span></span> <span data-ttu-id="2f8d2-151">這個範例示範如何以不變的*格式 "system.string" 傳遞*提供者名稱，從應用程式佈建檔抓取連接字串。</span><span class="sxs-lookup"><span data-stu-id="2f8d2-151">This example demonstrates how to retrieve a connection string from an application configuration file by passing the provider name in the invariant format "*System.Data.ProviderName*".</span></span> <span data-ttu-id="2f8d2-152">此程式碼會逐一查看 <xref:System.Configuration.ConnectionStringSettingsCollection>。</span><span class="sxs-lookup"><span data-stu-id="2f8d2-152">The code iterates through the <xref:System.Configuration.ConnectionStringSettingsCollection>.</span></span> <span data-ttu-id="2f8d2-153">然後，如果成功，它就會傳回 <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A>，否則便傳回 `null` (在 Visual Basic 中為 `Nothing`)。</span><span class="sxs-lookup"><span data-stu-id="2f8d2-153">It returns the <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A> on success; otherwise `null` (`Nothing` in Visual Basic).</span></span> <span data-ttu-id="2f8d2-154">如果某個提供者有多個項目，就會傳回第一個找到的項目。</span><span class="sxs-lookup"><span data-stu-id="2f8d2-154">If there are multiple entries for a provider, the first one found is returned.</span></span> <span data-ttu-id="2f8d2-155">如需從設定檔抓取連接字串的詳細資訊和範例，請參閱[連接字串和設定檔](connection-strings-and-configuration-files.md)。</span><span class="sxs-lookup"><span data-stu-id="2f8d2-155">For more information and examples of retrieving connection strings from configuration files, see [Connection Strings and Configuration Files](connection-strings-and-configuration-files.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2f8d2-156">您必須使用 `System.Configuration.dll` 的參考，才能讓此程式碼執行。</span><span class="sxs-lookup"><span data-stu-id="2f8d2-156">A reference to `System.Configuration.dll` is required in order for the code to run.</span></span>  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/VB/source.vb#1)]  
  
## <a name="creating-the-dbproviderfactory-and-dbconnection"></a><span data-ttu-id="2f8d2-157">建立 DbProviderFactory 和 DbConnection</span><span class="sxs-lookup"><span data-stu-id="2f8d2-157">Creating the DbProviderFactory and DbConnection</span></span>  
 <span data-ttu-id="2f8d2-158">這個範例會示範如何建立 <xref:System.Data.Common.DbProviderFactory> 和物件，方法是以 <xref:System.Data.Common.DbConnection> "system.string" 的格式傳遞提供*System.Data.ProviderName*者名稱和連接字串。</span><span class="sxs-lookup"><span data-stu-id="2f8d2-158">This example demonstrates how to create a <xref:System.Data.Common.DbProviderFactory> and <xref:System.Data.Common.DbConnection> object by passing it the provider name in the format "*System.Data.ProviderName*" and a connection string.</span></span> <span data-ttu-id="2f8d2-159">如果成功，它就會傳回 `DbConnection` 物件。如果發生任何錯誤，則會傳回 `null` (在 Visual Basic 中為 `Nothing`)。</span><span class="sxs-lookup"><span data-stu-id="2f8d2-159">A `DbConnection` object is returned on success; `null` (`Nothing` in Visual Basic) on any error.</span></span>  
  
 <span data-ttu-id="2f8d2-160">此程式碼會透過呼叫 `DbProviderFactory`，取得 <xref:System.Data.Common.DbProviderFactories.GetFactory%2A>。</span><span class="sxs-lookup"><span data-stu-id="2f8d2-160">The code obtains the `DbProviderFactory` by calling <xref:System.Data.Common.DbProviderFactories.GetFactory%2A>.</span></span> <span data-ttu-id="2f8d2-161">然後，<xref:System.Data.Common.DbProviderFactory.CreateConnection%2A> 方法會建立 <xref:System.Data.Common.DbConnection> 物件而且 <xref:System.Data.Common.DbConnection.ConnectionString%2A> 屬性會設定為連接字串。</span><span class="sxs-lookup"><span data-stu-id="2f8d2-161">Then the <xref:System.Data.Common.DbProviderFactory.CreateConnection%2A> method creates the <xref:System.Data.Common.DbConnection> object and the <xref:System.Data.Common.DbConnection.ConnectionString%2A> property is set to the connection string.</span></span>  
  
 [!code-csharp[DataWorks DbProviderFactories.GetFactory#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.GetFactory/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.GetFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.GetFactory/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="2f8d2-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2f8d2-162">See also</span></span>

- [<span data-ttu-id="2f8d2-163">DbProviderFactory</span><span class="sxs-lookup"><span data-stu-id="2f8d2-163">DbProviderFactories</span></span>](dbproviderfactories.md)
- [<span data-ttu-id="2f8d2-164">連接字串</span><span class="sxs-lookup"><span data-stu-id="2f8d2-164">Connection Strings</span></span>](connection-strings.md)
- <span data-ttu-id="2f8d2-165">[使用組態類別](https://docs.microsoft.com/previous-versions/aspnet/ms228063(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2f8d2-165">[Using the Configuration Classes](https://docs.microsoft.com/previous-versions/aspnet/ms228063(v=vs.100))</span></span>
- <span data-ttu-id="2f8d2-166">[ADO.NET 概觀](ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="2f8d2-166">[ADO.NET Overview](ado-net-overview.md)</span></span>
