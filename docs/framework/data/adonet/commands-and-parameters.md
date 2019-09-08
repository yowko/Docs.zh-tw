---
title: 命令和參數
ms.date: 03/30/2017
ms.assetid: b623f810-d871-49a5-b0f5-078cc3c34db6
ms.openlocfilehash: 1d0c3adb56e5ff44b5c5e065ac040f25584a1946
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784962"
---
# <a name="commands-and-parameters"></a><span data-ttu-id="a1121-102">命令和參數</span><span class="sxs-lookup"><span data-stu-id="a1121-102">Commands and Parameters</span></span>
<span data-ttu-id="a1121-103">建立連至資料來源的連接後，您可以執行命令，並使用 <xref:System.Data.Common.DbCommand> 物件從資料來源傳回結果。</span><span class="sxs-lookup"><span data-stu-id="a1121-103">After establishing a connection to a data source, you can execute commands and return results from the data source using a <xref:System.Data.Common.DbCommand> object.</span></span> <span data-ttu-id="a1121-104">您可以使用目前使用中 .NET Framework 資料提供者的其中一個命令建構函式 (Constructor) 來建立命令。</span><span class="sxs-lookup"><span data-stu-id="a1121-104">You can create a command using one of the command constructors for the .NET Framework data provider you are working with.</span></span> <span data-ttu-id="a1121-105">建構函式可以接受選擇性引數，例如要在資料來源執行的 SQL 陳述式、<xref:System.Data.Common.DbConnection> 物件或 <xref:System.Data.Common.DbTransaction> 物件。</span><span class="sxs-lookup"><span data-stu-id="a1121-105">Constructors can take optional arguments, such as an SQL statement to execute at the data source, a <xref:System.Data.Common.DbConnection> object, or a <xref:System.Data.Common.DbTransaction> object.</span></span> <span data-ttu-id="a1121-106">此外，您也可以將這些物件設定為命令的屬性。</span><span class="sxs-lookup"><span data-stu-id="a1121-106">You can also configure those objects as properties of the command.</span></span> <span data-ttu-id="a1121-107">您還可以使用 <xref:System.Data.Common.DbConnection.CreateCommand%2A> 物件的 `DbConnection` 方法，針對特定連接建立命令。</span><span class="sxs-lookup"><span data-stu-id="a1121-107">You can also create a command for a particular connection using the <xref:System.Data.Common.DbConnection.CreateCommand%2A> method of a `DbConnection` object.</span></span> <span data-ttu-id="a1121-108">您可以使用 <xref:System.Data.Common.DbCommand.CommandText%2A> 屬性來設定正由命令執行的 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="a1121-108">The SQL statement being executed by the command can be configured using the <xref:System.Data.Common.DbCommand.CommandText%2A> property.</span></span>  
  
 <span data-ttu-id="a1121-109">內含在 .NET Framework 中的每個 .NET Framework 資料提供者都有一個 `Command` 物件。</span><span class="sxs-lookup"><span data-stu-id="a1121-109">Each .NET Framework data provider included with the .NET Framework has a `Command` object.</span></span> <span data-ttu-id="a1121-110">.NET Framework Data Provider for OLE DB 包含 <xref:System.Data.OleDb.OleDbCommand> 物件、.NET Framework Data Provider for SQL Server 包含 <xref:System.Data.SqlClient.SqlCommand> 物件、.NET Framework Data Provider for ODBC 包含 <xref:System.Data.Odbc.OdbcCommand> 物件，而 .NET Framework Data Provider for Oracle 包含 <xref:System.Data.OracleClient.OracleCommand> 物件。</span><span class="sxs-lookup"><span data-stu-id="a1121-110">The .NET Framework Data Provider for OLE DB includes an <xref:System.Data.OleDb.OleDbCommand> object, the .NET Framework Data Provider for SQL Server includes a <xref:System.Data.SqlClient.SqlCommand> object, the .NET Framework Data Provider for ODBC includes an <xref:System.Data.Odbc.OdbcCommand> object, and the .NET Framework Data Provider for Oracle includes an <xref:System.Data.OracleClient.OracleCommand> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a1121-111">本節內容</span><span class="sxs-lookup"><span data-stu-id="a1121-111">In This Section</span></span>  
 [<span data-ttu-id="a1121-112">執行命令</span><span class="sxs-lookup"><span data-stu-id="a1121-112">Executing a Command</span></span>](executing-a-command.md)  
 <span data-ttu-id="a1121-113">說明 ADO.NET `Command` 物件，以及如何用它來針對資料來源執行查詢和命令。</span><span class="sxs-lookup"><span data-stu-id="a1121-113">Describes the ADO.NET `Command` object and how to use it to execute queries and commands against a data source.</span></span>  
  
 [<span data-ttu-id="a1121-114">設定參數和參數資料類型</span><span class="sxs-lookup"><span data-stu-id="a1121-114">Configuring Parameters and Parameter Data Types</span></span>](configuring-parameters-and-parameter-data-types.md)  
 <span data-ttu-id="a1121-115">說明如何使用 `Command` 參數，包括方向、資料型別和參數語法。</span><span class="sxs-lookup"><span data-stu-id="a1121-115">Describes working with `Command` parameters, including direction, data types, and parameter syntax.</span></span>  
  
 [<span data-ttu-id="a1121-116">使用 CommandBuilder 產生命令</span><span class="sxs-lookup"><span data-stu-id="a1121-116">Generating Commands with CommandBuilders</span></span>](generating-commands-with-commandbuilders.md)  
 <span data-ttu-id="a1121-117">說明如何使用命令產生器，針對具有單一資料表 SELECT 命令的 `DataAdapter` 自動產生 INSERT、UPDATE 和 DELETE 命令。</span><span class="sxs-lookup"><span data-stu-id="a1121-117">Describes how to use command builders to automatically generate INSERT, UPDATE, and DELETE commands for a `DataAdapter` that has a single-table SELECT command.</span></span>  
  
 [<span data-ttu-id="a1121-118">從資料庫取得單一值</span><span class="sxs-lookup"><span data-stu-id="a1121-118">Obtaining a Single Value from a Database</span></span>](obtaining-a-single-value-from-a-database.md)  
 <span data-ttu-id="a1121-119">說明如何使用 `ExecuteScalar` 物件的 `Command` 方法，從資料庫查詢傳回單一值。</span><span class="sxs-lookup"><span data-stu-id="a1121-119">Describes how to use the `ExecuteScalar` method of a `Command` object to return a single value from a database query.</span></span>  
  
 [<span data-ttu-id="a1121-120">使用命令修改資料</span><span class="sxs-lookup"><span data-stu-id="a1121-120">Using Commands to Modify Data</span></span>](using-commands-to-modify-data.md)  
 <span data-ttu-id="a1121-121">說明如何使用資料提供者來執行預存程序 (Stored Procedure) 或資料定義語言 (DDL) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="a1121-121">Describes how to use a data provider to execute stored procedures or data definition language (DDL) statements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1121-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a1121-122">See also</span></span>

- [<span data-ttu-id="a1121-123">DataAdapter 和 DataReader</span><span class="sxs-lookup"><span data-stu-id="a1121-123">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="a1121-124">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="a1121-124">DataSets, DataTables, and DataViews</span></span>](./dataset-datatable-dataview/index.md)
- [<span data-ttu-id="a1121-125">連接至資料來源</span><span class="sxs-lookup"><span data-stu-id="a1121-125">Connecting to a Data Source</span></span>](connecting-to-a-data-source.md)
- [<span data-ttu-id="a1121-126">ADO.NET 概觀</span><span class="sxs-lookup"><span data-stu-id="a1121-126">ADO.NET Overview</span></span>](ado-net-overview.md)
