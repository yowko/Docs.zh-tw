---
title: 執行命令
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 40494916-c25a-4cb8-8f7c-fcb8d378464e
ms.openlocfilehash: ed5ae1cbab40b57676219ffbe7d1d5696ac3bec4
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45698115"
---
# <a name="executing-a-command"></a><span data-ttu-id="714fd-102">執行命令</span><span class="sxs-lookup"><span data-stu-id="714fd-102">Executing a Command</span></span>
<span data-ttu-id="714fd-103">內含在 .NET Framework 中的每個 .NET Framework 資料提供者本身都有命令物件，此物件是繼承自 <xref:System.Data.Common.DbCommand>。</span><span class="sxs-lookup"><span data-stu-id="714fd-103">Each .NET Framework data provider included with the .NET Framework has its own command object that inherits from <xref:System.Data.Common.DbCommand>.</span></span> <span data-ttu-id="714fd-104">.NET Framework Data Provider for OLE DB 包含 <xref:System.Data.OleDb.OleDbCommand> 物件、.NET Framework Data Provider for SQL Server 包含 <xref:System.Data.SqlClient.SqlCommand> 物件、.NET Framework Data Provider for ODBC 包含 <xref:System.Data.Odbc.OdbcCommand> 物件，而 .NET Framework Data Provider for Oracle 包含 <xref:System.Data.OracleClient.OracleCommand> 物件。</span><span class="sxs-lookup"><span data-stu-id="714fd-104">The .NET Framework Data Provider for OLE DB includes an <xref:System.Data.OleDb.OleDbCommand> object, the .NET Framework Data Provider for SQL Server includes a <xref:System.Data.SqlClient.SqlCommand> object, the .NET Framework Data Provider for ODBC includes an <xref:System.Data.Odbc.OdbcCommand> object, and the .NET Framework Data Provider for Oracle includes an <xref:System.Data.OracleClient.OracleCommand> object.</span></span> <span data-ttu-id="714fd-105">上述每種物件都會根據命令類型和想要的傳回值而公開 (Expose) 執行命令的方法，如下表所述。</span><span class="sxs-lookup"><span data-stu-id="714fd-105">Each of these objects exposes methods for executing commands based on the type of command and desired return value, as described in the following table.</span></span>  
  
|<span data-ttu-id="714fd-106">命令</span><span class="sxs-lookup"><span data-stu-id="714fd-106">Command</span></span>|<span data-ttu-id="714fd-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="714fd-107">Return Value</span></span>|  
|-------------|------------------|  
|`ExecuteReader`|<span data-ttu-id="714fd-108">傳回 `DataReader` 物件。</span><span class="sxs-lookup"><span data-stu-id="714fd-108">Returns a `DataReader` object.</span></span>|  
|`ExecuteScalar`|<span data-ttu-id="714fd-109">傳回單一純量值。</span><span class="sxs-lookup"><span data-stu-id="714fd-109">Returns a single scalar value.</span></span>|  
|`ExecuteNonQuery`|<span data-ttu-id="714fd-110">執行不會傳回任何資料列的命令。</span><span class="sxs-lookup"><span data-stu-id="714fd-110">Executes a command that does not return any rows.</span></span>|  
|`ExecuteXMLReader`|<span data-ttu-id="714fd-111">傳回 <xref:System.Xml.XmlReader>。</span><span class="sxs-lookup"><span data-stu-id="714fd-111">Returns an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="714fd-112">僅適用於 `SqlCommand` 物件。</span><span class="sxs-lookup"><span data-stu-id="714fd-112">Available for a `SqlCommand` object only.</span></span>|  
  
 <span data-ttu-id="714fd-113">每個強型別 (Strongly Typed) 的命令物件也會支援 <xref:System.Data.CommandType> 列舉型別 (Enumeration)，此型別可指定解譯命令字串的方式。</span><span class="sxs-lookup"><span data-stu-id="714fd-113">Each strongly typed command object also supports a <xref:System.Data.CommandType> enumeration that specifies how a command string is interpreted, as described in the following table.</span></span>  
  
