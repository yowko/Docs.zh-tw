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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c254865800694af8eb754c3e8d4072688fd7e89a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="schema-restrictions"></a><span data-ttu-id="b1779-102">結構描述限制</span><span class="sxs-lookup"><span data-stu-id="b1779-102">Schema Restrictions</span></span>
<span data-ttu-id="b1779-103">第二個選擇性參數**GetSchema**方法會傳回用來限制的結構描述資訊量的限制，並將它傳遞至**GetSchema**方法的字串陣列.</span><span class="sxs-lookup"><span data-stu-id="b1779-103">The second optional parameter of the **GetSchema** method is the restrictions that are used to limit the amount of schema information returned, and it is passed to the **GetSchema** method as an array of strings.</span></span> <span data-ttu-id="b1779-104">陣列中的位置決定您可以傳遞的值，它相當於限制號碼。</span><span class="sxs-lookup"><span data-stu-id="b1779-104">The position in the array determines the values that you can pass, and this is equivalent to the restriction number.</span></span>  
  
 <span data-ttu-id="b1779-105">例如，下表說明使用 .NET Framework Data Provider for SQL Server 之 "Tables" 結構描述集合所支援的限制。</span><span class="sxs-lookup"><span data-stu-id="b1779-105">For example, the following table describes the restrictions supported by the "Tables" schema collection using the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="b1779-106">SQL Server 結構描述集合的其他限制將列於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="b1779-106">Additional restrictions for SQL Server schema collections are listed at the end of this topic.</span></span>  
  
|<span data-ttu-id="b1779-107">限制名稱</span><span class="sxs-lookup"><span data-stu-id="b1779-107">Restriction Name</span></span>|<span data-ttu-id="b1779-108">參數名稱</span><span class="sxs-lookup"><span data-stu-id="b1779-108">Parameter Name</span></span>|<span data-ttu-id="b1779-109">預設限制值</span><span class="sxs-lookup"><span data-stu-id="b1779-109">Restriction Default</span></span>|<span data-ttu-id="b1779-110">限制號碼</span><span class="sxs-lookup"><span data-stu-id="b1779-110">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="b1779-111">Catalog</span><span class="sxs-lookup"><span data-stu-id="b1779-111">Catalog</span></span>|@Catalog|<span data-ttu-id="b1779-112">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1779-112">TABLE_CATALOG</span></span>|<span data-ttu-id="b1779-113">1</span><span class="sxs-lookup"><span data-stu-id="b1779-113">1</span></span>|  
|<span data-ttu-id="b1779-114">Owner</span><span class="sxs-lookup"><span data-stu-id="b1779-114">Owner</span></span>|@Owner|<span data-ttu-id="b1779-115">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1779-115">TABLE_SCHEMA</span></span>|<span data-ttu-id="b1779-116">2</span><span class="sxs-lookup"><span data-stu-id="b1779-116">2</span></span>|  
|<span data-ttu-id="b1779-117">資料表</span><span class="sxs-lookup"><span data-stu-id="b1779-117">Table</span></span>|@Name|<span data-ttu-id="b1779-118">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b1779-118">TABLE_NAME</span></span>|<span data-ttu-id="b1779-119">3</span><span class="sxs-lookup"><span data-stu-id="b1779-119">3</span></span>|  
|<span data-ttu-id="b1779-120">TableType</span><span class="sxs-lookup"><span data-stu-id="b1779-120">TableType</span></span>|@TableType|<span data-ttu-id="b1779-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="b1779-121">TABLE_TYPE</span></span>|<span data-ttu-id="b1779-122">4</span><span class="sxs-lookup"><span data-stu-id="b1779-122">4</span></span>|  
  
