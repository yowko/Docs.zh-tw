---
title: "結構描述限制"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: f5b004b70716c61af8ac37fef76f660c488e5a74
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="schema-restrictions"></a><span data-ttu-id="afcea-102">結構描述限制</span><span class="sxs-lookup"><span data-stu-id="afcea-102">Schema Restrictions</span></span>
<span data-ttu-id="afcea-103">第二個選擇性參數**GetSchema**方法會傳回用來限制的結構描述資訊量的限制，並將它傳遞至**GetSchema**方法的字串陣列.</span><span class="sxs-lookup"><span data-stu-id="afcea-103">The second optional parameter of the **GetSchema** method is the restrictions that are used to limit the amount of schema information returned, and it is passed to the **GetSchema** method as an array of strings.</span></span> <span data-ttu-id="afcea-104">陣列中的位置決定您可以傳遞的值，它相當於限制號碼。</span><span class="sxs-lookup"><span data-stu-id="afcea-104">The position in the array determines the values that you can pass, and this is equivalent to the restriction number.</span></span>  
  
 <span data-ttu-id="afcea-105">例如，下表說明使用 .NET Framework Data Provider for SQL Server 之 "Tables" 結構描述集合所支援的限制。</span><span class="sxs-lookup"><span data-stu-id="afcea-105">For example, the following table describes the restrictions supported by the "Tables" schema collection using the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="afcea-106">SQL Server 結構描述集合的其他限制將列於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="afcea-106">Additional restrictions for SQL Server schema collections are listed at the end of this topic.</span></span>  
  
|<span data-ttu-id="afcea-107">限制名稱</span><span class="sxs-lookup"><span data-stu-id="afcea-107">Restriction Name</span></span>|<span data-ttu-id="afcea-108">參數名稱</span><span class="sxs-lookup"><span data-stu-id="afcea-108">Parameter Name</span></span>|<span data-ttu-id="afcea-109">預設限制值</span><span class="sxs-lookup"><span data-stu-id="afcea-109">Restriction Default</span></span>|<span data-ttu-id="afcea-110">限制號碼</span><span class="sxs-lookup"><span data-stu-id="afcea-110">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="afcea-111">Catalog</span><span class="sxs-lookup"><span data-stu-id="afcea-111">Catalog</span></span>|@Catalog|<span data-ttu-id="afcea-112">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="afcea-112">TABLE_CATALOG</span></span>|<span data-ttu-id="afcea-113">1</span><span class="sxs-lookup"><span data-stu-id="afcea-113">1</span></span>|  
|<span data-ttu-id="afcea-114">Owner</span><span class="sxs-lookup"><span data-stu-id="afcea-114">Owner</span></span>|@Owner|<span data-ttu-id="afcea-115">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="afcea-115">TABLE_SCHEMA</span></span>|<span data-ttu-id="afcea-116">2</span><span class="sxs-lookup"><span data-stu-id="afcea-116">2</span></span>|  
|<span data-ttu-id="afcea-117">資料表</span><span class="sxs-lookup"><span data-stu-id="afcea-117">Table</span></span>|@Name|<span data-ttu-id="afcea-118">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="afcea-118">TABLE_NAME</span></span>|<span data-ttu-id="afcea-119">3</span><span class="sxs-lookup"><span data-stu-id="afcea-119">3</span></span>|  
|<span data-ttu-id="afcea-120">TableType</span><span class="sxs-lookup"><span data-stu-id="afcea-120">TableType</span></span>|@TableType|<span data-ttu-id="afcea-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="afcea-121">TABLE_TYPE</span></span>|<span data-ttu-id="afcea-122">4</span><span class="sxs-lookup"><span data-stu-id="afcea-122">4</span></span>|  
  
