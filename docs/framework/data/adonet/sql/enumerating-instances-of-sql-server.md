---
title: 列舉 SQL Server 執行個體 (ADO.NET)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ddf1c83c-9d40-45e6-b04d-9828c6cbbfdc
ms.openlocfilehash: c464762e82a24aab399a23ecb26420b5dce61f55
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782384"
---
# <a name="enumerating-instances-of-sql-server-adonet"></a><span data-ttu-id="08cb1-102">列舉 SQL Server 執行個體 (ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="08cb1-102">Enumerating Instances of SQL Server (ADO.NET)</span></span>
<span data-ttu-id="08cb1-103">SQL Server 允許應用程式在目前網路內尋找 SQL Server 實例。</span><span class="sxs-lookup"><span data-stu-id="08cb1-103">SQL Server permits applications to find SQL Server instances within the current network.</span></span> <span data-ttu-id="08cb1-104"><xref:System.Data.Sql.SqlDataSourceEnumerator> 類別會將此資訊公開至應用程式開發人員，並提供包含所有可見伺服器之相關資訊的 <xref:System.Data.DataTable>。</span><span class="sxs-lookup"><span data-stu-id="08cb1-104">The <xref:System.Data.Sql.SqlDataSourceEnumerator> class exposes this information to the application developer, providing a <xref:System.Data.DataTable> containing information about all the visible servers.</span></span> <span data-ttu-id="08cb1-105">這個傳回的資料表包含網路上可用的伺服器實例清單，此清單會符合使用者嘗試建立新連接時所提供的清單，並展開包含連接屬性上所有可用伺服器的下拉式清單對話方塊。</span><span class="sxs-lookup"><span data-stu-id="08cb1-105">This returned table contains a list of server instances available on the network that matches the list provided when a user attempts to create a new connection, and expands the drop-down list containing all the available servers on the **Connection Properties** dialog box.</span></span> <span data-ttu-id="08cb1-106">顯示的結果不一定是完整的。</span><span class="sxs-lookup"><span data-stu-id="08cb1-106">The results displayed are not always complete.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="08cb1-107">與大部分的 Windows 服務一樣，最好使用儘可能少的權限來執行 SQL Browser 服務。</span><span class="sxs-lookup"><span data-stu-id="08cb1-107">As with most Windows services, it is best to run the SQL Browser service with the least possible privileges.</span></span> <span data-ttu-id="08cb1-108">如需 SQL Browser 服務及如何管理其行為的詳細資訊，請參閱《SQL Server 線上叢書》。</span><span class="sxs-lookup"><span data-stu-id="08cb1-108">See SQL Server Books Online for more information on the SQL Browser service, and how to manage its behavior.</span></span>  
  
## <a name="retrieving-an-enumerator-instance"></a><span data-ttu-id="08cb1-109">擷取列舉值執行個體</span><span class="sxs-lookup"><span data-stu-id="08cb1-109">Retrieving an Enumerator Instance</span></span>  
 <span data-ttu-id="08cb1-110">若要擷取包含可用 SQL Server 執行個體相關資訊的資料表，必須先使用共用/靜態 <xref:System.Data.Sql.SqlDataSourceEnumerator.Instance%2A> 屬性擷取列舉值：</span><span class="sxs-lookup"><span data-stu-id="08cb1-110">In order to retrieve the table containing information about the available SQL Server instances, you must first retrieve an enumerator, using the shared/static <xref:System.Data.Sql.SqlDataSourceEnumerator.Instance%2A> property:</span></span>  
  
```vb  
Dim instance As System.Data.Sql.SqlDataSourceEnumerator = _  
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
```csharp  
System.Data.Sql.SqlDataSourceEnumerator instance =   
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
 <span data-ttu-id="08cb1-111">擷取靜態執行個體後，您就可以呼叫 <xref:System.Data.Sql.SqlDataSourceEnumerator.GetDataSources%2A> 方法，它可用來傳回包含可用伺服器相關資訊的 <xref:System.Data.DataTable>：</span><span class="sxs-lookup"><span data-stu-id="08cb1-111">Once you have retrieved the static instance, you can call the <xref:System.Data.Sql.SqlDataSourceEnumerator.GetDataSources%2A> method, which returns a <xref:System.Data.DataTable> containing information about the available servers:</span></span>  
  
```vb  
Dim dataTable As System.Data.DataTable = instance.GetDataSources()  
```  
  