## <a name="specifying-restriction-values"></a><span data-ttu-id="b1779-123">指定限制值</span><span class="sxs-lookup"><span data-stu-id="b1779-123">Specifying Restriction Values</span></span>  
 <span data-ttu-id="b1779-124">若要使用 "Tables" 結構描述集合的其中一個限制，只需使用四個元素建立字串陣列，然後將符合限制數目的值置於元素中。</span><span class="sxs-lookup"><span data-stu-id="b1779-124">To use one of the restrictions of the "Tables" schema collection, simply create an array of strings with four elements, then place a value in the element that matches the restriction number.</span></span> <span data-ttu-id="b1779-125">例如，以限制資料表所傳回**GetSchema**只有"Sales"結構描述中的資料表的方法之前將其傳遞至設定為"Sales"陣列的第二個項目**GetSchema**方法。</span><span class="sxs-lookup"><span data-stu-id="b1779-125">For example, to restrict the tables returned by the **GetSchema** method to only those tables in the "Sales" schema, set the second element of the array to "Sales" before passing it to the **GetSchema** method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b1779-126">`SqlClient` 及 `OracleClient` 的限制集合具有其他 `ParameterName` 資料行。</span><span class="sxs-lookup"><span data-stu-id="b1779-126">The restrictions collections for `SqlClient` and `OracleClient` have an additional `ParameterName` column.</span></span> <span data-ttu-id="b1779-127">限制預設值資料行仍存在，用於回溯相容性，但目前會忽略它.</span><span class="sxs-lookup"><span data-stu-id="b1779-127">The restriction default column is still there for backwards compatibility, but is currently ignored.</span></span> <span data-ttu-id="b1779-128">指定限制值時，應使用參數化查詢而不是字串取代，來將 SQL 資料隱碼攻擊的風險減至最小。</span><span class="sxs-lookup"><span data-stu-id="b1779-128">Parameterized queries rather than string replacement should be used to minimize the risk of an SQL injection attack when specifying restriction values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b1779-129">陣列中的項目數目必須少於或等於指定結構描述集合所支援的限制數目，否則將擲回 <xref:System.ArgumentException>。</span><span class="sxs-lookup"><span data-stu-id="b1779-129">The number of elements in the array must be less than or equal to the number of restrictions supported for the specified schema collection else an <xref:System.ArgumentException> will be thrown.</span></span> <span data-ttu-id="b1779-130">可以少於限制的最大數目。</span><span class="sxs-lookup"><span data-stu-id="b1779-130">There can be fewer than the maximum number of restrictions.</span></span> <span data-ttu-id="b1779-131">假設遺漏的限制為 Null (未限制)。</span><span class="sxs-lookup"><span data-stu-id="b1779-131">The missing restrictions are assumed to be null (unrestricted).</span></span>  
  
 <span data-ttu-id="b1779-132">您可以查詢.NET Framework managed 提供者以決定支援的限制清單，藉由呼叫**GetSchema**方法具有限制結構描述集合，也就是 「 限制 」 的名稱。</span><span class="sxs-lookup"><span data-stu-id="b1779-132">You can query a .NET Framework managed provider to determine the list of supported restrictions by calling the **GetSchema** method with the name of the restrictions schema collection, which is "Restrictions".</span></span> <span data-ttu-id="b1779-133">這將傳回 <xref:System.Data.DataTable>，其包含集合名稱、限制名稱、預設限制值及限制號碼的清單。</span><span class="sxs-lookup"><span data-stu-id="b1779-133">This will return a <xref:System.Data.DataTable> with a list of the collection names, the restriction names, the default restriction values, and the restriction numbers.</span></span>  
  
### <a name="example"></a><span data-ttu-id="b1779-134">範例</span><span class="sxs-lookup"><span data-stu-id="b1779-134">Example</span></span>  
 <span data-ttu-id="b1779-135">下列範例示範如何使用<xref:System.Data.SqlClient.SqlConnection.GetSchema%2A>方法的.NET Framework Data Provider for SQL Server<xref:System.Data.SqlClient.SqlConnection>類別來擷取所有所包含的資料表結構描述資訊**AdventureWorks**範例資料庫，以及限制的資訊傳回至只有"Sales"結構描述中的資料表：</span><span class="sxs-lookup"><span data-stu-id="b1779-135">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database, and to restrict the information returned to only those tables in the "Sales" schema:</span></span>  
  
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
  
## <a name="sql-server-schema-restrictions"></a><span data-ttu-id="b1779-136">SQL Server 結構描述限制</span><span class="sxs-lookup"><span data-stu-id="b1779-136">SQL Server Schema Restrictions</span></span>  
 <span data-ttu-id="b1779-137">下表將列出 SQL Server 結構描述集合的限制。</span><span class="sxs-lookup"><span data-stu-id="b1779-137">The following tables list the restrictions for SQL Server schema collections.</span></span>  
  
### <a name="users"></a><span data-ttu-id="b1779-138">使用者</span><span class="sxs-lookup"><span data-stu-id="b1779-138">Users</span></span>  
  
|<span data-ttu-id="b1779-139">限制名稱</span><span class="sxs-lookup"><span data-stu-id="b1779-139">Restriction Name</span></span>|<span data-ttu-id="b1779-140">參數名稱</span><span class="sxs-lookup"><span data-stu-id="b1779-140">Parameter Name</span></span>|<span data-ttu-id="b1779-141">預設限制值</span><span class="sxs-lookup"><span data-stu-id="b1779-141">Restriction Default</span></span>|<span data-ttu-id="b1779-142">限制號碼</span><span class="sxs-lookup"><span data-stu-id="b1779-142">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="b1779-143">User_Name</span><span class="sxs-lookup"><span data-stu-id="b1779-143">User_Name</span></span>|@Name|<span data-ttu-id="b1779-144">name</span><span class="sxs-lookup"><span data-stu-id="b1779-144">name</span></span>|<span data-ttu-id="b1779-145">1</span><span class="sxs-lookup"><span data-stu-id="b1779-145">1</span></span>|  
  
### <a name="databases"></a><span data-ttu-id="b1779-146">資料庫</span><span class="sxs-lookup"><span data-stu-id="b1779-146">Databases</span></span>  
  
