---
title: 效能計數器
description: 使用 ADO.NET 效能計數器，以使用 Windows 效能監視器或以程式設計的方式監視您的應用程式狀態及其連接資源。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0b121b71-78f8-4ae2-9aa1-0b2e15778e57
ms.openlocfilehash: 4f645a51996078f8dd80b6c455c420633db36155
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164595"
---
# <a name="performance-counters-in-adonet"></a><span data-ttu-id="9f865-103">ADO.NET 中的效能計數器</span><span class="sxs-lookup"><span data-stu-id="9f865-103">Performance Counters in ADO.NET</span></span>

<span data-ttu-id="9f865-104">ADO.NET 2.0 導入了對效能計數器的擴充支援，其中包含對 <xref:System.Data.SqlClient> 和 <xref:System.Data.OracleClient> 的支援。</span><span class="sxs-lookup"><span data-stu-id="9f865-104">ADO.NET 2.0 introduced expanded support for performance counters that includes support for both <xref:System.Data.SqlClient> and <xref:System.Data.OracleClient>.</span></span> <span data-ttu-id="9f865-105">舊版 ADO.NET 中提供的 <xref:System.Data.SqlClient> 效能計數器已被本主題中討論的新效能計數器取代。</span><span class="sxs-lookup"><span data-stu-id="9f865-105">The <xref:System.Data.SqlClient> performance counters available in previous versions of ADO.NET have been deprecated and replaced with the new performance counters discussed in this topic.</span></span> <span data-ttu-id="9f865-106">您可以使用 ADO.NET 效能計數器來監控應用程式的狀態及其使用的連接資源。</span><span class="sxs-lookup"><span data-stu-id="9f865-106">You can use ADO.NET performance counters to monitor the status of your application and the connection resources that it uses.</span></span> <span data-ttu-id="9f865-107">效能計數器可藉由「Windows 效能監視器」來進行監視，或可藉由 <xref:System.Diagnostics.PerformanceCounter> 命名空間 (Namespace) 中的 <xref:System.Diagnostics> 類別以程式設計的方式存取。</span><span class="sxs-lookup"><span data-stu-id="9f865-107">Performance counters can be monitored by using Windows Performance Monitor or can be accessed programmatically using the <xref:System.Diagnostics.PerformanceCounter> class in the <xref:System.Diagnostics> namespace.</span></span>  
  
## <a name="available-performance-counters"></a><span data-ttu-id="9f865-108">可用的效能計數器</span><span class="sxs-lookup"><span data-stu-id="9f865-108">Available Performance Counters</span></span>  

 <span data-ttu-id="9f865-109">目前有 14 種不同的效能計數器可供 <xref:System.Data.SqlClient> 和 <xref:System.Data.OracleClient> 使用 (如下表所述)。</span><span class="sxs-lookup"><span data-stu-id="9f865-109">Currently there are 14 different performance counters available for <xref:System.Data.SqlClient> and <xref:System.Data.OracleClient> as described in the following table.</span></span> <span data-ttu-id="9f865-110">請注意，個別計數器的名稱並未在 Microsoft .NET Framework 的區域版本中當地語系化。</span><span class="sxs-lookup"><span data-stu-id="9f865-110">Note that the names for the individual counters are not localized across regional versions of the Microsoft .NET Framework.</span></span>  
  
