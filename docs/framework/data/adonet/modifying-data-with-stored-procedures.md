---
title: 使用預存程序修改資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7d8e9a46-1af6-4a02-bf61-969d77ae07e0
ms.openlocfilehash: 7dfd4f07ba0a0473975d87c7cd166635473344a6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59149327"
---
# <a name="modifying-data-with-stored-procedures"></a><span data-ttu-id="1fe37-102">使用預存程序修改資料</span><span class="sxs-lookup"><span data-stu-id="1fe37-102">Modifying Data with Stored Procedures</span></span>
<span data-ttu-id="1fe37-103">預存程序 (Stored Procedure) 可以接受資料做為輸入參數，也可以將資料以輸出參數、結果集 (Result Set) 或傳回值的形式傳回。</span><span class="sxs-lookup"><span data-stu-id="1fe37-103">Stored procedures can accept data as input parameters and can return data as output parameters, result sets, or return values.</span></span> <span data-ttu-id="1fe37-104">下列範例說明 ADO.NET 如何傳送及接收輸入參數、輸出參數和傳回值。</span><span class="sxs-lookup"><span data-stu-id="1fe37-104">The sample below illustrates how ADO.NET sends and receives input parameters, output parameters, and return values.</span></span> <span data-ttu-id="1fe37-105">此範例會將新記錄插入資料表 (該資料表的主索引鍵資料行是 SQL Server 資料庫中的識別欄位)。</span><span class="sxs-lookup"><span data-stu-id="1fe37-105">The example inserts a new record into a table where the primary key column is an identity column in a SQL Server database.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1fe37-106">如果您要使用 SQL Server 預存程序搭配 <xref:System.Data.SqlClient.SqlDataAdapter> 來編輯或刪除資料，請務必不要在預存程序定義中使用 SET NOCOUNT ON。</span><span class="sxs-lookup"><span data-stu-id="1fe37-106">If you are using SQL Server stored procedures to edit or delete data using a <xref:System.Data.SqlClient.SqlDataAdapter>, make sure that you do not use SET NOCOUNT ON in the stored procedure definition.</span></span> <span data-ttu-id="1fe37-107">因為這樣會讓傳回的受影響資料列計數成為零，而 `DataAdapter` 會將它解譯為並行衝突。</span><span class="sxs-lookup"><span data-stu-id="1fe37-107">This causes the rows affected count returned to be zero, which the `DataAdapter` interprets as a concurrency conflict.</span></span> <span data-ttu-id="1fe37-108">在此事件中，系統會擲回 <xref:System.Data.DBConcurrencyException>。</span><span class="sxs-lookup"><span data-stu-id="1fe37-108">In this event, a <xref:System.Data.DBConcurrencyException> will be thrown.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1fe37-109">範例</span><span class="sxs-lookup"><span data-stu-id="1fe37-109">Example</span></span>  
 <span data-ttu-id="1fe37-110">此範例會使用下列的預存程序插入至新的類別**Northwind** **類別**資料表。</span><span class="sxs-lookup"><span data-stu-id="1fe37-110">The sample uses the following stored procedure to insert a new category into the **Northwind** **Categories** table.</span></span> <span data-ttu-id="1fe37-111">預存程序會採用值**CategoryName**資料行做為輸入的參數，然後使用 scope_identity （） 函式來擷取識別欄位的新值**CategoryID**，並將它傳回做為輸出參數。</span><span class="sxs-lookup"><span data-stu-id="1fe37-111">The stored procedure takes the value in the **CategoryName** column as an input parameter and uses the SCOPE_IDENTITY() function to retrieve the new value of the identity field, **CategoryID**, and return it in an output parameter.</span></span> <span data-ttu-id="1fe37-112">RETURN 陳述式使用 @@ROWCOUNT函式傳回插入的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="1fe37-112">The RETURN statement uses the @@ROWCOUNT function to return the number of rows inserted.</span></span>  
  
```sql
CREATE PROCEDURE dbo.InsertCategory  
  @CategoryName nvarchar(15),  
  @Identity int OUT  
AS  
INSERT INTO Categories (CategoryName) VALUES(@CategoryName)  
SET @Identity = SCOPE_IDENTITY()  
RETURN @@ROWCOUNT  
```  
  
 <span data-ttu-id="1fe37-113">下列程式碼範例使用以上所示的 `InsertCategory` 預存程序做為 <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> 的 <xref:System.Data.SqlClient.SqlDataAdapter> 的來源。</span><span class="sxs-lookup"><span data-stu-id="1fe37-113">The following code example uses the `InsertCategory` stored procedure shown above as the source for the <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> of the <xref:System.Data.SqlClient.SqlDataAdapter>.</span></span> <span data-ttu-id="1fe37-114">在呼叫 `@Identity` 的 <xref:System.Data.DataSet> 方法而將記錄插入至資料庫之後，`Update` 輸出參數將反映在 <xref:System.Data.SqlClient.SqlDataAdapter> 中。</span><span class="sxs-lookup"><span data-stu-id="1fe37-114">The `@Identity` output parameter will be reflected in the <xref:System.Data.DataSet> after the record has been inserted into the database when the `Update` method of the <xref:System.Data.SqlClient.SqlDataAdapter> is called.</span></span> <span data-ttu-id="1fe37-115">程式碼也會擷取傳回值。</span><span class="sxs-lookup"><span data-stu-id="1fe37-115">The code also retrieves the return value.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1fe37-116">使用時<xref:System.Data.OleDb.OleDbDataAdapter>，您必須指定參數搭配<xref:System.Data.ParameterDirection>的**ReturnValue**之前其他參數。</span><span class="sxs-lookup"><span data-stu-id="1fe37-116">When using the <xref:System.Data.OleDb.OleDbDataAdapter>, you must specify parameters with a <xref:System.Data.ParameterDirection> of **ReturnValue** before the other parameters.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="1fe37-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1fe37-117">See also</span></span>

- [<span data-ttu-id="1fe37-118">在 ADO.NET 中擷取和修改資料</span><span class="sxs-lookup"><span data-stu-id="1fe37-118">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [<span data-ttu-id="1fe37-119">DataAdapter 和 DataReader</span><span class="sxs-lookup"><span data-stu-id="1fe37-119">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [<span data-ttu-id="1fe37-120">執行命令</span><span class="sxs-lookup"><span data-stu-id="1fe37-120">Executing a Command</span></span>](../../../../docs/framework/data/adonet/executing-a-command.md)
- [<span data-ttu-id="1fe37-121">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="1fe37-121">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