|<span data-ttu-id="b1779-147">限制名稱</span><span class="sxs-lookup"><span data-stu-id="b1779-147">Restriction Name</span></span>|<span data-ttu-id="b1779-148">參數名稱</span><span class="sxs-lookup"><span data-stu-id="b1779-148">Parameter Name</span></span>|<span data-ttu-id="b1779-149">預設限制值</span><span class="sxs-lookup"><span data-stu-id="b1779-149">Restriction Default</span></span>|<span data-ttu-id="b1779-150">限制號碼</span><span class="sxs-lookup"><span data-stu-id="b1779-150">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="b1779-151">名稱</span><span class="sxs-lookup"><span data-stu-id="b1779-151">Name</span></span>|@Name|<span data-ttu-id="b1779-152">名稱</span><span class="sxs-lookup"><span data-stu-id="b1779-152">Name</span></span>|<span data-ttu-id="b1779-153">1</span><span class="sxs-lookup"><span data-stu-id="b1779-153">1</span></span>|  
  
### <a name="tables"></a><span data-ttu-id="b1779-154">資料表</span><span class="sxs-lookup"><span data-stu-id="b1779-154">Tables</span></span>  
  
|<span data-ttu-id="b1779-155">限制名稱</span><span class="sxs-lookup"><span data-stu-id="b1779-155">Restriction Name</span></span>|<span data-ttu-id="b1779-156">參數名稱</span><span class="sxs-lookup"><span data-stu-id="b1779-156">Parameter Name</span></span>|<span data-ttu-id="b1779-157">預設限制值</span><span class="sxs-lookup"><span data-stu-id="b1779-157">Restriction Default</span></span>|<span data-ttu-id="b1779-158">限制號碼</span><span class="sxs-lookup"><span data-stu-id="b1779-158">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="b1779-159">Catalog</span><span class="sxs-lookup"><span data-stu-id="b1779-159">Catalog</span></span>|@Catalog|<span data-ttu-id="b1779-160">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1779-160">TABLE_CATALOG</span></span>|<span data-ttu-id="b1779-161">1</span><span class="sxs-lookup"><span data-stu-id="b1779-161">1</span></span>|  
|<span data-ttu-id="b1779-162">Owner</span><span class="sxs-lookup"><span data-stu-id="b1779-162">Owner</span></span>|@Owner|<span data-ttu-id="b1779-163">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1779-163">TABLE_SCHEMA</span></span>|<span data-ttu-id="b1779-164">2</span><span class="sxs-lookup"><span data-stu-id="b1779-164">2</span></span>|  
|<span data-ttu-id="b1779-165">資料表</span><span class="sxs-lookup"><span data-stu-id="b1779-165">Table</span></span>|@Name|<span data-ttu-id="b1779-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b1779-166">TABLE_NAME</span></span>|<span data-ttu-id="b1779-167">3</span><span class="sxs-lookup"><span data-stu-id="b1779-167">3</span></span>|  
|<span data-ttu-id="b1779-168">TableType</span><span class="sxs-lookup"><span data-stu-id="b1779-168">TableType</span></span>|@TableType|<span data-ttu-id="b1779-169">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="b1779-169">TABLE_TYPE</span></span>|<span data-ttu-id="b1779-170">4</span><span class="sxs-lookup"><span data-stu-id="b1779-170">4</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="b1779-171">資料行</span><span class="sxs-lookup"><span data-stu-id="b1779-171">Columns</span></span>  
  
|<span data-ttu-id="b1779-172">限制名稱</span><span class="sxs-lookup"><span data-stu-id="b1779-172">Restriction Name</span></span>|<span data-ttu-id="b1779-173">參數名稱</span><span class="sxs-lookup"><span data-stu-id="b1779-173">Parameter Name</span></span>|<span data-ttu-id="b1779-174">預設限制值</span><span class="sxs-lookup"><span data-stu-id="b1779-174">Restriction Default</span></span>|<span data-ttu-id="b1779-175">限制號碼</span><span class="sxs-lookup"><span data-stu-id="b1779-175">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="b1779-176">Catalog</span><span class="sxs-lookup"><span data-stu-id="b1779-176">Catalog</span></span>|@Catalog|<span data-ttu-id="b1779-177">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1779-177">TABLE_CATALOG</span></span>|<span data-ttu-id="b1779-178">1</span><span class="sxs-lookup"><span data-stu-id="b1779-178">1</span></span>|  
|<span data-ttu-id="b1779-179">Owner</span><span class="sxs-lookup"><span data-stu-id="b1779-179">Owner</span></span>|@Owner|<span data-ttu-id="b1779-180">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1779-180">TABLE_SCHEMA</span></span>|<span data-ttu-id="b1779-181">2</span><span class="sxs-lookup"><span data-stu-id="b1779-181">2</span></span>|  
|<span data-ttu-id="b1779-182">資料表</span><span class="sxs-lookup"><span data-stu-id="b1779-182">Table</span></span>|@Table|<span data-ttu-id="b1779-183">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b1779-183">TABLE_NAME</span></span>|<span data-ttu-id="b1779-184">3</span><span class="sxs-lookup"><span data-stu-id="b1779-184">3</span></span>|  
|<span data-ttu-id="b1779-185">資料行</span><span class="sxs-lookup"><span data-stu-id="b1779-185">Column</span></span>|@Column|<span data-ttu-id="b1779-186">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b1779-186">COLUMN_NAME</span></span>|<span data-ttu-id="b1779-187">4</span><span class="sxs-lookup"><span data-stu-id="b1779-187">4</span></span>|  
  