|<span data-ttu-id="714fd-114">CommandType</span><span class="sxs-lookup"><span data-stu-id="714fd-114">CommandType</span></span>|<span data-ttu-id="714fd-115">描述</span><span class="sxs-lookup"><span data-stu-id="714fd-115">Description</span></span>|  
|-----------------|-----------------|  
|`Text`|<span data-ttu-id="714fd-116">SQL 命令，可定義在資料來源執行的陳述式。</span><span class="sxs-lookup"><span data-stu-id="714fd-116">An SQL command defining the statements to be executed at the data source.</span></span>|  
|`StoredProcedure`|<span data-ttu-id="714fd-117">預存程序 (Stored Procedure) 的名稱。</span><span class="sxs-lookup"><span data-stu-id="714fd-117">The name of the stored procedure.</span></span> <span data-ttu-id="714fd-118">您可以使用命令的 `Parameters` 屬性來存取輸入和輸出參數及傳回值，不論呼叫的是哪一個 `Execute` 方法。</span><span class="sxs-lookup"><span data-stu-id="714fd-118">You can use the `Parameters` property of a command to access input and output parameters and return values, regardless of which `Execute` method is called.</span></span> <span data-ttu-id="714fd-119">在使用 `ExecuteReader` 時，無法在 `DataReader` 關閉之前存取傳回值和輸出參數。</span><span class="sxs-lookup"><span data-stu-id="714fd-119">When using `ExecuteReader`, return values and output parameters will not be accessible until the `DataReader` is closed.</span></span>|  
|`TableDirect`|<span data-ttu-id="714fd-120">資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="714fd-120">The name of a table.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="714fd-121">範例</span><span class="sxs-lookup"><span data-stu-id="714fd-121">Example</span></span>  
 <span data-ttu-id="714fd-122">下列程式碼範例示範如何建立 <xref:System.Data.SqlClient.SqlCommand> 物件，以藉由設定其屬性來執行預存程序。</span><span class="sxs-lookup"><span data-stu-id="714fd-122">The following code example demonstrates how to create a <xref:System.Data.SqlClient.SqlCommand> object to execute a stored procedure by setting its properties.</span></span> <span data-ttu-id="714fd-123">用來指定預存程序輸出參數的 <xref:System.Data.SqlClient.SqlParameter> 物件。</span><span class="sxs-lookup"><span data-stu-id="714fd-123">A <xref:System.Data.SqlClient.SqlParameter> object is used to specify the input parameter to the stored procedure.</span></span> <span data-ttu-id="714fd-124">此命令是藉由使用 <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> 方法來執行，而 <xref:System.Data.SqlClient.SqlDataReader> 的輸出則會顯示在主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="714fd-124">The command is executed using the <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> method, and the output from the <xref:System.Data.SqlClient.SqlDataReader> is displayed in the console window.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/VB/source.vb#1)]  
  
### <a name="troubleshooting-commands"></a><span data-ttu-id="714fd-125">疑難排解命令</span><span class="sxs-lookup"><span data-stu-id="714fd-125">Troubleshooting Commands</span></span>  
 <span data-ttu-id="714fd-126">.NET Framework Data Provider for SQL Server 加入一個效能計數器，可讓您偵測與失敗命令執行相關的週期性問題。</span><span class="sxs-lookup"><span data-stu-id="714fd-126">The .NET Framework Data Provider for SQL Server adds performance counters to enable you to detect intermittent problems related to failed command executions.</span></span> <span data-ttu-id="714fd-127">如需詳細資訊，請參閱[效能計數器](../../../../docs/framework/data/adonet/performance-counters.md)。</span><span class="sxs-lookup"><span data-stu-id="714fd-127">For more information see [Performance Counters](../../../../docs/framework/data/adonet/performance-counters.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="714fd-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="714fd-128">See Also</span></span>  
 [<span data-ttu-id="714fd-129">命令和參數</span><span class="sxs-lookup"><span data-stu-id="714fd-129">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="714fd-130">DataAdapter 和 DataReader</span><span class="sxs-lookup"><span data-stu-id="714fd-130">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="714fd-131">使用 Datareader</span><span class="sxs-lookup"><span data-stu-id="714fd-131">Working with DataReaders</span></span>](https://msdn.microsoft.com/library/126a966a-d08d-4d22-a19f-f432908b2b54)  
 [<span data-ttu-id="714fd-132">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="714fd-132">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
