---
title: 命令和參數
description: 瞭解如何針對每個 .NET Framework 資料提供者使用命令物件，以執行命令並從資料來源傳回結果。
ms.date: 03/30/2017
ms.assetid: b623f810-d871-49a5-b0f5-078cc3c34db6
ms.openlocfilehash: fb7b86dc3c826805e0e1dcec4764be2e484ec40b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203822"
---
# <a name="commands-and-parameters"></a><span data-ttu-id="2afd9-103">命令和參數</span><span class="sxs-lookup"><span data-stu-id="2afd9-103">Commands and Parameters</span></span>

<span data-ttu-id="2afd9-104">建立連至資料來源的連接後，您可以執行命令，並使用 <xref:System.Data.Common.DbCommand> 物件從資料來源傳回結果。</span><span class="sxs-lookup"><span data-stu-id="2afd9-104">After establishing a connection to a data source, you can execute commands and return results from the data source using a <xref:System.Data.Common.DbCommand> object.</span></span> <span data-ttu-id="2afd9-105">您可以使用目前使用中 .NET Framework 資料提供者的其中一個命令建構函式 (Constructor) 來建立命令。</span><span class="sxs-lookup"><span data-stu-id="2afd9-105">You can create a command using one of the command constructors for the .NET Framework data provider you are working with.</span></span> <span data-ttu-id="2afd9-106">建構函式可以接受選擇性引數，例如要在資料來源執行的 SQL 陳述式、<xref:System.Data.Common.DbConnection> 物件或 <xref:System.Data.Common.DbTransaction> 物件。</span><span class="sxs-lookup"><span data-stu-id="2afd9-106">Constructors can take optional arguments, such as an SQL statement to execute at the data source, a <xref:System.Data.Common.DbConnection> object, or a <xref:System.Data.Common.DbTransaction> object.</span></span> <span data-ttu-id="2afd9-107">此外，您也可以將這些物件設定為命令的屬性。</span><span class="sxs-lookup"><span data-stu-id="2afd9-107">You can also configure those objects as properties of the command.</span></span> <span data-ttu-id="2afd9-108">您還可以使用 <xref:System.Data.Common.DbConnection.CreateCommand%2A> 物件的 `DbConnection` 方法，針對特定連接建立命令。</span><span class="sxs-lookup"><span data-stu-id="2afd9-108">You can also create a command for a particular connection using the <xref:System.Data.Common.DbConnection.CreateCommand%2A> method of a `DbConnection` object.</span></span> <span data-ttu-id="2afd9-109">您可以使用 <xref:System.Data.Common.DbCommand.CommandText%2A> 屬性來設定正由命令執行的 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="2afd9-109">The SQL statement being executed by the command can be configured using the <xref:System.Data.Common.DbCommand.CommandText%2A> property.</span></span>  
  
 <span data-ttu-id="2afd9-110">內含在 .NET Framework 中的每個 .NET Framework 資料提供者都有一個 `Command` 物件。</span><span class="sxs-lookup"><span data-stu-id="2afd9-110">Each .NET Framework data provider included with the .NET Framework has a `Command` object.</span></span> <span data-ttu-id="2afd9-111">.NET Framework Data Provider for OLE DB 包含 <xref:System.Data.OleDb.OleDbCommand> 物件、.NET Framework Data Provider for SQL Server 包含 <xref:System.Data.SqlClient.SqlCommand> 物件、.NET Framework Data Provider for ODBC 包含 <xref:System.Data.Odbc.OdbcCommand> 物件，而 .NET Framework Data Provider for Oracle 包含 <xref:System.Data.OracleClient.OracleCommand> 物件。</span><span class="sxs-lookup"><span data-stu-id="2afd9-111">The .NET Framework Data Provider for OLE DB includes an <xref:System.Data.OleDb.OleDbCommand> object, the .NET Framework Data Provider for SQL Server includes a <xref:System.Data.SqlClient.SqlCommand> object, the .NET Framework Data Provider for ODBC includes an <xref:System.Data.Odbc.OdbcCommand> object, and the .NET Framework Data Provider for Oracle includes an <xref:System.Data.OracleClient.OracleCommand> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2afd9-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="2afd9-112">In This Section</span></span>  

 [<span data-ttu-id="2afd9-113">執行命令</span><span class="sxs-lookup"><span data-stu-id="2afd9-113">Executing a Command</span></span>](executing-a-command.md)  
 <span data-ttu-id="2afd9-114">說明 ADO.NET `Command` 物件，以及如何用它來針對資料來源執行查詢和命令。</span><span class="sxs-lookup"><span data-stu-id="2afd9-114">Describes the ADO.NET `Command` object and how to use it to execute queries and commands against a data source.</span></span>  
  
 [<span data-ttu-id="2afd9-115">設定參數和參數資料類型</span><span class="sxs-lookup"><span data-stu-id="2afd9-115">Configuring Parameters and Parameter Data Types</span></span>](configuring-parameters-and-parameter-data-types.md)  
 <span data-ttu-id="2afd9-116">說明如何使用 `Command` 參數，包括方向、資料型別和參數語法。</span><span class="sxs-lookup"><span data-stu-id="2afd9-116">Describes working with `Command` parameters, including direction, data types, and parameter syntax.</span></span>  
  
 [<span data-ttu-id="2afd9-117">使用 CommandBuilder 產生命令</span><span class="sxs-lookup"><span data-stu-id="2afd9-117">Generating Commands with CommandBuilders</span></span>](generating-commands-with-commandbuilders.md)  
 <span data-ttu-id="2afd9-118">說明如何使用命令產生器，針對具有單一資料表 SELECT 命令的 `DataAdapter` 自動產生 INSERT、UPDATE 和 DELETE 命令。</span><span class="sxs-lookup"><span data-stu-id="2afd9-118">Describes how to use command builders to automatically generate INSERT, UPDATE, and DELETE commands for a `DataAdapter` that has a single-table SELECT command.</span></span>  
  
 [<span data-ttu-id="2afd9-119">從資料庫取得單一值</span><span class="sxs-lookup"><span data-stu-id="2afd9-119">Obtaining a Single Value from a Database</span></span>](obtaining-a-single-value-from-a-database.md)  
 <span data-ttu-id="2afd9-120">說明如何使用 `ExecuteScalar` 物件的 `Command` 方法，從資料庫查詢傳回單一值。</span><span class="sxs-lookup"><span data-stu-id="2afd9-120">Describes how to use the `ExecuteScalar` method of a `Command` object to return a single value from a database query.</span></span>  
  
 [<span data-ttu-id="2afd9-121">使用命令修改資料</span><span class="sxs-lookup"><span data-stu-id="2afd9-121">Using Commands to Modify Data</span></span>](using-commands-to-modify-data.md)  
 <span data-ttu-id="2afd9-122">說明如何使用資料提供者來執行預存程序 (Stored Procedure) 或資料定義語言 (DDL) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="2afd9-122">Describes how to use a data provider to execute stored procedures or data definition language (DDL) statements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2afd9-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2afd9-123">See also</span></span>

- [<span data-ttu-id="2afd9-124">DataAdapter 和 DataReader</span><span class="sxs-lookup"><span data-stu-id="2afd9-124">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="2afd9-125">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="2afd9-125">DataSets, DataTables, and DataViews</span></span>](./dataset-datatable-dataview/index.md)
- [<span data-ttu-id="2afd9-126">連接到資料來源</span><span class="sxs-lookup"><span data-stu-id="2afd9-126">Connecting to a Data Source</span></span>](connecting-to-a-data-source.md)
- <span data-ttu-id="2afd9-127">[ADO.NET 概觀](ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="2afd9-127">[ADO.NET Overview](ado-net-overview.md)</span></span>