## <a name="specifying-restriction-values"></a><span data-ttu-id="afcea-123">指定限制值</span><span class="sxs-lookup"><span data-stu-id="afcea-123">Specifying Restriction Values</span></span>  
 <span data-ttu-id="afcea-124">若要使用 "Tables" 結構描述集合的其中一個限制，只需使用四個元素建立字串陣列，然後將符合限制數目的值置於元素中。</span><span class="sxs-lookup"><span data-stu-id="afcea-124">To use one of the restrictions of the "Tables" schema collection, simply create an array of strings with four elements, then place a value in the element that matches the restriction number.</span></span> <span data-ttu-id="afcea-125">例如，以限制資料表所傳回**GetSchema**只有"Sales"結構描述中的資料表的方法之前將其傳遞至設定為"Sales"陣列的第二個項目**GetSchema**方法。</span><span class="sxs-lookup"><span data-stu-id="afcea-125">For example, to restrict the tables returned by the **GetSchema** method to only those tables in the "Sales" schema, set the second element of the array to "Sales" before passing it to the **GetSchema** method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="afcea-126">`SqlClient` 及 `OracleClient` 的限制集合具有其他 `ParameterName` 資料行。</span><span class="sxs-lookup"><span data-stu-id="afcea-126">The restrictions collections for `SqlClient` and `OracleClient` have an additional `ParameterName` column.</span></span> <span data-ttu-id="afcea-127">限制預設值資料行仍存在，用於回溯相容性，但目前會忽略它.</span><span class="sxs-lookup"><span data-stu-id="afcea-127">The restriction default column is still there for backwards compatibility, but is currently ignored.</span></span> <span data-ttu-id="afcea-128">指定限制值時，應使用參數化查詢而不是字串取代，來將 SQL 資料隱碼攻擊的風險減至最小。</span><span class="sxs-lookup"><span data-stu-id="afcea-128">Parameterized queries rather than string replacement should be used to minimize the risk of an SQL injection attack when specifying restriction values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="afcea-129">陣列中的項目數目必須少於或等於指定結構描述集合所支援的限制數目，否則將擲回 <xref:System.ArgumentException>。</span><span class="sxs-lookup"><span data-stu-id="afcea-129">The number of elements in the array must be less than or equal to the number of restrictions supported for the specified schema collection else an <xref:System.ArgumentException> will be thrown.</span></span> <span data-ttu-id="afcea-130">可以少於限制的最大數目。</span><span class="sxs-lookup"><span data-stu-id="afcea-130">There can be fewer than the maximum number of restrictions.</span></span> <span data-ttu-id="afcea-131">假設遺漏的限制為 Null (未限制)。</span><span class="sxs-lookup"><span data-stu-id="afcea-131">The missing restrictions are assumed to be null (unrestricted).</span></span>  
  
 <span data-ttu-id="afcea-132">您可以查詢.NET Framework managed 提供者以決定支援的限制清單，藉由呼叫**GetSchema**方法具有限制結構描述集合，也就是 「 限制 」 的名稱。</span><span class="sxs-lookup"><span data-stu-id="afcea-132">You can query a .NET Framework managed provider to determine the list of supported restrictions by calling the **GetSchema** method with the name of the restrictions schema collection, which is "Restrictions".</span></span> <span data-ttu-id="afcea-133">這將傳回 <xref:System.Data.DataTable>，其包含集合名稱、限制名稱、預設限制值及限制號碼的清單。</span><span class="sxs-lookup"><span data-stu-id="afcea-133">This will return a <xref:System.Data.DataTable> with a list of the collection names, the restriction names, the default restriction values, and the restriction numbers.</span></span>  
  
### <a name="example"></a><span data-ttu-id="afcea-134">範例</span><span class="sxs-lookup"><span data-stu-id="afcea-134">Example</span></span>  
 <span data-ttu-id="afcea-135">下列範例示範如何使用<xref:System.Data.SqlClient.SqlConnection.GetSchema%2A>方法的.NET Framework Data Provider for SQL Server<xref:System.Data.SqlClient.SqlConnection>類別來擷取所有所包含的資料表結構描述資訊**AdventureWorks**範例資料庫，以及限制的資訊傳回至只有"Sales"結構描述中的資料表：</span><span class="sxs-lookup"><span data-stu-id="afcea-135">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database, and to restrict the information returned to only those tables in the "Sales" schema:</span></span>  
  
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
  
## <a name="sql-server-schema-restrictions"></a><span data-ttu-id="afcea-136">SQL Server 結構描述限制</span><span class="sxs-lookup"><span data-stu-id="afcea-136">SQL Server Schema Restrictions</span></span>  
 <span data-ttu-id="afcea-137">下表將列出 SQL Server 結構描述集合的限制。</span><span class="sxs-lookup"><span data-stu-id="afcea-137">The following tables list the restrictions for SQL Server schema collections.</span></span>  
  
### <a name="users"></a><span data-ttu-id="afcea-138">使用者</span><span class="sxs-lookup"><span data-stu-id="afcea-138">Users</span></span>  
  
|<span data-ttu-id="afcea-139">限制名稱</span><span class="sxs-lookup"><span data-stu-id="afcea-139">Restriction Name</span></span>|<span data-ttu-id="afcea-140">參數名稱</span><span class="sxs-lookup"><span data-stu-id="afcea-140">Parameter Name</span></span>|<span data-ttu-id="afcea-141">預設限制值</span><span class="sxs-lookup"><span data-stu-id="afcea-141">Restriction Default</span></span>|<span data-ttu-id="afcea-142">限制號碼</span><span class="sxs-lookup"><span data-stu-id="afcea-142">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="afcea-143">User_Name</span><span class="sxs-lookup"><span data-stu-id="afcea-143">User_Name</span></span>|@Name|<span data-ttu-id="afcea-144">name</span><span class="sxs-lookup"><span data-stu-id="afcea-144">name</span></span>|<span data-ttu-id="afcea-145">1</span><span class="sxs-lookup"><span data-stu-id="afcea-145">1</span></span>|  
  
### <a name="databases"></a><span data-ttu-id="afcea-146">資料庫</span><span class="sxs-lookup"><span data-stu-id="afcea-146">Databases</span></span>  
  
