---
title: 結構描述限制
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
ms.openlocfilehash: 040ecd8a2ce223f89601de735b77ccc81638c7af
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44079704"
---
# <a name="schema-restrictions"></a><span data-ttu-id="2206f-102">結構描述限制</span><span class="sxs-lookup"><span data-stu-id="2206f-102">Schema Restrictions</span></span>
<span data-ttu-id="2206f-103">第二個選擇性參數**GetSchema**方法會傳回用來限制結構描述資訊量的限制，並將它傳遞至**GetSchema**方法作為字串的陣列.</span><span class="sxs-lookup"><span data-stu-id="2206f-103">The second optional parameter of the **GetSchema** method is the restrictions that are used to limit the amount of schema information returned, and it is passed to the **GetSchema** method as an array of strings.</span></span> <span data-ttu-id="2206f-104">陣列中的位置決定您可以傳遞的值，它相當於限制號碼。</span><span class="sxs-lookup"><span data-stu-id="2206f-104">The position in the array determines the values that you can pass, and this is equivalent to the restriction number.</span></span>  
  
 <span data-ttu-id="2206f-105">例如，下表說明使用 .NET Framework Data Provider for SQL Server 之 "Tables" 結構描述集合所支援的限制。</span><span class="sxs-lookup"><span data-stu-id="2206f-105">For example, the following table describes the restrictions supported by the "Tables" schema collection using the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="2206f-106">SQL Server 結構描述集合的其他限制將列於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="2206f-106">Additional restrictions for SQL Server schema collections are listed at the end of this topic.</span></span>  
  
|<span data-ttu-id="2206f-107">限制名稱</span><span class="sxs-lookup"><span data-stu-id="2206f-107">Restriction Name</span></span>|<span data-ttu-id="2206f-108">參數名稱</span><span class="sxs-lookup"><span data-stu-id="2206f-108">Parameter Name</span></span>|<span data-ttu-id="2206f-109">預設限制值</span><span class="sxs-lookup"><span data-stu-id="2206f-109">Restriction Default</span></span>|<span data-ttu-id="2206f-110">限制號碼</span><span class="sxs-lookup"><span data-stu-id="2206f-110">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="2206f-111">Catalog</span><span class="sxs-lookup"><span data-stu-id="2206f-111">Catalog</span></span>|@Catalog|<span data-ttu-id="2206f-112">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2206f-112">TABLE_CATALOG</span></span>|<span data-ttu-id="2206f-113">1</span><span class="sxs-lookup"><span data-stu-id="2206f-113">1</span></span>|  
|<span data-ttu-id="2206f-114">Owner</span><span class="sxs-lookup"><span data-stu-id="2206f-114">Owner</span></span>|@Owner|<span data-ttu-id="2206f-115">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2206f-115">TABLE_SCHEMA</span></span>|<span data-ttu-id="2206f-116">2</span><span class="sxs-lookup"><span data-stu-id="2206f-116">2</span></span>|  
|<span data-ttu-id="2206f-117">資料表</span><span class="sxs-lookup"><span data-stu-id="2206f-117">Table</span></span>|@Name|<span data-ttu-id="2206f-118">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="2206f-118">TABLE_NAME</span></span>|<span data-ttu-id="2206f-119">3</span><span class="sxs-lookup"><span data-stu-id="2206f-119">3</span></span>|  
|<span data-ttu-id="2206f-120">TableType</span><span class="sxs-lookup"><span data-stu-id="2206f-120">TableType</span></span>|@TableType|<span data-ttu-id="2206f-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="2206f-121">TABLE_TYPE</span></span>|<span data-ttu-id="2206f-122">4</span><span class="sxs-lookup"><span data-stu-id="2206f-122">4</span></span>|  
  
