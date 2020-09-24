---
title: 結構描述限制
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
ms.openlocfilehash: c0a3cafef45341cd95fa0a4f65c818129e120e44
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91147820"
---
# <a name="schema-restrictions"></a><span data-ttu-id="7dc20-102">結構描述限制</span><span class="sxs-lookup"><span data-stu-id="7dc20-102">Schema Restrictions</span></span>

<span data-ttu-id="7dc20-103">**GetSchema**方法的第二個選擇性參數是用來限制傳回的架構資訊數量的限制，而且會以字串陣列的形式傳遞至**GetSchema**方法。</span><span class="sxs-lookup"><span data-stu-id="7dc20-103">The second optional parameter of the **GetSchema** method is the restrictions that are used to limit the amount of schema information returned, and it is passed to the **GetSchema** method as an array of strings.</span></span> <span data-ttu-id="7dc20-104">陣列中的位置決定您可以傳遞的值，它相當於限制號碼。</span><span class="sxs-lookup"><span data-stu-id="7dc20-104">The position in the array determines the values that you can pass, and this is equivalent to the restriction number.</span></span>  
  
 <span data-ttu-id="7dc20-105">例如，下表說明使用 .NET Framework Data Provider for SQL Server 之 "Tables" 結構描述集合所支援的限制。</span><span class="sxs-lookup"><span data-stu-id="7dc20-105">For example, the following table describes the restrictions supported by the "Tables" schema collection using the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="7dc20-106">SQL Server 結構描述集合的其他限制將列於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="7dc20-106">Additional restrictions for SQL Server schema collections are listed at the end of this topic.</span></span>  
  
|<span data-ttu-id="7dc20-107">限制名稱</span><span class="sxs-lookup"><span data-stu-id="7dc20-107">Restriction Name</span></span>|<span data-ttu-id="7dc20-108">參數名稱</span><span class="sxs-lookup"><span data-stu-id="7dc20-108">Parameter Name</span></span>|<span data-ttu-id="7dc20-109">預設限制值</span><span class="sxs-lookup"><span data-stu-id="7dc20-109">Restriction Default</span></span>|<span data-ttu-id="7dc20-110">限制號碼</span><span class="sxs-lookup"><span data-stu-id="7dc20-110">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="7dc20-111">目錄</span><span class="sxs-lookup"><span data-stu-id="7dc20-111">Catalog</span></span>|@Catalog|<span data-ttu-id="7dc20-112">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="7dc20-112">TABLE_CATALOG</span></span>|<span data-ttu-id="7dc20-113">1</span><span class="sxs-lookup"><span data-stu-id="7dc20-113">1</span></span>|  
|<span data-ttu-id="7dc20-114">擁有者</span><span class="sxs-lookup"><span data-stu-id="7dc20-114">Owner</span></span>|@Owner|<span data-ttu-id="7dc20-115">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="7dc20-115">TABLE_SCHEMA</span></span>|<span data-ttu-id="7dc20-116">2</span><span class="sxs-lookup"><span data-stu-id="7dc20-116">2</span></span>|  
|<span data-ttu-id="7dc20-117">資料表</span><span class="sxs-lookup"><span data-stu-id="7dc20-117">Table</span></span>|@Name|<span data-ttu-id="7dc20-118">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="7dc20-118">TABLE_NAME</span></span>|<span data-ttu-id="7dc20-119">3</span><span class="sxs-lookup"><span data-stu-id="7dc20-119">3</span></span>|  
|<span data-ttu-id="7dc20-120">TableType</span><span class="sxs-lookup"><span data-stu-id="7dc20-120">TableType</span></span>|@TableType|<span data-ttu-id="7dc20-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="7dc20-121">TABLE_TYPE</span></span>|<span data-ttu-id="7dc20-122">4</span><span class="sxs-lookup"><span data-stu-id="7dc20-122">4</span></span>|  
  
