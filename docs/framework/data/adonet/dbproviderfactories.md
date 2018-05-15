---
title: DbProviderFactory
ms.date: 03/30/2017
ms.assetid: 2a8e2640-3a49-42a1-a3a9-b43026907ae1
ms.openlocfilehash: 8692dc761f00e0ddc8ec9fad5a5df66b7fda7916
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="dbproviderfactories"></a><span data-ttu-id="4e833-102">DbProviderFactory</span><span class="sxs-lookup"><span data-stu-id="4e833-102">DbProviderFactories</span></span>
<span data-ttu-id="4e833-103"><xref:System.Data.Common> 命名空間 (Namespace) 提供類別 (Class)，可用於建立 <xref:System.Data.Common.DbProviderFactory> 執行個體 (Instance) 以使用特定的資料來源。</span><span class="sxs-lookup"><span data-stu-id="4e833-103">The <xref:System.Data.Common> namespace provides classes for creating <xref:System.Data.Common.DbProviderFactory> instances to work with specific data sources.</span></span> <span data-ttu-id="4e833-104">當您建立 <xref:System.Data.Common.DbProviderFactory> 執行個體並將資料提供者相關資訊傳遞給它時，`DbProviderFactory` 可以根據所提供的資訊來決定要傳回的正確強型別 (Strongly Typed) 物件。</span><span class="sxs-lookup"><span data-stu-id="4e833-104">When you create a <xref:System.Data.Common.DbProviderFactory> instance and pass it information about the data provider, the `DbProviderFactory` can determine the correct, strongly typed connection object to return based on the information it has been provided.</span></span>  
  
 <span data-ttu-id="4e833-105">從 .NET Framework 版本 4 開始，資料提供者 (例如：<xref:System.Data.Odbc>, <xref:System.Data.OleDb>、<xref:System.Data.SqlClient> 及 <xref:System.Data.OracleClient>) 不會再列於 machine.config 檔案中，但自訂提供者會繼續列於該檔案中。</span><span class="sxs-lookup"><span data-stu-id="4e833-105">Beginning in the .NET Framework version 4, data providers such as <xref:System.Data.Odbc>, <xref:System.Data.OleDb>, <xref:System.Data.SqlClient>, and <xref:System.Data.OracleClient> are no longer listed in machine.config file, but custom providers will continue to be listed there.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4e833-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="4e833-106">In This Section</span></span>  
 [<span data-ttu-id="4e833-107">處理站模型概觀</span><span class="sxs-lookup"><span data-stu-id="4e833-107">Factory Model Overview</span></span>](../../../../docs/framework/data/adonet/factory-model-overview.md)  
 <span data-ttu-id="4e833-108">提供 Factory 設計模式和程式設計介面的概觀。</span><span class="sxs-lookup"><span data-stu-id="4e833-108">Provides an overview of the factory design pattern and programming interface.</span></span>  
  
 [<span data-ttu-id="4e833-109">取得 DbProviderFactory</span><span class="sxs-lookup"><span data-stu-id="4e833-109">Obtaining a DbProviderFactory</span></span>](../../../../docs/framework/data/adonet/obtaining-a-dbproviderfactory.md)  
 <span data-ttu-id="4e833-110">示範如何列出已安裝的資料提供者，以及如何從 <xref:System.Data.Common.DbConnection> 建立 `DbProviderFactory`。</span><span class="sxs-lookup"><span data-stu-id="4e833-110">Demonstrates how to list the installed data providers and create a <xref:System.Data.Common.DbConnection> from a `DbProviderFactory`.</span></span>  
  
 [<span data-ttu-id="4e833-111">DbConnection、DbCommand 和 DbException</span><span class="sxs-lookup"><span data-stu-id="4e833-111">DbConnection, DbCommand and DbException</span></span>](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)  
 <span data-ttu-id="4e833-112">示範如何建立 <xref:System.Data.Common.DbCommand> 和 <xref:System.Data.Common.DbDataReader>，以及如何使用 <xref:System.Data.Common.DbException> 處理資料錯誤。</span><span class="sxs-lookup"><span data-stu-id="4e833-112">Demonstrates how to create a <xref:System.Data.Common.DbCommand> and <xref:System.Data.Common.DbDataReader>, and how to handle data errors using <xref:System.Data.Common.DbException>.</span></span>  
  
 [<span data-ttu-id="4e833-113">使用 DbDataAdapter 修改資料</span><span class="sxs-lookup"><span data-stu-id="4e833-113">Modifying Data with a DbDataAdapter</span></span>](../../../../docs/framework/data/adonet/modifying-data-with-a-dbdataadapter.md)  
 <span data-ttu-id="4e833-114">示範如何使用具有 <xref:System.Data.Common.DbCommandBuilder> 的 <xref:System.Data.Common.DbDataAdapter> 擷取及修改資料。</span><span class="sxs-lookup"><span data-stu-id="4e833-114">Demonstrates how to use a <xref:System.Data.Common.DbCommandBuilder> with a <xref:System.Data.Common.DbDataAdapter> to retrieve and modify data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e833-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e833-115">See Also</span></span>  
 [<span data-ttu-id="4e833-116">在 ADO.NET 中擷取和修改資料</span><span class="sxs-lookup"><span data-stu-id="4e833-116">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="4e833-117">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="4e833-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