## <a name="specifying-restriction-values"></a><span data-ttu-id="2206f-123">指定限制值</span><span class="sxs-lookup"><span data-stu-id="2206f-123">Specifying Restriction Values</span></span>  
 <span data-ttu-id="2206f-124">若要使用 "Tables" 結構描述集合的其中一個限制，只需使用四個元素建立字串陣列，然後將符合限制數目的值置於元素中。</span><span class="sxs-lookup"><span data-stu-id="2206f-124">To use one of the restrictions of the "Tables" schema collection, simply create an array of strings with four elements, then place a value in the element that matches the restriction number.</span></span> <span data-ttu-id="2206f-125">例如，若要限制資料表所傳回**GetSchema**方法，以只有"Sales"結構描述中的資料表設定為"Sales"陣列的第二個項目之前將其傳遞給**GetSchema**方法。</span><span class="sxs-lookup"><span data-stu-id="2206f-125">For example, to restrict the tables returned by the **GetSchema** method to only those tables in the "Sales" schema, set the second element of the array to "Sales" before passing it to the **GetSchema** method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2206f-126">`SqlClient` 及 `OracleClient` 的限制集合具有其他 `ParameterName` 資料行。</span><span class="sxs-lookup"><span data-stu-id="2206f-126">The restrictions collections for `SqlClient` and `OracleClient` have an additional `ParameterName` column.</span></span> <span data-ttu-id="2206f-127">限制預設值資料行仍存在，用於回溯相容性，但目前會忽略它.</span><span class="sxs-lookup"><span data-stu-id="2206f-127">The restriction default column is still there for backwards compatibility, but is currently ignored.</span></span> <span data-ttu-id="2206f-128">指定限制值時，應使用參數化查詢而不是字串取代，來將 SQL 資料隱碼攻擊的風險減至最小。</span><span class="sxs-lookup"><span data-stu-id="2206f-128">Parameterized queries rather than string replacement should be used to minimize the risk of an SQL injection attack when specifying restriction values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2206f-129">陣列中的項目數目必須少於或等於指定結構描述集合所支援的限制數目，否則將擲回 <xref:System.ArgumentException>。</span><span class="sxs-lookup"><span data-stu-id="2206f-129">The number of elements in the array must be less than or equal to the number of restrictions supported for the specified schema collection else an <xref:System.ArgumentException> will be thrown.</span></span> <span data-ttu-id="2206f-130">可以少於限制的最大數目。</span><span class="sxs-lookup"><span data-stu-id="2206f-130">There can be fewer than the maximum number of restrictions.</span></span> <span data-ttu-id="2206f-131">假設遺漏的限制為 Null (未限制)。</span><span class="sxs-lookup"><span data-stu-id="2206f-131">The missing restrictions are assumed to be null (unrestricted).</span></span>  
  
 <span data-ttu-id="2206f-132">您可以查詢來判斷支援的限制清單，藉由呼叫.NET Framework managed 提供者**GetSchema**方法具有限制結構描述集合，也就是 「 限制 」 的名稱。</span><span class="sxs-lookup"><span data-stu-id="2206f-132">You can query a .NET Framework managed provider to determine the list of supported restrictions by calling the **GetSchema** method with the name of the restrictions schema collection, which is "Restrictions".</span></span> <span data-ttu-id="2206f-133">這將傳回 <xref:System.Data.DataTable>，其包含集合名稱、限制名稱、預設限制值及限制號碼的清單。</span><span class="sxs-lookup"><span data-stu-id="2206f-133">This will return a <xref:System.Data.DataTable> with a list of the collection names, the restriction names, the default restriction values, and the restriction numbers.</span></span>  
  
### <a name="example"></a><span data-ttu-id="2206f-134">範例</span><span class="sxs-lookup"><span data-stu-id="2206f-134">Example</span></span>  
 <span data-ttu-id="2206f-135">下列範例示範如何使用<xref:System.Data.SqlClient.SqlConnection.GetSchema%2A>的.NET Framework Data Provider for SQL Server 的方法<xref:System.Data.SqlClient.SqlConnection>類別來擷取相關的所有資料表中所包含的結構描述資訊**AdventureWorks**範例資料庫，並將資訊限制傳回只有"Sales"結構描述中的資料表：</span><span class="sxs-lookup"><span data-stu-id="2206f-135">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database, and to restrict the information returned to only those tables in the "Sales" schema:</span></span>  
  
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
  
## <a name="sql-server-schema-restrictions"></a><span data-ttu-id="2206f-136">SQL Server 結構描述限制</span><span class="sxs-lookup"><span data-stu-id="2206f-136">SQL Server Schema Restrictions</span></span>  
 <span data-ttu-id="2206f-137">下表將列出 SQL Server 結構描述集合的限制。</span><span class="sxs-lookup"><span data-stu-id="2206f-137">The following tables list the restrictions for SQL Server schema collections.</span></span>  
  
### <a name="users"></a><span data-ttu-id="2206f-138">使用者</span><span class="sxs-lookup"><span data-stu-id="2206f-138">Users</span></span>  
  
|<span data-ttu-id="2206f-139">限制名稱</span><span class="sxs-lookup"><span data-stu-id="2206f-139">Restriction Name</span></span>|<span data-ttu-id="2206f-140">參數名稱</span><span class="sxs-lookup"><span data-stu-id="2206f-140">Parameter Name</span></span>|<span data-ttu-id="2206f-141">預設限制值</span><span class="sxs-lookup"><span data-stu-id="2206f-141">Restriction Default</span></span>|<span data-ttu-id="2206f-142">限制號碼</span><span class="sxs-lookup"><span data-stu-id="2206f-142">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="2206f-143">User_Name</span><span class="sxs-lookup"><span data-stu-id="2206f-143">User_Name</span></span>|@Name|<span data-ttu-id="2206f-144">名稱</span><span class="sxs-lookup"><span data-stu-id="2206f-144">name</span></span>|<span data-ttu-id="2206f-145">1</span><span class="sxs-lookup"><span data-stu-id="2206f-145">1</span></span>|  
  
### <a name="databases"></a><span data-ttu-id="2206f-146">資料庫</span><span class="sxs-lookup"><span data-stu-id="2206f-146">Databases</span></span>  
  