## <a name="specifying-restriction-values"></a><span data-ttu-id="7dc20-123">指定限制值</span><span class="sxs-lookup"><span data-stu-id="7dc20-123">Specifying Restriction Values</span></span>  

 <span data-ttu-id="7dc20-124">若要使用 "Tables" 結構描述集合的其中一個限制，只需使用四個元素建立字串陣列，然後將符合限制數目的值置於元素中。</span><span class="sxs-lookup"><span data-stu-id="7dc20-124">To use one of the restrictions of the "Tables" schema collection, simply create an array of strings with four elements, then place a value in the element that matches the restriction number.</span></span> <span data-ttu-id="7dc20-125">例如，若要將 **GetSchema** 方法所傳回的資料表限制為只有 "sales" 架構中的資料表，請先將陣列的第二個元素設定為 "sales"，再將它傳遞給 **GetSchema** 方法。</span><span class="sxs-lookup"><span data-stu-id="7dc20-125">For example, to restrict the tables returned by the **GetSchema** method to only those tables in the "Sales" schema, set the second element of the array to "Sales" before passing it to the **GetSchema** method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7dc20-126">`SqlClient` 及 `OracleClient` 的限制集合具有其他 `ParameterName` 資料行。</span><span class="sxs-lookup"><span data-stu-id="7dc20-126">The restrictions collections for `SqlClient` and `OracleClient` have an additional `ParameterName` column.</span></span> <span data-ttu-id="7dc20-127">限制預設值資料行仍存在，用於回溯相容性，但目前會忽略它.</span><span class="sxs-lookup"><span data-stu-id="7dc20-127">The restriction default column is still there for backwards compatibility, but is currently ignored.</span></span> <span data-ttu-id="7dc20-128">指定限制值時，應使用參數化查詢而不是字串取代，來將 SQL 資料隱碼攻擊的風險減至最小。</span><span class="sxs-lookup"><span data-stu-id="7dc20-128">Parameterized queries rather than string replacement should be used to minimize the risk of an SQL injection attack when specifying restriction values.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7dc20-129">陣列中的項目數目必須少於或等於指定結構描述集合所支援的限制數目，否則將擲回 <xref:System.ArgumentException>。</span><span class="sxs-lookup"><span data-stu-id="7dc20-129">The number of elements in the array must be less than or equal to the number of restrictions supported for the specified schema collection else an <xref:System.ArgumentException> will be thrown.</span></span> <span data-ttu-id="7dc20-130">可以少於限制的最大數目。</span><span class="sxs-lookup"><span data-stu-id="7dc20-130">There can be fewer than the maximum number of restrictions.</span></span> <span data-ttu-id="7dc20-131">假設遺漏的限制為 Null (未限制)。</span><span class="sxs-lookup"><span data-stu-id="7dc20-131">The missing restrictions are assumed to be null (unrestricted).</span></span>  
  
 <span data-ttu-id="7dc20-132">您可以使用限制架構集合的名稱（也就是「限制」）來呼叫 **GetSchema** 方法，以查詢 .NET Framework 的 managed 提供者來判斷支援的限制清單。</span><span class="sxs-lookup"><span data-stu-id="7dc20-132">You can query a .NET Framework managed provider to determine the list of supported restrictions by calling the **GetSchema** method with the name of the restrictions schema collection, which is "Restrictions".</span></span> <span data-ttu-id="7dc20-133">這將傳回 <xref:System.Data.DataTable>，其包含集合名稱、限制名稱、預設限制值及限制號碼的清單。</span><span class="sxs-lookup"><span data-stu-id="7dc20-133">This will return a <xref:System.Data.DataTable> with a list of the collection names, the restriction names, the default restriction values, and the restriction numbers.</span></span>  
  
### <a name="example"></a><span data-ttu-id="7dc20-134">範例</span><span class="sxs-lookup"><span data-stu-id="7dc20-134">Example</span></span>  

 <span data-ttu-id="7dc20-135">下列範例示範如何使用 <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> .NET Framework Data Provider 的方法，讓 SQL Server <xref:System.Data.SqlClient.SqlConnection> 類別取得 **AdventureWorks** 範例資料庫中包含之所有資料表的架構資訊，並將傳回的資訊限制為只有 "Sales" 架構中的資料表：</span><span class="sxs-lookup"><span data-stu-id="7dc20-135">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database, and to restrict the information returned to only those tables in the "Sales" schema:</span></span>  
  
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
  
## <a name="sql-server-schema-restrictions"></a><span data-ttu-id="7dc20-136">SQL Server 結構描述限制</span><span class="sxs-lookup"><span data-stu-id="7dc20-136">SQL Server Schema Restrictions</span></span>  

 <span data-ttu-id="7dc20-137">下表將列出 SQL Server 結構描述集合的限制。</span><span class="sxs-lookup"><span data-stu-id="7dc20-137">The following tables list the restrictions for SQL Server schema collections.</span></span>  
  
### <a name="users"></a><span data-ttu-id="7dc20-138">使用者</span><span class="sxs-lookup"><span data-stu-id="7dc20-138">Users</span></span>  
  
|<span data-ttu-id="7dc20-139">限制名稱</span><span class="sxs-lookup"><span data-stu-id="7dc20-139">Restriction Name</span></span>|<span data-ttu-id="7dc20-140">參數名稱</span><span class="sxs-lookup"><span data-stu-id="7dc20-140">Parameter Name</span></span>|<span data-ttu-id="7dc20-141">預設限制值</span><span class="sxs-lookup"><span data-stu-id="7dc20-141">Restriction Default</span></span>|<span data-ttu-id="7dc20-142">限制號碼</span><span class="sxs-lookup"><span data-stu-id="7dc20-142">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="7dc20-143">User_Name</span><span class="sxs-lookup"><span data-stu-id="7dc20-143">User_Name</span></span>|@Name|<span data-ttu-id="7dc20-144">NAME</span><span class="sxs-lookup"><span data-stu-id="7dc20-144">name</span></span>|<span data-ttu-id="7dc20-145">1</span><span class="sxs-lookup"><span data-stu-id="7dc20-145">1</span></span>|  
  
### <a name="databases"></a><span data-ttu-id="7dc20-146">資料庫</span><span class="sxs-lookup"><span data-stu-id="7dc20-146">Databases</span></span>  
  
|<span data-ttu-id="7dc20-147">限制名稱</span><span class="sxs-lookup"><span data-stu-id="7dc20-147">Restriction Name</span></span>|<span data-ttu-id="7dc20-148">參數名稱</span><span class="sxs-lookup"><span data-stu-id="7dc20-148">Parameter Name</span></span>|<span data-ttu-id="7dc20-149">預設限制值</span><span class="sxs-lookup"><span data-stu-id="7dc20-149">Restriction Default</span></span>|<span data-ttu-id="7dc20-150">限制號碼</span><span class="sxs-lookup"><span data-stu-id="7dc20-150">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="7dc20-151">Name</span><span class="sxs-lookup"><span data-stu-id="7dc20-151">Name</span></span>|@Name|<span data-ttu-id="7dc20-152">名稱</span><span class="sxs-lookup"><span data-stu-id="7dc20-152">Name</span></span>|<span data-ttu-id="7dc20-153">1</span><span class="sxs-lookup"><span data-stu-id="7dc20-153">1</span></span>|  
  
