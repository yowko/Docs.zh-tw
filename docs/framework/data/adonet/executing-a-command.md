---
title: 執行命令
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 40494916-c25a-4cb8-8f7c-fcb8d378464e
ms.openlocfilehash: f749ea37e1655f006e4de26e7cb279b778fe4faf
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795116"
---
# <a name="executing-a-command"></a><span data-ttu-id="7316a-102">執行命令</span><span class="sxs-lookup"><span data-stu-id="7316a-102">Executing a Command</span></span>
<span data-ttu-id="7316a-103">內含在 .NET Framework 中的每個 .NET Framework 資料提供者本身都有命令物件，此物件是繼承自 <xref:System.Data.Common.DbCommand>。</span><span class="sxs-lookup"><span data-stu-id="7316a-103">Each .NET Framework data provider included with the .NET Framework has its own command object that inherits from <xref:System.Data.Common.DbCommand>.</span></span> <span data-ttu-id="7316a-104">.NET Framework Data Provider for OLE DB 包含 <xref:System.Data.OleDb.OleDbCommand> 物件、.NET Framework Data Provider for SQL Server 包含 <xref:System.Data.SqlClient.SqlCommand> 物件、.NET Framework Data Provider for ODBC 包含 <xref:System.Data.Odbc.OdbcCommand> 物件，而 .NET Framework Data Provider for Oracle 包含 <xref:System.Data.OracleClient.OracleCommand> 物件。</span><span class="sxs-lookup"><span data-stu-id="7316a-104">The .NET Framework Data Provider for OLE DB includes an <xref:System.Data.OleDb.OleDbCommand> object, the .NET Framework Data Provider for SQL Server includes a <xref:System.Data.SqlClient.SqlCommand> object, the .NET Framework Data Provider for ODBC includes an <xref:System.Data.Odbc.OdbcCommand> object, and the .NET Framework Data Provider for Oracle includes an <xref:System.Data.OracleClient.OracleCommand> object.</span></span> <span data-ttu-id="7316a-105">上述每種物件都會根據命令類型和想要的傳回值而公開 (Expose) 執行命令的方法，如下表所述。</span><span class="sxs-lookup"><span data-stu-id="7316a-105">Each of these objects exposes methods for executing commands based on the type of command and desired return value, as described in the following table.</span></span>  
  
|<span data-ttu-id="7316a-106">命令</span><span class="sxs-lookup"><span data-stu-id="7316a-106">Command</span></span>|<span data-ttu-id="7316a-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="7316a-107">Return Value</span></span>|  
|-------------|------------------|  
|`ExecuteReader`|<span data-ttu-id="7316a-108">傳回 `DataReader` 物件。</span><span class="sxs-lookup"><span data-stu-id="7316a-108">Returns a `DataReader` object.</span></span>|  
|`ExecuteScalar`|<span data-ttu-id="7316a-109">傳回單一純量值。</span><span class="sxs-lookup"><span data-stu-id="7316a-109">Returns a single scalar value.</span></span>|  
|`ExecuteNonQuery`|<span data-ttu-id="7316a-110">執行不會傳回任何資料列的命令。</span><span class="sxs-lookup"><span data-stu-id="7316a-110">Executes a command that does not return any rows.</span></span>|  
|`ExecuteXMLReader`|<span data-ttu-id="7316a-111">傳回 <xref:System.Xml.XmlReader>。</span><span class="sxs-lookup"><span data-stu-id="7316a-111">Returns an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="7316a-112">僅適用於 `SqlCommand` 物件。</span><span class="sxs-lookup"><span data-stu-id="7316a-112">Available for a `SqlCommand` object only.</span></span>|  
  
 <span data-ttu-id="7316a-113">每個強型別 (Strongly Typed) 的命令物件也會支援 <xref:System.Data.CommandType> 列舉型別 (Enumeration)，此型別可指定解譯命令字串的方式。</span><span class="sxs-lookup"><span data-stu-id="7316a-113">Each strongly typed command object also supports a <xref:System.Data.CommandType> enumeration that specifies how a command string is interpreted, as described in the following table.</span></span>  
  