|<span data-ttu-id="2206f-147">限制名稱</span><span class="sxs-lookup"><span data-stu-id="2206f-147">Restriction Name</span></span>|<span data-ttu-id="2206f-148">參數名稱</span><span class="sxs-lookup"><span data-stu-id="2206f-148">Parameter Name</span></span>|<span data-ttu-id="2206f-149">預設限制值</span><span class="sxs-lookup"><span data-stu-id="2206f-149">Restriction Default</span></span>|<span data-ttu-id="2206f-150">限制號碼</span><span class="sxs-lookup"><span data-stu-id="2206f-150">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="2206f-151">名稱</span><span class="sxs-lookup"><span data-stu-id="2206f-151">Name</span></span>|@Name|<span data-ttu-id="2206f-152">名稱</span><span class="sxs-lookup"><span data-stu-id="2206f-152">Name</span></span>|<span data-ttu-id="2206f-153">1</span><span class="sxs-lookup"><span data-stu-id="2206f-153">1</span></span>|  
  
### <a name="tables"></a><span data-ttu-id="2206f-154">資料表</span><span class="sxs-lookup"><span data-stu-id="2206f-154">Tables</span></span>  
  
|<span data-ttu-id="2206f-155">限制名稱</span><span class="sxs-lookup"><span data-stu-id="2206f-155">Restriction Name</span></span>|<span data-ttu-id="2206f-156">參數名稱</span><span class="sxs-lookup"><span data-stu-id="2206f-156">Parameter Name</span></span>|<span data-ttu-id="2206f-157">預設限制值</span><span class="sxs-lookup"><span data-stu-id="2206f-157">Restriction Default</span></span>|<span data-ttu-id="2206f-158">限制號碼</span><span class="sxs-lookup"><span data-stu-id="2206f-158">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="2206f-159">Catalog</span><span class="sxs-lookup"><span data-stu-id="2206f-159">Catalog</span></span>|@Catalog|<span data-ttu-id="2206f-160">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2206f-160">TABLE_CATALOG</span></span>|<span data-ttu-id="2206f-161">1</span><span class="sxs-lookup"><span data-stu-id="2206f-161">1</span></span>|  
|<span data-ttu-id="2206f-162">Owner</span><span class="sxs-lookup"><span data-stu-id="2206f-162">Owner</span></span>|@Owner|<span data-ttu-id="2206f-163">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2206f-163">TABLE_SCHEMA</span></span>|<span data-ttu-id="2206f-164">2</span><span class="sxs-lookup"><span data-stu-id="2206f-164">2</span></span>|  
|<span data-ttu-id="2206f-165">資料表</span><span class="sxs-lookup"><span data-stu-id="2206f-165">Table</span></span>|@Name|<span data-ttu-id="2206f-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="2206f-166">TABLE_NAME</span></span>|<span data-ttu-id="2206f-167">3</span><span class="sxs-lookup"><span data-stu-id="2206f-167">3</span></span>|  
|<span data-ttu-id="2206f-168">TableType</span><span class="sxs-lookup"><span data-stu-id="2206f-168">TableType</span></span>|@TableType|<span data-ttu-id="2206f-169">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="2206f-169">TABLE_TYPE</span></span>|<span data-ttu-id="2206f-170">4</span><span class="sxs-lookup"><span data-stu-id="2206f-170">4</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="2206f-171">資料行</span><span class="sxs-lookup"><span data-stu-id="2206f-171">Columns</span></span>  
  
|<span data-ttu-id="2206f-172">限制名稱</span><span class="sxs-lookup"><span data-stu-id="2206f-172">Restriction Name</span></span>|<span data-ttu-id="2206f-173">參數名稱</span><span class="sxs-lookup"><span data-stu-id="2206f-173">Parameter Name</span></span>|<span data-ttu-id="2206f-174">預設限制值</span><span class="sxs-lookup"><span data-stu-id="2206f-174">Restriction Default</span></span>|<span data-ttu-id="2206f-175">限制號碼</span><span class="sxs-lookup"><span data-stu-id="2206f-175">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="2206f-176">Catalog</span><span class="sxs-lookup"><span data-stu-id="2206f-176">Catalog</span></span>|@Catalog|<span data-ttu-id="2206f-177">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2206f-177">TABLE_CATALOG</span></span>|<span data-ttu-id="2206f-178">1</span><span class="sxs-lookup"><span data-stu-id="2206f-178">1</span></span>|  
|<span data-ttu-id="2206f-179">Owner</span><span class="sxs-lookup"><span data-stu-id="2206f-179">Owner</span></span>|@Owner|<span data-ttu-id="2206f-180">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2206f-180">TABLE_SCHEMA</span></span>|<span data-ttu-id="2206f-181">2</span><span class="sxs-lookup"><span data-stu-id="2206f-181">2</span></span>|  
|<span data-ttu-id="2206f-182">資料表</span><span class="sxs-lookup"><span data-stu-id="2206f-182">Table</span></span>|@Table|<span data-ttu-id="2206f-183">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="2206f-183">TABLE_NAME</span></span>|<span data-ttu-id="2206f-184">3</span><span class="sxs-lookup"><span data-stu-id="2206f-184">3</span></span>|  
|<span data-ttu-id="2206f-185">資料行</span><span class="sxs-lookup"><span data-stu-id="2206f-185">Column</span></span>|@Column|<span data-ttu-id="2206f-186">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="2206f-186">COLUMN_NAME</span></span>|<span data-ttu-id="2206f-187">4</span><span class="sxs-lookup"><span data-stu-id="2206f-187">4</span></span>|  
  