|<span data-ttu-id="afcea-147">限制名稱</span><span class="sxs-lookup"><span data-stu-id="afcea-147">Restriction Name</span></span>|<span data-ttu-id="afcea-148">參數名稱</span><span class="sxs-lookup"><span data-stu-id="afcea-148">Parameter Name</span></span>|<span data-ttu-id="afcea-149">預設限制值</span><span class="sxs-lookup"><span data-stu-id="afcea-149">Restriction Default</span></span>|<span data-ttu-id="afcea-150">限制號碼</span><span class="sxs-lookup"><span data-stu-id="afcea-150">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="afcea-151">名稱</span><span class="sxs-lookup"><span data-stu-id="afcea-151">Name</span></span>|@Name|<span data-ttu-id="afcea-152">名稱</span><span class="sxs-lookup"><span data-stu-id="afcea-152">Name</span></span>|<span data-ttu-id="afcea-153">1</span><span class="sxs-lookup"><span data-stu-id="afcea-153">1</span></span>|  
  
### <a name="tables"></a><span data-ttu-id="afcea-154">資料表</span><span class="sxs-lookup"><span data-stu-id="afcea-154">Tables</span></span>  
  
|<span data-ttu-id="afcea-155">限制名稱</span><span class="sxs-lookup"><span data-stu-id="afcea-155">Restriction Name</span></span>|<span data-ttu-id="afcea-156">參數名稱</span><span class="sxs-lookup"><span data-stu-id="afcea-156">Parameter Name</span></span>|<span data-ttu-id="afcea-157">預設限制值</span><span class="sxs-lookup"><span data-stu-id="afcea-157">Restriction Default</span></span>|<span data-ttu-id="afcea-158">限制號碼</span><span class="sxs-lookup"><span data-stu-id="afcea-158">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="afcea-159">Catalog</span><span class="sxs-lookup"><span data-stu-id="afcea-159">Catalog</span></span>|@Catalog|<span data-ttu-id="afcea-160">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="afcea-160">TABLE_CATALOG</span></span>|<span data-ttu-id="afcea-161">1</span><span class="sxs-lookup"><span data-stu-id="afcea-161">1</span></span>|  
|<span data-ttu-id="afcea-162">Owner</span><span class="sxs-lookup"><span data-stu-id="afcea-162">Owner</span></span>|@Owner|<span data-ttu-id="afcea-163">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="afcea-163">TABLE_SCHEMA</span></span>|<span data-ttu-id="afcea-164">2</span><span class="sxs-lookup"><span data-stu-id="afcea-164">2</span></span>|  
|<span data-ttu-id="afcea-165">資料表</span><span class="sxs-lookup"><span data-stu-id="afcea-165">Table</span></span>|@Name|<span data-ttu-id="afcea-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="afcea-166">TABLE_NAME</span></span>|<span data-ttu-id="afcea-167">3</span><span class="sxs-lookup"><span data-stu-id="afcea-167">3</span></span>|  
|<span data-ttu-id="afcea-168">TableType</span><span class="sxs-lookup"><span data-stu-id="afcea-168">TableType</span></span>|@TableType|<span data-ttu-id="afcea-169">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="afcea-169">TABLE_TYPE</span></span>|<span data-ttu-id="afcea-170">4</span><span class="sxs-lookup"><span data-stu-id="afcea-170">4</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="afcea-171">資料行</span><span class="sxs-lookup"><span data-stu-id="afcea-171">Columns</span></span>  
  
|<span data-ttu-id="afcea-172">限制名稱</span><span class="sxs-lookup"><span data-stu-id="afcea-172">Restriction Name</span></span>|<span data-ttu-id="afcea-173">參數名稱</span><span class="sxs-lookup"><span data-stu-id="afcea-173">Parameter Name</span></span>|<span data-ttu-id="afcea-174">預設限制值</span><span class="sxs-lookup"><span data-stu-id="afcea-174">Restriction Default</span></span>|<span data-ttu-id="afcea-175">限制號碼</span><span class="sxs-lookup"><span data-stu-id="afcea-175">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="afcea-176">Catalog</span><span class="sxs-lookup"><span data-stu-id="afcea-176">Catalog</span></span>|@Catalog|<span data-ttu-id="afcea-177">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="afcea-177">TABLE_CATALOG</span></span>|<span data-ttu-id="afcea-178">1</span><span class="sxs-lookup"><span data-stu-id="afcea-178">1</span></span>|  
|<span data-ttu-id="afcea-179">Owner</span><span class="sxs-lookup"><span data-stu-id="afcea-179">Owner</span></span>|@Owner|<span data-ttu-id="afcea-180">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="afcea-180">TABLE_SCHEMA</span></span>|<span data-ttu-id="afcea-181">2</span><span class="sxs-lookup"><span data-stu-id="afcea-181">2</span></span>|  
|<span data-ttu-id="afcea-182">資料表</span><span class="sxs-lookup"><span data-stu-id="afcea-182">Table</span></span>|@Table|<span data-ttu-id="afcea-183">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="afcea-183">TABLE_NAME</span></span>|<span data-ttu-id="afcea-184">3</span><span class="sxs-lookup"><span data-stu-id="afcea-184">3</span></span>|  
|<span data-ttu-id="afcea-185">資料行</span><span class="sxs-lookup"><span data-stu-id="afcea-185">Column</span></span>|@Column|<span data-ttu-id="afcea-186">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="afcea-186">COLUMN_NAME</span></span>|<span data-ttu-id="afcea-187">4</span><span class="sxs-lookup"><span data-stu-id="afcea-187">4</span></span>|  
  