### <a name="tables"></a><span data-ttu-id="7dc20-154">資料表</span><span class="sxs-lookup"><span data-stu-id="7dc20-154">Tables</span></span>  
  
|<span data-ttu-id="7dc20-155">限制名稱</span><span class="sxs-lookup"><span data-stu-id="7dc20-155">Restriction Name</span></span>|<span data-ttu-id="7dc20-156">參數名稱</span><span class="sxs-lookup"><span data-stu-id="7dc20-156">Parameter Name</span></span>|<span data-ttu-id="7dc20-157">預設限制值</span><span class="sxs-lookup"><span data-stu-id="7dc20-157">Restriction Default</span></span>|<span data-ttu-id="7dc20-158">限制號碼</span><span class="sxs-lookup"><span data-stu-id="7dc20-158">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="7dc20-159">目錄</span><span class="sxs-lookup"><span data-stu-id="7dc20-159">Catalog</span></span>|@Catalog|<span data-ttu-id="7dc20-160">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="7dc20-160">TABLE_CATALOG</span></span>|<span data-ttu-id="7dc20-161">1</span><span class="sxs-lookup"><span data-stu-id="7dc20-161">1</span></span>|  
|<span data-ttu-id="7dc20-162">擁有者</span><span class="sxs-lookup"><span data-stu-id="7dc20-162">Owner</span></span>|@Owner|<span data-ttu-id="7dc20-163">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="7dc20-163">TABLE_SCHEMA</span></span>|<span data-ttu-id="7dc20-164">2</span><span class="sxs-lookup"><span data-stu-id="7dc20-164">2</span></span>|  
|<span data-ttu-id="7dc20-165">資料表</span><span class="sxs-lookup"><span data-stu-id="7dc20-165">Table</span></span>|@Name|<span data-ttu-id="7dc20-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="7dc20-166">TABLE_NAME</span></span>|<span data-ttu-id="7dc20-167">3</span><span class="sxs-lookup"><span data-stu-id="7dc20-167">3</span></span>|  
|<span data-ttu-id="7dc20-168">TableType</span><span class="sxs-lookup"><span data-stu-id="7dc20-168">TableType</span></span>|@TableType|<span data-ttu-id="7dc20-169">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="7dc20-169">TABLE_TYPE</span></span>|<span data-ttu-id="7dc20-170">4</span><span class="sxs-lookup"><span data-stu-id="7dc20-170">4</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="7dc20-171">資料行</span><span class="sxs-lookup"><span data-stu-id="7dc20-171">Columns</span></span>  
  
|<span data-ttu-id="7dc20-172">限制名稱</span><span class="sxs-lookup"><span data-stu-id="7dc20-172">Restriction Name</span></span>|<span data-ttu-id="7dc20-173">參數名稱</span><span class="sxs-lookup"><span data-stu-id="7dc20-173">Parameter Name</span></span>|<span data-ttu-id="7dc20-174">預設限制值</span><span class="sxs-lookup"><span data-stu-id="7dc20-174">Restriction Default</span></span>|<span data-ttu-id="7dc20-175">限制號碼</span><span class="sxs-lookup"><span data-stu-id="7dc20-175">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="7dc20-176">目錄</span><span class="sxs-lookup"><span data-stu-id="7dc20-176">Catalog</span></span>|@Catalog|<span data-ttu-id="7dc20-177">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="7dc20-177">TABLE_CATALOG</span></span>|<span data-ttu-id="7dc20-178">1</span><span class="sxs-lookup"><span data-stu-id="7dc20-178">1</span></span>|  
|<span data-ttu-id="7dc20-179">擁有者</span><span class="sxs-lookup"><span data-stu-id="7dc20-179">Owner</span></span>|@Owner|<span data-ttu-id="7dc20-180">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="7dc20-180">TABLE_SCHEMA</span></span>|<span data-ttu-id="7dc20-181">2</span><span class="sxs-lookup"><span data-stu-id="7dc20-181">2</span></span>|  
|<span data-ttu-id="7dc20-182">資料表</span><span class="sxs-lookup"><span data-stu-id="7dc20-182">Table</span></span>|@Table|<span data-ttu-id="7dc20-183">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="7dc20-183">TABLE_NAME</span></span>|<span data-ttu-id="7dc20-184">3</span><span class="sxs-lookup"><span data-stu-id="7dc20-184">3</span></span>|  
|<span data-ttu-id="7dc20-185">資料行</span><span class="sxs-lookup"><span data-stu-id="7dc20-185">Column</span></span>|@Column|<span data-ttu-id="7dc20-186">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="7dc20-186">COLUMN_NAME</span></span>|<span data-ttu-id="7dc20-187">4</span><span class="sxs-lookup"><span data-stu-id="7dc20-187">4</span></span>|  
  
### <a name="structuredtypemembers"></a><span data-ttu-id="7dc20-188">StructuredTypeMembers</span><span class="sxs-lookup"><span data-stu-id="7dc20-188">StructuredTypeMembers</span></span>  
  