### <a name="structuredtypemembers"></a><span data-ttu-id="2206f-188">StructuredTypeMembers</span><span class="sxs-lookup"><span data-stu-id="2206f-188">StructuredTypeMembers</span></span>  
  
|<span data-ttu-id="2206f-189">限制名稱</span><span class="sxs-lookup"><span data-stu-id="2206f-189">Restriction Name</span></span>|<span data-ttu-id="2206f-190">參數名稱</span><span class="sxs-lookup"><span data-stu-id="2206f-190">Parameter Name</span></span>|<span data-ttu-id="2206f-191">預設限制值</span><span class="sxs-lookup"><span data-stu-id="2206f-191">Restriction Default</span></span>|<span data-ttu-id="2206f-192">限制號碼</span><span class="sxs-lookup"><span data-stu-id="2206f-192">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="2206f-193">Catalog</span><span class="sxs-lookup"><span data-stu-id="2206f-193">Catalog</span></span>|@Catalog|<span data-ttu-id="2206f-194">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2206f-194">TABLE_CATALOG</span></span>|<span data-ttu-id="2206f-195">1</span><span class="sxs-lookup"><span data-stu-id="2206f-195">1</span></span>|  
|<span data-ttu-id="2206f-196">Owner</span><span class="sxs-lookup"><span data-stu-id="2206f-196">Owner</span></span>|@Owner|<span data-ttu-id="2206f-197">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2206f-197">TABLE_SCHEMA</span></span>|<span data-ttu-id="2206f-198">2</span><span class="sxs-lookup"><span data-stu-id="2206f-198">2</span></span>|  
|<span data-ttu-id="2206f-199">資料表</span><span class="sxs-lookup"><span data-stu-id="2206f-199">Table</span></span>|@Table|<span data-ttu-id="2206f-200">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="2206f-200">TABLE_NAME</span></span>|<span data-ttu-id="2206f-201">3</span><span class="sxs-lookup"><span data-stu-id="2206f-201">3</span></span>|  
|<span data-ttu-id="2206f-202">資料行</span><span class="sxs-lookup"><span data-stu-id="2206f-202">Column</span></span>|@Column|<span data-ttu-id="2206f-203">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="2206f-203">COLUMN_NAME</span></span>|<span data-ttu-id="2206f-204">4</span><span class="sxs-lookup"><span data-stu-id="2206f-204">4</span></span>|  
  
### <a name="views"></a><span data-ttu-id="2206f-205">檢視</span><span class="sxs-lookup"><span data-stu-id="2206f-205">Views</span></span>  
  
|<span data-ttu-id="2206f-206">限制名稱</span><span class="sxs-lookup"><span data-stu-id="2206f-206">Restriction Name</span></span>|<span data-ttu-id="2206f-207">參數名稱</span><span class="sxs-lookup"><span data-stu-id="2206f-207">Parameter Name</span></span>|<span data-ttu-id="2206f-208">預設限制值</span><span class="sxs-lookup"><span data-stu-id="2206f-208">Restriction Default</span></span>|<span data-ttu-id="2206f-209">限制號碼</span><span class="sxs-lookup"><span data-stu-id="2206f-209">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="2206f-210">Catalog</span><span class="sxs-lookup"><span data-stu-id="2206f-210">Catalog</span></span>|@Catalog|<span data-ttu-id="2206f-211">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2206f-211">TABLE_CATALOG</span></span>|<span data-ttu-id="2206f-212">1</span><span class="sxs-lookup"><span data-stu-id="2206f-212">1</span></span>|  
|<span data-ttu-id="2206f-213">Owner</span><span class="sxs-lookup"><span data-stu-id="2206f-213">Owner</span></span>|@Owner|<span data-ttu-id="2206f-214">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2206f-214">TABLE_SCHEMA</span></span>|<span data-ttu-id="2206f-215">2</span><span class="sxs-lookup"><span data-stu-id="2206f-215">2</span></span>|  
|<span data-ttu-id="2206f-216">資料表</span><span class="sxs-lookup"><span data-stu-id="2206f-216">Table</span></span>|@Table|<span data-ttu-id="2206f-217">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="2206f-217">TABLE_NAME</span></span>|<span data-ttu-id="2206f-218">3</span><span class="sxs-lookup"><span data-stu-id="2206f-218">3</span></span>|  
  
### <a name="viewcolumns"></a><span data-ttu-id="2206f-219">ViewColumns</span><span class="sxs-lookup"><span data-stu-id="2206f-219">ViewColumns</span></span>  
  