|<span data-ttu-id="9f865-111">效能計數器</span><span class="sxs-lookup"><span data-stu-id="9f865-111">Performance counter</span></span>|<span data-ttu-id="9f865-112">描述</span><span class="sxs-lookup"><span data-stu-id="9f865-112">Description</span></span>|  
|-------------------------|-----------------|  
|`HardConnectsPerSecond`|<span data-ttu-id="9f865-113">每秒鐘對資料庫伺服器所建立的連接數目。</span><span class="sxs-lookup"><span data-stu-id="9f865-113">The number of connections per second that are being made to a database server.</span></span>|  
|`HardDisconnectsPerSecond`|<span data-ttu-id="9f865-114">每秒鐘對資料庫伺服器所進行的中斷連接數目。</span><span class="sxs-lookup"><span data-stu-id="9f865-114">The number of disconnects per second that are being made to a database server.</span></span>|  
|`NumberOfActiveConnectionPoolGroups`|<span data-ttu-id="9f865-115">使用中的唯一連接集區群組的數目。</span><span class="sxs-lookup"><span data-stu-id="9f865-115">The number of unique connection pool groups that are active.</span></span> <span data-ttu-id="9f865-116">這個計數器是由 AppDomain 中找到的唯一連接字串數目所控制。</span><span class="sxs-lookup"><span data-stu-id="9f865-116">This counter is controlled by the number of unique connection strings that are found in the AppDomain.</span></span>|  
|`NumberOfActiveConnectionPools`|<span data-ttu-id="9f865-117">連接集區的總數。</span><span class="sxs-lookup"><span data-stu-id="9f865-117">The total number of connection pools.</span></span>|  
|`NumberOfActiveConnections`|<span data-ttu-id="9f865-118">目前使用中的現用連接的數目。</span><span class="sxs-lookup"><span data-stu-id="9f865-118">The number of active connections that are currently in use.</span></span> <span data-ttu-id="9f865-119">**注意：**  預設不會啟用此效能計數器。</span><span class="sxs-lookup"><span data-stu-id="9f865-119">**Note:**  This performance counter is not enabled by default.</span></span> <span data-ttu-id="9f865-120">若要啟用此效能計數器，請參閱啟用 [預設為預設的計數器](#ActivatingOffByDefault)。</span><span class="sxs-lookup"><span data-stu-id="9f865-120">To enable this performance counter, see [Activating Off-By-Default Counters](#ActivatingOffByDefault).</span></span>|  
|`NumberOfFreeConnections`|<span data-ttu-id="9f865-121">連接集區中可用的連接數目。</span><span class="sxs-lookup"><span data-stu-id="9f865-121">The number of connections available for use in the connection pools.</span></span> <span data-ttu-id="9f865-122">**注意：**  預設不會啟用此效能計數器。</span><span class="sxs-lookup"><span data-stu-id="9f865-122">**Note:**  This performance counter is not enabled by default.</span></span> <span data-ttu-id="9f865-123">若要啟用此效能計數器，請參閱啟用 [預設為預設的計數器](#ActivatingOffByDefault)。</span><span class="sxs-lookup"><span data-stu-id="9f865-123">To enable this performance counter, see [Activating Off-By-Default Counters](#ActivatingOffByDefault).</span></span>|  
|`NumberOfInactiveConnectionPoolGroups`|<span data-ttu-id="9f865-124">標示為清除的唯一連接集區群組的數目。</span><span class="sxs-lookup"><span data-stu-id="9f865-124">The number of unique connection pool groups that are marked for pruning.</span></span> <span data-ttu-id="9f865-125">這個計數器是由 AppDomain 中找到的唯一連接字串數目所控制。</span><span class="sxs-lookup"><span data-stu-id="9f865-125">This counter is controlled by the number of unique connection strings that are found in the AppDomain.</span></span>|  
|`NumberOfInactiveConnectionPools`|<span data-ttu-id="9f865-126">最近未有任何活動且正等候處置 (Dispose) 的非現用連接集區數目。</span><span class="sxs-lookup"><span data-stu-id="9f865-126">The number of inactive connection pools that have not had any recent activity and are waiting to be disposed.</span></span>|  
|`NumberOfNonPooledConnections`|<span data-ttu-id="9f865-127">尚未共用的現用連接的數目。</span><span class="sxs-lookup"><span data-stu-id="9f865-127">The number of active connections that are not pooled.</span></span>|  
|`NumberOfPooledConnections`|<span data-ttu-id="9f865-128">正由連接共用基礎結構所管理的現用連接的數目。</span><span class="sxs-lookup"><span data-stu-id="9f865-128">The number of active connections that are being managed by the connection pooling infrastructure.</span></span>|  
|`NumberOfReclaimedConnections`|<span data-ttu-id="9f865-129">已透過記憶體回收作業回收的連接數目，其中 `Close` 或 `Dispose` 並非由應用程式呼叫。</span><span class="sxs-lookup"><span data-stu-id="9f865-129">The number of connections that have been reclaimed through garbage collection where `Close` or `Dispose` was not called by the application.</span></span> <span data-ttu-id="9f865-130">未明確關閉或處置連接都會損及效能。</span><span class="sxs-lookup"><span data-stu-id="9f865-130">Not explicitly closing or disposing connections hurts performance.</span></span>|  
|`NumberOfStasisConnections`|<span data-ttu-id="9f865-131">目前正等候動作完成因此無法提供應用程式使用的連接數目。</span><span class="sxs-lookup"><span data-stu-id="9f865-131">The number of connections currently awaiting completion of an action and which are therefore unavailable for use by your application.</span></span>|  
|`SoftConnectsPerSecond`|<span data-ttu-id="9f865-132">正從連接集區提取的現用連接的數目。</span><span class="sxs-lookup"><span data-stu-id="9f865-132">The number of active connections being pulled from the connection pool.</span></span> <span data-ttu-id="9f865-133">**注意：**  預設不會啟用此效能計數器。</span><span class="sxs-lookup"><span data-stu-id="9f865-133">**Note:**  This performance counter is not enabled by default.</span></span> <span data-ttu-id="9f865-134">若要啟用此效能計數器，請參閱啟用 [預設為預設的計數器](#ActivatingOffByDefault)。</span><span class="sxs-lookup"><span data-stu-id="9f865-134">To enable this performance counter, see [Activating Off-By-Default Counters](#ActivatingOffByDefault).</span></span>|  
|`SoftDisconnectsPerSecond`|<span data-ttu-id="9f865-135">正傳回至連接集區的現用連接的數目。</span><span class="sxs-lookup"><span data-stu-id="9f865-135">The number of active connections that are being returned to the connection pool.</span></span> <span data-ttu-id="9f865-136">**注意：**  預設不會啟用此效能計數器。</span><span class="sxs-lookup"><span data-stu-id="9f865-136">**Note:**  This performance counter is not enabled by default.</span></span> <span data-ttu-id="9f865-137">若要啟用此效能計數器，請參閱啟用 [預設為預設的計數器](#ActivatingOffByDefault)。</span><span class="sxs-lookup"><span data-stu-id="9f865-137">To enable this performance counter, see [Activating Off-By-Default Counters](#ActivatingOffByDefault).</span></span>|  
  
### <a name="connection-pool-groups-and-connection-pools"></a><span data-ttu-id="9f865-138">連接集區群組和連接集區</span><span class="sxs-lookup"><span data-stu-id="9f865-138">Connection Pool Groups and Connection Pools</span></span>  

 <span data-ttu-id="9f865-139">在使用「Windows 驗證」(整合式安全性) 時，必須同時監控 `NumberOfActiveConnectionPoolGroups` 和 `NumberOfActiveConnectionPools` 效能計數器。</span><span class="sxs-lookup"><span data-stu-id="9f865-139">When using Windows Authentication (integrated security), you must monitor both the `NumberOfActiveConnectionPoolGroups` and `NumberOfActiveConnectionPools` performance counters.</span></span> <span data-ttu-id="9f865-140">原因是連接集區群組會對應至唯一的連接字串。</span><span class="sxs-lookup"><span data-stu-id="9f865-140">The reason is that connection pool groups map to unique connection strings.</span></span> <span data-ttu-id="9f865-141">使用整合式安全性時，連接集區會對應至連接字串，並針對個別的 Windows 識別 (Identity) 額外建立獨立的集區。</span><span class="sxs-lookup"><span data-stu-id="9f865-141">When integrated security is used, connection pools map to connection strings and additionally create separate pools for individual Windows identities.</span></span> <span data-ttu-id="9f865-142">例如，如果 Fred 和 Julie 位於相同的 AppDomain 內，且兩者都使用連接字串 `"Data Source=MySqlServer;Integrated Security=true"`，則會針對連接字串建立連接集區群組，並針對 Fred 和 Julie 建立兩個額外的集區。</span><span class="sxs-lookup"><span data-stu-id="9f865-142">For example, if Fred and Julie, each within the same AppDomain, both use the connection string `"Data Source=MySqlServer;Integrated Security=true"`, a connection pool group is created for the connection string, and two additional pools are created, one for Fred and one for Julie.</span></span> <span data-ttu-id="9f865-143">如果 John 和 Martha 使用的連接字串具有相同的 SQL Server 登入， `"Data Source=MySqlServer;User Id=lowPrivUser;Password=Strong?Password"` 則只會針對 **lowPrivUser** 身分識別建立單一集區。</span><span class="sxs-lookup"><span data-stu-id="9f865-143">If John and Martha use a connection string with an identical SQL Server login, `"Data Source=MySqlServer;User Id=lowPrivUser;Password=Strong?Password"`, then only a single pool is created for the **lowPrivUser** identity.</span></span>  
  
<a name="ActivatingOffByDefault"></a>

### <a name="activating-off-by-default-counters"></a><span data-ttu-id="9f865-144">啟動依預設關閉的計數器</span><span class="sxs-lookup"><span data-stu-id="9f865-144">Activating Off-By-Default Counters</span></span>  

 <span data-ttu-id="9f865-145">效能計數器 `NumberOfFreeConnections`、`NumberOfActiveConnections`、`SoftDisconnectsPerSecond` 和 `SoftConnectsPerSecond` 預設會關閉。</span><span class="sxs-lookup"><span data-stu-id="9f865-145">The performance counters `NumberOfFreeConnections`, `NumberOfActiveConnections`, `SoftDisconnectsPerSecond`, and `SoftConnectsPerSecond` are off by default.</span></span> <span data-ttu-id="9f865-146">請將下列資訊加入至應用程式的組態檔加以啟用：</span><span class="sxs-lookup"><span data-stu-id="9f865-146">Add the following information to the application's configuration file to enable them:</span></span>  
  
```xml  
<system.diagnostics>  
  <switches>  
    <add name="ConnectionPoolPerformanceCounterDetail"  
         value="4"/>  
  </switches>  
</system.diagnostics>  
```  
  
## <a name="retrieving-performance-counter-values"></a><span data-ttu-id="9f865-147">擷取效能計數器值</span><span class="sxs-lookup"><span data-stu-id="9f865-147">Retrieving Performance Counter Values</span></span>  

 <span data-ttu-id="9f865-148">下列主控台應用程式顯示如何在應用程式中擷取效能計數器值。</span><span class="sxs-lookup"><span data-stu-id="9f865-148">The following console application shows how to retrieve performance counter values in your application.</span></span> <span data-ttu-id="9f865-149">連接必須為開啟及使用中，才能傳回所有 ADO.NET 效能計數器的資訊。</span><span class="sxs-lookup"><span data-stu-id="9f865-149">Connections must be open and active for information to be returned for all of the ADO.NET performance counters.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9f865-150">此範例會使用 SQL Server 隨附的範例 **AdventureWorks** 資料庫。</span><span class="sxs-lookup"><span data-stu-id="9f865-150">This example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="9f865-151">範例程式碼中提供的連接字串假設該資料庫已安裝且可用於具有 SqlExpress 執行個體名稱的本機電腦上，而且您已建立符合連接字串中所提供登入的 SQL Server 登入。</span><span class="sxs-lookup"><span data-stu-id="9f865-151">The connection strings provided in the sample code assume that the database is installed and available on the local computer with an instance name of SqlExpress, and that you have created SQL Server logins that match those supplied in the connection strings.</span></span> <span data-ttu-id="9f865-152">如果伺服器是使用僅允許「Windows 驗證」的預設安全性設定而設定，則可能需要啟用 SQL Server 登入。</span><span class="sxs-lookup"><span data-stu-id="9f865-152">You may need to enable SQL Server logins if your server is configured using the default security settings which allow only Windows Authentication.</span></span> <span data-ttu-id="9f865-153">請視環境需要修改連接字串。</span><span class="sxs-lookup"><span data-stu-id="9f865-153">Modify the connection strings as necessary to suit your environment.</span></span>  
  
### <a name="example"></a><span data-ttu-id="9f865-154">範例</span><span class="sxs-lookup"><span data-stu-id="9f865-154">Example</span></span>  
  
```vb  
Option Explicit On  
Option Strict On  
  
Imports System.Data.SqlClient  
Imports System.Diagnostics  
Imports System.Runtime.InteropServices  
  
Class Program  
  
    Private PerfCounters(9) As PerformanceCounter  
    Private connection As SqlConnection = New SqlConnection  
  
    Public Shared Sub Main()  
        Dim prog As Program = New Program  
        ' Open a connection and create the performance counters.
        prog.connection.ConnectionString = _  
           GetIntegratedSecurityConnectionString()  
        prog.SetUpPerformanceCounters()  
        Console.WriteLine("Available Performance Counters:")  
  
        ' Create the connections and display the results.  
        prog.CreateConnections()  
        Console.WriteLine("Press Enter to finish.")  
        Console.ReadLine()  
    End Sub  
  
    Private Sub CreateConnections()  
        ' List the Performance counters.  
        WritePerformanceCounters()  
  
        ' Create 4 connections and display counter information.  
        Dim connection1 As SqlConnection = New SqlConnection( _  
           GetIntegratedSecurityConnectionString)  
        connection1.Open()  
        Console.WriteLine("Opened the 1st Connection:")  
        WritePerformanceCounters()  
  
        Dim connection2 As SqlConnection = New SqlConnection( _  
           GetSqlConnectionStringDifferent)  
        connection2.Open()  
        Console.WriteLine("Opened the 2nd Connection:")  
        WritePerformanceCounters()  
  
        Console.WriteLine("Opened the 3rd Connection:")  
        Dim connection3 As SqlConnection = New SqlConnection( _  
           GetSqlConnectionString)  
        connection3.Open()  
        WritePerformanceCounters()  
  
        Dim connection4 As SqlConnection = New SqlConnection( _  
           GetSqlConnectionString)  
        connection4.Open()  
        Console.WriteLine("Opened the 4th Connection:")  
        WritePerformanceCounters()  
  
        connection1.Close()  
        Console.WriteLine("Closed the 1st Connection:")  
        WritePerformanceCounters()  
  
        connection2.Close()  
        Console.WriteLine("Closed the 2nd Connection:")  
        WritePerformanceCounters()  
  
        connection3.Close()  
        Console.WriteLine("Closed the 3rd Connection:")  
        WritePerformanceCounters()  
  
        connection4.Close()  
        Console.WriteLine("Closed the 4th Connection:")  
        WritePerformanceCounters()  
    End Sub  
  
    Private Enum ADO_Net_Performance_Counters  
        NumberOfActiveConnectionPools  
        NumberOfReclaimedConnections  
        HardConnectsPerSecond  
        HardDisconnectsPerSecond  
        NumberOfActiveConnectionPoolGroups  
        NumberOfInactiveConnectionPoolGroups  
        NumberOfInactiveConnectionPools  
        NumberOfNonPooledConnections  
        NumberOfPooledConnections  
        NumberOfStasisConnections  
        ' The following performance counters are more expensive to track.  
        ' Enable ConnectionPoolPerformanceCounterDetail in your config file.  
        '     SoftConnectsPerSecond  
        '     SoftDisconnectsPerSecond  
        '     NumberOfActiveConnections  
        '     NumberOfFreeConnections  
    End Enum  
  
    Private Sub SetUpPerformanceCounters()  
        connection.Close()  
        Me.PerfCounters(9) = New PerformanceCounter()  
  
        Dim instanceName As String = GetInstanceName()  
        Dim apc As Type = GetType(ADO_Net_Performance_Counters)  
        Dim i As Integer = 0  
        Dim s As String = ""  
        For Each s In [Enum].GetNames(apc)  
            Me.PerfCounters(i) = New PerformanceCounter()  
            Me.PerfCounters(i).CategoryName = ".NET Data Provider for SqlServer"  
            Me.PerfCounters(i).CounterName = s  
            Me.PerfCounters(i).InstanceName = instanceName  
            i = (i + 1)  
        Next  
    End Sub  
  
    Private Declare Function GetCurrentProcessId Lib "kernel32.dll" () As Integer  
  
    Private Function GetInstanceName() As String  
        'This works for Winforms apps.
        Dim instanceName As String = _  
           System.Reflection.Assembly.GetEntryAssembly.GetName.Name  
  
        ' Must replace special characters like (, ), #, /, \\
        Dim instanceName2 As String = _  
           AppDomain.CurrentDomain.FriendlyName.ToString.Replace("(", "[") _  
           .Replace(")", "]").Replace("#", "_").Replace("/", "_").Replace("\\", "_")  
  
        'For ASP.NET applications your instanceName will be your CurrentDomain's
        'FriendlyName. Replace the line above that sets the instanceName with this:
        'instanceName = AppDomain.CurrentDomain.FriendlyName.ToString.Replace("(", "[") _  
        '    .Replace(")", "]").Replace("#", "_").Replace("/", "_").Replace("\\", "_")  
  
        Dim pid As String = GetCurrentProcessId.ToString  
        instanceName = (instanceName + ("[" & (pid & "]")))  
        Console.WriteLine("Instance Name: {0}", instanceName)  
        Console.WriteLine("---------------------------")  
        Return instanceName  
    End Function  
  
    Private Sub WritePerformanceCounters()  
        Console.WriteLine("---------------------------")  
        For Each p As PerformanceCounter In Me.PerfCounters  
            Console.WriteLine("{0} = {1}", p.CounterName, p.NextValue)  
        Next  
        Console.WriteLine("---------------------------")  
    End Sub  
  
    Private Shared Function GetIntegratedSecurityConnectionString() As String  
        ' To avoid storing the connection string in your code,
        ' you can retrieve it from a configuration file.
        Return ("Data Source=.\SqlExpress;Integrated Security=True;" &
          "Initial Catalog=AdventureWorks")  
    End Function  
  
    Private Shared Function GetSqlConnectionString() As String  
        ' To avoid storing the connection string in your code,
        ' you can retrieve it from a configuration file.
        Return ("Data Source=.\SqlExpress;User Id=LowPriv;Password=Data!05;" &
          "Initial Catalog=AdventureWorks")  
    End Function  
  
    Private Shared Function GetSqlConnectionStringDifferent() As String  
        ' To avoid storing the connection string in your code,
        ' you can retrieve it from a configuration file.
        Return ("Initial Catalog=AdventureWorks;Data Source=.\SqlExpress;" & _  
          "User Id=LowPriv;Password=Data!05;")  
    End Function  
End Class  
```  

```csharp  
using System;  
using System.Data.SqlClient;  
using System.Diagnostics;  
using System.Runtime.InteropServices;  
  
class Program  
{  
    PerformanceCounter[] PerfCounters = new PerformanceCounter[10];  
    SqlConnection connection = new SqlConnection();  
  
    static void Main()  
    {  
        Program prog = new Program();  
        // Open a connection and create the performance counters.  
        prog.connection.ConnectionString =  
           GetIntegratedSecurityConnectionString();  
        prog.SetUpPerformanceCounters();  
        Console.WriteLine("Available Performance Counters:");  
  
        // Create the connections and display the results.  
        prog.CreateConnections();  
        Console.WriteLine("Press Enter to finish.");  
        Console.ReadLine();  
    }  
  
    private void CreateConnections()  
    {  
        // List the Performance counters.  
        WritePerformanceCounters();  
  
        // Create 4 connections and display counter information.  
        SqlConnection connection1 = new SqlConnection(  
              GetIntegratedSecurityConnectionString());  
        connection1.Open();  
        Console.WriteLine("Opened the 1st Connection:");  
        WritePerformanceCounters();  
  
        SqlConnection connection2 = new SqlConnection(  
              GetSqlConnectionStringDifferent());  
        connection2.Open();  
        Console.WriteLine("Opened the 2nd Connection:");  
        WritePerformanceCounters();  
  
        SqlConnection connection3 = new SqlConnection(  
              GetSqlConnectionString());  
        connection3.Open();  
        Console.WriteLine("Opened the 3rd Connection:");  
        WritePerformanceCounters();  
  
        SqlConnection connection4 = new SqlConnection(  
              GetSqlConnectionString());  
        connection4.Open();  
        Console.WriteLine("Opened the 4th Connection:");  
        WritePerformanceCounters();  
  
        connection1.Close();  
        Console.WriteLine("Closed the 1st Connection:");  
        WritePerformanceCounters();  
  
        connection2.Close();  
        Console.WriteLine("Closed the 2nd Connection:");  
        WritePerformanceCounters();  
  
        connection3.Close();  
        Console.WriteLine("Closed the 3rd Connection:");  
        WritePerformanceCounters();  
  
        connection4.Close();  
        Console.WriteLine("Closed the 4th Connection:");  
        WritePerformanceCounters();  
    }  
  
    private enum ADO_Net_Performance_Counters  
    {  
        NumberOfActiveConnectionPools,  
        NumberOfReclaimedConnections,  
        HardConnectsPerSecond,  
        HardDisconnectsPerSecond,  
        NumberOfActiveConnectionPoolGroups,  
        NumberOfInactiveConnectionPoolGroups,  
        NumberOfInactiveConnectionPools,  
        NumberOfNonPooledConnections,  
        NumberOfPooledConnections,  
        NumberOfStasisConnections  
        // The following performance counters are more expensive to track.  
        // Enable ConnectionPoolPerformanceCounterDetail in your config file.  
        //     SoftConnectsPerSecond  
        //     SoftDisconnectsPerSecond  
        //     NumberOfActiveConnections  
        //     NumberOfFreeConnections  
    }  
  
    private void SetUpPerformanceCounters()  
    {  
        connection.Close();  
        this.PerfCounters = new PerformanceCounter[10];  
        string instanceName = GetInstanceName();  
        Type apc = typeof(ADO_Net_Performance_Counters);  
        int i = 0;  
        foreach (string s in Enum.GetNames(apc))  
        {  
            this.PerfCounters[i] = new PerformanceCounter();  
            this.PerfCounters[i].CategoryName = ".NET Data Provider for SqlServer";  
            this.PerfCounters[i].CounterName = s;  
            this.PerfCounters[i].InstanceName = instanceName;  
            i++;  
        }  
    }  
  
    [DllImport("kernel32.dll", SetLastError = true)]  
    static extern int GetCurrentProcessId();  
  
    private string GetInstanceName()  
    {  
        //This works for Winforms apps.  
        string instanceName =  
            System.Reflection.Assembly.GetEntryAssembly().GetName().Name;  
  
        // Must replace special characters like (, ), #, /, \\  
        string instanceName2 =  
            AppDomain.CurrentDomain.FriendlyName.ToString().Replace('(', '[')  
            .Replace(')', ']').Replace('#', '_').Replace('/', '_').Replace('\\', '_');  
  
        // For ASP.NET applications your instanceName will be your CurrentDomain's
        // FriendlyName. Replace the line above that sets the instanceName with this:  
        // instanceName = AppDomain.CurrentDomain.FriendlyName.ToString().Replace('(','[')  
        // .Replace(')',']').Replace('#','_').Replace('/','_').Replace('\\','_');  
  
        string pid = GetCurrentProcessId().ToString();  
        instanceName = instanceName + "[" + pid + "]";  
        Console.WriteLine("Instance Name: {0}", instanceName);  
        Console.WriteLine("---------------------------");  
        return instanceName;  
    }  
  
    private void WritePerformanceCounters()  
    {  
        Console.WriteLine("---------------------------");  
        foreach (PerformanceCounter p in this.PerfCounters)  
        {  
            Console.WriteLine("{0} = {1}", p.CounterName, p.NextValue());  
        }  
        Console.WriteLine("---------------------------");  
    }  
  
    private static string GetIntegratedSecurityConnectionString()  
    {  
        // To avoid storing the connection string in your code,  
        // you can retrieve it from a configuration file.  
        return @"Data Source=.\SqlExpress;Integrated Security=True;" +  
          "Initial Catalog=AdventureWorks";  
    }  
    private static string GetSqlConnectionString()  
    {  
        // To avoid storing the connection string in your code,  
        // you can retrieve it from a configuration file.  
        return @"Data Source=.\SqlExpress;User Id=LowPriv;Password=Data!05;" +  
          "Initial Catalog=AdventureWorks";  
    }  
  
    private static string GetSqlConnectionStringDifferent()  
    {  
        // To avoid storing the connection string in your code,  
        // you can retrieve it from a configuration file.  
        return @"Initial Catalog=AdventureWorks;Data Source=.\SqlExpress;" +  
          "User Id=LowPriv;Password=Data!05;";  
    }  
}  
```  

## <a name="see-also"></a><span data-ttu-id="9f865-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9f865-155">See also</span></span>

- [<span data-ttu-id="9f865-156">連接到資料來源</span><span class="sxs-lookup"><span data-stu-id="9f865-156">Connecting to a Data Source</span></span>](connecting-to-a-data-source.md)
- [<span data-ttu-id="9f865-157">OLE DB、ODBC 和 Oracle 連接共用</span><span class="sxs-lookup"><span data-stu-id="9f865-157">OLE DB, ODBC, and Oracle Connection Pooling</span></span>](ole-db-odbc-and-oracle-connection-pooling.md)
- <span data-ttu-id="9f865-158">[ASP.NET 的效能計數器](/previous-versions/aspnet/fxk122b4(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9f865-158">[Performance Counters for ASP.NET](/previous-versions/aspnet/fxk122b4(v=vs.100))</span></span>
- [<span data-ttu-id="9f865-159">執行階段分析</span><span class="sxs-lookup"><span data-stu-id="9f865-159">Runtime Profiling</span></span>](../../debug-trace-profile/runtime-profiling.md)
- <span data-ttu-id="9f865-160">[監視效能閾值簡介](/previous-versions/visualstudio/visual-studio-2008/bd20x32d(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="9f865-160">[Introduction to Monitoring Performance Thresholds](/previous-versions/visualstudio/visual-studio-2008/bd20x32d(v=vs.90))</span></span>
- <span data-ttu-id="9f865-161">[ADO.NET 概觀](ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="9f865-161">[ADO.NET Overview](ado-net-overview.md)</span></span>
