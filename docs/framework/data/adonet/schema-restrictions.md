---
title: 結構描述限制
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
ms.openlocfilehash: 17c42c5131252993d1f16e4a2f7a6450f0984d11
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149007"
---
# <a name="schema-restrictions"></a><span data-ttu-id="c912b-102">結構描述限制</span><span class="sxs-lookup"><span data-stu-id="c912b-102">Schema Restrictions</span></span>
<span data-ttu-id="c912b-103">**GetSchema**方法的第二個可選參數是用於限制返回的架構資訊量的限制，它作為字串陣列傳遞給**GetSchema**方法。</span><span class="sxs-lookup"><span data-stu-id="c912b-103">The second optional parameter of the **GetSchema** method is the restrictions that are used to limit the amount of schema information returned, and it is passed to the **GetSchema** method as an array of strings.</span></span> <span data-ttu-id="c912b-104">陣列中的位置決定您可以傳遞的值，它相當於限制號碼。</span><span class="sxs-lookup"><span data-stu-id="c912b-104">The position in the array determines the values that you can pass, and this is equivalent to the restriction number.</span></span>  
  
 <span data-ttu-id="c912b-105">例如，下表說明使用 .NET Framework Data Provider for SQL Server 之 "Tables" 結構描述集合所支援的限制。</span><span class="sxs-lookup"><span data-stu-id="c912b-105">For example, the following table describes the restrictions supported by the "Tables" schema collection using the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="c912b-106">SQL Server 結構描述集合的其他限制將列於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="c912b-106">Additional restrictions for SQL Server schema collections are listed at the end of this topic.</span></span>  
  
|<span data-ttu-id="c912b-107">限制名稱</span><span class="sxs-lookup"><span data-stu-id="c912b-107">Restriction Name</span></span>|<span data-ttu-id="c912b-108">參數名稱</span><span class="sxs-lookup"><span data-stu-id="c912b-108">Parameter Name</span></span>|<span data-ttu-id="c912b-109">預設限制值</span><span class="sxs-lookup"><span data-stu-id="c912b-109">Restriction Default</span></span>|<span data-ttu-id="c912b-110">限制號碼</span><span class="sxs-lookup"><span data-stu-id="c912b-110">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="c912b-111">目錄</span><span class="sxs-lookup"><span data-stu-id="c912b-111">Catalog</span></span>|@Catalog|<span data-ttu-id="c912b-112">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c912b-112">TABLE_CATALOG</span></span>|<span data-ttu-id="c912b-113">1</span><span class="sxs-lookup"><span data-stu-id="c912b-113">1</span></span>|  
|<span data-ttu-id="c912b-114">擁有者</span><span class="sxs-lookup"><span data-stu-id="c912b-114">Owner</span></span>|@Owner|<span data-ttu-id="c912b-115">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c912b-115">TABLE_SCHEMA</span></span>|<span data-ttu-id="c912b-116">2</span><span class="sxs-lookup"><span data-stu-id="c912b-116">2</span></span>|  
|<span data-ttu-id="c912b-117">Table</span><span class="sxs-lookup"><span data-stu-id="c912b-117">Table</span></span>|@Name|<span data-ttu-id="c912b-118">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="c912b-118">TABLE_NAME</span></span>|<span data-ttu-id="c912b-119">3</span><span class="sxs-lookup"><span data-stu-id="c912b-119">3</span></span>|  
|<span data-ttu-id="c912b-120">TableType</span><span class="sxs-lookup"><span data-stu-id="c912b-120">TableType</span></span>|@TableType|<span data-ttu-id="c912b-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="c912b-121">TABLE_TYPE</span></span>|<span data-ttu-id="c912b-122">4</span><span class="sxs-lookup"><span data-stu-id="c912b-122">4</span></span>|  
  