### <a name="structuredtypemembers"></a><span data-ttu-id="b1779-188">StructuredTypeMembers</span><span class="sxs-lookup"><span data-stu-id="b1779-188">StructuredTypeMembers</span></span>  
  
|<span data-ttu-id="b1779-189">限制名稱</span><span class="sxs-lookup"><span data-stu-id="b1779-189">Restriction Name</span></span>|<span data-ttu-id="b1779-190">參數名稱</span><span class="sxs-lookup"><span data-stu-id="b1779-190">Parameter Name</span></span>|<span data-ttu-id="b1779-191">預設限制值</span><span class="sxs-lookup"><span data-stu-id="b1779-191">Restriction Default</span></span>|<span data-ttu-id="b1779-192">限制號碼</span><span class="sxs-lookup"><span data-stu-id="b1779-192">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="b1779-193">Catalog</span><span class="sxs-lookup"><span data-stu-id="b1779-193">Catalog</span></span>|@Catalog|<span data-ttu-id="b1779-194">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1779-194">TABLE_CATALOG</span></span>|<span data-ttu-id="b1779-195">1</span><span class="sxs-lookup"><span data-stu-id="b1779-195">1</span></span>|  
|<span data-ttu-id="b1779-196">Owner</span><span class="sxs-lookup"><span data-stu-id="b1779-196">Owner</span></span>|@Owner|<span data-ttu-id="b1779-197">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1779-197">TABLE_SCHEMA</span></span>|<span data-ttu-id="b1779-198">2</span><span class="sxs-lookup"><span data-stu-id="b1779-198">2</span></span>|  
|<span data-ttu-id="b1779-199">資料表</span><span class="sxs-lookup"><span data-stu-id="b1779-199">Table</span></span>|@Table|<span data-ttu-id="b1779-200">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b1779-200">TABLE_NAME</span></span>|<span data-ttu-id="b1779-201">3</span><span class="sxs-lookup"><span data-stu-id="b1779-201">3</span></span>|  
|<span data-ttu-id="b1779-202">資料行</span><span class="sxs-lookup"><span data-stu-id="b1779-202">Column</span></span>|@Column|<span data-ttu-id="b1779-203">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b1779-203">COLUMN_NAME</span></span>|<span data-ttu-id="b1779-204">4</span><span class="sxs-lookup"><span data-stu-id="b1779-204">4</span></span>|  
  
### <a name="views"></a><span data-ttu-id="b1779-205">檢視</span><span class="sxs-lookup"><span data-stu-id="b1779-205">Views</span></span>  
  
|<span data-ttu-id="b1779-206">限制名稱</span><span class="sxs-lookup"><span data-stu-id="b1779-206">Restriction Name</span></span>|<span data-ttu-id="b1779-207">參數名稱</span><span class="sxs-lookup"><span data-stu-id="b1779-207">Parameter Name</span></span>|<span data-ttu-id="b1779-208">預設限制值</span><span class="sxs-lookup"><span data-stu-id="b1779-208">Restriction Default</span></span>|<span data-ttu-id="b1779-209">限制號碼</span><span class="sxs-lookup"><span data-stu-id="b1779-209">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="b1779-210">Catalog</span><span class="sxs-lookup"><span data-stu-id="b1779-210">Catalog</span></span>|@Catalog|<span data-ttu-id="b1779-211">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1779-211">TABLE_CATALOG</span></span>|<span data-ttu-id="b1779-212">1</span><span class="sxs-lookup"><span data-stu-id="b1779-212">1</span></span>|  
|<span data-ttu-id="b1779-213">Owner</span><span class="sxs-lookup"><span data-stu-id="b1779-213">Owner</span></span>|@Owner|<span data-ttu-id="b1779-214">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1779-214">TABLE_SCHEMA</span></span>|<span data-ttu-id="b1779-215">2</span><span class="sxs-lookup"><span data-stu-id="b1779-215">2</span></span>|  
|<span data-ttu-id="b1779-216">資料表</span><span class="sxs-lookup"><span data-stu-id="b1779-216">Table</span></span>|@Table|<span data-ttu-id="b1779-217">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b1779-217">TABLE_NAME</span></span>|<span data-ttu-id="b1779-218">3</span><span class="sxs-lookup"><span data-stu-id="b1779-218">3</span></span>|  
  
### <a name="viewcolumns"></a><span data-ttu-id="b1779-219">ViewColumns</span><span class="sxs-lookup"><span data-stu-id="b1779-219">ViewColumns</span></span>  
  