|<span data-ttu-id="2206f-220">限制名稱</span><span class="sxs-lookup"><span data-stu-id="2206f-220">Restriction Name</span></span>|<span data-ttu-id="2206f-221">參數名稱</span><span class="sxs-lookup"><span data-stu-id="2206f-221">Parameter Name</span></span>|<span data-ttu-id="2206f-222">預設限制值</span><span class="sxs-lookup"><span data-stu-id="2206f-222">Restriction Default</span></span>|<span data-ttu-id="2206f-223">限制號碼</span><span class="sxs-lookup"><span data-stu-id="2206f-223">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="2206f-224">Catalog</span><span class="sxs-lookup"><span data-stu-id="2206f-224">Catalog</span></span>|@Catalog|<span data-ttu-id="2206f-225">VIEW_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2206f-225">VIEW_CATALOG</span></span>|<span data-ttu-id="2206f-226">1</span><span class="sxs-lookup"><span data-stu-id="2206f-226">1</span></span>|  
|<span data-ttu-id="2206f-227">Owner</span><span class="sxs-lookup"><span data-stu-id="2206f-227">Owner</span></span>|@Owner|<span data-ttu-id="2206f-228">VIEW_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2206f-228">VIEW_SCHEMA</span></span>|<span data-ttu-id="2206f-229">2</span><span class="sxs-lookup"><span data-stu-id="2206f-229">2</span></span>|  
|<span data-ttu-id="2206f-230">資料表</span><span class="sxs-lookup"><span data-stu-id="2206f-230">Table</span></span>|@Table|<span data-ttu-id="2206f-231">VIEW_NAME</span><span class="sxs-lookup"><span data-stu-id="2206f-231">VIEW_NAME</span></span>|<span data-ttu-id="2206f-232">3</span><span class="sxs-lookup"><span data-stu-id="2206f-232">3</span></span>|  
|<span data-ttu-id="2206f-233">資料行</span><span class="sxs-lookup"><span data-stu-id="2206f-233">Column</span></span>|@Column|<span data-ttu-id="2206f-234">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="2206f-234">COLUMN_NAME</span></span>|<span data-ttu-id="2206f-235">4</span><span class="sxs-lookup"><span data-stu-id="2206f-235">4</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="2206f-236">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="2206f-236">ProcedureParameters</span></span>  
  
|<span data-ttu-id="2206f-237">限制名稱</span><span class="sxs-lookup"><span data-stu-id="2206f-237">Restriction Name</span></span>|<span data-ttu-id="2206f-238">參數名稱</span><span class="sxs-lookup"><span data-stu-id="2206f-238">Parameter Name</span></span>|<span data-ttu-id="2206f-239">預設限制值</span><span class="sxs-lookup"><span data-stu-id="2206f-239">Restriction Default</span></span>|<span data-ttu-id="2206f-240">限制號碼</span><span class="sxs-lookup"><span data-stu-id="2206f-240">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="2206f-241">Catalog</span><span class="sxs-lookup"><span data-stu-id="2206f-241">Catalog</span></span>|@Catalog|<span data-ttu-id="2206f-242">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2206f-242">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="2206f-243">1</span><span class="sxs-lookup"><span data-stu-id="2206f-243">1</span></span>|  
|<span data-ttu-id="2206f-244">Owner</span><span class="sxs-lookup"><span data-stu-id="2206f-244">Owner</span></span>|@Owner|<span data-ttu-id="2206f-245">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2206f-245">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="2206f-246">2</span><span class="sxs-lookup"><span data-stu-id="2206f-246">2</span></span>|  
|<span data-ttu-id="2206f-247">名稱</span><span class="sxs-lookup"><span data-stu-id="2206f-247">Name</span></span>|@Name|<span data-ttu-id="2206f-248">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="2206f-248">SPECIFIC_NAME</span></span>|<span data-ttu-id="2206f-249">3</span><span class="sxs-lookup"><span data-stu-id="2206f-249">3</span></span>|  
|<span data-ttu-id="2206f-250">參數</span><span class="sxs-lookup"><span data-stu-id="2206f-250">Parameter</span></span>|@Parameter|<span data-ttu-id="2206f-251">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="2206f-251">PARAMETER_NAME</span></span>|<span data-ttu-id="2206f-252">4</span><span class="sxs-lookup"><span data-stu-id="2206f-252">4</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="2206f-253">程序</span><span class="sxs-lookup"><span data-stu-id="2206f-253">Procedures</span></span>  
  
|<span data-ttu-id="2206f-254">限制名稱</span><span class="sxs-lookup"><span data-stu-id="2206f-254">Restriction Name</span></span>|<span data-ttu-id="2206f-255">參數名稱</span><span class="sxs-lookup"><span data-stu-id="2206f-255">Parameter Name</span></span>|<span data-ttu-id="2206f-256">預設限制值</span><span class="sxs-lookup"><span data-stu-id="2206f-256">Restriction Default</span></span>|<span data-ttu-id="2206f-257">限制號碼</span><span class="sxs-lookup"><span data-stu-id="2206f-257">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="2206f-258">Catalog</span><span class="sxs-lookup"><span data-stu-id="2206f-258">Catalog</span></span>|@Catalog|<span data-ttu-id="2206f-259">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2206f-259">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="2206f-260">1</span><span class="sxs-lookup"><span data-stu-id="2206f-260">1</span></span>|  
|<span data-ttu-id="2206f-261">Owner</span><span class="sxs-lookup"><span data-stu-id="2206f-261">Owner</span></span>|@Owner|<span data-ttu-id="2206f-262">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2206f-262">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="2206f-263">2</span><span class="sxs-lookup"><span data-stu-id="2206f-263">2</span></span>|  
|<span data-ttu-id="2206f-264">名稱</span><span class="sxs-lookup"><span data-stu-id="2206f-264">Name</span></span>|@Name|<span data-ttu-id="2206f-265">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="2206f-265">SPECIFIC_NAME</span></span>|<span data-ttu-id="2206f-266">3</span><span class="sxs-lookup"><span data-stu-id="2206f-266">3</span></span>|  
|<span data-ttu-id="2206f-267">類型</span><span class="sxs-lookup"><span data-stu-id="2206f-267">Type</span></span>|@Type|<span data-ttu-id="2206f-268">ROUTINE_TYPE</span><span class="sxs-lookup"><span data-stu-id="2206f-268">ROUTINE_TYPE</span></span>|<span data-ttu-id="2206f-269">4</span><span class="sxs-lookup"><span data-stu-id="2206f-269">4</span></span>|  
  