### <a name="structuredtypemembers"></a><span data-ttu-id="afcea-188">StructuredTypeMembers</span><span class="sxs-lookup"><span data-stu-id="afcea-188">StructuredTypeMembers</span></span>  
  
|<span data-ttu-id="afcea-189">限制名稱</span><span class="sxs-lookup"><span data-stu-id="afcea-189">Restriction Name</span></span>|<span data-ttu-id="afcea-190">參數名稱</span><span class="sxs-lookup"><span data-stu-id="afcea-190">Parameter Name</span></span>|<span data-ttu-id="afcea-191">預設限制值</span><span class="sxs-lookup"><span data-stu-id="afcea-191">Restriction Default</span></span>|<span data-ttu-id="afcea-192">限制號碼</span><span class="sxs-lookup"><span data-stu-id="afcea-192">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="afcea-193">Catalog</span><span class="sxs-lookup"><span data-stu-id="afcea-193">Catalog</span></span>|@Catalog|<span data-ttu-id="afcea-194">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="afcea-194">TABLE_CATALOG</span></span>|<span data-ttu-id="afcea-195">1</span><span class="sxs-lookup"><span data-stu-id="afcea-195">1</span></span>|  
|<span data-ttu-id="afcea-196">Owner</span><span class="sxs-lookup"><span data-stu-id="afcea-196">Owner</span></span>|@Owner|<span data-ttu-id="afcea-197">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="afcea-197">TABLE_SCHEMA</span></span>|<span data-ttu-id="afcea-198">2</span><span class="sxs-lookup"><span data-stu-id="afcea-198">2</span></span>|  
|<span data-ttu-id="afcea-199">資料表</span><span class="sxs-lookup"><span data-stu-id="afcea-199">Table</span></span>|@Table|<span data-ttu-id="afcea-200">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="afcea-200">TABLE_NAME</span></span>|<span data-ttu-id="afcea-201">3</span><span class="sxs-lookup"><span data-stu-id="afcea-201">3</span></span>|  
|<span data-ttu-id="afcea-202">資料行</span><span class="sxs-lookup"><span data-stu-id="afcea-202">Column</span></span>|@Column|<span data-ttu-id="afcea-203">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="afcea-203">COLUMN_NAME</span></span>|<span data-ttu-id="afcea-204">4</span><span class="sxs-lookup"><span data-stu-id="afcea-204">4</span></span>|  
  
### <a name="views"></a><span data-ttu-id="afcea-205">檢視</span><span class="sxs-lookup"><span data-stu-id="afcea-205">Views</span></span>  
  
|<span data-ttu-id="afcea-206">限制名稱</span><span class="sxs-lookup"><span data-stu-id="afcea-206">Restriction Name</span></span>|<span data-ttu-id="afcea-207">參數名稱</span><span class="sxs-lookup"><span data-stu-id="afcea-207">Parameter Name</span></span>|<span data-ttu-id="afcea-208">預設限制值</span><span class="sxs-lookup"><span data-stu-id="afcea-208">Restriction Default</span></span>|<span data-ttu-id="afcea-209">限制號碼</span><span class="sxs-lookup"><span data-stu-id="afcea-209">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="afcea-210">Catalog</span><span class="sxs-lookup"><span data-stu-id="afcea-210">Catalog</span></span>|@Catalog|<span data-ttu-id="afcea-211">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="afcea-211">TABLE_CATALOG</span></span>|<span data-ttu-id="afcea-212">1</span><span class="sxs-lookup"><span data-stu-id="afcea-212">1</span></span>|  
|<span data-ttu-id="afcea-213">Owner</span><span class="sxs-lookup"><span data-stu-id="afcea-213">Owner</span></span>|@Owner|<span data-ttu-id="afcea-214">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="afcea-214">TABLE_SCHEMA</span></span>|<span data-ttu-id="afcea-215">2</span><span class="sxs-lookup"><span data-stu-id="afcea-215">2</span></span>|  
|<span data-ttu-id="afcea-216">資料表</span><span class="sxs-lookup"><span data-stu-id="afcea-216">Table</span></span>|@Table|<span data-ttu-id="afcea-217">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="afcea-217">TABLE_NAME</span></span>|<span data-ttu-id="afcea-218">3</span><span class="sxs-lookup"><span data-stu-id="afcea-218">3</span></span>|  
  
### <a name="viewcolumns"></a><span data-ttu-id="afcea-219">ViewColumns</span><span class="sxs-lookup"><span data-stu-id="afcea-219">ViewColumns</span></span>  
  