|<span data-ttu-id="b1779-220">限制名稱</span><span class="sxs-lookup"><span data-stu-id="b1779-220">Restriction Name</span></span>|<span data-ttu-id="b1779-221">參數名稱</span><span class="sxs-lookup"><span data-stu-id="b1779-221">Parameter Name</span></span>|<span data-ttu-id="b1779-222">預設限制值</span><span class="sxs-lookup"><span data-stu-id="b1779-222">Restriction Default</span></span>|<span data-ttu-id="b1779-223">限制號碼</span><span class="sxs-lookup"><span data-stu-id="b1779-223">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="b1779-224">Catalog</span><span class="sxs-lookup"><span data-stu-id="b1779-224">Catalog</span></span>|@Catalog|<span data-ttu-id="b1779-225">VIEW_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1779-225">VIEW_CATALOG</span></span>|<span data-ttu-id="b1779-226">1</span><span class="sxs-lookup"><span data-stu-id="b1779-226">1</span></span>|  
|<span data-ttu-id="b1779-227">Owner</span><span class="sxs-lookup"><span data-stu-id="b1779-227">Owner</span></span>|@Owner|<span data-ttu-id="b1779-228">VIEW_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1779-228">VIEW_SCHEMA</span></span>|<span data-ttu-id="b1779-229">2</span><span class="sxs-lookup"><span data-stu-id="b1779-229">2</span></span>|  
|<span data-ttu-id="b1779-230">資料表</span><span class="sxs-lookup"><span data-stu-id="b1779-230">Table</span></span>|@Table|<span data-ttu-id="b1779-231">VIEW_NAME</span><span class="sxs-lookup"><span data-stu-id="b1779-231">VIEW_NAME</span></span>|<span data-ttu-id="b1779-232">3</span><span class="sxs-lookup"><span data-stu-id="b1779-232">3</span></span>|  
|<span data-ttu-id="b1779-233">資料行</span><span class="sxs-lookup"><span data-stu-id="b1779-233">Column</span></span>|@Column|<span data-ttu-id="b1779-234">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b1779-234">COLUMN_NAME</span></span>|<span data-ttu-id="b1779-235">4</span><span class="sxs-lookup"><span data-stu-id="b1779-235">4</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="b1779-236">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="b1779-236">ProcedureParameters</span></span>  
  
|<span data-ttu-id="b1779-237">限制名稱</span><span class="sxs-lookup"><span data-stu-id="b1779-237">Restriction Name</span></span>|<span data-ttu-id="b1779-238">參數名稱</span><span class="sxs-lookup"><span data-stu-id="b1779-238">Parameter Name</span></span>|<span data-ttu-id="b1779-239">預設限制值</span><span class="sxs-lookup"><span data-stu-id="b1779-239">Restriction Default</span></span>|<span data-ttu-id="b1779-240">限制號碼</span><span class="sxs-lookup"><span data-stu-id="b1779-240">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="b1779-241">Catalog</span><span class="sxs-lookup"><span data-stu-id="b1779-241">Catalog</span></span>|@Catalog|<span data-ttu-id="b1779-242">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1779-242">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="b1779-243">1</span><span class="sxs-lookup"><span data-stu-id="b1779-243">1</span></span>|  
|<span data-ttu-id="b1779-244">Owner</span><span class="sxs-lookup"><span data-stu-id="b1779-244">Owner</span></span>|@Owner|<span data-ttu-id="b1779-245">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1779-245">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="b1779-246">2</span><span class="sxs-lookup"><span data-stu-id="b1779-246">2</span></span>|  
|<span data-ttu-id="b1779-247">名稱</span><span class="sxs-lookup"><span data-stu-id="b1779-247">Name</span></span>|@Name|<span data-ttu-id="b1779-248">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="b1779-248">SPECIFIC_NAME</span></span>|<span data-ttu-id="b1779-249">3</span><span class="sxs-lookup"><span data-stu-id="b1779-249">3</span></span>|  
|<span data-ttu-id="b1779-250">參數</span><span class="sxs-lookup"><span data-stu-id="b1779-250">Parameter</span></span>|@Parameter|<span data-ttu-id="b1779-251">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="b1779-251">PARAMETER_NAME</span></span>|<span data-ttu-id="b1779-252">4</span><span class="sxs-lookup"><span data-stu-id="b1779-252">4</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="b1779-253">程序</span><span class="sxs-lookup"><span data-stu-id="b1779-253">Procedures</span></span>  
  
|<span data-ttu-id="b1779-254">限制名稱</span><span class="sxs-lookup"><span data-stu-id="b1779-254">Restriction Name</span></span>|<span data-ttu-id="b1779-255">參數名稱</span><span class="sxs-lookup"><span data-stu-id="b1779-255">Parameter Name</span></span>|<span data-ttu-id="b1779-256">預設限制值</span><span class="sxs-lookup"><span data-stu-id="b1779-256">Restriction Default</span></span>|<span data-ttu-id="b1779-257">限制號碼</span><span class="sxs-lookup"><span data-stu-id="b1779-257">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="b1779-258">Catalog</span><span class="sxs-lookup"><span data-stu-id="b1779-258">Catalog</span></span>|@Catalog|<span data-ttu-id="b1779-259">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1779-259">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="b1779-260">1</span><span class="sxs-lookup"><span data-stu-id="b1779-260">1</span></span>|  
|<span data-ttu-id="b1779-261">Owner</span><span class="sxs-lookup"><span data-stu-id="b1779-261">Owner</span></span>|@Owner|<span data-ttu-id="b1779-262">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1779-262">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="b1779-263">2</span><span class="sxs-lookup"><span data-stu-id="b1779-263">2</span></span>|  
|<span data-ttu-id="b1779-264">名稱</span><span class="sxs-lookup"><span data-stu-id="b1779-264">Name</span></span>|@Name|<span data-ttu-id="b1779-265">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="b1779-265">SPECIFIC_NAME</span></span>|<span data-ttu-id="b1779-266">3</span><span class="sxs-lookup"><span data-stu-id="b1779-266">3</span></span>|  
|<span data-ttu-id="b1779-267">類型</span><span class="sxs-lookup"><span data-stu-id="b1779-267">Type</span></span>|@Type|<span data-ttu-id="b1779-268">ROUTINE_TYPE</span><span class="sxs-lookup"><span data-stu-id="b1779-268">ROUTINE_TYPE</span></span>|<span data-ttu-id="b1779-269">4</span><span class="sxs-lookup"><span data-stu-id="b1779-269">4</span></span>|  
  