|<span data-ttu-id="7dc20-189">限制名稱</span><span class="sxs-lookup"><span data-stu-id="7dc20-189">Restriction Name</span></span>|<span data-ttu-id="7dc20-190">參數名稱</span><span class="sxs-lookup"><span data-stu-id="7dc20-190">Parameter Name</span></span>|<span data-ttu-id="7dc20-191">預設限制值</span><span class="sxs-lookup"><span data-stu-id="7dc20-191">Restriction Default</span></span>|<span data-ttu-id="7dc20-192">限制號碼</span><span class="sxs-lookup"><span data-stu-id="7dc20-192">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="7dc20-193">目錄</span><span class="sxs-lookup"><span data-stu-id="7dc20-193">Catalog</span></span>|@Catalog|<span data-ttu-id="7dc20-194">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="7dc20-194">TABLE_CATALOG</span></span>|<span data-ttu-id="7dc20-195">1</span><span class="sxs-lookup"><span data-stu-id="7dc20-195">1</span></span>|  
|<span data-ttu-id="7dc20-196">擁有者</span><span class="sxs-lookup"><span data-stu-id="7dc20-196">Owner</span></span>|@Owner|<span data-ttu-id="7dc20-197">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="7dc20-197">TABLE_SCHEMA</span></span>|<span data-ttu-id="7dc20-198">2</span><span class="sxs-lookup"><span data-stu-id="7dc20-198">2</span></span>|  
|<span data-ttu-id="7dc20-199">資料表</span><span class="sxs-lookup"><span data-stu-id="7dc20-199">Table</span></span>|@Table|<span data-ttu-id="7dc20-200">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="7dc20-200">TABLE_NAME</span></span>|<span data-ttu-id="7dc20-201">3</span><span class="sxs-lookup"><span data-stu-id="7dc20-201">3</span></span>|  
|<span data-ttu-id="7dc20-202">資料行</span><span class="sxs-lookup"><span data-stu-id="7dc20-202">Column</span></span>|@Column|<span data-ttu-id="7dc20-203">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="7dc20-203">COLUMN_NAME</span></span>|<span data-ttu-id="7dc20-204">4</span><span class="sxs-lookup"><span data-stu-id="7dc20-204">4</span></span>|  
  
### <a name="views"></a><span data-ttu-id="7dc20-205">檢視</span><span class="sxs-lookup"><span data-stu-id="7dc20-205">Views</span></span>  
  
|<span data-ttu-id="7dc20-206">限制名稱</span><span class="sxs-lookup"><span data-stu-id="7dc20-206">Restriction Name</span></span>|<span data-ttu-id="7dc20-207">參數名稱</span><span class="sxs-lookup"><span data-stu-id="7dc20-207">Parameter Name</span></span>|<span data-ttu-id="7dc20-208">預設限制值</span><span class="sxs-lookup"><span data-stu-id="7dc20-208">Restriction Default</span></span>|<span data-ttu-id="7dc20-209">限制號碼</span><span class="sxs-lookup"><span data-stu-id="7dc20-209">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="7dc20-210">目錄</span><span class="sxs-lookup"><span data-stu-id="7dc20-210">Catalog</span></span>|@Catalog|<span data-ttu-id="7dc20-211">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="7dc20-211">TABLE_CATALOG</span></span>|<span data-ttu-id="7dc20-212">1</span><span class="sxs-lookup"><span data-stu-id="7dc20-212">1</span></span>|  
|<span data-ttu-id="7dc20-213">擁有者</span><span class="sxs-lookup"><span data-stu-id="7dc20-213">Owner</span></span>|@Owner|<span data-ttu-id="7dc20-214">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="7dc20-214">TABLE_SCHEMA</span></span>|<span data-ttu-id="7dc20-215">2</span><span class="sxs-lookup"><span data-stu-id="7dc20-215">2</span></span>|  
|<span data-ttu-id="7dc20-216">資料表</span><span class="sxs-lookup"><span data-stu-id="7dc20-216">Table</span></span>|@Table|<span data-ttu-id="7dc20-217">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="7dc20-217">TABLE_NAME</span></span>|<span data-ttu-id="7dc20-218">3</span><span class="sxs-lookup"><span data-stu-id="7dc20-218">3</span></span>|  
  
### <a name="viewcolumns"></a><span data-ttu-id="7dc20-219">ViewColumns</span><span class="sxs-lookup"><span data-stu-id="7dc20-219">ViewColumns</span></span>  
  