### <a name="indexcolumns"></a><span data-ttu-id="2206f-270">IndexColumns</span><span class="sxs-lookup"><span data-stu-id="2206f-270">IndexColumns</span></span>  
  
|<span data-ttu-id="2206f-271">限制名稱</span><span class="sxs-lookup"><span data-stu-id="2206f-271">Restriction Name</span></span>|<span data-ttu-id="2206f-272">參數名稱</span><span class="sxs-lookup"><span data-stu-id="2206f-272">Parameter Name</span></span>|<span data-ttu-id="2206f-273">預設限制值</span><span class="sxs-lookup"><span data-stu-id="2206f-273">Restriction Default</span></span>|<span data-ttu-id="2206f-274">限制號碼</span><span class="sxs-lookup"><span data-stu-id="2206f-274">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="2206f-275">Catalog</span><span class="sxs-lookup"><span data-stu-id="2206f-275">Catalog</span></span>|@Catalog|<span data-ttu-id="2206f-276">db_name()</span><span class="sxs-lookup"><span data-stu-id="2206f-276">db_name()</span></span>|<span data-ttu-id="2206f-277">1</span><span class="sxs-lookup"><span data-stu-id="2206f-277">1</span></span>|  
|<span data-ttu-id="2206f-278">Owner</span><span class="sxs-lookup"><span data-stu-id="2206f-278">Owner</span></span>|@Owner|<span data-ttu-id="2206f-279">user_name()</span><span class="sxs-lookup"><span data-stu-id="2206f-279">user_name()</span></span>|<span data-ttu-id="2206f-280">2</span><span class="sxs-lookup"><span data-stu-id="2206f-280">2</span></span>|  
|<span data-ttu-id="2206f-281">資料表</span><span class="sxs-lookup"><span data-stu-id="2206f-281">Table</span></span>|@Table|<span data-ttu-id="2206f-282">o.name</span><span class="sxs-lookup"><span data-stu-id="2206f-282">o.name</span></span>|<span data-ttu-id="2206f-283">3</span><span class="sxs-lookup"><span data-stu-id="2206f-283">3</span></span>|  
|<span data-ttu-id="2206f-284">ConstraintName</span><span class="sxs-lookup"><span data-stu-id="2206f-284">ConstraintName</span></span>|@ConstraintName|<span data-ttu-id="2206f-285">x.name</span><span class="sxs-lookup"><span data-stu-id="2206f-285">x.name</span></span>|<span data-ttu-id="2206f-286">4</span><span class="sxs-lookup"><span data-stu-id="2206f-286">4</span></span>|  
|<span data-ttu-id="2206f-287">資料行</span><span class="sxs-lookup"><span data-stu-id="2206f-287">Column</span></span>|@Column|<span data-ttu-id="2206f-288">c.name</span><span class="sxs-lookup"><span data-stu-id="2206f-288">c.name</span></span>|<span data-ttu-id="2206f-289">5</span><span class="sxs-lookup"><span data-stu-id="2206f-289">5</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="2206f-290">Indexes</span><span class="sxs-lookup"><span data-stu-id="2206f-290">Indexes</span></span>  
  
|<span data-ttu-id="2206f-291">限制名稱</span><span class="sxs-lookup"><span data-stu-id="2206f-291">Restriction Name</span></span>|<span data-ttu-id="2206f-292">參數名稱</span><span class="sxs-lookup"><span data-stu-id="2206f-292">Parameter Name</span></span>|<span data-ttu-id="2206f-293">預設限制值</span><span class="sxs-lookup"><span data-stu-id="2206f-293">Restriction Default</span></span>|<span data-ttu-id="2206f-294">限制號碼</span><span class="sxs-lookup"><span data-stu-id="2206f-294">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="2206f-295">Catalog</span><span class="sxs-lookup"><span data-stu-id="2206f-295">Catalog</span></span>|@Catalog|<span data-ttu-id="2206f-296">db_name()</span><span class="sxs-lookup"><span data-stu-id="2206f-296">db_name()</span></span>|<span data-ttu-id="2206f-297">1</span><span class="sxs-lookup"><span data-stu-id="2206f-297">1</span></span>|  
|<span data-ttu-id="2206f-298">Owner</span><span class="sxs-lookup"><span data-stu-id="2206f-298">Owner</span></span>|@Owner|<span data-ttu-id="2206f-299">user_name()</span><span class="sxs-lookup"><span data-stu-id="2206f-299">user_name()</span></span>|<span data-ttu-id="2206f-300">2</span><span class="sxs-lookup"><span data-stu-id="2206f-300">2</span></span>|  
|<span data-ttu-id="2206f-301">資料表</span><span class="sxs-lookup"><span data-stu-id="2206f-301">Table</span></span>|@Table|<span data-ttu-id="2206f-302">o.name</span><span class="sxs-lookup"><span data-stu-id="2206f-302">o.name</span></span>|<span data-ttu-id="2206f-303">3</span><span class="sxs-lookup"><span data-stu-id="2206f-303">3</span></span>|  
  
