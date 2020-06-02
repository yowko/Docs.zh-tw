---
title: 連接到資料來源
deescription: Learn about Connection objects, used to connect to data sources in ADO.NET. The Connection object you choose depends on the type of data source.
ms.date: 03/30/2017
ms.assetid: 9abc3f92-1be3-4e1a-b360-762dc689650e
ms.openlocfilehash: a14fe179cf2fc8714a54e52252c53bd71346cad3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287073"
---
# <a name="connecting-to-a-data-source-in-adonet"></a><span data-ttu-id="9246c-102">在 ADO.NET 中連接至資料來源</span><span class="sxs-lookup"><span data-stu-id="9246c-102">Connecting to a Data Source in ADO.NET</span></span>

<span data-ttu-id="9246c-103">在 ADO.NET 中，您可以使用**連接**物件來連接到特定的資料來源，方法是在連接字串中提供必要的驗證資訊。</span><span class="sxs-lookup"><span data-stu-id="9246c-103">In ADO.NET, you use a **Connection** object to connect to a specific data source by supplying necessary authentication information in a connection string.</span></span> <span data-ttu-id="9246c-104">您所使用的**連接**物件取決於資料來源的類型。</span><span class="sxs-lookup"><span data-stu-id="9246c-104">The **Connection** object you use depends on the type of data source.</span></span>  
  
 <span data-ttu-id="9246c-105">內含在 .NET Framework 中的每個 .NET Framework 資料提供者都有 <xref:System.Data.Common.DbConnection> 物件：.NET Framework Data Provider for OLE DB 包含 <xref:System.Data.OleDb.OleDbConnection> 物件、.NET Framework Data Provider for SQL Server 包含 <xref:System.Data.SqlClient.SqlConnection> 物件、.NET Framework Data Provider for ODBC 包含 <xref:System.Data.Odbc.OdbcConnection> 物件，而且 .NET Framework Data Provider for Oracle 包含 <xref:System.Data.OracleClient.OracleConnection> 物件。</span><span class="sxs-lookup"><span data-stu-id="9246c-105">Each .NET Framework data provider included with the .NET Framework has a <xref:System.Data.Common.DbConnection> object: the .NET Framework Data Provider for OLE DB includes an <xref:System.Data.OleDb.OleDbConnection> object, the .NET Framework Data Provider for SQL Server includes a <xref:System.Data.SqlClient.SqlConnection> object, the .NET Framework Data Provider for ODBC includes an <xref:System.Data.Odbc.OdbcConnection> object, and the .NET Framework Data Provider for Oracle includes an <xref:System.Data.OracleClient.OracleConnection> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9246c-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="9246c-106">In This Section</span></span>  
 <span data-ttu-id="9246c-107">[建立連接](establishing-the-connection.md)</span><span class="sxs-lookup"><span data-stu-id="9246c-107">[Establishing the Connection](establishing-the-connection.md)</span></span>\
 <span data-ttu-id="9246c-108">描述如何使用**連接**物件來建立資料來源的連接。</span><span class="sxs-lookup"><span data-stu-id="9246c-108">Describes how to use a **Connection** object to establish a connection to a data source.</span></span>  
  
 <span data-ttu-id="9246c-109">[連接事件](connection-events.md)</span><span class="sxs-lookup"><span data-stu-id="9246c-109">[Connection Events](connection-events.md)</span></span>\
 <span data-ttu-id="9246c-110">描述如何使用**InfoMessage**事件從資料來源取出參考用訊息。</span><span class="sxs-lookup"><span data-stu-id="9246c-110">Describes how to use an **InfoMessage** event to retrieve informational messages from a data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9246c-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9246c-111">See also</span></span>

- [<span data-ttu-id="9246c-112">連接字串</span><span class="sxs-lookup"><span data-stu-id="9246c-112">Connection Strings</span></span>](connection-strings.md)
- [<span data-ttu-id="9246c-113">連接共用</span><span class="sxs-lookup"><span data-stu-id="9246c-113">Connection Pooling</span></span>](connection-pooling.md)
- [<span data-ttu-id="9246c-114">命令和參數</span><span class="sxs-lookup"><span data-stu-id="9246c-114">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="9246c-115">DataAdapter 和 DataReader</span><span class="sxs-lookup"><span data-stu-id="9246c-115">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="9246c-116">異動和並行存取</span><span class="sxs-lookup"><span data-stu-id="9246c-116">Transactions and Concurrency</span></span>](transactions-and-concurrency.md)
- <span data-ttu-id="9246c-117">[ADO.NET 概觀](ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="9246c-117">[ADO.NET Overview](ado-net-overview.md)</span></span>