|<span data-ttu-id="7dc20-220">限制名稱</span><span class="sxs-lookup"><span data-stu-id="7dc20-220">Restriction Name</span></span>|<span data-ttu-id="7dc20-221">參數名稱</span><span class="sxs-lookup"><span data-stu-id="7dc20-221">Parameter Name</span></span>|<span data-ttu-id="7dc20-222">預設限制值</span><span class="sxs-lookup"><span data-stu-id="7dc20-222">Restriction Default</span></span>|<span data-ttu-id="7dc20-223">限制號碼</span><span class="sxs-lookup"><span data-stu-id="7dc20-223">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="7dc20-224">目錄</span><span class="sxs-lookup"><span data-stu-id="7dc20-224">Catalog</span></span>|@Catalog|<span data-ttu-id="7dc20-225">VIEW_CATALOG</span><span class="sxs-lookup"><span data-stu-id="7dc20-225">VIEW_CATALOG</span></span>|<span data-ttu-id="7dc20-226">1</span><span class="sxs-lookup"><span data-stu-id="7dc20-226">1</span></span>|  
|<span data-ttu-id="7dc20-227">擁有者</span><span class="sxs-lookup"><span data-stu-id="7dc20-227">Owner</span></span>|@Owner|<span data-ttu-id="7dc20-228">VIEW_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="7dc20-228">VIEW_SCHEMA</span></span>|<span data-ttu-id="7dc20-229">2</span><span class="sxs-lookup"><span data-stu-id="7dc20-229">2</span></span>|  
|<span data-ttu-id="7dc20-230">資料表</span><span class="sxs-lookup"><span data-stu-id="7dc20-230">Table</span></span>|@Table|<span data-ttu-id="7dc20-231">VIEW_NAME</span><span class="sxs-lookup"><span data-stu-id="7dc20-231">VIEW_NAME</span></span>|<span data-ttu-id="7dc20-232">3</span><span class="sxs-lookup"><span data-stu-id="7dc20-232">3</span></span>|  
|<span data-ttu-id="7dc20-233">資料行</span><span class="sxs-lookup"><span data-stu-id="7dc20-233">Column</span></span>|@Column|<span data-ttu-id="7dc20-234">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="7dc20-234">COLUMN_NAME</span></span>|<span data-ttu-id="7dc20-235">4</span><span class="sxs-lookup"><span data-stu-id="7dc20-235">4</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="7dc20-236">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="7dc20-236">ProcedureParameters</span></span>  
  
|<span data-ttu-id="7dc20-237">限制名稱</span><span class="sxs-lookup"><span data-stu-id="7dc20-237">Restriction Name</span></span>|<span data-ttu-id="7dc20-238">參數名稱</span><span class="sxs-lookup"><span data-stu-id="7dc20-238">Parameter Name</span></span>|<span data-ttu-id="7dc20-239">預設限制值</span><span class="sxs-lookup"><span data-stu-id="7dc20-239">Restriction Default</span></span>|<span data-ttu-id="7dc20-240">限制號碼</span><span class="sxs-lookup"><span data-stu-id="7dc20-240">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="7dc20-241">目錄</span><span class="sxs-lookup"><span data-stu-id="7dc20-241">Catalog</span></span>|@Catalog|<span data-ttu-id="7dc20-242">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="7dc20-242">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="7dc20-243">1</span><span class="sxs-lookup"><span data-stu-id="7dc20-243">1</span></span>|  
|<span data-ttu-id="7dc20-244">擁有者</span><span class="sxs-lookup"><span data-stu-id="7dc20-244">Owner</span></span>|@Owner|<span data-ttu-id="7dc20-245">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="7dc20-245">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="7dc20-246">2</span><span class="sxs-lookup"><span data-stu-id="7dc20-246">2</span></span>|  
|<span data-ttu-id="7dc20-247">Name</span><span class="sxs-lookup"><span data-stu-id="7dc20-247">Name</span></span>|@Name|<span data-ttu-id="7dc20-248">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="7dc20-248">SPECIFIC_NAME</span></span>|<span data-ttu-id="7dc20-249">3</span><span class="sxs-lookup"><span data-stu-id="7dc20-249">3</span></span>|  
|<span data-ttu-id="7dc20-250">參數</span><span class="sxs-lookup"><span data-stu-id="7dc20-250">Parameter</span></span>|@Parameter|<span data-ttu-id="7dc20-251">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="7dc20-251">PARAMETER_NAME</span></span>|<span data-ttu-id="7dc20-252">4</span><span class="sxs-lookup"><span data-stu-id="7dc20-252">4</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="7dc20-253">程序</span><span class="sxs-lookup"><span data-stu-id="7dc20-253">Procedures</span></span>  
  
|<span data-ttu-id="7dc20-254">限制名稱</span><span class="sxs-lookup"><span data-stu-id="7dc20-254">Restriction Name</span></span>|<span data-ttu-id="7dc20-255">參數名稱</span><span class="sxs-lookup"><span data-stu-id="7dc20-255">Parameter Name</span></span>|<span data-ttu-id="7dc20-256">預設限制值</span><span class="sxs-lookup"><span data-stu-id="7dc20-256">Restriction Default</span></span>|<span data-ttu-id="7dc20-257">限制號碼</span><span class="sxs-lookup"><span data-stu-id="7dc20-257">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="7dc20-258">目錄</span><span class="sxs-lookup"><span data-stu-id="7dc20-258">Catalog</span></span>|@Catalog|<span data-ttu-id="7dc20-259">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="7dc20-259">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="7dc20-260">1</span><span class="sxs-lookup"><span data-stu-id="7dc20-260">1</span></span>|  
|<span data-ttu-id="7dc20-261">擁有者</span><span class="sxs-lookup"><span data-stu-id="7dc20-261">Owner</span></span>|@Owner|<span data-ttu-id="7dc20-262">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="7dc20-262">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="7dc20-263">2</span><span class="sxs-lookup"><span data-stu-id="7dc20-263">2</span></span>|  
|<span data-ttu-id="7dc20-264">Name</span><span class="sxs-lookup"><span data-stu-id="7dc20-264">Name</span></span>|@Name|<span data-ttu-id="7dc20-265">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="7dc20-265">SPECIFIC_NAME</span></span>|<span data-ttu-id="7dc20-266">3</span><span class="sxs-lookup"><span data-stu-id="7dc20-266">3</span></span>|  
|<span data-ttu-id="7dc20-267">類型</span><span class="sxs-lookup"><span data-stu-id="7dc20-267">Type</span></span>|@Type|<span data-ttu-id="7dc20-268">ROUTINE_TYPE</span><span class="sxs-lookup"><span data-stu-id="7dc20-268">ROUTINE_TYPE</span></span>|<span data-ttu-id="7dc20-269">4</span><span class="sxs-lookup"><span data-stu-id="7dc20-269">4</span></span>|  
  