|<span data-ttu-id="afcea-220">限制名稱</span><span class="sxs-lookup"><span data-stu-id="afcea-220">Restriction Name</span></span>|<span data-ttu-id="afcea-221">參數名稱</span><span class="sxs-lookup"><span data-stu-id="afcea-221">Parameter Name</span></span>|<span data-ttu-id="afcea-222">預設限制值</span><span class="sxs-lookup"><span data-stu-id="afcea-222">Restriction Default</span></span>|<span data-ttu-id="afcea-223">限制號碼</span><span class="sxs-lookup"><span data-stu-id="afcea-223">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="afcea-224">Catalog</span><span class="sxs-lookup"><span data-stu-id="afcea-224">Catalog</span></span>|@Catalog|<span data-ttu-id="afcea-225">VIEW_CATALOG</span><span class="sxs-lookup"><span data-stu-id="afcea-225">VIEW_CATALOG</span></span>|<span data-ttu-id="afcea-226">1</span><span class="sxs-lookup"><span data-stu-id="afcea-226">1</span></span>|  
|<span data-ttu-id="afcea-227">Owner</span><span class="sxs-lookup"><span data-stu-id="afcea-227">Owner</span></span>|@Owner|<span data-ttu-id="afcea-228">VIEW_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="afcea-228">VIEW_SCHEMA</span></span>|<span data-ttu-id="afcea-229">2</span><span class="sxs-lookup"><span data-stu-id="afcea-229">2</span></span>|  
|<span data-ttu-id="afcea-230">資料表</span><span class="sxs-lookup"><span data-stu-id="afcea-230">Table</span></span>|@Table|<span data-ttu-id="afcea-231">VIEW_NAME</span><span class="sxs-lookup"><span data-stu-id="afcea-231">VIEW_NAME</span></span>|<span data-ttu-id="afcea-232">3</span><span class="sxs-lookup"><span data-stu-id="afcea-232">3</span></span>|  
|<span data-ttu-id="afcea-233">資料行</span><span class="sxs-lookup"><span data-stu-id="afcea-233">Column</span></span>|@Column|<span data-ttu-id="afcea-234">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="afcea-234">COLUMN_NAME</span></span>|<span data-ttu-id="afcea-235">4</span><span class="sxs-lookup"><span data-stu-id="afcea-235">4</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="afcea-236">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="afcea-236">ProcedureParameters</span></span>  
  
|<span data-ttu-id="afcea-237">限制名稱</span><span class="sxs-lookup"><span data-stu-id="afcea-237">Restriction Name</span></span>|<span data-ttu-id="afcea-238">參數名稱</span><span class="sxs-lookup"><span data-stu-id="afcea-238">Parameter Name</span></span>|<span data-ttu-id="afcea-239">預設限制值</span><span class="sxs-lookup"><span data-stu-id="afcea-239">Restriction Default</span></span>|<span data-ttu-id="afcea-240">限制號碼</span><span class="sxs-lookup"><span data-stu-id="afcea-240">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="afcea-241">Catalog</span><span class="sxs-lookup"><span data-stu-id="afcea-241">Catalog</span></span>|@Catalog|<span data-ttu-id="afcea-242">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="afcea-242">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="afcea-243">1</span><span class="sxs-lookup"><span data-stu-id="afcea-243">1</span></span>|  
|<span data-ttu-id="afcea-244">Owner</span><span class="sxs-lookup"><span data-stu-id="afcea-244">Owner</span></span>|@Owner|<span data-ttu-id="afcea-245">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="afcea-245">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="afcea-246">2</span><span class="sxs-lookup"><span data-stu-id="afcea-246">2</span></span>|  
|<span data-ttu-id="afcea-247">名稱</span><span class="sxs-lookup"><span data-stu-id="afcea-247">Name</span></span>|@Name|<span data-ttu-id="afcea-248">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="afcea-248">SPECIFIC_NAME</span></span>|<span data-ttu-id="afcea-249">3</span><span class="sxs-lookup"><span data-stu-id="afcea-249">3</span></span>|  
|<span data-ttu-id="afcea-250">參數</span><span class="sxs-lookup"><span data-stu-id="afcea-250">Parameter</span></span>|@Parameter|<span data-ttu-id="afcea-251">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="afcea-251">PARAMETER_NAME</span></span>|<span data-ttu-id="afcea-252">4</span><span class="sxs-lookup"><span data-stu-id="afcea-252">4</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="afcea-253">程序</span><span class="sxs-lookup"><span data-stu-id="afcea-253">Procedures</span></span>  
  
|<span data-ttu-id="afcea-254">限制名稱</span><span class="sxs-lookup"><span data-stu-id="afcea-254">Restriction Name</span></span>|<span data-ttu-id="afcea-255">參數名稱</span><span class="sxs-lookup"><span data-stu-id="afcea-255">Parameter Name</span></span>|<span data-ttu-id="afcea-256">預設限制值</span><span class="sxs-lookup"><span data-stu-id="afcea-256">Restriction Default</span></span>|<span data-ttu-id="afcea-257">限制號碼</span><span class="sxs-lookup"><span data-stu-id="afcea-257">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="afcea-258">Catalog</span><span class="sxs-lookup"><span data-stu-id="afcea-258">Catalog</span></span>|@Catalog|<span data-ttu-id="afcea-259">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="afcea-259">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="afcea-260">1</span><span class="sxs-lookup"><span data-stu-id="afcea-260">1</span></span>|  
|<span data-ttu-id="afcea-261">Owner</span><span class="sxs-lookup"><span data-stu-id="afcea-261">Owner</span></span>|@Owner|<span data-ttu-id="afcea-262">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="afcea-262">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="afcea-263">2</span><span class="sxs-lookup"><span data-stu-id="afcea-263">2</span></span>|  
|<span data-ttu-id="afcea-264">名稱</span><span class="sxs-lookup"><span data-stu-id="afcea-264">Name</span></span>|@Name|<span data-ttu-id="afcea-265">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="afcea-265">SPECIFIC_NAME</span></span>|<span data-ttu-id="afcea-266">3</span><span class="sxs-lookup"><span data-stu-id="afcea-266">3</span></span>|  
|<span data-ttu-id="afcea-267">類型</span><span class="sxs-lookup"><span data-stu-id="afcea-267">Type</span></span>|@Type|<span data-ttu-id="afcea-268">ROUTINE_TYPE</span><span class="sxs-lookup"><span data-stu-id="afcea-268">ROUTINE_TYPE</span></span>|<span data-ttu-id="afcea-269">4</span><span class="sxs-lookup"><span data-stu-id="afcea-269">4</span></span>|  
  