## <a name="specifying-restriction-values"></a><span data-ttu-id="c912b-123">指定限制值</span><span class="sxs-lookup"><span data-stu-id="c912b-123">Specifying Restriction Values</span></span>  
 <span data-ttu-id="c912b-124">若要使用 "Tables" 結構描述集合的其中一個限制，只需使用四個元素建立字串陣列，然後將符合限制數目的值置於元素中。</span><span class="sxs-lookup"><span data-stu-id="c912b-124">To use one of the restrictions of the "Tables" schema collection, simply create an array of strings with four elements, then place a value in the element that matches the restriction number.</span></span> <span data-ttu-id="c912b-125">例如，要將**GetSchema**方法返回的表限制為"銷售"架構中的這些表，在將其傳遞給**GetSchema**方法之前，將陣列的第二個元素設置為"Sales"。</span><span class="sxs-lookup"><span data-stu-id="c912b-125">For example, to restrict the tables returned by the **GetSchema** method to only those tables in the "Sales" schema, set the second element of the array to "Sales" before passing it to the **GetSchema** method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c912b-126">`SqlClient` 及 `OracleClient` 的限制集合具有其他 `ParameterName` 資料行。</span><span class="sxs-lookup"><span data-stu-id="c912b-126">The restrictions collections for `SqlClient` and `OracleClient` have an additional `ParameterName` column.</span></span> <span data-ttu-id="c912b-127">限制預設值資料行仍存在，用於回溯相容性，但目前會忽略它.</span><span class="sxs-lookup"><span data-stu-id="c912b-127">The restriction default column is still there for backwards compatibility, but is currently ignored.</span></span> <span data-ttu-id="c912b-128">指定限制值時，應使用參數化查詢而不是字串取代，來將 SQL 資料隱碼攻擊的風險減至最小。</span><span class="sxs-lookup"><span data-stu-id="c912b-128">Parameterized queries rather than string replacement should be used to minimize the risk of an SQL injection attack when specifying restriction values.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c912b-129">陣列中的項目數目必須少於或等於指定結構描述集合所支援的限制數目，否則將擲回 <xref:System.ArgumentException>。</span><span class="sxs-lookup"><span data-stu-id="c912b-129">The number of elements in the array must be less than or equal to the number of restrictions supported for the specified schema collection else an <xref:System.ArgumentException> will be thrown.</span></span> <span data-ttu-id="c912b-130">可以少於限制的最大數目。</span><span class="sxs-lookup"><span data-stu-id="c912b-130">There can be fewer than the maximum number of restrictions.</span></span> <span data-ttu-id="c912b-131">假設遺漏的限制為 Null (未限制)。</span><span class="sxs-lookup"><span data-stu-id="c912b-131">The missing restrictions are assumed to be null (unrestricted).</span></span>  
  
 <span data-ttu-id="c912b-132">您可以查詢 .NET Framework 託管提供程式，通過調用具有限制架構集合名稱的**GetSchema**方法（即"限制"）來確定受支援限制的清單。</span><span class="sxs-lookup"><span data-stu-id="c912b-132">You can query a .NET Framework managed provider to determine the list of supported restrictions by calling the **GetSchema** method with the name of the restrictions schema collection, which is "Restrictions".</span></span> <span data-ttu-id="c912b-133">這將傳回 <xref:System.Data.DataTable>，其包含集合名稱、限制名稱、預設限制值及限制號碼的清單。</span><span class="sxs-lookup"><span data-stu-id="c912b-133">This will return a <xref:System.Data.DataTable> with a list of the collection names, the restriction names, the default restriction values, and the restriction numbers.</span></span>  
  
### <a name="example"></a><span data-ttu-id="c912b-134">範例</span><span class="sxs-lookup"><span data-stu-id="c912b-134">Example</span></span>  
 <span data-ttu-id="c912b-135">以下示例演示如何使用 SQL Server<xref:System.Data.SqlClient.SqlConnection.GetSchema%2A><xref:System.Data.SqlClient.SqlConnection>類的 .NET 框架資料提供程式的方法檢索有關**AdventureWorks**示例資料庫中包含的所有表的架構資訊，並將返回的資訊限制為"銷售"架構中僅返回的資訊：</span><span class="sxs-lookup"><span data-stu-id="c912b-135">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database, and to restrict the information returned to only those tables in the "Sales" schema:</span></span>  
  
```vb  
Imports System.Data.SqlClient  
  
Module Module1  
Sub Main()  
  Dim connectionString As String = _  
    "Data Source=(local);Database=AdventureWorks;" & _  
       "Integrated Security=true;";  
  
  Dim restrictions(3) As String  
  Using connection As New SqlConnection(connectionString)  
    connection.Open()  
  
    'Specify the restrictions.  
    restrictions(1) = "Sales"  
    Dim table As DataTable = connection.GetSchema("Tables", _  
       restrictions)  
  
    ' Display the contents of the table.  
      For Each row As DataRow In table.Rows  
         For Each col As DataColumn In table.Columns  
            Console.WriteLine("{0} = {1}", col.ColumnName, row(col))  
         Next  
         Console.WriteLine("============================")  
      Next  
    Console.WriteLine("Press any key to continue.")  
    Console.ReadKey()  
  End Using  
End Sub  
End Module  
```  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlClient;  
  
class Program  
{  
  static void Main()  
  {  
    string connectionString =
       "Data Source=(local);Database=AdventureWorks;" +  
       "Integrated Security=true;";  
    using (SqlConnection connection =  
       new SqlConnection(connectionString))  
    {  
        connection.Open();  
  
        // Specify the restrictions.  
        string[] restrictions = new string[4];  
        restrictions[1] = "Sales";  
        System.Data.DataTable table = connection.GetSchema(  
          "Tables", restrictions);  
  
        // Display the contents of the table.  
        foreach (System.Data.DataRow row in table.Rows)  
        {  
            foreach (System.Data.DataColumn col in table.Columns)  
            {  
                Console.WriteLine("{0} = {1}",
                  col.ColumnName, row[col]);  
            }  
            Console.WriteLine("============================");  
        }  
        Console.WriteLine("Press any key to continue.");  
        Console.ReadKey();  
    }  
  }  
  
  private static string GetConnectionString()  
  {  
     // To avoid storing the connection string in your code,  
     // you can retrieve it from a configuration file.  
     return "Data Source=(local);Database=AdventureWorks;" +  
        "Integrated Security=true;";  
  }  
  