```csharp  
System.Data.DataTable dataTable = instance.GetDataSources();  
```  
  
 <span data-ttu-id="08cb1-112">從方法呼叫傳回的資料表包含下列資料行 (其中都包含 `string` 值)：</span><span class="sxs-lookup"><span data-stu-id="08cb1-112">The table returned from the method call contains the following columns, all of which contain `string` values:</span></span>  
  
|<span data-ttu-id="08cb1-113">「資料行」</span><span class="sxs-lookup"><span data-stu-id="08cb1-113">Column</span></span>|<span data-ttu-id="08cb1-114">描述</span><span class="sxs-lookup"><span data-stu-id="08cb1-114">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="08cb1-115">**ServerName**</span><span class="sxs-lookup"><span data-stu-id="08cb1-115">**ServerName**</span></span>|<span data-ttu-id="08cb1-116">伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="08cb1-116">Name of the server.</span></span>|  
|<span data-ttu-id="08cb1-117">**InstanceName**</span><span class="sxs-lookup"><span data-stu-id="08cb1-117">**InstanceName**</span></span>|<span data-ttu-id="08cb1-118">伺服器執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="08cb1-118">Name of the server instance.</span></span> <span data-ttu-id="08cb1-119">如果伺服器做為預設執行個體執行，則此處為空白。</span><span class="sxs-lookup"><span data-stu-id="08cb1-119">Blank if the server is running as the default instance.</span></span>|  
|<span data-ttu-id="08cb1-120">**IsClustered**</span><span class="sxs-lookup"><span data-stu-id="08cb1-120">**IsClustered**</span></span>|<span data-ttu-id="08cb1-121">表示伺服器是否為叢集的一部分。</span><span class="sxs-lookup"><span data-stu-id="08cb1-121">Indicates whether the server is part of a cluster.</span></span>|  
|<span data-ttu-id="08cb1-122">**版本**</span><span class="sxs-lookup"><span data-stu-id="08cb1-122">**Version**</span></span>|<span data-ttu-id="08cb1-123">伺服器版本。</span><span class="sxs-lookup"><span data-stu-id="08cb1-123">Version of the server.</span></span> <span data-ttu-id="08cb1-124">例如：</span><span class="sxs-lookup"><span data-stu-id="08cb1-124">For example:</span></span><br /><br /> <span data-ttu-id="08cb1-125">-9.00. x （SQL Server 2005）</span><span class="sxs-lookup"><span data-stu-id="08cb1-125">-   9.00.x (SQL Server 2005)</span></span><br /><span data-ttu-id="08cb1-126">-10.0. xx （SQL Server 2008）</span><span class="sxs-lookup"><span data-stu-id="08cb1-126">-   10.0.xx (SQL Server 2008)</span></span><br /><span data-ttu-id="08cb1-127">-10.50. x （SQL Server 2008 R2）</span><span class="sxs-lookup"><span data-stu-id="08cb1-127">-   10.50.x (SQL Server 2008 R2)</span></span><br /><span data-ttu-id="08cb1-128">-11.0. xx （SQL Server 2012）</span><span class="sxs-lookup"><span data-stu-id="08cb1-128">-   11.0.xx (SQL Server 2012)</span></span>|  
  