### <a name="indexcolumns"></a><span data-ttu-id="afcea-270">IndexColumns</span><span class="sxs-lookup"><span data-stu-id="afcea-270">IndexColumns</span></span>  
  
|<span data-ttu-id="afcea-271">限制名稱</span><span class="sxs-lookup"><span data-stu-id="afcea-271">Restriction Name</span></span>|<span data-ttu-id="afcea-272">參數名稱</span><span class="sxs-lookup"><span data-stu-id="afcea-272">Parameter Name</span></span>|<span data-ttu-id="afcea-273">預設限制值</span><span class="sxs-lookup"><span data-stu-id="afcea-273">Restriction Default</span></span>|<span data-ttu-id="afcea-274">限制號碼</span><span class="sxs-lookup"><span data-stu-id="afcea-274">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="afcea-275">Catalog</span><span class="sxs-lookup"><span data-stu-id="afcea-275">Catalog</span></span>|@Catalog|<span data-ttu-id="afcea-276">db_name()</span><span class="sxs-lookup"><span data-stu-id="afcea-276">db_name()</span></span>|<span data-ttu-id="afcea-277">1</span><span class="sxs-lookup"><span data-stu-id="afcea-277">1</span></span>|  
|<span data-ttu-id="afcea-278">Owner</span><span class="sxs-lookup"><span data-stu-id="afcea-278">Owner</span></span>|@Owner|<span data-ttu-id="afcea-279">user_name()</span><span class="sxs-lookup"><span data-stu-id="afcea-279">user_name()</span></span>|<span data-ttu-id="afcea-280">2</span><span class="sxs-lookup"><span data-stu-id="afcea-280">2</span></span>|  
|<span data-ttu-id="afcea-281">資料表</span><span class="sxs-lookup"><span data-stu-id="afcea-281">Table</span></span>|@Table|<span data-ttu-id="afcea-282">o.name</span><span class="sxs-lookup"><span data-stu-id="afcea-282">o.name</span></span>|<span data-ttu-id="afcea-283">3</span><span class="sxs-lookup"><span data-stu-id="afcea-283">3</span></span>|  
|<span data-ttu-id="afcea-284">ConstraintName</span><span class="sxs-lookup"><span data-stu-id="afcea-284">ConstraintName</span></span>|@ConstraintName|<span data-ttu-id="afcea-285">x.name</span><span class="sxs-lookup"><span data-stu-id="afcea-285">x.name</span></span>|<span data-ttu-id="afcea-286">4</span><span class="sxs-lookup"><span data-stu-id="afcea-286">4</span></span>|  
|<span data-ttu-id="afcea-287">資料行</span><span class="sxs-lookup"><span data-stu-id="afcea-287">Column</span></span>|@Column|<span data-ttu-id="afcea-288">c.name</span><span class="sxs-lookup"><span data-stu-id="afcea-288">c.name</span></span>|<span data-ttu-id="afcea-289">5</span><span class="sxs-lookup"><span data-stu-id="afcea-289">5</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="afcea-290">Indexes</span><span class="sxs-lookup"><span data-stu-id="afcea-290">Indexes</span></span>  
  
|<span data-ttu-id="afcea-291">限制名稱</span><span class="sxs-lookup"><span data-stu-id="afcea-291">Restriction Name</span></span>|<span data-ttu-id="afcea-292">參數名稱</span><span class="sxs-lookup"><span data-stu-id="afcea-292">Parameter Name</span></span>|<span data-ttu-id="afcea-293">預設限制值</span><span class="sxs-lookup"><span data-stu-id="afcea-293">Restriction Default</span></span>|<span data-ttu-id="afcea-294">限制號碼</span><span class="sxs-lookup"><span data-stu-id="afcea-294">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="afcea-295">Catalog</span><span class="sxs-lookup"><span data-stu-id="afcea-295">Catalog</span></span>|@Catalog|<span data-ttu-id="afcea-296">db_name()</span><span class="sxs-lookup"><span data-stu-id="afcea-296">db_name()</span></span>|<span data-ttu-id="afcea-297">1</span><span class="sxs-lookup"><span data-stu-id="afcea-297">1</span></span>|  
|<span data-ttu-id="afcea-298">Owner</span><span class="sxs-lookup"><span data-stu-id="afcea-298">Owner</span></span>|@Owner|<span data-ttu-id="afcea-299">user_name()</span><span class="sxs-lookup"><span data-stu-id="afcea-299">user_name()</span></span>|<span data-ttu-id="afcea-300">2</span><span class="sxs-lookup"><span data-stu-id="afcea-300">2</span></span>|  
|<span data-ttu-id="afcea-301">資料表</span><span class="sxs-lookup"><span data-stu-id="afcea-301">Table</span></span>|@Table|<span data-ttu-id="afcea-302">o.name</span><span class="sxs-lookup"><span data-stu-id="afcea-302">o.name</span></span>|<span data-ttu-id="afcea-303">3</span><span class="sxs-lookup"><span data-stu-id="afcea-303">3</span></span>|  
  