### <a name="userdefinedtypes"></a><span data-ttu-id="2206f-304">UserDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="2206f-304">UserDefinedTypes</span></span>  
  
|<span data-ttu-id="2206f-305">限制名稱</span><span class="sxs-lookup"><span data-stu-id="2206f-305">Restriction Name</span></span>|<span data-ttu-id="2206f-306">參數名稱</span><span class="sxs-lookup"><span data-stu-id="2206f-306">Parameter Name</span></span>|<span data-ttu-id="2206f-307">預設限制值</span><span class="sxs-lookup"><span data-stu-id="2206f-307">Restriction Default</span></span>|<span data-ttu-id="2206f-308">限制號碼</span><span class="sxs-lookup"><span data-stu-id="2206f-308">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="2206f-309">assembly_name</span><span class="sxs-lookup"><span data-stu-id="2206f-309">assembly_name</span></span>|@AssemblyName|<span data-ttu-id="2206f-310">assemblies.name</span><span class="sxs-lookup"><span data-stu-id="2206f-310">assemblies.name</span></span>|<span data-ttu-id="2206f-311">1</span><span class="sxs-lookup"><span data-stu-id="2206f-311">1</span></span>|  
|<span data-ttu-id="2206f-312">udt_name</span><span class="sxs-lookup"><span data-stu-id="2206f-312">udt_name</span></span>|@UDTName|<span data-ttu-id="2206f-313">types.assembly_class</span><span class="sxs-lookup"><span data-stu-id="2206f-313">types.assembly_class</span></span>|<span data-ttu-id="2206f-314">2</span><span class="sxs-lookup"><span data-stu-id="2206f-314">2</span></span>|  
  
### <a name="foreignkeys"></a><span data-ttu-id="2206f-315">ForeignKeys</span><span class="sxs-lookup"><span data-stu-id="2206f-315">ForeignKeys</span></span>  
  
|<span data-ttu-id="2206f-316">限制名稱</span><span class="sxs-lookup"><span data-stu-id="2206f-316">Restriction Name</span></span>|<span data-ttu-id="2206f-317">參數名稱</span><span class="sxs-lookup"><span data-stu-id="2206f-317">Parameter Name</span></span>|<span data-ttu-id="2206f-318">預設限制值</span><span class="sxs-lookup"><span data-stu-id="2206f-318">Restriction Default</span></span>|<span data-ttu-id="2206f-319">限制號碼</span><span class="sxs-lookup"><span data-stu-id="2206f-319">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="2206f-320">Catalog</span><span class="sxs-lookup"><span data-stu-id="2206f-320">Catalog</span></span>|@Catalog|<span data-ttu-id="2206f-321">CONSTRAINT_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2206f-321">CONSTRAINT_CATALOG</span></span>|<span data-ttu-id="2206f-322">1</span><span class="sxs-lookup"><span data-stu-id="2206f-322">1</span></span>|  
|<span data-ttu-id="2206f-323">Owner</span><span class="sxs-lookup"><span data-stu-id="2206f-323">Owner</span></span>|@Owner|<span data-ttu-id="2206f-324">CONSTRAINT_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2206f-324">CONSTRAINT_SCHEMA</span></span>|<span data-ttu-id="2206f-325">2</span><span class="sxs-lookup"><span data-stu-id="2206f-325">2</span></span>|  
|<span data-ttu-id="2206f-326">資料表</span><span class="sxs-lookup"><span data-stu-id="2206f-326">Table</span></span>|@Table|<span data-ttu-id="2206f-327">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="2206f-327">TABLE_NAME</span></span>|<span data-ttu-id="2206f-328">3</span><span class="sxs-lookup"><span data-stu-id="2206f-328">3</span></span>|  
|<span data-ttu-id="2206f-329">名稱</span><span class="sxs-lookup"><span data-stu-id="2206f-329">Name</span></span>|@Name|<span data-ttu-id="2206f-330">CONSTRAINT_NAME</span><span class="sxs-lookup"><span data-stu-id="2206f-330">CONSTRAINT_NAME</span></span>|<span data-ttu-id="2206f-331">4</span><span class="sxs-lookup"><span data-stu-id="2206f-331">4</span></span>|  
  
