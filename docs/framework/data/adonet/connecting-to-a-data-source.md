---
title: 在 ADO.NET 中連接至資料來源
ms.date: 03/30/2017
ms.assetid: 9abc3f92-1be3-4e1a-b360-762dc689650e
ms.openlocfilehash: c04624be758e4bc7c8b1981ad6a9dc44430d62b5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59083708"
---
# <a name="connecting-to-a-data-source-in-adonet"></a><span data-ttu-id="1012f-102">在 ADO.NET 中連接至資料來源</span><span class="sxs-lookup"><span data-stu-id="1012f-102">Connecting to a Data Source in ADO.NET</span></span>
<span data-ttu-id="1012f-103">在 ADO.NET 中使用**連線**物件來連接到特定的資料來源提供連接字串中的所需的驗證資訊。</span><span class="sxs-lookup"><span data-stu-id="1012f-103">In ADO.NET you use a **Connection** object to connect to a specific data source by supplying necessary authentication information in a connection string.</span></span> <span data-ttu-id="1012f-104">**連線**您所使用的物件取決於資料來源的類型。</span><span class="sxs-lookup"><span data-stu-id="1012f-104">The **Connection** object you use depends on the type of data source.</span></span>  
  
 <span data-ttu-id="1012f-105">內含在 .NET Framework 中的每個 .NET Framework 資料提供者都有 <xref:System.Data.Common.DbConnection> 物件：.NET Framework Data Provider for OLE DB 包含 <xref:System.Data.OleDb.OleDbConnection> 物件、.NET Framework Data Provider for SQL Server 包含 <xref:System.Data.SqlClient.SqlConnection> 物件、.NET Framework Data Provider for ODBC 包含 <xref:System.Data.Odbc.OdbcConnection> 物件，而且 .NET Framework Data Provider for Oracle 包含 <xref:System.Data.OracleClient.OracleConnection> 物件。</span><span class="sxs-lookup"><span data-stu-id="1012f-105">Each .NET Framework data provider included with the .NET Framework has a <xref:System.Data.Common.DbConnection> object: the .NET Framework Data Provider for OLE DB includes an <xref:System.Data.OleDb.OleDbConnection> object, the .NET Framework Data Provider for SQL Server includes a <xref:System.Data.SqlClient.SqlConnection> object, the .NET Framework Data Provider for ODBC includes an <xref:System.Data.Odbc.OdbcConnection> object, and the .NET Framework Data Provider for Oracle includes an <xref:System.Data.OracleClient.OracleConnection> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1012f-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="1012f-106">In This Section</span></span>  
 [<span data-ttu-id="1012f-107">建立連接</span><span class="sxs-lookup"><span data-stu-id="1012f-107">Establishing the Connection</span></span>](../../../../docs/framework/data/adonet/establishing-the-connection.md)  
 <span data-ttu-id="1012f-108">描述如何使用**連線**物件來建立資料來源的連接。</span><span class="sxs-lookup"><span data-stu-id="1012f-108">Describes how to use a **Connection** object to establish a connection to a data source.</span></span>  
  
 [<span data-ttu-id="1012f-109">Connection 的事件</span><span class="sxs-lookup"><span data-stu-id="1012f-109">Connection Events</span></span>](../../../../docs/framework/data/adonet/connection-events.md)  
 <span data-ttu-id="1012f-110">描述如何使用**InfoMessage**事件，以擷取從資料來源的參考用訊息。</span><span class="sxs-lookup"><span data-stu-id="1012f-110">Describes how to use an **InfoMessage** event to retrieve informational messages from a data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1012f-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1012f-111">See also</span></span>

- [<span data-ttu-id="1012f-112">連接字串</span><span class="sxs-lookup"><span data-stu-id="1012f-112">Connection Strings</span></span>](../../../../docs/framework/data/adonet/connection-strings.md)
- [<span data-ttu-id="1012f-113">連接共用</span><span class="sxs-lookup"><span data-stu-id="1012f-113">Connection Pooling</span></span>](../../../../docs/framework/data/adonet/connection-pooling.md)
- [<span data-ttu-id="1012f-114">命令和參數</span><span class="sxs-lookup"><span data-stu-id="1012f-114">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [<span data-ttu-id="1012f-115">DataAdapter 和 DataReader</span><span class="sxs-lookup"><span data-stu-id="1012f-115">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [<span data-ttu-id="1012f-116">異動和並行存取</span><span class="sxs-lookup"><span data-stu-id="1012f-116">Transactions and Concurrency</span></span>](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)
- [<span data-ttu-id="1012f-117">ADO.NET Managed 提供者和DataSet開發人員中心</span><span class="sxs-lookup"><span data-stu-id="1012f-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
