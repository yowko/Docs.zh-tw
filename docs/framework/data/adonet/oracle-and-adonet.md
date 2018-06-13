---
title: Oracle 和 ADO.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8ee8e389-53cf-45cf-80bd-1df63ef34f2e
ms.openlocfilehash: d4a86abeca19a0c634d362c1a8a41f5be7346ed7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32765785"
---
# <a name="oracle-and-adonet"></a><span data-ttu-id="4e66f-102">Oracle 和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="4e66f-102">Oracle and ADO.NET</span></span>
> [!NOTE]
>  <span data-ttu-id="4e66f-103"><xref:System.Data.OracleClient> 中的型別已被取代。</span><span class="sxs-lookup"><span data-stu-id="4e66f-103">The types in <xref:System.Data.OracleClient> are deprecated.</span></span> <span data-ttu-id="4e66f-104">目前版本的 .NET Framework 仍然支援這些型別，不過未來的版本就會將其移除。</span><span class="sxs-lookup"><span data-stu-id="4e66f-104">The types remain supported in the current version of.NET Framework but will be removed in a future release.</span></span> <span data-ttu-id="4e66f-105">Microsoft 建議您使用協力廠商的 Oracle 提供者。</span><span class="sxs-lookup"><span data-stu-id="4e66f-105">Microsoft recommends that you use a third-party Oracle provider.</span></span>  
  
 <span data-ttu-id="4e66f-106">本節說明 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for Oracle 特定的功能與行為。</span><span class="sxs-lookup"><span data-stu-id="4e66f-106">This section describes features and behaviors that are specific to the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for Oracle.</span></span>  
  
 <span data-ttu-id="4e66f-107">[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for Oracle 利用 Oracle 用戶端軟體所提供的「Oracle 呼叫介面」(OCI) 來存取 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="4e66f-107">The [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for Oracle provides access to an Oracle database using the Oracle Call Interface (OCI) as provided by Oracle Client software.</span></span> <span data-ttu-id="4e66f-108">資料提供者的功能設計類似於的[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]SQL Server、 OLE DB 和 ODBC 資料提供者。</span><span class="sxs-lookup"><span data-stu-id="4e66f-108">The functionality of the data provider is designed to be similar to that of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] data providers for SQL Server, OLE DB, and ODBC.</span></span>  
  
 <span data-ttu-id="4e66f-109">若要使用 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for Oracle，應用程式必須參考 <xref:System.Data.OracleClient> 命名空間，如下所示：</span><span class="sxs-lookup"><span data-stu-id="4e66f-109">To use the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for Oracle, an application must reference the <xref:System.Data.OracleClient> namespace as follows:</span></span>  
  
```vb  
Imports System.Data.OracleClient  
```  
  
```csharp  
using System.Data.OracleClient;  
```  
  
 <span data-ttu-id="4e66f-110">當您編譯程式碼時，還必須將參考併入 DLL 中。</span><span class="sxs-lookup"><span data-stu-id="4e66f-110">You also must include a reference to the DLL when you compile your code.</span></span> <span data-ttu-id="4e66f-111">例如，如果編譯 C# 程式，則命令列應包括：</span><span class="sxs-lookup"><span data-stu-id="4e66f-111">For example, if you are compiling a C# program, your command line should include:</span></span>  
  
```  
csc /r:System.Data.OracleClient.dll  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="4e66f-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="4e66f-112">In This Section</span></span>  
 [<span data-ttu-id="4e66f-113">系統需求</span><span class="sxs-lookup"><span data-stu-id="4e66f-113">System Requirements</span></span>](../../../../docs/framework/data/adonet/system-requirements-for-the-dotnet-data-provider-for-oracle.md)  
 <span data-ttu-id="4e66f-114">說明使用 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for Oracle 的需求，以及一些在使用時所要注意的問題。</span><span class="sxs-lookup"><span data-stu-id="4e66f-114">Describes requirements for using the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for Oracle, and describes a number of issues to be aware when using it.</span></span>  
  
 [<span data-ttu-id="4e66f-115">Oracle BFILE</span><span class="sxs-lookup"><span data-stu-id="4e66f-115">Oracle BFILEs</span></span>](../../../../docs/framework/data/adonet/oracle-bfiles.md)  
 <span data-ttu-id="4e66f-116">說明用來與 Oracle BFILE 資料型別搭配使用的 <xref:System.Data.OracleClient.OracleBFile> 類別。</span><span class="sxs-lookup"><span data-stu-id="4e66f-116">Describes the <xref:System.Data.OracleClient.OracleBFile> class, which is used to work with the Oracle BFILE data type.</span></span>  
  
 [<span data-ttu-id="4e66f-117">Oracle LOB</span><span class="sxs-lookup"><span data-stu-id="4e66f-117">Oracle LOBs</span></span>](../../../../docs/framework/data/adonet/oracle-lobs.md)  
 <span data-ttu-id="4e66f-118">說明用來與 Oracle LOB 資料型別搭配使用的 <xref:System.Data.OracleClient.OracleLob> 類別。</span><span class="sxs-lookup"><span data-stu-id="4e66f-118">Describes the <xref:System.Data.OracleClient.OracleLob> class, which is used to work with Oracle LOB data types.</span></span>  
  
 [<span data-ttu-id="4e66f-119">Oracle REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="4e66f-119">Oracle REF CURSORs</span></span>](../../../../docs/framework/data/adonet/oracle-ref-cursors.md)  
 <span data-ttu-id="4e66f-120">說明 Oracle REF CURSOR 資料型別的支援。</span><span class="sxs-lookup"><span data-stu-id="4e66f-120">Describes support for the Oracle REF CURSOR data type.</span></span>  
  
 [<span data-ttu-id="4e66f-121">OracleType</span><span class="sxs-lookup"><span data-stu-id="4e66f-121">OracleTypes</span></span>](../../../../docs/framework/data/adonet/oracletypes.md)  
 <span data-ttu-id="4e66f-122">說明可用來與 Oracle 資料型別搭配使用的結構，包括 <xref:System.Data.OracleClient.OracleNumber> 及 <xref:System.Data.OracleClient.OracleString>。</span><span class="sxs-lookup"><span data-stu-id="4e66f-122">Describes structures you can use to work with Oracle data types, including <xref:System.Data.OracleClient.OracleNumber> and <xref:System.Data.OracleClient.OracleString>.</span></span>  
  
 [<span data-ttu-id="4e66f-123">Oracle 序列</span><span class="sxs-lookup"><span data-stu-id="4e66f-123">Oracle Sequences</span></span>](../../../../docs/framework/data/adonet/oracle-sequences.md)  
 <span data-ttu-id="4e66f-124">說明針對擷取伺服器產生的索引鍵 Oracle Sequence 值所提供的支援。</span><span class="sxs-lookup"><span data-stu-id="4e66f-124">Describes support for retrieving the server-generated key Oracle Sequence values.</span></span>  
  
 [<span data-ttu-id="4e66f-125">Oracle 資料類型對應</span><span class="sxs-lookup"><span data-stu-id="4e66f-125">Oracle Data Type Mappings</span></span>](../../../../docs/framework/data/adonet/oracle-data-type-mappings.md)  
 <span data-ttu-id="4e66f-126">列出 Oracle 資料型別及其與 <xref:System.Data.OracleClient.OracleDataReader> 的對應。</span><span class="sxs-lookup"><span data-stu-id="4e66f-126">Lists Oracle data types and their mappings to the <xref:System.Data.OracleClient.OracleDataReader>.</span></span>  
  
 [<span data-ttu-id="4e66f-127">Oracle 分散式異動</span><span class="sxs-lookup"><span data-stu-id="4e66f-127">Oracle Distributed Transactions</span></span>](../../../../docs/framework/data/adonet/oracle-distributed-transactions.md)  
 <span data-ttu-id="4e66f-128">說明如果 <xref:System.Data.OracleClient.OracleConnection> 物件判定交易處於作用中，它會如何自動登記在現有的分散式交易中。</span><span class="sxs-lookup"><span data-stu-id="4e66f-128">Describes how the <xref:System.Data.OracleClient.OracleConnection> object automatically enlists in an existing distributed transaction if it determines that a transaction is active.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="4e66f-129">相關章節</span><span class="sxs-lookup"><span data-stu-id="4e66f-129">Related Sections</span></span>  
 [<span data-ttu-id="4e66f-130">設定 ADO.NET 應用程式的安全性</span><span class="sxs-lookup"><span data-stu-id="4e66f-130">Securing ADO.NET Applications</span></span>](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 <span data-ttu-id="4e66f-131">說明使用 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 的安全程式碼撰寫實施方針。</span><span class="sxs-lookup"><span data-stu-id="4e66f-131">Describes secure coding practices when using [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].</span></span>  
  
 [<span data-ttu-id="4e66f-132">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="4e66f-132">DataSets, DataTables, and DataViews</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 <span data-ttu-id="4e66f-133">說明如何建立及使用 `DataSets`、具型別 `DataSets`、`DataTables` 和 `DataViews`。</span><span class="sxs-lookup"><span data-stu-id="4e66f-133">Describes how to create and use `DataSets`, typed `DataSets`, `DataTables`, and `DataViews`.</span></span>  
  
 [<span data-ttu-id="4e66f-134">在 ADO.NET 中擷取和修改資料</span><span class="sxs-lookup"><span data-stu-id="4e66f-134">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 <span data-ttu-id="4e66f-135">說明如何使用 ADO.NET 中的資料。</span><span class="sxs-lookup"><span data-stu-id="4e66f-135">Describes how to work with data in ADO.NET.</span></span>  
  
 [<span data-ttu-id="4e66f-136">SQL Server 和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="4e66f-136">SQL Server and ADO.NET</span></span>](../../../../docs/framework/data/adonet/sql/index.md)  
 <span data-ttu-id="4e66f-137">說明如何使用 SQL Server 特有的特性和功能。</span><span class="sxs-lookup"><span data-stu-id="4e66f-137">Describes how to work with features and functionality that are specific to SQL Server.</span></span>  
  
 [<span data-ttu-id="4e66f-138">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="4e66f-138">DbProviderFactories</span></span>](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 <span data-ttu-id="4e66f-139">說明可讓您在 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 中撰寫提供者獨立程式碼的泛用類別。</span><span class="sxs-lookup"><span data-stu-id="4e66f-139">Describes generic classes that allow you to write provider-independent code in [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e66f-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e66f-140">See Also</span></span>  
 [<span data-ttu-id="4e66f-141">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="4e66f-141">ADO.NET</span></span>](../../../../docs/framework/data/adonet/index.md)  
 [<span data-ttu-id="4e66f-142">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="4e66f-142">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