### <a name="indexcolumns"></a><span data-ttu-id="7dc20-270">IndexColumns</span><span class="sxs-lookup"><span data-stu-id="7dc20-270">IndexColumns</span></span>  
  
|<span data-ttu-id="7dc20-271">限制名稱</span><span class="sxs-lookup"><span data-stu-id="7dc20-271">Restriction Name</span></span>|<span data-ttu-id="7dc20-272">參數名稱</span><span class="sxs-lookup"><span data-stu-id="7dc20-272">Parameter Name</span></span>|<span data-ttu-id="7dc20-273">預設限制值</span><span class="sxs-lookup"><span data-stu-id="7dc20-273">Restriction Default</span></span>|<span data-ttu-id="7dc20-274">限制號碼</span><span class="sxs-lookup"><span data-stu-id="7dc20-274">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="7dc20-275">目錄</span><span class="sxs-lookup"><span data-stu-id="7dc20-275">Catalog</span></span>|@Catalog|<span data-ttu-id="7dc20-276">db_name()</span><span class="sxs-lookup"><span data-stu-id="7dc20-276">db_name()</span></span>|<span data-ttu-id="7dc20-277">1</span><span class="sxs-lookup"><span data-stu-id="7dc20-277">1</span></span>|  
|<span data-ttu-id="7dc20-278">擁有者</span><span class="sxs-lookup"><span data-stu-id="7dc20-278">Owner</span></span>|@Owner|<span data-ttu-id="7dc20-279">user_name()</span><span class="sxs-lookup"><span data-stu-id="7dc20-279">user_name()</span></span>|<span data-ttu-id="7dc20-280">2</span><span class="sxs-lookup"><span data-stu-id="7dc20-280">2</span></span>|  
|<span data-ttu-id="7dc20-281">資料表</span><span class="sxs-lookup"><span data-stu-id="7dc20-281">Table</span></span>|@Table|<span data-ttu-id="7dc20-282">o.name</span><span class="sxs-lookup"><span data-stu-id="7dc20-282">o.name</span></span>|<span data-ttu-id="7dc20-283">3</span><span class="sxs-lookup"><span data-stu-id="7dc20-283">3</span></span>|  
|<span data-ttu-id="7dc20-284">ConstraintName</span><span class="sxs-lookup"><span data-stu-id="7dc20-284">ConstraintName</span></span>|@ConstraintName|<span data-ttu-id="7dc20-285">x.name</span><span class="sxs-lookup"><span data-stu-id="7dc20-285">x.name</span></span>|<span data-ttu-id="7dc20-286">4</span><span class="sxs-lookup"><span data-stu-id="7dc20-286">4</span></span>|  
|<span data-ttu-id="7dc20-287">資料行</span><span class="sxs-lookup"><span data-stu-id="7dc20-287">Column</span></span>|@Column|<span data-ttu-id="7dc20-288">c.name</span><span class="sxs-lookup"><span data-stu-id="7dc20-288">c.name</span></span>|<span data-ttu-id="7dc20-289">5</span><span class="sxs-lookup"><span data-stu-id="7dc20-289">5</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="7dc20-290">索引</span><span class="sxs-lookup"><span data-stu-id="7dc20-290">Indexes</span></span>  
  
|<span data-ttu-id="7dc20-291">限制名稱</span><span class="sxs-lookup"><span data-stu-id="7dc20-291">Restriction Name</span></span>|<span data-ttu-id="7dc20-292">參數名稱</span><span class="sxs-lookup"><span data-stu-id="7dc20-292">Parameter Name</span></span>|<span data-ttu-id="7dc20-293">預設限制值</span><span class="sxs-lookup"><span data-stu-id="7dc20-293">Restriction Default</span></span>|<span data-ttu-id="7dc20-294">限制號碼</span><span class="sxs-lookup"><span data-stu-id="7dc20-294">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="7dc20-295">目錄</span><span class="sxs-lookup"><span data-stu-id="7dc20-295">Catalog</span></span>|@Catalog|<span data-ttu-id="7dc20-296">db_name()</span><span class="sxs-lookup"><span data-stu-id="7dc20-296">db_name()</span></span>|<span data-ttu-id="7dc20-297">1</span><span class="sxs-lookup"><span data-stu-id="7dc20-297">1</span></span>|  
|<span data-ttu-id="7dc20-298">擁有者</span><span class="sxs-lookup"><span data-stu-id="7dc20-298">Owner</span></span>|@Owner|<span data-ttu-id="7dc20-299">user_name()</span><span class="sxs-lookup"><span data-stu-id="7dc20-299">user_name()</span></span>|<span data-ttu-id="7dc20-300">2</span><span class="sxs-lookup"><span data-stu-id="7dc20-300">2</span></span>|  
|<span data-ttu-id="7dc20-301">資料表</span><span class="sxs-lookup"><span data-stu-id="7dc20-301">Table</span></span>|@Table|<span data-ttu-id="7dc20-302">o.name</span><span class="sxs-lookup"><span data-stu-id="7dc20-302">o.name</span></span>|<span data-ttu-id="7dc20-303">3</span><span class="sxs-lookup"><span data-stu-id="7dc20-303">3</span></span>|  
  
