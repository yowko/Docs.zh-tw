---
title: SQL Server 資料類型和 ADO.NET
ms.date: 03/30/2017
ms.assetid: 81b43550-23e8-43bb-b460-7eb8ac825c33
ms.openlocfilehash: 878bbe41f259f1e50cd0a41669c7a352e78bc0f1
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2018
ms.locfileid: "44493572"
---
# <a name="sql-server-data-types-and-adonet"></a><span data-ttu-id="998e6-102">SQL Server 資料類型和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="998e6-102">SQL Server Data Types and ADO.NET</span></span>
<span data-ttu-id="998e6-103">SQL Server 和 .NET Framework 是以不同的型別系統為基礎，而且可能會導致資料遺失。</span><span class="sxs-lookup"><span data-stu-id="998e6-103">SQL Server and the .NET Framework are based on different type systems, which can result in potential data loss.</span></span> <span data-ttu-id="998e6-104">為了保留資料完整性，.NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>) 針對使用 SQL Server 資料提供了具型別的存取子方法。</span><span class="sxs-lookup"><span data-stu-id="998e6-104">To preserve data integrity, the .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>) provides typed accessor methods for working with SQL Server data.</span></span> <span data-ttu-id="998e6-105">您可以使用 <xref:System.Data.SqlDbType> 類別 (Class) 中的列舉型別 (Enumeration) 來指定 <xref:System.Data.SqlClient.SqlParameter> 資料型別。</span><span class="sxs-lookup"><span data-stu-id="998e6-105">You can use the enumerations in the <xref:System.Data.SqlDbType> classes to specify <xref:System.Data.SqlClient.SqlParameter> data types.</span></span>  
  
 <span data-ttu-id="998e6-106">如需詳細資訊的資料表，描述的資料類型 SQL Server 與.NET Framework 資料型別之間的對應中，請參閱[SQL Server 資料類型對應](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)。</span><span class="sxs-lookup"><span data-stu-id="998e6-106">For more information and a table that that describes the data type mappings between SQL Server and .NET Framework data types, see [SQL Server Data Type Mappings](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md).</span></span>  
  
 <span data-ttu-id="998e6-107">SQL Server 2008 導入了一些設計成符合商務需求的新資料型別，以便使用日期和時間、結構化、半結構化和非結構化資料。</span><span class="sxs-lookup"><span data-stu-id="998e6-107">SQL Server 2008 introduces new data types that are designed to meet business needs to work with date and time, structured, semi-structured, and unstructured data.</span></span> <span data-ttu-id="998e6-108">這些資料型別列於《SQL Server 2008 線上叢書》中。</span><span class="sxs-lookup"><span data-stu-id="998e6-108">These are documented in SQL Server 2008 Books Online.</span></span>  
  
 <span data-ttu-id="998e6-109">可用於應用程式中的 SQL Server 資料型別取決於您所使用的 SQL Server 版本。</span><span class="sxs-lookup"><span data-stu-id="998e6-109">The SQL Server data types that are available for use in your application depends on the version of SQL Server that you are using.</span></span> <span data-ttu-id="998e6-110">如需詳細資訊，請參閱下表中的相關《SQL Server 線上叢書》版本。</span><span class="sxs-lookup"><span data-stu-id="998e6-110">For more information, see the relevant version of SQL Server Books Online in the following table.</span></span>  
  
 <span data-ttu-id="998e6-111">**SQL Server 線上叢書**</span><span class="sxs-lookup"><span data-stu-id="998e6-111">**SQL Server Books Online**</span></span>  
  
