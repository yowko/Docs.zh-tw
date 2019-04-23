---
title: DbConnection、DbCommand 和 DbException
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 58aab611-7e6f-4749-b983-28ab7ae87dbe
ms.openlocfilehash: 759b2f36f9d38cdac0cfe4ff8e451b38012493e1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59143828"
---
# <a name="dbconnection-dbcommand-and-dbexception"></a><span data-ttu-id="0996e-102">DbConnection、DbCommand 和 DbException</span><span class="sxs-lookup"><span data-stu-id="0996e-102">DbConnection, DbCommand and DbException</span></span>
<span data-ttu-id="0996e-103">在建立 <xref:System.Data.Common.DbProviderFactory> 和 <xref:System.Data.Common.DbConnection> 之後，接著就可以使用命令和資料讀取器從資料來源擷取資料。</span><span class="sxs-lookup"><span data-stu-id="0996e-103">Once you have created a <xref:System.Data.Common.DbProviderFactory> and a <xref:System.Data.Common.DbConnection>, you can then work with commands and data readers to retrieve data from the data source.</span></span>  
  
## <a name="retrieving-data-example"></a><span data-ttu-id="0996e-104">擷取資料範例</span><span class="sxs-lookup"><span data-stu-id="0996e-104">Retrieving Data Example</span></span>  
 <span data-ttu-id="0996e-105">這個範例會使用 `DbConnection` 物件做為引數。</span><span class="sxs-lookup"><span data-stu-id="0996e-105">This example takes a `DbConnection` object as an argument.</span></span> <span data-ttu-id="0996e-106">然後會建立 <xref:System.Data.Common.DbCommand>，並藉由設定 SQL SELECT 陳述式的 <xref:System.Data.Common.DbCommand.CommandText%2A>，從 Categories 資料表選擇資料。</span><span class="sxs-lookup"><span data-stu-id="0996e-106">A <xref:System.Data.Common.DbCommand> is created to select data from the Categories table by setting the <xref:System.Data.Common.DbCommand.CommandText%2A> to a SQL SELECT statement.</span></span> <span data-ttu-id="0996e-107">程式碼假設 Categories 資料表位於資料來源。</span><span class="sxs-lookup"><span data-stu-id="0996e-107">The code assumes that the Categories table exists at the data source.</span></span> <span data-ttu-id="0996e-108">接著會開啟連接，並使用 <xref:System.Data.Common.DbDataReader> 擷取資料。</span><span class="sxs-lookup"><span data-stu-id="0996e-108">The connection is opened and the data is retrieved using a <xref:System.Data.Common.DbDataReader>.</span></span>  
  
 [!code-csharp[DataWorks DbProviderFactories.DbCommandData#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommandData/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbCommandData#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommandData/VB/source.vb#1)]  
  
## <a name="executing-a-command-example"></a><span data-ttu-id="0996e-109">執行命令範例</span><span class="sxs-lookup"><span data-stu-id="0996e-109">Executing a Command Example</span></span>  
 <span data-ttu-id="0996e-110">這個範例會使用 `DbConnection` 物件做為引數。</span><span class="sxs-lookup"><span data-stu-id="0996e-110">This example takes a `DbConnection` object as an argument.</span></span> <span data-ttu-id="0996e-111">如果 `DbConnection` 有效，則連接會開啟，接著再建立及執行 <xref:System.Data.Common.DbCommand>。</span><span class="sxs-lookup"><span data-stu-id="0996e-111">If the `DbConnection` is valid, the connection is opened and a <xref:System.Data.Common.DbCommand> is created and executed.</span></span> <span data-ttu-id="0996e-112"><xref:System.Data.Common.DbCommand.CommandText%2A> 會設定為 SQL INSERT 陳述式，以對 Northwind 資料庫的 Categories 資料表執行插入作業。</span><span class="sxs-lookup"><span data-stu-id="0996e-112">The <xref:System.Data.Common.DbCommand.CommandText%2A> is set to a SQL INSERT statement that performs an insert to the Categories table in the Northwind database.</span></span> <span data-ttu-id="0996e-113">程式碼會假設 Northwind 資料庫位於資料來源，而用於 INSERT 陳述式的 SQL 語法則對指定的提供者有效。</span><span class="sxs-lookup"><span data-stu-id="0996e-113">The code assumes that the Northwind database exists at the data source, and that the SQL syntax used in the INSERT statement is valid for the specified provider.</span></span> <span data-ttu-id="0996e-114">發生在資料來源的錯誤會由 <xref:System.Data.Common.DbException> 程式碼區塊處理，所有其他的例外則是在 <xref:System.Exception> 區塊中處理。</span><span class="sxs-lookup"><span data-stu-id="0996e-114">Errors occurring at the data source are handled by the <xref:System.Data.Common.DbException> code block, and all other exceptions are handled in the <xref:System.Exception> block.</span></span>  
  
 [!code-csharp[DataWorks DbProviderFactories.DbCommand#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommand/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbCommand#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommand/VB/source.vb#1)]  
  
## <a name="handling-data-errors-with-dbexception"></a><span data-ttu-id="0996e-115">使用 DbException 處理資料錯誤</span><span class="sxs-lookup"><span data-stu-id="0996e-115">Handling Data Errors with DbException</span></span>  
 <span data-ttu-id="0996e-116"><xref:System.Data.Common.DbException> 類別是代表資料來源所擲回之所有例外狀況的基底類別 (Base Class)。</span><span class="sxs-lookup"><span data-stu-id="0996e-116">The <xref:System.Data.Common.DbException> class is the base class for all exceptions thrown on behalf of a data source.</span></span> <span data-ttu-id="0996e-117">您可以將此類別運用於例外狀況處理程式碼中，如此可以處理由不同提供者所擲回的例外狀況，但不必參照特定的例外狀況類別。</span><span class="sxs-lookup"><span data-stu-id="0996e-117">You can use it in your exception handling code to handle exceptions thrown by different providers without having to reference a specific exception class.</span></span> <span data-ttu-id="0996e-118">下列程式碼片段示範如何使用 <xref:System.Data.Common.DbException>，顯示由資料來源藉由 <xref:System.Exception.GetType%2A>、<xref:System.Exception.Source%2A>、<xref:System.Runtime.InteropServices.ExternalException.ErrorCode%2A> 和 <xref:System.Exception.Message%2A> 等屬性所傳回的錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="0996e-118">The following code fragment demonstrates how to use <xref:System.Data.Common.DbException> to display error information returned by the data source using <xref:System.Exception.GetType%2A>, <xref:System.Exception.Source%2A>, <xref:System.Runtime.InteropServices.ExternalException.ErrorCode%2A>, and <xref:System.Exception.Message%2A> properties.</span></span> <span data-ttu-id="0996e-119">輸出中會顯示錯誤類別、代表提供者名稱的來源、錯誤碼以及與錯誤相關聯的訊息。</span><span class="sxs-lookup"><span data-stu-id="0996e-119">The output will display the type of error, the source indicating the provider name, an error code, and the message associated with the error.</span></span>  
  
```vb  
Try  
    ' Do work here.  
Catch ex As DbException  
    ' Display information about the exception.  
    Console.WriteLine("GetType: {0}", ex.GetType())  
    Console.WriteLine("Source: {0}", ex.Source)  
    Console.WriteLine("ErrorCode: {0}", ex.ErrorCode)  
    Console.WriteLine("Message: {0}", ex.Message)  
Finally  
    ' Perform cleanup here.  
End Try  
```  
  
```csharp  
try  
{  
    // Do work here.  
}  
catch (DbException ex)  
{  
    // Display information about the exception.  
    Console.WriteLine("GetType: {0}", ex.GetType());  
    Console.WriteLine("Source: {0}", ex.Source);  
    Console.WriteLine("ErrorCode: {0}", ex.ErrorCode);  
    Console.WriteLine("Message: {0}", ex.Message);  
}  
finally  
{  
    // Perform cleanup here.  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="0996e-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0996e-120">See also</span></span>

- [<span data-ttu-id="0996e-121">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="0996e-121">DbProviderFactories</span></span>](../../../../docs/framework/data/adonet/dbproviderfactories.md)
- [<span data-ttu-id="0996e-122">取得 DbProviderFactory</span><span class="sxs-lookup"><span data-stu-id="0996e-122">Obtaining a DbProviderFactory</span></span>](../../../../docs/framework/data/adonet/obtaining-a-dbproviderfactory.md)
- [<span data-ttu-id="0996e-123">使用 DbDataAdapter 修改資料</span><span class="sxs-lookup"><span data-stu-id="0996e-123">Modifying Data with a DbDataAdapter</span></span>](../../../../docs/framework/data/adonet/modifying-data-with-a-dbdataadapter.md)
- [<span data-ttu-id="0996e-124">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="0996e-124">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
