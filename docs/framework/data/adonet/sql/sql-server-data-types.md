---
title: SQL Server 資料類型和 ADO.NET
titleSuffix: ''
ms.date: 03/30/2017
ms.assetid: 81b43550-23e8-43bb-b460-7eb8ac825c33
ms.openlocfilehash: db4618ac624ea8401cab682a8c21d8f23c253d05
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91155454"
---
# <a name="sql-server-data-types-and-adonet"></a><span data-ttu-id="5f377-102">SQL Server 資料類型和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="5f377-102">SQL Server Data Types and ADO.NET</span></span>

<span data-ttu-id="5f377-103">SQL Server 和 .NET Framework 是以不同的型別系統為基礎，而且可能會導致資料遺失。</span><span class="sxs-lookup"><span data-stu-id="5f377-103">SQL Server and the .NET Framework are based on different type systems, which can result in potential data loss.</span></span> <span data-ttu-id="5f377-104">為了保留資料完整性，.NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>) 針對使用 SQL Server 資料提供了具型別的存取子方法。</span><span class="sxs-lookup"><span data-stu-id="5f377-104">To preserve data integrity, the .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>) provides typed accessor methods for working with SQL Server data.</span></span> <span data-ttu-id="5f377-105">您可以使用 <xref:System.Data.SqlDbType> 類別中的列舉來指定 <xref:System.Data.SqlClient.SqlParameter> 資料類型。</span><span class="sxs-lookup"><span data-stu-id="5f377-105">You can use the enumerations in the <xref:System.Data.SqlDbType> classes to specify <xref:System.Data.SqlClient.SqlParameter> data types.</span></span>  
  
 <span data-ttu-id="5f377-106">如需描述 SQL Server 和 .NET Framework 資料類型之間資料類型對應的詳細資訊和資料表，請參閱 [SQL Server 資料類型](../sql-server-data-type-mappings.md)對應。</span><span class="sxs-lookup"><span data-stu-id="5f377-106">For more information and a table that describes the data type mappings between SQL Server and .NET Framework data types, see [SQL Server Data Type Mappings](../sql-server-data-type-mappings.md).</span></span>  
  
 <span data-ttu-id="5f377-107">SQL Server 2008 引進了新的資料類型，其設計目的是為了符合商務需求，以處理日期和時間、結構化、半結構化與非結構化資料。</span><span class="sxs-lookup"><span data-stu-id="5f377-107">SQL Server 2008 introduces new data types that are designed to meet business needs to work with date and time, structured, semi-structured, and unstructured data.</span></span> <span data-ttu-id="5f377-108">《SQL Server 2008 線上叢書》中有說明。</span><span class="sxs-lookup"><span data-stu-id="5f377-108">These are documented in SQL Server 2008 Books Online.</span></span>  
  
 <span data-ttu-id="5f377-109">可在應用程式中使用的 SQL Server 資料類型，取決於您目前使用的 SQL Server 版本。</span><span class="sxs-lookup"><span data-stu-id="5f377-109">The SQL Server data types that are available for use in your application depends on the version of SQL Server that you are using.</span></span> <span data-ttu-id="5f377-110">如需詳細資訊，請參閱下表中的相關《SQL Server 線上叢書》版本。</span><span class="sxs-lookup"><span data-stu-id="5f377-110">For more information, see the relevant version of SQL Server Books Online in the following table.</span></span>  
  
 <span data-ttu-id="5f377-111">**SQL Server 文件**</span><span class="sxs-lookup"><span data-stu-id="5f377-111">**SQL Server documentation**</span></span>  
  
1. [<span data-ttu-id="5f377-112">資料類型 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="5f377-112">Data Types (Transact-SQL)</span></span>](/sql/t-sql/data-types/data-types-transact-sql)  
  