### <a name="userdefinedtypes"></a><span data-ttu-id="afcea-304">UserDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="afcea-304">UserDefinedTypes</span></span>  
  
|<span data-ttu-id="afcea-305">限制名稱</span><span class="sxs-lookup"><span data-stu-id="afcea-305">Restriction Name</span></span>|<span data-ttu-id="afcea-306">參數名稱</span><span class="sxs-lookup"><span data-stu-id="afcea-306">Parameter Name</span></span>|<span data-ttu-id="afcea-307">預設限制值</span><span class="sxs-lookup"><span data-stu-id="afcea-307">Restriction Default</span></span>|<span data-ttu-id="afcea-308">限制號碼</span><span class="sxs-lookup"><span data-stu-id="afcea-308">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="afcea-309">assembly_name</span><span class="sxs-lookup"><span data-stu-id="afcea-309">assembly_name</span></span>|@AssemblyName|<span data-ttu-id="afcea-310">assemblies.name</span><span class="sxs-lookup"><span data-stu-id="afcea-310">assemblies.name</span></span>|<span data-ttu-id="afcea-311">1</span><span class="sxs-lookup"><span data-stu-id="afcea-311">1</span></span>|  
|<span data-ttu-id="afcea-312">udt_name</span><span class="sxs-lookup"><span data-stu-id="afcea-312">udt_name</span></span>|@UDTName|<span data-ttu-id="afcea-313">types.assembly_class</span><span class="sxs-lookup"><span data-stu-id="afcea-313">types.assembly_class</span></span>|<span data-ttu-id="afcea-314">2</span><span class="sxs-lookup"><span data-stu-id="afcea-314">2</span></span>|  
  
### <a name="foreignkeys"></a><span data-ttu-id="afcea-315">ForeignKeys</span><span class="sxs-lookup"><span data-stu-id="afcea-315">ForeignKeys</span></span>  
  
|<span data-ttu-id="afcea-316">限制名稱</span><span class="sxs-lookup"><span data-stu-id="afcea-316">Restriction Name</span></span>|<span data-ttu-id="afcea-317">參數名稱</span><span class="sxs-lookup"><span data-stu-id="afcea-317">Parameter Name</span></span>|<span data-ttu-id="afcea-318">預設限制值</span><span class="sxs-lookup"><span data-stu-id="afcea-318">Restriction Default</span></span>|<span data-ttu-id="afcea-319">限制號碼</span><span class="sxs-lookup"><span data-stu-id="afcea-319">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="afcea-320">Catalog</span><span class="sxs-lookup"><span data-stu-id="afcea-320">Catalog</span></span>|@Catalog|<span data-ttu-id="afcea-321">CONSTRAINT_CATALOG</span><span class="sxs-lookup"><span data-stu-id="afcea-321">CONSTRAINT_CATALOG</span></span>|<span data-ttu-id="afcea-322">1</span><span class="sxs-lookup"><span data-stu-id="afcea-322">1</span></span>|  
|<span data-ttu-id="afcea-323">Owner</span><span class="sxs-lookup"><span data-stu-id="afcea-323">Owner</span></span>|@Owner|<span data-ttu-id="afcea-324">CONSTRAINT_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="afcea-324">CONSTRAINT_SCHEMA</span></span>|<span data-ttu-id="afcea-325">2</span><span class="sxs-lookup"><span data-stu-id="afcea-325">2</span></span>|  
|<span data-ttu-id="afcea-326">資料表</span><span class="sxs-lookup"><span data-stu-id="afcea-326">Table</span></span>|@Table|<span data-ttu-id="afcea-327">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="afcea-327">TABLE_NAME</span></span>|<span data-ttu-id="afcea-328">3</span><span class="sxs-lookup"><span data-stu-id="afcea-328">3</span></span>|  
|<span data-ttu-id="afcea-329">名稱</span><span class="sxs-lookup"><span data-stu-id="afcea-329">Name</span></span>|@Name|<span data-ttu-id="afcea-330">CONSTRAINT_NAME</span><span class="sxs-lookup"><span data-stu-id="afcea-330">CONSTRAINT_NAME</span></span>|<span data-ttu-id="afcea-331">4</span><span class="sxs-lookup"><span data-stu-id="afcea-331">4</span></span>|  
  