### <a name="indexcolumns"></a><span data-ttu-id="b1779-270">IndexColumns</span><span class="sxs-lookup"><span data-stu-id="b1779-270">IndexColumns</span></span>  
  
|<span data-ttu-id="b1779-271">限制名稱</span><span class="sxs-lookup"><span data-stu-id="b1779-271">Restriction Name</span></span>|<span data-ttu-id="b1779-272">參數名稱</span><span class="sxs-lookup"><span data-stu-id="b1779-272">Parameter Name</span></span>|<span data-ttu-id="b1779-273">預設限制值</span><span class="sxs-lookup"><span data-stu-id="b1779-273">Restriction Default</span></span>|<span data-ttu-id="b1779-274">限制號碼</span><span class="sxs-lookup"><span data-stu-id="b1779-274">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="b1779-275">Catalog</span><span class="sxs-lookup"><span data-stu-id="b1779-275">Catalog</span></span>|@Catalog|<span data-ttu-id="b1779-276">db_name()</span><span class="sxs-lookup"><span data-stu-id="b1779-276">db_name()</span></span>|<span data-ttu-id="b1779-277">1</span><span class="sxs-lookup"><span data-stu-id="b1779-277">1</span></span>|  
|<span data-ttu-id="b1779-278">Owner</span><span class="sxs-lookup"><span data-stu-id="b1779-278">Owner</span></span>|@Owner|<span data-ttu-id="b1779-279">user_name()</span><span class="sxs-lookup"><span data-stu-id="b1779-279">user_name()</span></span>|<span data-ttu-id="b1779-280">2</span><span class="sxs-lookup"><span data-stu-id="b1779-280">2</span></span>|  
|<span data-ttu-id="b1779-281">資料表</span><span class="sxs-lookup"><span data-stu-id="b1779-281">Table</span></span>|@Table|<span data-ttu-id="b1779-282">o.name</span><span class="sxs-lookup"><span data-stu-id="b1779-282">o.name</span></span>|<span data-ttu-id="b1779-283">3</span><span class="sxs-lookup"><span data-stu-id="b1779-283">3</span></span>|  
|<span data-ttu-id="b1779-284">ConstraintName</span><span class="sxs-lookup"><span data-stu-id="b1779-284">ConstraintName</span></span>|@ConstraintName|<span data-ttu-id="b1779-285">x.name</span><span class="sxs-lookup"><span data-stu-id="b1779-285">x.name</span></span>|<span data-ttu-id="b1779-286">4</span><span class="sxs-lookup"><span data-stu-id="b1779-286">4</span></span>|  
|<span data-ttu-id="b1779-287">資料行</span><span class="sxs-lookup"><span data-stu-id="b1779-287">Column</span></span>|@Column|<span data-ttu-id="b1779-288">c.name</span><span class="sxs-lookup"><span data-stu-id="b1779-288">c.name</span></span>|<span data-ttu-id="b1779-289">5</span><span class="sxs-lookup"><span data-stu-id="b1779-289">5</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="b1779-290">Indexes</span><span class="sxs-lookup"><span data-stu-id="b1779-290">Indexes</span></span>  
  
|<span data-ttu-id="b1779-291">限制名稱</span><span class="sxs-lookup"><span data-stu-id="b1779-291">Restriction Name</span></span>|<span data-ttu-id="b1779-292">參數名稱</span><span class="sxs-lookup"><span data-stu-id="b1779-292">Parameter Name</span></span>|<span data-ttu-id="b1779-293">預設限制值</span><span class="sxs-lookup"><span data-stu-id="b1779-293">Restriction Default</span></span>|<span data-ttu-id="b1779-294">限制號碼</span><span class="sxs-lookup"><span data-stu-id="b1779-294">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="b1779-295">Catalog</span><span class="sxs-lookup"><span data-stu-id="b1779-295">Catalog</span></span>|@Catalog|<span data-ttu-id="b1779-296">db_name()</span><span class="sxs-lookup"><span data-stu-id="b1779-296">db_name()</span></span>|<span data-ttu-id="b1779-297">1</span><span class="sxs-lookup"><span data-stu-id="b1779-297">1</span></span>|  
|<span data-ttu-id="b1779-298">Owner</span><span class="sxs-lookup"><span data-stu-id="b1779-298">Owner</span></span>|@Owner|<span data-ttu-id="b1779-299">user_name()</span><span class="sxs-lookup"><span data-stu-id="b1779-299">user_name()</span></span>|<span data-ttu-id="b1779-300">2</span><span class="sxs-lookup"><span data-stu-id="b1779-300">2</span></span>|  
|<span data-ttu-id="b1779-301">資料表</span><span class="sxs-lookup"><span data-stu-id="b1779-301">Table</span></span>|@Table|<span data-ttu-id="b1779-302">o.name</span><span class="sxs-lookup"><span data-stu-id="b1779-302">o.name</span></span>|<span data-ttu-id="b1779-303">3</span><span class="sxs-lookup"><span data-stu-id="b1779-303">3</span></span>|  
  