## <a name="in-this-section"></a><span data-ttu-id="5f377-113">本節內容</span><span class="sxs-lookup"><span data-stu-id="5f377-113">In This Section</span></span>  

 [<span data-ttu-id="5f377-114">SqlTypes 和資料集</span><span class="sxs-lookup"><span data-stu-id="5f377-114">SqlTypes and the DataSet</span></span>](sqltypes-and-the-dataset.md)  
 <span data-ttu-id="5f377-115">說明針對 `DataSet` 中的 `SqlTypes` 所提供的類型支援。</span><span class="sxs-lookup"><span data-stu-id="5f377-115">Describes type support for `SqlTypes` in the `DataSet`.</span></span>  
  
 [<span data-ttu-id="5f377-116">處理 Null 值</span><span class="sxs-lookup"><span data-stu-id="5f377-116">Handling Null Values</span></span>](handling-null-values.md)  
 <span data-ttu-id="5f377-117">示範如何處理 Null 值與三值邏輯。</span><span class="sxs-lookup"><span data-stu-id="5f377-117">Demonstrates how to work with null values and three-valued logic.</span></span>  
  
 [<span data-ttu-id="5f377-118">比較 GUID 和 uniqueidentifier 值</span><span class="sxs-lookup"><span data-stu-id="5f377-118">Comparing GUID and uniqueidentifier Values</span></span>](comparing-guid-and-uniqueidentifier-values.md)  
 <span data-ttu-id="5f377-119">示範如何在 SQL Server 和 .NET Framework 中使用 GUID 和 uniqueidentifier 值。</span><span class="sxs-lookup"><span data-stu-id="5f377-119">Demonstrates how to work with GUID and uniqueidentifier values in SQL Server and the .NET Framework.</span></span>  
  
 [<span data-ttu-id="5f377-120">日期和時間資料</span><span class="sxs-lookup"><span data-stu-id="5f377-120">Date and Time Data</span></span>](date-and-time-data.md)  
 <span data-ttu-id="5f377-121">描述如何使用 SQL Server 2008 中引進的新日期和時間資料類型。</span><span class="sxs-lookup"><span data-stu-id="5f377-121">Describes how to use the new date and time data types introduced in SQL Server 2008.</span></span>  
  
 [<span data-ttu-id="5f377-122">大型 UDT</span><span class="sxs-lookup"><span data-stu-id="5f377-122">Large UDTs</span></span>](large-udts.md)  
 <span data-ttu-id="5f377-123">示範如何從 SQL Server 2008 引進的大型值 UDT 擷取資料。</span><span class="sxs-lookup"><span data-stu-id="5f377-123">Demonstrates how to retrieve data from large value UDTs introduced in SQL Server 2008.</span></span>  
  
 [<span data-ttu-id="5f377-124">SQL Server 中的 XML 資料</span><span class="sxs-lookup"><span data-stu-id="5f377-124">XML Data in SQL Server</span></span>](xml-data-in-sql-server.md)  
 <span data-ttu-id="5f377-125">說明如何使用從 SQL Server 擷取的 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="5f377-125">Describes how to work with XML data retrieved from SQL Server.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="5f377-126">參考</span><span class="sxs-lookup"><span data-stu-id="5f377-126">Reference</span></span>  

 <xref:System.Data.DataSet>  
 <span data-ttu-id="5f377-127">描述 `DataSet` 類別與其所有成員。</span><span class="sxs-lookup"><span data-stu-id="5f377-127">Describes the `DataSet` class and all of its members.</span></span>  
  
 <xref:System.Data.SqlTypes>  
 <span data-ttu-id="5f377-128">描述 `SqlTypes` 命名空間與其所有成員。</span><span class="sxs-lookup"><span data-stu-id="5f377-128">Describes the `SqlTypes` namespace and all of its members.</span></span>  
  
 <xref:System.Data.SqlDbType>  
 <span data-ttu-id="5f377-129">描述 `SqlDbType` 列舉與其所有成員。</span><span class="sxs-lookup"><span data-stu-id="5f377-129">Describes the `SqlDbType` enumeration and all of its members.</span></span>  
  
 <xref:System.Data.DbType>  
 <span data-ttu-id="5f377-130">描述 `DbType` 列舉與其所有成員。</span><span class="sxs-lookup"><span data-stu-id="5f377-130">Describes the `DbType` enumeration and all of its members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f377-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f377-131">See also</span></span>

- [<span data-ttu-id="5f377-132">SQL Server 資料類型對應</span><span class="sxs-lookup"><span data-stu-id="5f377-132">SQL Server Data Type Mappings</span></span>](../sql-server-data-type-mappings.md)
- [<span data-ttu-id="5f377-133">設定參數和參數資料類型</span><span class="sxs-lookup"><span data-stu-id="5f377-133">Configuring Parameters and Parameter Data Types</span></span>](../configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="5f377-134">資料表值參數</span><span class="sxs-lookup"><span data-stu-id="5f377-134">Table-Valued Parameters</span></span>](table-valued-parameters.md)
- [<span data-ttu-id="5f377-135">SQL Server 二進位和大數值資料</span><span class="sxs-lookup"><span data-stu-id="5f377-135">SQL Server Binary and Large-Value Data</span></span>](sql-server-binary-and-large-value-data.md)
- <span data-ttu-id="5f377-136">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="5f377-136">[ADO.NET Overview](../ado-net-overview.md)</span></span>