## <a name="sql-server-2008-schema-restrictions"></a><span data-ttu-id="2206f-332">SQL Server 2008 結構描述限制</span><span class="sxs-lookup"><span data-stu-id="2206f-332">SQL Server 2008 Schema Restrictions</span></span>  
 <span data-ttu-id="2206f-333">下表將列出 SQL Server 2008 結構描述集合的限制。</span><span class="sxs-lookup"><span data-stu-id="2206f-333">The following tables list the restrictions for SQL Server 2008 schema collections.</span></span> <span data-ttu-id="2206f-334">從 .NET Framework 3.5 版 SP1 和 SQL Server 2008 開始，這些限制便有效。</span><span class="sxs-lookup"><span data-stu-id="2206f-334">These restrictions are valid beginning with version 3.5 SP1 of the .NET Framework and SQL Server 2008.</span></span> <span data-ttu-id="2206f-335">舊版 .NET Framework 和 SQL Server 不支援它們。</span><span class="sxs-lookup"><span data-stu-id="2206f-335">They are not supported in earlier versions of the .NET Framework and SQL Server.</span></span>  
  
### <a name="columnsetcolumns"></a><span data-ttu-id="2206f-336">ColumnSetColumns</span><span class="sxs-lookup"><span data-stu-id="2206f-336">ColumnSetColumns</span></span>  
  
|<span data-ttu-id="2206f-337">限制名稱</span><span class="sxs-lookup"><span data-stu-id="2206f-337">Restriction Name</span></span>|<span data-ttu-id="2206f-338">參數名稱</span><span class="sxs-lookup"><span data-stu-id="2206f-338">Parameter Name</span></span>|<span data-ttu-id="2206f-339">預設限制值</span><span class="sxs-lookup"><span data-stu-id="2206f-339">Restriction Default</span></span>|<span data-ttu-id="2206f-340">限制號碼</span><span class="sxs-lookup"><span data-stu-id="2206f-340">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="2206f-341">Catalog</span><span class="sxs-lookup"><span data-stu-id="2206f-341">Catalog</span></span>|@Catalog|<span data-ttu-id="2206f-342">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2206f-342">TABLE_CATALOG</span></span>|<span data-ttu-id="2206f-343">1</span><span class="sxs-lookup"><span data-stu-id="2206f-343">1</span></span>|  
|<span data-ttu-id="2206f-344">Owner</span><span class="sxs-lookup"><span data-stu-id="2206f-344">Owner</span></span>|@Owner|<span data-ttu-id="2206f-345">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2206f-345">TABLE_SCHEMA</span></span>|<span data-ttu-id="2206f-346">2</span><span class="sxs-lookup"><span data-stu-id="2206f-346">2</span></span>|  
|<span data-ttu-id="2206f-347">資料表</span><span class="sxs-lookup"><span data-stu-id="2206f-347">Table</span></span>|@Table|<span data-ttu-id="2206f-348">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="2206f-348">TABLE_NAME</span></span>|<span data-ttu-id="2206f-349">3</span><span class="sxs-lookup"><span data-stu-id="2206f-349">3</span></span>|  
  
### <a name="allcolumns"></a><span data-ttu-id="2206f-350">AllColumns</span><span class="sxs-lookup"><span data-stu-id="2206f-350">AllColumns</span></span>  
  
|<span data-ttu-id="2206f-351">限制名稱</span><span class="sxs-lookup"><span data-stu-id="2206f-351">Restriction Name</span></span>|<span data-ttu-id="2206f-352">參數名稱</span><span class="sxs-lookup"><span data-stu-id="2206f-352">Parameter Name</span></span>|<span data-ttu-id="2206f-353">預設限制值</span><span class="sxs-lookup"><span data-stu-id="2206f-353">Restriction Default</span></span>|<span data-ttu-id="2206f-354">限制號碼</span><span class="sxs-lookup"><span data-stu-id="2206f-354">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="2206f-355">Catalog</span><span class="sxs-lookup"><span data-stu-id="2206f-355">Catalog</span></span>|@Catalog|<span data-ttu-id="2206f-356">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2206f-356">TABLE_CATALOG</span></span>|<span data-ttu-id="2206f-357">1</span><span class="sxs-lookup"><span data-stu-id="2206f-357">1</span></span>|  
|<span data-ttu-id="2206f-358">Owner</span><span class="sxs-lookup"><span data-stu-id="2206f-358">Owner</span></span>|@Owner|<span data-ttu-id="2206f-359">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2206f-359">TABLE_SCHEMA</span></span>|<span data-ttu-id="2206f-360">2</span><span class="sxs-lookup"><span data-stu-id="2206f-360">2</span></span>|  
|<span data-ttu-id="2206f-361">資料表</span><span class="sxs-lookup"><span data-stu-id="2206f-361">Table</span></span>|@Table|<span data-ttu-id="2206f-362">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="2206f-362">TABLE_NAME</span></span>|<span data-ttu-id="2206f-363">3</span><span class="sxs-lookup"><span data-stu-id="2206f-363">3</span></span>|  
|<span data-ttu-id="2206f-364">資料行</span><span class="sxs-lookup"><span data-stu-id="2206f-364">Column</span></span>|@Column|<span data-ttu-id="2206f-365">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="2206f-365">COLUMN_NAME</span></span>|<span data-ttu-id="2206f-366">4</span><span class="sxs-lookup"><span data-stu-id="2206f-366">4</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2206f-367">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2206f-367">See Also</span></span>  
 [<span data-ttu-id="2206f-368">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="2206f-368">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