  private static void DisplayData(System.Data.DataTable table)  
  {  
     foreach (System.Data.DataRow row in table.Rows)  
     {  
        foreach (System.Data.DataColumn col in table.Columns)  
        {  
           Console.WriteLine("{0} = {1}", col.ColumnName, row[col]);  
        }  
     Console.WriteLine("============================");  
     }  
  }  
}  
```  
  
## <a name="sql-server-schema-restrictions"></a><span data-ttu-id="c912b-136">SQL Server 結構描述限制</span><span class="sxs-lookup"><span data-stu-id="c912b-136">SQL Server Schema Restrictions</span></span>  
 <span data-ttu-id="c912b-137">下表將列出 SQL Server 結構描述集合的限制。</span><span class="sxs-lookup"><span data-stu-id="c912b-137">The following tables list the restrictions for SQL Server schema collections.</span></span>  
  
### <a name="users"></a><span data-ttu-id="c912b-138">使用者</span><span class="sxs-lookup"><span data-stu-id="c912b-138">Users</span></span>  
  
|<span data-ttu-id="c912b-139">限制名稱</span><span class="sxs-lookup"><span data-stu-id="c912b-139">Restriction Name</span></span>|<span data-ttu-id="c912b-140">參數名稱</span><span class="sxs-lookup"><span data-stu-id="c912b-140">Parameter Name</span></span>|<span data-ttu-id="c912b-141">預設限制值</span><span class="sxs-lookup"><span data-stu-id="c912b-141">Restriction Default</span></span>|<span data-ttu-id="c912b-142">限制號碼</span><span class="sxs-lookup"><span data-stu-id="c912b-142">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="c912b-143">User_Name</span><span class="sxs-lookup"><span data-stu-id="c912b-143">User_Name</span></span>|@Name|<span data-ttu-id="c912b-144">NAME</span><span class="sxs-lookup"><span data-stu-id="c912b-144">name</span></span>|<span data-ttu-id="c912b-145">1</span><span class="sxs-lookup"><span data-stu-id="c912b-145">1</span></span>|  
  
### <a name="databases"></a><span data-ttu-id="c912b-146">資料庫</span><span class="sxs-lookup"><span data-stu-id="c912b-146">Databases</span></span>  
  
|<span data-ttu-id="c912b-147">限制名稱</span><span class="sxs-lookup"><span data-stu-id="c912b-147">Restriction Name</span></span>|<span data-ttu-id="c912b-148">參數名稱</span><span class="sxs-lookup"><span data-stu-id="c912b-148">Parameter Name</span></span>|<span data-ttu-id="c912b-149">預設限制值</span><span class="sxs-lookup"><span data-stu-id="c912b-149">Restriction Default</span></span>|<span data-ttu-id="c912b-150">限制號碼</span><span class="sxs-lookup"><span data-stu-id="c912b-150">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="c912b-151">名稱</span><span class="sxs-lookup"><span data-stu-id="c912b-151">Name</span></span>|@Name|<span data-ttu-id="c912b-152">名稱</span><span class="sxs-lookup"><span data-stu-id="c912b-152">Name</span></span>|<span data-ttu-id="c912b-153">1</span><span class="sxs-lookup"><span data-stu-id="c912b-153">1</span></span>|  
  
### <a name="tables"></a><span data-ttu-id="c912b-154">資料表</span><span class="sxs-lookup"><span data-stu-id="c912b-154">Tables</span></span>  
  
|<span data-ttu-id="c912b-155">限制名稱</span><span class="sxs-lookup"><span data-stu-id="c912b-155">Restriction Name</span></span>|<span data-ttu-id="c912b-156">參數名稱</span><span class="sxs-lookup"><span data-stu-id="c912b-156">Parameter Name</span></span>|<span data-ttu-id="c912b-157">預設限制值</span><span class="sxs-lookup"><span data-stu-id="c912b-157">Restriction Default</span></span>|<span data-ttu-id="c912b-158">限制號碼</span><span class="sxs-lookup"><span data-stu-id="c912b-158">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="c912b-159">目錄</span><span class="sxs-lookup"><span data-stu-id="c912b-159">Catalog</span></span>|@Catalog|<span data-ttu-id="c912b-160">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c912b-160">TABLE_CATALOG</span></span>|<span data-ttu-id="c912b-161">1</span><span class="sxs-lookup"><span data-stu-id="c912b-161">1</span></span>|  
|<span data-ttu-id="c912b-162">擁有者</span><span class="sxs-lookup"><span data-stu-id="c912b-162">Owner</span></span>|@Owner|<span data-ttu-id="c912b-163">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c912b-163">TABLE_SCHEMA</span></span>|<span data-ttu-id="c912b-164">2</span><span class="sxs-lookup"><span data-stu-id="c912b-164">2</span></span>|  
|<span data-ttu-id="c912b-165">Table</span><span class="sxs-lookup"><span data-stu-id="c912b-165">Table</span></span>|@Name|<span data-ttu-id="c912b-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="c912b-166">TABLE_NAME</span></span>|<span data-ttu-id="c912b-167">3</span><span class="sxs-lookup"><span data-stu-id="c912b-167">3</span></span>|  
|<span data-ttu-id="c912b-168">TableType</span><span class="sxs-lookup"><span data-stu-id="c912b-168">TableType</span></span>|@TableType|<span data-ttu-id="c912b-169">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="c912b-169">TABLE_TYPE</span></span>|<span data-ttu-id="c912b-170">4</span><span class="sxs-lookup"><span data-stu-id="c912b-170">4</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="c912b-171">資料行</span><span class="sxs-lookup"><span data-stu-id="c912b-171">Columns</span></span>  
  
|<span data-ttu-id="c912b-172">限制名稱</span><span class="sxs-lookup"><span data-stu-id="c912b-172">Restriction Name</span></span>|<span data-ttu-id="c912b-173">參數名稱</span><span class="sxs-lookup"><span data-stu-id="c912b-173">Parameter Name</span></span>|<span data-ttu-id="c912b-174">預設限制值</span><span class="sxs-lookup"><span data-stu-id="c912b-174">Restriction Default</span></span>|<span data-ttu-id="c912b-175">限制號碼</span><span class="sxs-lookup"><span data-stu-id="c912b-175">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="c912b-176">目錄</span><span class="sxs-lookup"><span data-stu-id="c912b-176">Catalog</span></span>|@Catalog|<span data-ttu-id="c912b-177">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c912b-177">TABLE_CATALOG</span></span>|<span data-ttu-id="c912b-178">1</span><span class="sxs-lookup"><span data-stu-id="c912b-178">1</span></span>|  
|<span data-ttu-id="c912b-179">擁有者</span><span class="sxs-lookup"><span data-stu-id="c912b-179">Owner</span></span>|@Owner|<span data-ttu-id="c912b-180">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c912b-180">TABLE_SCHEMA</span></span>|<span data-ttu-id="c912b-181">2</span><span class="sxs-lookup"><span data-stu-id="c912b-181">2</span></span>|  
|<span data-ttu-id="c912b-182">Table</span><span class="sxs-lookup"><span data-stu-id="c912b-182">Table</span></span>|@Table|<span data-ttu-id="c912b-183">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="c912b-183">TABLE_NAME</span></span>|<span data-ttu-id="c912b-184">3</span><span class="sxs-lookup"><span data-stu-id="c912b-184">3</span></span>|  
|<span data-ttu-id="c912b-185">資料行</span><span class="sxs-lookup"><span data-stu-id="c912b-185">Column</span></span>|@Column|<span data-ttu-id="c912b-186">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="c912b-186">COLUMN_NAME</span></span>|<span data-ttu-id="c912b-187">4</span><span class="sxs-lookup"><span data-stu-id="c912b-187">4</span></span>|  
  
### <a name="structuredtypemembers"></a><span data-ttu-id="c912b-188">StructuredTypeMembers</span><span class="sxs-lookup"><span data-stu-id="c912b-188">StructuredTypeMembers</span></span>  
  
|<span data-ttu-id="c912b-189">限制名稱</span><span class="sxs-lookup"><span data-stu-id="c912b-189">Restriction Name</span></span>|<span data-ttu-id="c912b-190">參數名稱</span><span class="sxs-lookup"><span data-stu-id="c912b-190">Parameter Name</span></span>|<span data-ttu-id="c912b-191">預設限制值</span><span class="sxs-lookup"><span data-stu-id="c912b-191">Restriction Default</span></span>|<span data-ttu-id="c912b-192">限制號碼</span><span class="sxs-lookup"><span data-stu-id="c912b-192">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="c912b-193">目錄</span><span class="sxs-lookup"><span data-stu-id="c912b-193">Catalog</span></span>|@Catalog|<span data-ttu-id="c912b-194">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c912b-194">TABLE_CATALOG</span></span>|<span data-ttu-id="c912b-195">1</span><span class="sxs-lookup"><span data-stu-id="c912b-195">1</span></span>|  
|<span data-ttu-id="c912b-196">擁有者</span><span class="sxs-lookup"><span data-stu-id="c912b-196">Owner</span></span>|@Owner|<span data-ttu-id="c912b-197">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c912b-197">TABLE_SCHEMA</span></span>|<span data-ttu-id="c912b-198">2</span><span class="sxs-lookup"><span data-stu-id="c912b-198">2</span></span>|  
|<span data-ttu-id="c912b-199">Table</span><span class="sxs-lookup"><span data-stu-id="c912b-199">Table</span></span>|@Table|<span data-ttu-id="c912b-200">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="c912b-200">TABLE_NAME</span></span>|<span data-ttu-id="c912b-201">3</span><span class="sxs-lookup"><span data-stu-id="c912b-201">3</span></span>|  
|<span data-ttu-id="c912b-202">資料行</span><span class="sxs-lookup"><span data-stu-id="c912b-202">Column</span></span>|@Column|<span data-ttu-id="c912b-203">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="c912b-203">COLUMN_NAME</span></span>|<span data-ttu-id="c912b-204">4</span><span class="sxs-lookup"><span data-stu-id="c912b-204">4</span></span>|  
  
### <a name="views"></a><span data-ttu-id="c912b-205">檢視</span><span class="sxs-lookup"><span data-stu-id="c912b-205">Views</span></span>  
  
|<span data-ttu-id="c912b-206">限制名稱</span><span class="sxs-lookup"><span data-stu-id="c912b-206">Restriction Name</span></span>|<span data-ttu-id="c912b-207">參數名稱</span><span class="sxs-lookup"><span data-stu-id="c912b-207">Parameter Name</span></span>|<span data-ttu-id="c912b-208">預設限制值</span><span class="sxs-lookup"><span data-stu-id="c912b-208">Restriction Default</span></span>|<span data-ttu-id="c912b-209">限制號碼</span><span class="sxs-lookup"><span data-stu-id="c912b-209">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="c912b-210">目錄</span><span class="sxs-lookup"><span data-stu-id="c912b-210">Catalog</span></span>|@Catalog|<span data-ttu-id="c912b-211">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c912b-211">TABLE_CATALOG</span></span>|<span data-ttu-id="c912b-212">1</span><span class="sxs-lookup"><span data-stu-id="c912b-212">1</span></span>|  
|<span data-ttu-id="c912b-213">擁有者</span><span class="sxs-lookup"><span data-stu-id="c912b-213">Owner</span></span>|@Owner|<span data-ttu-id="c912b-214">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c912b-214">TABLE_SCHEMA</span></span>|<span data-ttu-id="c912b-215">2</span><span class="sxs-lookup"><span data-stu-id="c912b-215">2</span></span>|  
|<span data-ttu-id="c912b-216">Table</span><span class="sxs-lookup"><span data-stu-id="c912b-216">Table</span></span>|@Table|<span data-ttu-id="c912b-217">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="c912b-217">TABLE_NAME</span></span>|<span data-ttu-id="c912b-218">3</span><span class="sxs-lookup"><span data-stu-id="c912b-218">3</span></span>|  
  
### <a name="viewcolumns"></a><span data-ttu-id="c912b-219">ViewColumns</span><span class="sxs-lookup"><span data-stu-id="c912b-219">ViewColumns</span></span>  
  
|<span data-ttu-id="c912b-220">限制名稱</span><span class="sxs-lookup"><span data-stu-id="c912b-220">Restriction Name</span></span>|<span data-ttu-id="c912b-221">參數名稱</span><span class="sxs-lookup"><span data-stu-id="c912b-221">Parameter Name</span></span>|<span data-ttu-id="c912b-222">預設限制值</span><span class="sxs-lookup"><span data-stu-id="c912b-222">Restriction Default</span></span>|<span data-ttu-id="c912b-223">限制號碼</span><span class="sxs-lookup"><span data-stu-id="c912b-223">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="c912b-224">目錄</span><span class="sxs-lookup"><span data-stu-id="c912b-224">Catalog</span></span>|@Catalog|<span data-ttu-id="c912b-225">VIEW_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c912b-225">VIEW_CATALOG</span></span>|<span data-ttu-id="c912b-226">1</span><span class="sxs-lookup"><span data-stu-id="c912b-226">1</span></span>|  
|<span data-ttu-id="c912b-227">擁有者</span><span class="sxs-lookup"><span data-stu-id="c912b-227">Owner</span></span>|@Owner|<span data-ttu-id="c912b-228">VIEW_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c912b-228">VIEW_SCHEMA</span></span>|<span data-ttu-id="c912b-229">2</span><span class="sxs-lookup"><span data-stu-id="c912b-229">2</span></span>|  
|<span data-ttu-id="c912b-230">Table</span><span class="sxs-lookup"><span data-stu-id="c912b-230">Table</span></span>|@Table|<span data-ttu-id="c912b-231">VIEW_NAME</span><span class="sxs-lookup"><span data-stu-id="c912b-231">VIEW_NAME</span></span>|<span data-ttu-id="c912b-232">3</span><span class="sxs-lookup"><span data-stu-id="c912b-232">3</span></span>|  
|<span data-ttu-id="c912b-233">資料行</span><span class="sxs-lookup"><span data-stu-id="c912b-233">Column</span></span>|@Column|<span data-ttu-id="c912b-234">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="c912b-234">COLUMN_NAME</span></span>|<span data-ttu-id="c912b-235">4</span><span class="sxs-lookup"><span data-stu-id="c912b-235">4</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="c912b-236">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="c912b-236">ProcedureParameters</span></span>  
  
|<span data-ttu-id="c912b-237">限制名稱</span><span class="sxs-lookup"><span data-stu-id="c912b-237">Restriction Name</span></span>|<span data-ttu-id="c912b-238">參數名稱</span><span class="sxs-lookup"><span data-stu-id="c912b-238">Parameter Name</span></span>|<span data-ttu-id="c912b-239">預設限制值</span><span class="sxs-lookup"><span data-stu-id="c912b-239">Restriction Default</span></span>|<span data-ttu-id="c912b-240">限制號碼</span><span class="sxs-lookup"><span data-stu-id="c912b-240">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="c912b-241">目錄</span><span class="sxs-lookup"><span data-stu-id="c912b-241">Catalog</span></span>|@Catalog|<span data-ttu-id="c912b-242">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c912b-242">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="c912b-243">1</span><span class="sxs-lookup"><span data-stu-id="c912b-243">1</span></span>|  
|<span data-ttu-id="c912b-244">擁有者</span><span class="sxs-lookup"><span data-stu-id="c912b-244">Owner</span></span>|@Owner|<span data-ttu-id="c912b-245">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c912b-245">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="c912b-246">2</span><span class="sxs-lookup"><span data-stu-id="c912b-246">2</span></span>|  
|<span data-ttu-id="c912b-247">名稱</span><span class="sxs-lookup"><span data-stu-id="c912b-247">Name</span></span>|@Name|<span data-ttu-id="c912b-248">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="c912b-248">SPECIFIC_NAME</span></span>|<span data-ttu-id="c912b-249">3</span><span class="sxs-lookup"><span data-stu-id="c912b-249">3</span></span>|  
|<span data-ttu-id="c912b-250">參數</span><span class="sxs-lookup"><span data-stu-id="c912b-250">Parameter</span></span>|@Parameter|<span data-ttu-id="c912b-251">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="c912b-251">PARAMETER_NAME</span></span>|<span data-ttu-id="c912b-252">4</span><span class="sxs-lookup"><span data-stu-id="c912b-252">4</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="c912b-253">程序</span><span class="sxs-lookup"><span data-stu-id="c912b-253">Procedures</span></span>  
  
|<span data-ttu-id="c912b-254">限制名稱</span><span class="sxs-lookup"><span data-stu-id="c912b-254">Restriction Name</span></span>|<span data-ttu-id="c912b-255">參數名稱</span><span class="sxs-lookup"><span data-stu-id="c912b-255">Parameter Name</span></span>|<span data-ttu-id="c912b-256">預設限制值</span><span class="sxs-lookup"><span data-stu-id="c912b-256">Restriction Default</span></span>|<span data-ttu-id="c912b-257">限制號碼</span><span class="sxs-lookup"><span data-stu-id="c912b-257">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="c912b-258">目錄</span><span class="sxs-lookup"><span data-stu-id="c912b-258">Catalog</span></span>|@Catalog|<span data-ttu-id="c912b-259">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c912b-259">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="c912b-260">1</span><span class="sxs-lookup"><span data-stu-id="c912b-260">1</span></span>|  
|<span data-ttu-id="c912b-261">擁有者</span><span class="sxs-lookup"><span data-stu-id="c912b-261">Owner</span></span>|@Owner|<span data-ttu-id="c912b-262">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c912b-262">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="c912b-263">2</span><span class="sxs-lookup"><span data-stu-id="c912b-263">2</span></span>|  
|<span data-ttu-id="c912b-264">名稱</span><span class="sxs-lookup"><span data-stu-id="c912b-264">Name</span></span>|@Name|<span data-ttu-id="c912b-265">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="c912b-265">SPECIFIC_NAME</span></span>|<span data-ttu-id="c912b-266">3</span><span class="sxs-lookup"><span data-stu-id="c912b-266">3</span></span>|  
|<span data-ttu-id="c912b-267">類型</span><span class="sxs-lookup"><span data-stu-id="c912b-267">Type</span></span>|@Type|<span data-ttu-id="c912b-268">ROUTINE_TYPE</span><span class="sxs-lookup"><span data-stu-id="c912b-268">ROUTINE_TYPE</span></span>|<span data-ttu-id="c912b-269">4</span><span class="sxs-lookup"><span data-stu-id="c912b-269">4</span></span>|  
  
### <a name="indexcolumns"></a><span data-ttu-id="c912b-270">IndexColumns</span><span class="sxs-lookup"><span data-stu-id="c912b-270">IndexColumns</span></span>  
  
|<span data-ttu-id="c912b-271">限制名稱</span><span class="sxs-lookup"><span data-stu-id="c912b-271">Restriction Name</span></span>|<span data-ttu-id="c912b-272">參數名稱</span><span class="sxs-lookup"><span data-stu-id="c912b-272">Parameter Name</span></span>|<span data-ttu-id="c912b-273">預設限制值</span><span class="sxs-lookup"><span data-stu-id="c912b-273">Restriction Default</span></span>|<span data-ttu-id="c912b-274">限制號碼</span><span class="sxs-lookup"><span data-stu-id="c912b-274">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="c912b-275">目錄</span><span class="sxs-lookup"><span data-stu-id="c912b-275">Catalog</span></span>|@Catalog|<span data-ttu-id="c912b-276">db_name()</span><span class="sxs-lookup"><span data-stu-id="c912b-276">db_name()</span></span>|<span data-ttu-id="c912b-277">1</span><span class="sxs-lookup"><span data-stu-id="c912b-277">1</span></span>|  
|<span data-ttu-id="c912b-278">擁有者</span><span class="sxs-lookup"><span data-stu-id="c912b-278">Owner</span></span>|@Owner|<span data-ttu-id="c912b-279">user_name()</span><span class="sxs-lookup"><span data-stu-id="c912b-279">user_name()</span></span>|<span data-ttu-id="c912b-280">2</span><span class="sxs-lookup"><span data-stu-id="c912b-280">2</span></span>|  
|<span data-ttu-id="c912b-281">Table</span><span class="sxs-lookup"><span data-stu-id="c912b-281">Table</span></span>|@Table|<span data-ttu-id="c912b-282">o.name</span><span class="sxs-lookup"><span data-stu-id="c912b-282">o.name</span></span>|<span data-ttu-id="c912b-283">3</span><span class="sxs-lookup"><span data-stu-id="c912b-283">3</span></span>|  
|<span data-ttu-id="c912b-284">ConstraintName</span><span class="sxs-lookup"><span data-stu-id="c912b-284">ConstraintName</span></span>|@ConstraintName|<span data-ttu-id="c912b-285">x.name</span><span class="sxs-lookup"><span data-stu-id="c912b-285">x.name</span></span>|<span data-ttu-id="c912b-286">4</span><span class="sxs-lookup"><span data-stu-id="c912b-286">4</span></span>|  
|<span data-ttu-id="c912b-287">資料行</span><span class="sxs-lookup"><span data-stu-id="c912b-287">Column</span></span>|@Column|<span data-ttu-id="c912b-288">c.name</span><span class="sxs-lookup"><span data-stu-id="c912b-288">c.name</span></span>|<span data-ttu-id="c912b-289">5</span><span class="sxs-lookup"><span data-stu-id="c912b-289">5</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="c912b-290">索引</span><span class="sxs-lookup"><span data-stu-id="c912b-290">Indexes</span></span>  
  
|<span data-ttu-id="c912b-291">限制名稱</span><span class="sxs-lookup"><span data-stu-id="c912b-291">Restriction Name</span></span>|<span data-ttu-id="c912b-292">參數名稱</span><span class="sxs-lookup"><span data-stu-id="c912b-292">Parameter Name</span></span>|<span data-ttu-id="c912b-293">預設限制值</span><span class="sxs-lookup"><span data-stu-id="c912b-293">Restriction Default</span></span>|<span data-ttu-id="c912b-294">限制號碼</span><span class="sxs-lookup"><span data-stu-id="c912b-294">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="c912b-295">目錄</span><span class="sxs-lookup"><span data-stu-id="c912b-295">Catalog</span></span>|@Catalog|<span data-ttu-id="c912b-296">db_name()</span><span class="sxs-lookup"><span data-stu-id="c912b-296">db_name()</span></span>|<span data-ttu-id="c912b-297">1</span><span class="sxs-lookup"><span data-stu-id="c912b-297">1</span></span>|  
|<span data-ttu-id="c912b-298">擁有者</span><span class="sxs-lookup"><span data-stu-id="c912b-298">Owner</span></span>|@Owner|<span data-ttu-id="c912b-299">user_name()</span><span class="sxs-lookup"><span data-stu-id="c912b-299">user_name()</span></span>|<span data-ttu-id="c912b-300">2</span><span class="sxs-lookup"><span data-stu-id="c912b-300">2</span></span>|  
|<span data-ttu-id="c912b-301">Table</span><span class="sxs-lookup"><span data-stu-id="c912b-301">Table</span></span>|@Table|<span data-ttu-id="c912b-302">o.name</span><span class="sxs-lookup"><span data-stu-id="c912b-302">o.name</span></span>|<span data-ttu-id="c912b-303">3</span><span class="sxs-lookup"><span data-stu-id="c912b-303">3</span></span>|  
  
### <a name="userdefinedtypes"></a><span data-ttu-id="c912b-304">UserDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="c912b-304">UserDefinedTypes</span></span>  
  
|<span data-ttu-id="c912b-305">限制名稱</span><span class="sxs-lookup"><span data-stu-id="c912b-305">Restriction Name</span></span>|<span data-ttu-id="c912b-306">參數名稱</span><span class="sxs-lookup"><span data-stu-id="c912b-306">Parameter Name</span></span>|<span data-ttu-id="c912b-307">預設限制值</span><span class="sxs-lookup"><span data-stu-id="c912b-307">Restriction Default</span></span>|<span data-ttu-id="c912b-308">限制號碼</span><span class="sxs-lookup"><span data-stu-id="c912b-308">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="c912b-309">assembly_name</span><span class="sxs-lookup"><span data-stu-id="c912b-309">assembly_name</span></span>|@AssemblyName|<span data-ttu-id="c912b-310">assemblies.name</span><span class="sxs-lookup"><span data-stu-id="c912b-310">assemblies.name</span></span>|<span data-ttu-id="c912b-311">1</span><span class="sxs-lookup"><span data-stu-id="c912b-311">1</span></span>|  
|<span data-ttu-id="c912b-312">udt_name</span><span class="sxs-lookup"><span data-stu-id="c912b-312">udt_name</span></span>|@UDTName|<span data-ttu-id="c912b-313">types.assembly_class</span><span class="sxs-lookup"><span data-stu-id="c912b-313">types.assembly_class</span></span>|<span data-ttu-id="c912b-314">2</span><span class="sxs-lookup"><span data-stu-id="c912b-314">2</span></span>|  
  
### <a name="foreignkeys"></a><span data-ttu-id="c912b-315">ForeignKeys</span><span class="sxs-lookup"><span data-stu-id="c912b-315">ForeignKeys</span></span>  
  
|<span data-ttu-id="c912b-316">限制名稱</span><span class="sxs-lookup"><span data-stu-id="c912b-316">Restriction Name</span></span>|<span data-ttu-id="c912b-317">參數名稱</span><span class="sxs-lookup"><span data-stu-id="c912b-317">Parameter Name</span></span>|<span data-ttu-id="c912b-318">預設限制值</span><span class="sxs-lookup"><span data-stu-id="c912b-318">Restriction Default</span></span>|<span data-ttu-id="c912b-319">限制號碼</span><span class="sxs-lookup"><span data-stu-id="c912b-319">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="c912b-320">目錄</span><span class="sxs-lookup"><span data-stu-id="c912b-320">Catalog</span></span>|@Catalog|<span data-ttu-id="c912b-321">CONSTRAINT_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c912b-321">CONSTRAINT_CATALOG</span></span>|<span data-ttu-id="c912b-322">1</span><span class="sxs-lookup"><span data-stu-id="c912b-322">1</span></span>|  
|<span data-ttu-id="c912b-323">擁有者</span><span class="sxs-lookup"><span data-stu-id="c912b-323">Owner</span></span>|@Owner|<span data-ttu-id="c912b-324">CONSTRAINT_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c912b-324">CONSTRAINT_SCHEMA</span></span>|<span data-ttu-id="c912b-325">2</span><span class="sxs-lookup"><span data-stu-id="c912b-325">2</span></span>|  
|<span data-ttu-id="c912b-326">Table</span><span class="sxs-lookup"><span data-stu-id="c912b-326">Table</span></span>|@Table|<span data-ttu-id="c912b-327">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="c912b-327">TABLE_NAME</span></span>|<span data-ttu-id="c912b-328">3</span><span class="sxs-lookup"><span data-stu-id="c912b-328">3</span></span>|  
|<span data-ttu-id="c912b-329">名稱</span><span class="sxs-lookup"><span data-stu-id="c912b-329">Name</span></span>|@Name|<span data-ttu-id="c912b-330">CONSTRAINT_NAME</span><span class="sxs-lookup"><span data-stu-id="c912b-330">CONSTRAINT_NAME</span></span>|<span data-ttu-id="c912b-331">4</span><span class="sxs-lookup"><span data-stu-id="c912b-331">4</span></span>|  
  
## <a name="sql-server-2008-schema-restrictions"></a><span data-ttu-id="c912b-332">SQL Server 2008 結構描述限制</span><span class="sxs-lookup"><span data-stu-id="c912b-332">SQL Server 2008 Schema Restrictions</span></span>  
 <span data-ttu-id="c912b-333">下表將列出 SQL Server 2008 結構描述集合的限制。</span><span class="sxs-lookup"><span data-stu-id="c912b-333">The following tables list the restrictions for SQL Server 2008 schema collections.</span></span> <span data-ttu-id="c912b-334">從 .NET Framework 3.5 版 SP1 和 SQL Server 2008 開始，這些限制便有效。</span><span class="sxs-lookup"><span data-stu-id="c912b-334">These restrictions are valid beginning with version 3.5 SP1 of the .NET Framework and SQL Server 2008.</span></span> <span data-ttu-id="c912b-335">舊版 .NET Framework 和 SQL Server 不支援它們。</span><span class="sxs-lookup"><span data-stu-id="c912b-335">They are not supported in earlier versions of the .NET Framework and SQL Server.</span></span>  
  
### <a name="columnsetcolumns"></a><span data-ttu-id="c912b-336">ColumnSetColumns</span><span class="sxs-lookup"><span data-stu-id="c912b-336">ColumnSetColumns</span></span>  
  
|<span data-ttu-id="c912b-337">限制名稱</span><span class="sxs-lookup"><span data-stu-id="c912b-337">Restriction Name</span></span>|<span data-ttu-id="c912b-338">參數名稱</span><span class="sxs-lookup"><span data-stu-id="c912b-338">Parameter Name</span></span>|<span data-ttu-id="c912b-339">預設限制值</span><span class="sxs-lookup"><span data-stu-id="c912b-339">Restriction Default</span></span>|<span data-ttu-id="c912b-340">限制號碼</span><span class="sxs-lookup"><span data-stu-id="c912b-340">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="c912b-341">目錄</span><span class="sxs-lookup"><span data-stu-id="c912b-341">Catalog</span></span>|@Catalog|<span data-ttu-id="c912b-342">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c912b-342">TABLE_CATALOG</span></span>|<span data-ttu-id="c912b-343">1</span><span class="sxs-lookup"><span data-stu-id="c912b-343">1</span></span>|  
|<span data-ttu-id="c912b-344">擁有者</span><span class="sxs-lookup"><span data-stu-id="c912b-344">Owner</span></span>|@Owner|<span data-ttu-id="c912b-345">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c912b-345">TABLE_SCHEMA</span></span>|<span data-ttu-id="c912b-346">2</span><span class="sxs-lookup"><span data-stu-id="c912b-346">2</span></span>|  
|<span data-ttu-id="c912b-347">Table</span><span class="sxs-lookup"><span data-stu-id="c912b-347">Table</span></span>|@Table|<span data-ttu-id="c912b-348">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="c912b-348">TABLE_NAME</span></span>|<span data-ttu-id="c912b-349">3</span><span class="sxs-lookup"><span data-stu-id="c912b-349">3</span></span>|  
  
### <a name="allcolumns"></a><span data-ttu-id="c912b-350">AllColumns</span><span class="sxs-lookup"><span data-stu-id="c912b-350">AllColumns</span></span>  
  
|<span data-ttu-id="c912b-351">限制名稱</span><span class="sxs-lookup"><span data-stu-id="c912b-351">Restriction Name</span></span>|<span data-ttu-id="c912b-352">參數名稱</span><span class="sxs-lookup"><span data-stu-id="c912b-352">Parameter Name</span></span>|<span data-ttu-id="c912b-353">預設限制值</span><span class="sxs-lookup"><span data-stu-id="c912b-353">Restriction Default</span></span>|<span data-ttu-id="c912b-354">限制號碼</span><span class="sxs-lookup"><span data-stu-id="c912b-354">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="c912b-355">目錄</span><span class="sxs-lookup"><span data-stu-id="c912b-355">Catalog</span></span>|@Catalog|<span data-ttu-id="c912b-356">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c912b-356">TABLE_CATALOG</span></span>|<span data-ttu-id="c912b-357">1</span><span class="sxs-lookup"><span data-stu-id="c912b-357">1</span></span>|  
|<span data-ttu-id="c912b-358">擁有者</span><span class="sxs-lookup"><span data-stu-id="c912b-358">Owner</span></span>|@Owner|<span data-ttu-id="c912b-359">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c912b-359">TABLE_SCHEMA</span></span>|<span data-ttu-id="c912b-360">2</span><span class="sxs-lookup"><span data-stu-id="c912b-360">2</span></span>|  
|<span data-ttu-id="c912b-361">Table</span><span class="sxs-lookup"><span data-stu-id="c912b-361">Table</span></span>|@Table|<span data-ttu-id="c912b-362">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="c912b-362">TABLE_NAME</span></span>|<span data-ttu-id="c912b-363">3</span><span class="sxs-lookup"><span data-stu-id="c912b-363">3</span></span>|  
|<span data-ttu-id="c912b-364">資料行</span><span class="sxs-lookup"><span data-stu-id="c912b-364">Column</span></span>|@Column|<span data-ttu-id="c912b-365">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="c912b-365">COLUMN_NAME</span></span>|<span data-ttu-id="c912b-366">4</span><span class="sxs-lookup"><span data-stu-id="c912b-366">4</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c912b-367">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c912b-367">See also</span></span>

- <span data-ttu-id="c912b-368">[ADO.NET 概觀](ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="c912b-368">[ADO.NET Overview](ado-net-overview.md)</span></span>