1.  [<span data-ttu-id="998e6-112">資料類型 (Database Engine)</span><span class="sxs-lookup"><span data-stu-id="998e6-112">Data Types (Database Engine)</span></span>](https://go.microsoft.com/fwlink/?LinkID=107468)  
  
## <a name="in-this-section"></a><span data-ttu-id="998e6-113">本節內容</span><span class="sxs-lookup"><span data-stu-id="998e6-113">In This Section</span></span>  
 [<span data-ttu-id="998e6-114">SqlTypes 和資料集</span><span class="sxs-lookup"><span data-stu-id="998e6-114">SqlTypes and the DataSet</span></span>](../../../../../docs/framework/data/adonet/sql/sqltypes-and-the-dataset.md)  
 <span data-ttu-id="998e6-115">說明針對 `SqlTypes` 中的 `DataSet` 所提供的型別支援。</span><span class="sxs-lookup"><span data-stu-id="998e6-115">Describes type support for `SqlTypes` in the `DataSet`.</span></span>  
  
 [<span data-ttu-id="998e6-116">處理 Null 值</span><span class="sxs-lookup"><span data-stu-id="998e6-116">Handling Null Values</span></span>](../../../../../docs/framework/data/adonet/sql/handling-null-values.md)  
 <span data-ttu-id="998e6-117">示範如何使用 Null 值和三種值的邏輯。</span><span class="sxs-lookup"><span data-stu-id="998e6-117">Demonstrates how to work with null values and three-valued logic.</span></span>  
  
 [<span data-ttu-id="998e6-118">比較 GUID 和 uniqueidentifier 值</span><span class="sxs-lookup"><span data-stu-id="998e6-118">Comparing GUID and uniqueidentifier Values</span></span>](../../../../../docs/framework/data/adonet/sql/comparing-guid-and-uniqueidentifier-values.md)  
 <span data-ttu-id="998e6-119">示範如何在 SQL Server 和 .NET Framework 中使用 GUID 和 uniqueidentifier 值。</span><span class="sxs-lookup"><span data-stu-id="998e6-119">Demonstrates how to work with GUID and uniqueidentifier values in SQL Server and the .NET Framework.</span></span>  
  
 [<span data-ttu-id="998e6-120">日期和時間資料</span><span class="sxs-lookup"><span data-stu-id="998e6-120">Date and Time Data</span></span>](../../../../../docs/framework/data/adonet/sql/date-and-time-data.md)  
 <span data-ttu-id="998e6-121">說明如何使用 SQL Server 2008 所導入的新日期和時間資料型別。</span><span class="sxs-lookup"><span data-stu-id="998e6-121">Describes how to use the new date and time data types introduced in SQL Server 2008.</span></span>  
  
 [<span data-ttu-id="998e6-122">大型 UDT</span><span class="sxs-lookup"><span data-stu-id="998e6-122">Large UDTs</span></span>](../../../../../docs/framework/data/adonet/sql/large-udts.md)  
 <span data-ttu-id="998e6-123">示範如何從 SQL Server 2008 所導入的大數值 UDT 中擷取資料。</span><span class="sxs-lookup"><span data-stu-id="998e6-123">Demonstrates how to retrieve data from large value UDTs introduced in SQL Server 2008.</span></span>  
  
 [<span data-ttu-id="998e6-124">SQL Server 中的 XML 資料</span><span class="sxs-lookup"><span data-stu-id="998e6-124">XML Data in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/xml-data-in-sql-server.md)  
 <span data-ttu-id="998e6-125">說明如何使用從 SQL Server 擷取的 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="998e6-125">Describes how to work with XML data retrieved from SQL Server.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="998e6-126">參考資料</span><span class="sxs-lookup"><span data-stu-id="998e6-126">Reference</span></span>  
 <xref:System.Data.DataSet>  
 <span data-ttu-id="998e6-127">說明 `DataSet` 類別及其所有成員。</span><span class="sxs-lookup"><span data-stu-id="998e6-127">Describes the `DataSet` class and all of its members.</span></span>  
  
 <xref:System.Data.SqlTypes>  
 <span data-ttu-id="998e6-128">說明 `SqlTypes` 命名空間 (Namespace) 及其所有成員。</span><span class="sxs-lookup"><span data-stu-id="998e6-128">Describes the `SqlTypes` namespace and all of its members.</span></span>  
  
 <xref:System.Data.SqlDbType>  
 <span data-ttu-id="998e6-129">說明 `SqlDbType` 列舉型別及其所有成員。</span><span class="sxs-lookup"><span data-stu-id="998e6-129">Describes the `SqlDbType` enumeration and all of its members.</span></span>  
  
 <xref:System.Data.DbType>  
 <span data-ttu-id="998e6-130">說明 `DbType` 列舉型別及其所有成員。</span><span class="sxs-lookup"><span data-stu-id="998e6-130">Describes the `DbType` enumeration and all of its members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="998e6-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="998e6-131">See Also</span></span>  
 [<span data-ttu-id="998e6-132">SQL Server 資料類型對應</span><span class="sxs-lookup"><span data-stu-id="998e6-132">SQL Server Data Type Mappings</span></span>](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 [<span data-ttu-id="998e6-133">設定參數和參數資料類型</span><span class="sxs-lookup"><span data-stu-id="998e6-133">Configuring Parameters and Parameter Data Types</span></span>](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [<span data-ttu-id="998e6-134">資料表值參數</span><span class="sxs-lookup"><span data-stu-id="998e6-134">Table-Valued Parameters</span></span>](../../../../../docs/framework/data/adonet/sql/table-valued-parameters.md)  
 [<span data-ttu-id="998e6-135">SQL Server 二進位和大量數值資料</span><span class="sxs-lookup"><span data-stu-id="998e6-135">SQL Server Binary and Large-Value Data</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 [<span data-ttu-id="998e6-136">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="998e6-136">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