### <a name="userdefinedtypes"></a><span data-ttu-id="7dc20-304">UserDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="7dc20-304">UserDefinedTypes</span></span>  
  
|<span data-ttu-id="7dc20-305">限制名稱</span><span class="sxs-lookup"><span data-stu-id="7dc20-305">Restriction Name</span></span>|<span data-ttu-id="7dc20-306">參數名稱</span><span class="sxs-lookup"><span data-stu-id="7dc20-306">Parameter Name</span></span>|<span data-ttu-id="7dc20-307">預設限制值</span><span class="sxs-lookup"><span data-stu-id="7dc20-307">Restriction Default</span></span>|<span data-ttu-id="7dc20-308">限制號碼</span><span class="sxs-lookup"><span data-stu-id="7dc20-308">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="7dc20-309">assembly_name</span><span class="sxs-lookup"><span data-stu-id="7dc20-309">assembly_name</span></span>|@AssemblyName|<span data-ttu-id="7dc20-310">assemblies.name</span><span class="sxs-lookup"><span data-stu-id="7dc20-310">assemblies.name</span></span>|<span data-ttu-id="7dc20-311">1</span><span class="sxs-lookup"><span data-stu-id="7dc20-311">1</span></span>|  
|<span data-ttu-id="7dc20-312">udt_name</span><span class="sxs-lookup"><span data-stu-id="7dc20-312">udt_name</span></span>|@UDTName|<span data-ttu-id="7dc20-313">types.assembly_class</span><span class="sxs-lookup"><span data-stu-id="7dc20-313">types.assembly_class</span></span>|<span data-ttu-id="7dc20-314">2</span><span class="sxs-lookup"><span data-stu-id="7dc20-314">2</span></span>|  
  
### <a name="foreignkeys"></a><span data-ttu-id="7dc20-315">ForeignKeys</span><span class="sxs-lookup"><span data-stu-id="7dc20-315">ForeignKeys</span></span>  
  
|<span data-ttu-id="7dc20-316">限制名稱</span><span class="sxs-lookup"><span data-stu-id="7dc20-316">Restriction Name</span></span>|<span data-ttu-id="7dc20-317">參數名稱</span><span class="sxs-lookup"><span data-stu-id="7dc20-317">Parameter Name</span></span>|<span data-ttu-id="7dc20-318">預設限制值</span><span class="sxs-lookup"><span data-stu-id="7dc20-318">Restriction Default</span></span>|<span data-ttu-id="7dc20-319">限制號碼</span><span class="sxs-lookup"><span data-stu-id="7dc20-319">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="7dc20-320">目錄</span><span class="sxs-lookup"><span data-stu-id="7dc20-320">Catalog</span></span>|@Catalog|<span data-ttu-id="7dc20-321">CONSTRAINT_CATALOG</span><span class="sxs-lookup"><span data-stu-id="7dc20-321">CONSTRAINT_CATALOG</span></span>|<span data-ttu-id="7dc20-322">1</span><span class="sxs-lookup"><span data-stu-id="7dc20-322">1</span></span>|  
|<span data-ttu-id="7dc20-323">擁有者</span><span class="sxs-lookup"><span data-stu-id="7dc20-323">Owner</span></span>|@Owner|<span data-ttu-id="7dc20-324">CONSTRAINT_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="7dc20-324">CONSTRAINT_SCHEMA</span></span>|<span data-ttu-id="7dc20-325">2</span><span class="sxs-lookup"><span data-stu-id="7dc20-325">2</span></span>|  
|<span data-ttu-id="7dc20-326">資料表</span><span class="sxs-lookup"><span data-stu-id="7dc20-326">Table</span></span>|@Table|<span data-ttu-id="7dc20-327">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="7dc20-327">TABLE_NAME</span></span>|<span data-ttu-id="7dc20-328">3</span><span class="sxs-lookup"><span data-stu-id="7dc20-328">3</span></span>|  
|<span data-ttu-id="7dc20-329">Name</span><span class="sxs-lookup"><span data-stu-id="7dc20-329">Name</span></span>|@Name|<span data-ttu-id="7dc20-330">CONSTRAINT_NAME</span><span class="sxs-lookup"><span data-stu-id="7dc20-330">CONSTRAINT_NAME</span></span>|<span data-ttu-id="7dc20-331">4</span><span class="sxs-lookup"><span data-stu-id="7dc20-331">4</span></span>|  
  