|<span data-ttu-id="7316a-114">CommandType</span><span class="sxs-lookup"><span data-stu-id="7316a-114">CommandType</span></span>|<span data-ttu-id="7316a-115">描述</span><span class="sxs-lookup"><span data-stu-id="7316a-115">Description</span></span>|  
|-----------------|-----------------|  
|`Text`|<span data-ttu-id="7316a-116">SQL 命令，可定義在資料來源執行的陳述式。</span><span class="sxs-lookup"><span data-stu-id="7316a-116">An SQL command defining the statements to be executed at the data source.</span></span>|  
|`StoredProcedure`|<span data-ttu-id="7316a-117">預存程序 (Stored Procedure) 的名稱。</span><span class="sxs-lookup"><span data-stu-id="7316a-117">The name of the stored procedure.</span></span> <span data-ttu-id="7316a-118">您可以使用命令的 `Parameters` 屬性來存取輸入和輸出參數及傳回值，不論呼叫的是哪一個 `Execute` 方法。</span><span class="sxs-lookup"><span data-stu-id="7316a-118">You can use the `Parameters` property of a command to access input and output parameters and return values, regardless of which `Execute` method is called.</span></span> <span data-ttu-id="7316a-119">在使用 `ExecuteReader` 時，無法在 `DataReader` 關閉之前存取傳回值和輸出參數。</span><span class="sxs-lookup"><span data-stu-id="7316a-119">When using `ExecuteReader`, return values and output parameters will not be accessible until the `DataReader` is closed.</span></span>|  
|`TableDirect`|<span data-ttu-id="7316a-120">資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="7316a-120">The name of a table.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7316a-121">範例</span><span class="sxs-lookup"><span data-stu-id="7316a-121">Example</span></span>  
 <span data-ttu-id="7316a-122">下列程式碼範例示範如何建立 <xref:System.Data.SqlClient.SqlCommand> 物件，以藉由設定其屬性來執行預存程序。</span><span class="sxs-lookup"><span data-stu-id="7316a-122">The following code example demonstrates how to create a <xref:System.Data.SqlClient.SqlCommand> object to execute a stored procedure by setting its properties.</span></span> <span data-ttu-id="7316a-123">用來指定預存程序輸出參數的 <xref:System.Data.SqlClient.SqlParameter> 物件。</span><span class="sxs-lookup"><span data-stu-id="7316a-123">A <xref:System.Data.SqlClient.SqlParameter> object is used to specify the input parameter to the stored procedure.</span></span> <span data-ttu-id="7316a-124">此命令是藉由使用 <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> 方法來執行，而 <xref:System.Data.SqlClient.SqlDataReader> 的輸出則會顯示在主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="7316a-124">The command is executed using the <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> method, and the output from the <xref:System.Data.SqlClient.SqlDataReader> is displayed in the console window.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/VB/source.vb#1)]  
  
### <a name="troubleshooting-commands"></a><span data-ttu-id="7316a-125">疑難排解命令</span><span class="sxs-lookup"><span data-stu-id="7316a-125">Troubleshooting Commands</span></span>  
 <span data-ttu-id="7316a-126">.NET Framework Data Provider for SQL Server 加入一個效能計數器，可讓您偵測與失敗命令執行相關的週期性問題。</span><span class="sxs-lookup"><span data-stu-id="7316a-126">The .NET Framework Data Provider for SQL Server adds performance counters to enable you to detect intermittent problems related to failed command executions.</span></span> <span data-ttu-id="7316a-127">如需詳細資訊，請參閱[效能計數器](performance-counters.md)。</span><span class="sxs-lookup"><span data-stu-id="7316a-127">For more information see [Performance Counters](performance-counters.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7316a-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7316a-128">See also</span></span>

- [<span data-ttu-id="7316a-129">命令和參數</span><span class="sxs-lookup"><span data-stu-id="7316a-129">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="7316a-130">DataAdapter 和 DataReader</span><span class="sxs-lookup"><span data-stu-id="7316a-130">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="7316a-131">ADO.NET 概觀</span><span class="sxs-lookup"><span data-stu-id="7316a-131">ADO.NET Overview</span></span>](ado-net-overview.md)