## <a name="sql-server-2008-schema-restrictions"></a><span data-ttu-id="afcea-332">SQL Server 2008 結構描述限制</span><span class="sxs-lookup"><span data-stu-id="afcea-332">SQL Server 2008 Schema Restrictions</span></span>  
 <span data-ttu-id="afcea-333">下表將列出 SQL Server 2008 結構描述集合的限制。</span><span class="sxs-lookup"><span data-stu-id="afcea-333">The following tables list the restrictions for SQL Server 2008 schema collections.</span></span> <span data-ttu-id="afcea-334">從 .NET Framework 3.5 版 SP1 和 SQL Server 2008 開始，這些限制便有效。</span><span class="sxs-lookup"><span data-stu-id="afcea-334">These restrictions are valid beginning with version 3.5 SP1 of the .NET Framework and SQL Server 2008.</span></span> <span data-ttu-id="afcea-335">舊版 .NET Framework 和 SQL Server 不支援它們。</span><span class="sxs-lookup"><span data-stu-id="afcea-335">They are not supported in earlier versions of the .NET Framework and SQL Server.</span></span>  
  
### <a name="columnsetcolumns"></a><span data-ttu-id="afcea-336">ColumnSetColumns</span><span class="sxs-lookup"><span data-stu-id="afcea-336">ColumnSetColumns</span></span>  
  
|<span data-ttu-id="afcea-337">限制名稱</span><span class="sxs-lookup"><span data-stu-id="afcea-337">Restriction Name</span></span>|<span data-ttu-id="afcea-338">參數名稱</span><span class="sxs-lookup"><span data-stu-id="afcea-338">Parameter Name</span></span>|<span data-ttu-id="afcea-339">預設限制值</span><span class="sxs-lookup"><span data-stu-id="afcea-339">Restriction Default</span></span>|<span data-ttu-id="afcea-340">限制號碼</span><span class="sxs-lookup"><span data-stu-id="afcea-340">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="afcea-341">Catalog</span><span class="sxs-lookup"><span data-stu-id="afcea-341">Catalog</span></span>|@Catalog|<span data-ttu-id="afcea-342">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="afcea-342">TABLE_CATALOG</span></span>|<span data-ttu-id="afcea-343">1</span><span class="sxs-lookup"><span data-stu-id="afcea-343">1</span></span>|  
|<span data-ttu-id="afcea-344">Owner</span><span class="sxs-lookup"><span data-stu-id="afcea-344">Owner</span></span>|@Owner|<span data-ttu-id="afcea-345">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="afcea-345">TABLE_SCHEMA</span></span>|<span data-ttu-id="afcea-346">2</span><span class="sxs-lookup"><span data-stu-id="afcea-346">2</span></span>|  
|<span data-ttu-id="afcea-347">資料表</span><span class="sxs-lookup"><span data-stu-id="afcea-347">Table</span></span>|@Table|<span data-ttu-id="afcea-348">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="afcea-348">TABLE_NAME</span></span>|<span data-ttu-id="afcea-349">3</span><span class="sxs-lookup"><span data-stu-id="afcea-349">3</span></span>|  
  
### <a name="allcolumns"></a><span data-ttu-id="afcea-350">AllColumns</span><span class="sxs-lookup"><span data-stu-id="afcea-350">AllColumns</span></span>  
  
|<span data-ttu-id="afcea-351">限制名稱</span><span class="sxs-lookup"><span data-stu-id="afcea-351">Restriction Name</span></span>|<span data-ttu-id="afcea-352">參數名稱</span><span class="sxs-lookup"><span data-stu-id="afcea-352">Parameter Name</span></span>|<span data-ttu-id="afcea-353">預設限制值</span><span class="sxs-lookup"><span data-stu-id="afcea-353">Restriction Default</span></span>|<span data-ttu-id="afcea-354">限制號碼</span><span class="sxs-lookup"><span data-stu-id="afcea-354">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="afcea-355">Catalog</span><span class="sxs-lookup"><span data-stu-id="afcea-355">Catalog</span></span>|@Catalog|<span data-ttu-id="afcea-356">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="afcea-356">TABLE_CATALOG</span></span>|<span data-ttu-id="afcea-357">1</span><span class="sxs-lookup"><span data-stu-id="afcea-357">1</span></span>|  
|<span data-ttu-id="afcea-358">Owner</span><span class="sxs-lookup"><span data-stu-id="afcea-358">Owner</span></span>|@Owner|<span data-ttu-id="afcea-359">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="afcea-359">TABLE_SCHEMA</span></span>|<span data-ttu-id="afcea-360">2</span><span class="sxs-lookup"><span data-stu-id="afcea-360">2</span></span>|  
|<span data-ttu-id="afcea-361">資料表</span><span class="sxs-lookup"><span data-stu-id="afcea-361">Table</span></span>|@Table|<span data-ttu-id="afcea-362">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="afcea-362">TABLE_NAME</span></span>|<span data-ttu-id="afcea-363">3</span><span class="sxs-lookup"><span data-stu-id="afcea-363">3</span></span>|  
|<span data-ttu-id="afcea-364">資料行</span><span class="sxs-lookup"><span data-stu-id="afcea-364">Column</span></span>|@Column|<span data-ttu-id="afcea-365">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="afcea-365">COLUMN_NAME</span></span>|<span data-ttu-id="afcea-366">4</span><span class="sxs-lookup"><span data-stu-id="afcea-366">4</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="afcea-367">請參閱</span><span class="sxs-lookup"><span data-stu-id="afcea-367">See Also</span></span>  
 [<span data-ttu-id="afcea-368">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="afcea-368">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