## <a name="sql-server-2008-schema-restrictions"></a><span data-ttu-id="7dc20-332">SQL Server 2008 結構描述限制</span><span class="sxs-lookup"><span data-stu-id="7dc20-332">SQL Server 2008 Schema Restrictions</span></span>  

 <span data-ttu-id="7dc20-333">下表將列出 SQL Server 2008 結構描述集合的限制。</span><span class="sxs-lookup"><span data-stu-id="7dc20-333">The following tables list the restrictions for SQL Server 2008 schema collections.</span></span> <span data-ttu-id="7dc20-334">從 .NET Framework 3.5 版 SP1 和 SQL Server 2008 開始，這些限制便有效。</span><span class="sxs-lookup"><span data-stu-id="7dc20-334">These restrictions are valid beginning with version 3.5 SP1 of the .NET Framework and SQL Server 2008.</span></span> <span data-ttu-id="7dc20-335">舊版 .NET Framework 和 SQL Server 不支援它們。</span><span class="sxs-lookup"><span data-stu-id="7dc20-335">They are not supported in earlier versions of the .NET Framework and SQL Server.</span></span>  
  
### <a name="columnsetcolumns"></a><span data-ttu-id="7dc20-336">ColumnSetColumns</span><span class="sxs-lookup"><span data-stu-id="7dc20-336">ColumnSetColumns</span></span>  
  
|<span data-ttu-id="7dc20-337">限制名稱</span><span class="sxs-lookup"><span data-stu-id="7dc20-337">Restriction Name</span></span>|<span data-ttu-id="7dc20-338">參數名稱</span><span class="sxs-lookup"><span data-stu-id="7dc20-338">Parameter Name</span></span>|<span data-ttu-id="7dc20-339">預設限制值</span><span class="sxs-lookup"><span data-stu-id="7dc20-339">Restriction Default</span></span>|<span data-ttu-id="7dc20-340">限制號碼</span><span class="sxs-lookup"><span data-stu-id="7dc20-340">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="7dc20-341">目錄</span><span class="sxs-lookup"><span data-stu-id="7dc20-341">Catalog</span></span>|@Catalog|<span data-ttu-id="7dc20-342">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="7dc20-342">TABLE_CATALOG</span></span>|<span data-ttu-id="7dc20-343">1</span><span class="sxs-lookup"><span data-stu-id="7dc20-343">1</span></span>|  
|<span data-ttu-id="7dc20-344">擁有者</span><span class="sxs-lookup"><span data-stu-id="7dc20-344">Owner</span></span>|@Owner|<span data-ttu-id="7dc20-345">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="7dc20-345">TABLE_SCHEMA</span></span>|<span data-ttu-id="7dc20-346">2</span><span class="sxs-lookup"><span data-stu-id="7dc20-346">2</span></span>|  
|<span data-ttu-id="7dc20-347">資料表</span><span class="sxs-lookup"><span data-stu-id="7dc20-347">Table</span></span>|@Table|<span data-ttu-id="7dc20-348">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="7dc20-348">TABLE_NAME</span></span>|<span data-ttu-id="7dc20-349">3</span><span class="sxs-lookup"><span data-stu-id="7dc20-349">3</span></span>|  
  
### <a name="allcolumns"></a><span data-ttu-id="7dc20-350">AllColumns</span><span class="sxs-lookup"><span data-stu-id="7dc20-350">AllColumns</span></span>  
  
|<span data-ttu-id="7dc20-351">限制名稱</span><span class="sxs-lookup"><span data-stu-id="7dc20-351">Restriction Name</span></span>|<span data-ttu-id="7dc20-352">參數名稱</span><span class="sxs-lookup"><span data-stu-id="7dc20-352">Parameter Name</span></span>|<span data-ttu-id="7dc20-353">預設限制值</span><span class="sxs-lookup"><span data-stu-id="7dc20-353">Restriction Default</span></span>|<span data-ttu-id="7dc20-354">限制號碼</span><span class="sxs-lookup"><span data-stu-id="7dc20-354">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="7dc20-355">目錄</span><span class="sxs-lookup"><span data-stu-id="7dc20-355">Catalog</span></span>|@Catalog|<span data-ttu-id="7dc20-356">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="7dc20-356">TABLE_CATALOG</span></span>|<span data-ttu-id="7dc20-357">1</span><span class="sxs-lookup"><span data-stu-id="7dc20-357">1</span></span>|  
|<span data-ttu-id="7dc20-358">擁有者</span><span class="sxs-lookup"><span data-stu-id="7dc20-358">Owner</span></span>|@Owner|<span data-ttu-id="7dc20-359">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="7dc20-359">TABLE_SCHEMA</span></span>|<span data-ttu-id="7dc20-360">2</span><span class="sxs-lookup"><span data-stu-id="7dc20-360">2</span></span>|  
|<span data-ttu-id="7dc20-361">資料表</span><span class="sxs-lookup"><span data-stu-id="7dc20-361">Table</span></span>|@Table|<span data-ttu-id="7dc20-362">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="7dc20-362">TABLE_NAME</span></span>|<span data-ttu-id="7dc20-363">3</span><span class="sxs-lookup"><span data-stu-id="7dc20-363">3</span></span>|  
|<span data-ttu-id="7dc20-364">資料行</span><span class="sxs-lookup"><span data-stu-id="7dc20-364">Column</span></span>|@Column|<span data-ttu-id="7dc20-365">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="7dc20-365">COLUMN_NAME</span></span>|<span data-ttu-id="7dc20-366">4</span><span class="sxs-lookup"><span data-stu-id="7dc20-366">4</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7dc20-367">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7dc20-367">See also</span></span>

- <span data-ttu-id="7dc20-368">[ADO.NET 概觀](ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="7dc20-368">[ADO.NET Overview](ado-net-overview.md)</span></span>