### <a name="userdefinedtypes"></a><span data-ttu-id="b1779-304">UserDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="b1779-304">UserDefinedTypes</span></span>  
  
|<span data-ttu-id="b1779-305">限制名稱</span><span class="sxs-lookup"><span data-stu-id="b1779-305">Restriction Name</span></span>|<span data-ttu-id="b1779-306">參數名稱</span><span class="sxs-lookup"><span data-stu-id="b1779-306">Parameter Name</span></span>|<span data-ttu-id="b1779-307">預設限制值</span><span class="sxs-lookup"><span data-stu-id="b1779-307">Restriction Default</span></span>|<span data-ttu-id="b1779-308">限制號碼</span><span class="sxs-lookup"><span data-stu-id="b1779-308">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="b1779-309">assembly_name</span><span class="sxs-lookup"><span data-stu-id="b1779-309">assembly_name</span></span>|@AssemblyName|<span data-ttu-id="b1779-310">assemblies.name</span><span class="sxs-lookup"><span data-stu-id="b1779-310">assemblies.name</span></span>|<span data-ttu-id="b1779-311">1</span><span class="sxs-lookup"><span data-stu-id="b1779-311">1</span></span>|  
|<span data-ttu-id="b1779-312">udt_name</span><span class="sxs-lookup"><span data-stu-id="b1779-312">udt_name</span></span>|@UDTName|<span data-ttu-id="b1779-313">types.assembly_class</span><span class="sxs-lookup"><span data-stu-id="b1779-313">types.assembly_class</span></span>|<span data-ttu-id="b1779-314">2</span><span class="sxs-lookup"><span data-stu-id="b1779-314">2</span></span>|  
  
### <a name="foreignkeys"></a><span data-ttu-id="b1779-315">ForeignKeys</span><span class="sxs-lookup"><span data-stu-id="b1779-315">ForeignKeys</span></span>  
  
|<span data-ttu-id="b1779-316">限制名稱</span><span class="sxs-lookup"><span data-stu-id="b1779-316">Restriction Name</span></span>|<span data-ttu-id="b1779-317">參數名稱</span><span class="sxs-lookup"><span data-stu-id="b1779-317">Parameter Name</span></span>|<span data-ttu-id="b1779-318">預設限制值</span><span class="sxs-lookup"><span data-stu-id="b1779-318">Restriction Default</span></span>|<span data-ttu-id="b1779-319">限制號碼</span><span class="sxs-lookup"><span data-stu-id="b1779-319">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="b1779-320">Catalog</span><span class="sxs-lookup"><span data-stu-id="b1779-320">Catalog</span></span>|@Catalog|<span data-ttu-id="b1779-321">CONSTRAINT_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1779-321">CONSTRAINT_CATALOG</span></span>|<span data-ttu-id="b1779-322">1</span><span class="sxs-lookup"><span data-stu-id="b1779-322">1</span></span>|  
|<span data-ttu-id="b1779-323">Owner</span><span class="sxs-lookup"><span data-stu-id="b1779-323">Owner</span></span>|@Owner|<span data-ttu-id="b1779-324">CONSTRAINT_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1779-324">CONSTRAINT_SCHEMA</span></span>|<span data-ttu-id="b1779-325">2</span><span class="sxs-lookup"><span data-stu-id="b1779-325">2</span></span>|  
|<span data-ttu-id="b1779-326">資料表</span><span class="sxs-lookup"><span data-stu-id="b1779-326">Table</span></span>|@Table|<span data-ttu-id="b1779-327">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b1779-327">TABLE_NAME</span></span>|<span data-ttu-id="b1779-328">3</span><span class="sxs-lookup"><span data-stu-id="b1779-328">3</span></span>|  
|<span data-ttu-id="b1779-329">名稱</span><span class="sxs-lookup"><span data-stu-id="b1779-329">Name</span></span>|@Name|<span data-ttu-id="b1779-330">CONSTRAINT_NAME</span><span class="sxs-lookup"><span data-stu-id="b1779-330">CONSTRAINT_NAME</span></span>|<span data-ttu-id="b1779-331">4</span><span class="sxs-lookup"><span data-stu-id="b1779-331">4</span></span>|  
  