## <a name="enumeration-limitations"></a><span data-ttu-id="08cb1-129">列舉型別限制</span><span class="sxs-lookup"><span data-stu-id="08cb1-129">Enumeration Limitations</span></span>  
 <span data-ttu-id="08cb1-130">可能會，也可能不會列出所有可用的伺服器。</span><span class="sxs-lookup"><span data-stu-id="08cb1-130">All of the available servers may or may not be listed.</span></span> <span data-ttu-id="08cb1-131">此清單需視逾時及網路流量之類的因素而定。</span><span class="sxs-lookup"><span data-stu-id="08cb1-131">The list can vary depending on factors such as timeouts and network traffic.</span></span> <span data-ttu-id="08cb1-132">這可能會導致兩個連續呼叫的清單不同，</span><span class="sxs-lookup"><span data-stu-id="08cb1-132">This can cause the list to be different on two consecutive calls.</span></span> <span data-ttu-id="08cb1-133">而只會列出相同網路上的伺服器。</span><span class="sxs-lookup"><span data-stu-id="08cb1-133">Only servers on the same network will be listed.</span></span> <span data-ttu-id="08cb1-134">廣播封包通常不會周遊路由器，因此您可能看不到某個列出的伺服器，但它在所有呼叫中都是穩定的。</span><span class="sxs-lookup"><span data-stu-id="08cb1-134">Broadcast packets typically won't traverse routers, which is why you may not see a server listed, but it will be stable across calls.</span></span>  
  
 <span data-ttu-id="08cb1-135">列出的伺服器不一定具有 `IsClustered` 及版本之類的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="08cb1-135">Listed servers may or may not have additional information such as `IsClustered` and version.</span></span> <span data-ttu-id="08cb1-136">這要視取得清單的方式而定。</span><span class="sxs-lookup"><span data-stu-id="08cb1-136">This is dependent on how the list was obtained.</span></span> <span data-ttu-id="08cb1-137">透過 SQL Server 瀏覽器服務列出的伺服器所具有的詳細資訊，要多於透過 Windows 基礎結構找到的伺服器 (僅列出名稱)。</span><span class="sxs-lookup"><span data-stu-id="08cb1-137">Servers listed through the SQL Server browser service will have more details than those found through the Windows infrastructure, which will list only the name.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="08cb1-138">只有在完全信任下執行時，伺服器列舉型別才可使用。</span><span class="sxs-lookup"><span data-stu-id="08cb1-138">Server enumeration is only available when running in full-trust.</span></span> <span data-ttu-id="08cb1-139">執行在部分信任環境中的組件即使具有 <xref:System.Data.SqlClient.SqlClientPermission> 程式碼存取安全性 (CAS) 使用權限，也無法使用伺服器列舉型別。</span><span class="sxs-lookup"><span data-stu-id="08cb1-139">Assemblies running in a partially-trusted environment will not be able to use it, even if they have the <xref:System.Data.SqlClient.SqlClientPermission> Code Access Security (CAS) permission.</span></span>  
  
 <span data-ttu-id="08cb1-140">SQL Server 透過使用名為<xref:System.Data.Sql.SqlDataSourceEnumerator> SQL Browser 的外部 Windows 服務，提供的資訊。</span><span class="sxs-lookup"><span data-stu-id="08cb1-140">SQL Server provides information for the <xref:System.Data.Sql.SqlDataSourceEnumerator> through the use of an external Windows service named SQL Browser.</span></span> <span data-ttu-id="08cb1-141">依預設會啟用此服務，但系統管理員可能會關閉或停用服務，讓此類別看不到伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="08cb1-141">This service is enabled by default, but administrators may turn it off or disable it, making the server instance invisible to this class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="08cb1-142">範例</span><span class="sxs-lookup"><span data-stu-id="08cb1-142">Example</span></span>  
 <span data-ttu-id="08cb1-143">下列主控台應用程式會擷取所有可見 SQL Server 執行個體的相關資訊，並在主控台視窗中顯示資訊。</span><span class="sxs-lookup"><span data-stu-id="08cb1-143">The following console application retrieves information about all of the visible SQL Server instances and displays the information in the console window.</span></span>  
  
```vb  
Imports System.Data.Sql  
  
Module Module1  
  Sub Main()  
    ' Retrieve the enumerator instance and then the data.  
    Dim instance As SqlDataSourceEnumerator = _  
     SqlDataSourceEnumerator.Instance  
    Dim table As System.Data.DataTable = instance.GetDataSources()  
  
    ' Display the contents of the table.  
    DisplayData(table)  
  
    Console.WriteLine("Press any key to continue.")  
    Console.ReadKey()  
  End Sub  
  
  Private Sub DisplayData(ByVal table As DataTable)  
    For Each row As DataRow In table.Rows  
      For Each col As DataColumn In table.Columns  
        Console.WriteLine("{0} = {1}", col.ColumnName, row(col))  
      Next  
      Console.WriteLine("============================")  
    Next  
  End Sub  
End Module  
```  
  
```csharp  
using System.Data.Sql;  
  
class Program  
{  
  static void Main()  
  {  
    // Retrieve the enumerator instance and then the data.  
    SqlDataSourceEnumerator instance =  
      SqlDataSourceEnumerator.Instance;  
    System.Data.DataTable table = instance.GetDataSources();  
  
    // Display the contents of the table.  
    DisplayData(table);  
  
    Console.WriteLine("Press any key to continue.");  
    Console.ReadKey();  
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
  
## <a name="see-also"></a><span data-ttu-id="08cb1-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="08cb1-144">See also</span></span>

- [<span data-ttu-id="08cb1-145">SQL Server 和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="08cb1-145">SQL Server and ADO.NET</span></span>](index.md)
- [<span data-ttu-id="08cb1-146">ADO.NET 概觀</span><span class="sxs-lookup"><span data-stu-id="08cb1-146">ADO.NET Overview</span></span>](../ado-net-overview.md)
