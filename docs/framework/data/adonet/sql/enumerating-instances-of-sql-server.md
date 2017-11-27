---
title: "列舉 SQL Server 執行個體 (ADO.NET)"
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
ms.assetid: ddf1c83c-9d40-45e6-b04d-9828c6cbbfdc
caps.latest.revision: "8"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 99111cb9e48bd5ccd4463afcee6b78bc2387cf7b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="enumerating-instances-of-sql-server-adonet"></a><span data-ttu-id="23df8-102">列舉 SQL Server 執行個體 (ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="23df8-102">Enumerating Instances of SQL Server (ADO.NET)</span></span>
[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]<span data-ttu-id="23df8-103"> 允許應用程式在目前網路內尋找 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="23df8-103"> permits applications to find [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] instances within the current network.</span></span> <span data-ttu-id="23df8-104"><xref:System.Data.Sql.SqlDataSourceEnumerator> 類別會將此資訊公開至應用程式開發人員，並提供包含所有可見伺服器之相關資訊的 <xref:System.Data.DataTable>。</span><span class="sxs-lookup"><span data-stu-id="23df8-104">The <xref:System.Data.Sql.SqlDataSourceEnumerator> class exposes this information to the application developer, providing a <xref:System.Data.DataTable> containing information about all the visible servers.</span></span> <span data-ttu-id="23df8-105">傳回這個資料表包含一份符合使用者嘗試建立新的連接時所提供的清單，並展開下拉式清單包含所有可用的伺服器上的網路上可用的伺服器執行個體**連線屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="23df8-105">This returned table contains a list of server instances available on the network that matches the list provided when a user attempts to create a new connection, and expands the drop-down list containing all the available servers on the **Connection Properties** dialog box.</span></span> <span data-ttu-id="23df8-106">顯示的結果不一定是完整的。</span><span class="sxs-lookup"><span data-stu-id="23df8-106">The results displayed are not always complete.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="23df8-107">與大部分的 Windows 服務一樣，最好使用儘可能少的權限來執行 SQL Browser 服務。</span><span class="sxs-lookup"><span data-stu-id="23df8-107">As with most Windows services, it is best to run the SQL Browser service with the least possible privileges.</span></span> <span data-ttu-id="23df8-108">如需 SQL Browser 服務及如何管理其行為的詳細資訊，請參閱《[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 線上叢書》。</span><span class="sxs-lookup"><span data-stu-id="23df8-108">See [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Books Online for more information on the SQL Browser service, and how to manage its behavior.</span></span>  
  
## <a name="retrieving-an-enumerator-instance"></a><span data-ttu-id="23df8-109">擷取列舉值執行個體</span><span class="sxs-lookup"><span data-stu-id="23df8-109">Retrieving an Enumerator Instance</span></span>  
 <span data-ttu-id="23df8-110">若要擷取包含可用 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 執行個體相關資訊的資料表，您必須先使用共用/靜態 <xref:System.Data.Sql.SqlDataSourceEnumerator.Instance%2A> 屬性擷取列舉值：</span><span class="sxs-lookup"><span data-stu-id="23df8-110">In order to retrieve the table containing information about the available [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] instances, you must first retrieve an enumerator, using the shared/static <xref:System.Data.Sql.SqlDataSourceEnumerator.Instance%2A> property:</span></span>  
  
```vb  
Dim instance As System.Data.Sql.SqlDataSourceEnumerator = _  
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
```csharp  
System.Data.Sql.SqlDataSourceEnumerator instance =   
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
 <span data-ttu-id="23df8-111">擷取靜態執行個體後，您就可以呼叫 <xref:System.Data.Sql.SqlDataSourceEnumerator.GetDataSources%2A> 方法，它可用來傳回包含可用伺服器相關資訊的 <xref:System.Data.DataTable>：</span><span class="sxs-lookup"><span data-stu-id="23df8-111">Once you have retrieved the static instance, you can call the <xref:System.Data.Sql.SqlDataSourceEnumerator.GetDataSources%2A> method, which returns a <xref:System.Data.DataTable> containing information about the available servers:</span></span>  
  
```vb  
Dim dataTable As System.Data.DataTable = instance.GetDataSources()  
```  
  
```csharp  
System.Data.DataTable dataTable = instance.GetDataSources();  
```  
  
 <span data-ttu-id="23df8-112">從方法呼叫傳回的資料表包含下列資料行 (其中都包含 `string` 值)：</span><span class="sxs-lookup"><span data-stu-id="23df8-112">The table returned from the method call contains the following columns, all of which contain `string` values:</span></span>  
  
|<span data-ttu-id="23df8-113">Column</span><span class="sxs-lookup"><span data-stu-id="23df8-113">Column</span></span>|<span data-ttu-id="23df8-114">說明</span><span class="sxs-lookup"><span data-stu-id="23df8-114">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="23df8-115">**伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="23df8-115">**ServerName**</span></span>|<span data-ttu-id="23df8-116">伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="23df8-116">Name of the server.</span></span>|  
|<span data-ttu-id="23df8-117">**執行個體名稱**</span><span class="sxs-lookup"><span data-stu-id="23df8-117">**InstanceName**</span></span>|<span data-ttu-id="23df8-118">伺服器執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="23df8-118">Name of the server instance.</span></span> <span data-ttu-id="23df8-119">如果伺服器做為預設執行個體執行，則此處為空白。</span><span class="sxs-lookup"><span data-stu-id="23df8-119">Blank if the server is running as the default instance.</span></span>|  
|<span data-ttu-id="23df8-120">**IsClustered**</span><span class="sxs-lookup"><span data-stu-id="23df8-120">**IsClustered**</span></span>|<span data-ttu-id="23df8-121">表示伺服器是否為叢集的一部分。</span><span class="sxs-lookup"><span data-stu-id="23df8-121">Indicates whether the server is part of a cluster.</span></span>|  
|<span data-ttu-id="23df8-122">**版本**</span><span class="sxs-lookup"><span data-stu-id="23df8-122">**Version**</span></span>|<span data-ttu-id="23df8-123">伺服器版本。</span><span class="sxs-lookup"><span data-stu-id="23df8-123">Version of the server.</span></span> <span data-ttu-id="23df8-124">例如: </span><span class="sxs-lookup"><span data-stu-id="23df8-124">For example:</span></span><br /><br /> <span data-ttu-id="23df8-125">-9.00.x ([!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)])</span><span class="sxs-lookup"><span data-stu-id="23df8-125">-   9.00.x ([!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)])</span></span><br /><span data-ttu-id="23df8-126">-10.0.xx ([!INCLUDE[ssKatmai](../../../../../includes/sskatmai-md.md)])</span><span class="sxs-lookup"><span data-stu-id="23df8-126">-   10.0.xx ([!INCLUDE[ssKatmai](../../../../../includes/sskatmai-md.md)])</span></span><br /><span data-ttu-id="23df8-127">-10.50.x ([!INCLUDE[ssKilimanjaro](../../../../../includes/sskilimanjaro-md.md)])</span><span class="sxs-lookup"><span data-stu-id="23df8-127">-   10.50.x ([!INCLUDE[ssKilimanjaro](../../../../../includes/sskilimanjaro-md.md)])</span></span><br /><span data-ttu-id="23df8-128">-11.0.xx ([!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 2012年)</span><span class="sxs-lookup"><span data-stu-id="23df8-128">-   11.0.xx ([!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 2012)</span></span>|  
  
## <a name="enumeration-limitations"></a><span data-ttu-id="23df8-129">列舉型別限制</span><span class="sxs-lookup"><span data-stu-id="23df8-129">Enumeration Limitations</span></span>  
 <span data-ttu-id="23df8-130">可能會，也可能不會列出所有可用的伺服器。</span><span class="sxs-lookup"><span data-stu-id="23df8-130">All of the available servers may or may not be listed.</span></span> <span data-ttu-id="23df8-131">此清單需視逾時及網路流量之類的因素而定。</span><span class="sxs-lookup"><span data-stu-id="23df8-131">The list can vary depending on factors such as timeouts and network traffic.</span></span> <span data-ttu-id="23df8-132">這可能會導致兩個連續呼叫的清單不同，</span><span class="sxs-lookup"><span data-stu-id="23df8-132">This can cause the list to be different on two consecutive calls.</span></span> <span data-ttu-id="23df8-133">而只會列出相同網路上的伺服器。</span><span class="sxs-lookup"><span data-stu-id="23df8-133">Only servers on the same network will be listed.</span></span> <span data-ttu-id="23df8-134">廣播封包通常不會周遊路由器，因此您可能看不到某個列出的伺服器，但它在所有呼叫中都是穩定的。</span><span class="sxs-lookup"><span data-stu-id="23df8-134">Broadcast packets typically won't traverse routers, which is why you may not see a server listed, but it will be stable across calls.</span></span>  
  
 <span data-ttu-id="23df8-135">列出的伺服器不一定具有 `IsClustered` 及版本之類的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="23df8-135">Listed servers may or may not have additional information such as `IsClustered` and version.</span></span> <span data-ttu-id="23df8-136">這要視取得清單的方式而定。</span><span class="sxs-lookup"><span data-stu-id="23df8-136">This is dependent on how the list was obtained.</span></span> <span data-ttu-id="23df8-137">透過 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Browser 服務列出的伺服器所具有的詳細資訊，要多於透過 Windows 基礎結構找到的伺服器 (僅列出名稱)。</span><span class="sxs-lookup"><span data-stu-id="23df8-137">Servers listed through the [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] browser service will have more details than those found through the Windows infrastructure, which will list only the name.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="23df8-138">只有在完全信任下執行時，伺服器列舉型別才可使用。</span><span class="sxs-lookup"><span data-stu-id="23df8-138">Server enumeration is only available when running in full-trust.</span></span> <span data-ttu-id="23df8-139">執行在部分信任環境中的組件即使具有 <xref:System.Data.SqlClient.SqlClientPermission> 程式碼存取安全性 (CAS) 使用權限，也無法使用伺服器列舉型別。</span><span class="sxs-lookup"><span data-stu-id="23df8-139">Assemblies running in a partially-trusted environment will not be able to use it, even if they have the <xref:System.Data.SqlClient.SqlClientPermission> Code Access Security (CAS) permission.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]<span data-ttu-id="23df8-140"> 可藉由使用名為 SQL Browser 的外部 Windows 服務來提供 <xref:System.Data.Sql.SqlDataSourceEnumerator> 相關資訊。</span><span class="sxs-lookup"><span data-stu-id="23df8-140"> provides information for the <xref:System.Data.Sql.SqlDataSourceEnumerator> through the use of an external Windows service named SQL Browser.</span></span> <span data-ttu-id="23df8-141">依預設會啟用此服務，但系統管理員可能會關閉或停用服務，讓此類別看不到伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="23df8-141">This service is enabled by default, but administrators may turn it off or disable it, making the server instance invisible to this class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="23df8-142">範例</span><span class="sxs-lookup"><span data-stu-id="23df8-142">Example</span></span>  
 <span data-ttu-id="23df8-143">下列主控台應用程式會擷取所有可見 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 執行個體的相關資訊，並在主控台視窗中顯示資訊。</span><span class="sxs-lookup"><span data-stu-id="23df8-143">The following console application retrieves information about all of the visible [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] instances and displays the information in the console window.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="23df8-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="23df8-144">See Also</span></span>  
 [<span data-ttu-id="23df8-145">SQL Server 和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="23df8-145">SQL Server and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/index.md)  
 [<span data-ttu-id="23df8-146">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="23df8-146">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