## <a name="sql-server-2008-schema-restrictions"></a><span data-ttu-id="b1779-332">SQL Server 2008 結構描述限制</span><span class="sxs-lookup"><span data-stu-id="b1779-332">SQL Server 2008 Schema Restrictions</span></span>  
 <span data-ttu-id="b1779-333">下表將列出 SQL Server 2008 結構描述集合的限制。</span><span class="sxs-lookup"><span data-stu-id="b1779-333">The following tables list the restrictions for SQL Server 2008 schema collections.</span></span> <span data-ttu-id="b1779-334">從 .NET Framework 3.5 版 SP1 和 SQL Server 2008 開始，這些限制便有效。</span><span class="sxs-lookup"><span data-stu-id="b1779-334">These restrictions are valid beginning with version 3.5 SP1 of the .NET Framework and SQL Server 2008.</span></span> <span data-ttu-id="b1779-335">舊版 .NET Framework 和 SQL Server 不支援它們。</span><span class="sxs-lookup"><span data-stu-id="b1779-335">They are not supported in earlier versions of the .NET Framework and SQL Server.</span></span>  
  
### <a name="columnsetcolumns"></a><span data-ttu-id="b1779-336">ColumnSetColumns</span><span class="sxs-lookup"><span data-stu-id="b1779-336">ColumnSetColumns</span></span>  
  
|<span data-ttu-id="b1779-337">限制名稱</span><span class="sxs-lookup"><span data-stu-id="b1779-337">Restriction Name</span></span>|<span data-ttu-id="b1779-338">參數名稱</span><span class="sxs-lookup"><span data-stu-id="b1779-338">Parameter Name</span></span>|<span data-ttu-id="b1779-339">預設限制值</span><span class="sxs-lookup"><span data-stu-id="b1779-339">Restriction Default</span></span>|<span data-ttu-id="b1779-340">限制號碼</span><span class="sxs-lookup"><span data-stu-id="b1779-340">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="b1779-341">Catalog</span><span class="sxs-lookup"><span data-stu-id="b1779-341">Catalog</span></span>|@Catalog|<span data-ttu-id="b1779-342">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1779-342">TABLE_CATALOG</span></span>|<span data-ttu-id="b1779-343">1</span><span class="sxs-lookup"><span data-stu-id="b1779-343">1</span></span>|  
|<span data-ttu-id="b1779-344">Owner</span><span class="sxs-lookup"><span data-stu-id="b1779-344">Owner</span></span>|@Owner|<span data-ttu-id="b1779-345">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1779-345">TABLE_SCHEMA</span></span>|<span data-ttu-id="b1779-346">2</span><span class="sxs-lookup"><span data-stu-id="b1779-346">2</span></span>|  
|<span data-ttu-id="b1779-347">資料表</span><span class="sxs-lookup"><span data-stu-id="b1779-347">Table</span></span>|@Table|<span data-ttu-id="b1779-348">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b1779-348">TABLE_NAME</span></span>|<span data-ttu-id="b1779-349">3</span><span class="sxs-lookup"><span data-stu-id="b1779-349">3</span></span>|  
  
### <a name="allcolumns"></a><span data-ttu-id="b1779-350">AllColumns</span><span class="sxs-lookup"><span data-stu-id="b1779-350">AllColumns</span></span>  
  
|<span data-ttu-id="b1779-351">限制名稱</span><span class="sxs-lookup"><span data-stu-id="b1779-351">Restriction Name</span></span>|<span data-ttu-id="b1779-352">參數名稱</span><span class="sxs-lookup"><span data-stu-id="b1779-352">Parameter Name</span></span>|<span data-ttu-id="b1779-353">預設限制值</span><span class="sxs-lookup"><span data-stu-id="b1779-353">Restriction Default</span></span>|<span data-ttu-id="b1779-354">限制號碼</span><span class="sxs-lookup"><span data-stu-id="b1779-354">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="b1779-355">Catalog</span><span class="sxs-lookup"><span data-stu-id="b1779-355">Catalog</span></span>|@Catalog|<span data-ttu-id="b1779-356">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1779-356">TABLE_CATALOG</span></span>|<span data-ttu-id="b1779-357">1</span><span class="sxs-lookup"><span data-stu-id="b1779-357">1</span></span>|  
|<span data-ttu-id="b1779-358">Owner</span><span class="sxs-lookup"><span data-stu-id="b1779-358">Owner</span></span>|@Owner|<span data-ttu-id="b1779-359">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1779-359">TABLE_SCHEMA</span></span>|<span data-ttu-id="b1779-360">2</span><span class="sxs-lookup"><span data-stu-id="b1779-360">2</span></span>|  
|<span data-ttu-id="b1779-361">資料表</span><span class="sxs-lookup"><span data-stu-id="b1779-361">Table</span></span>|@Table|<span data-ttu-id="b1779-362">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b1779-362">TABLE_NAME</span></span>|<span data-ttu-id="b1779-363">3</span><span class="sxs-lookup"><span data-stu-id="b1779-363">3</span></span>|  
|<span data-ttu-id="b1779-364">資料行</span><span class="sxs-lookup"><span data-stu-id="b1779-364">Column</span></span>|@Column|<span data-ttu-id="b1779-365">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b1779-365">COLUMN_NAME</span></span>|<span data-ttu-id="b1779-366">4</span><span class="sxs-lookup"><span data-stu-id="b1779-366">4</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b1779-367">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1779-367">See Also</span></span>  
 [<span data-ttu-id="b1779-368">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="b1779-368">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
