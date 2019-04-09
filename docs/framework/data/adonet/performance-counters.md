---
title: ADO.NET 中的效能計數器
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0b121b71-78f8-4ae2-9aa1-0b2e15778e57
ms.openlocfilehash: e7e7ba379f6f92f3ba8fba55f22c8eaec81ab1cf
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59133883"
---
# <a name="performance-counters-in-adonet"></a>ADO.NET 中的效能計數器
ADO.NET 2.0 導入了對效能計數器的擴充支援，其中包含對 <xref:System.Data.SqlClient> 和 <xref:System.Data.OracleClient> 的支援。 舊版 ADO.NET 中提供的 <xref:System.Data.SqlClient> 效能計數器已被本主題中討論的新效能計數器取代。 您可以使用 ADO.NET 效能計數器來監控應用程式的狀態及其使用的連接資源。 效能計數器可藉由「Windows 效能監視器」來進行監視，或可藉由 <xref:System.Diagnostics.PerformanceCounter> 命名空間 (Namespace) 中的 <xref:System.Diagnostics> 類別以程式設計的方式存取。  
  
## <a name="available-performance-counters"></a>可用的效能計數器  
 目前有 14 種不同的效能計數器可供 <xref:System.Data.SqlClient> 和 <xref:System.Data.OracleClient> 使用 (如下表所述)。 請注意，個別計數器的名稱並未在 Microsoft .NET Framework 的區域版本中當地語系化。  
  
|效能計數器|描述|  
|-------------------------|-----------------|  
|`HardConnectsPerSecond`|每秒鐘對資料庫伺服器所建立的連接數目。|  
|`HardDisconnectsPerSecond`|每秒鐘對資料庫伺服器所進行的中斷連接數目。|  
|`NumberOfActiveConnectionPoolGroups`|使用中的唯一連接集區群組的數目。 這個計數器是由 AppDomain 中找到的唯一連接字串數目所控制。|  
|`NumberOfActiveConnectionPools`|連接集區的總數。|  
|`NumberOfActiveConnections`|目前使用中的現用連接的數目。 **注意：** 這個效能計數器預設未啟用。 若要啟用這個效能計數器，請參閱[啟動依預設關閉的計數器](#ActivatingOffByDefault)。|  
|`NumberOfFreeConnections`|連接集區中可用的連接數目。 **注意：** 這個效能計數器預設未啟用。 若要啟用這個效能計數器，請參閱[啟動依預設關閉的計數器](#ActivatingOffByDefault)。|  
|`NumberOfInactiveConnectionPoolGroups`|標示為清除的唯一連接集區群組的數目。 這個計數器是由 AppDomain 中找到的唯一連接字串數目所控制。|  
|`NumberOfInactiveConnectionPools`|最近未有任何活動且正等候處置 (Dispose) 的非現用連接集區數目。|  
|`NumberOfNonPooledConnections`|尚未共用的現用連接的數目。|  
|`NumberOfPooledConnections`|正由連接共用基礎結構所管理的現用連接的數目。|  
|`NumberOfReclaimedConnections`|已透過記憶體回收作業回收的連接數目，其中 `Close` 或 `Dispose` 並非由應用程式呼叫。 未明確關閉或處置連接都會損及效能。|  
|`NumberOfStasisConnections`|目前正等候動作完成因此無法提供應用程式使用的連接數目。|  
|`SoftConnectsPerSecond`|正從連接集區提取的現用連接的數目。 **注意：** 這個效能計數器預設未啟用。 若要啟用這個效能計數器，請參閱[啟動依預設關閉的計數器](#ActivatingOffByDefault)。|  
|`SoftDisconnectsPerSecond`|正傳回至連接集區的現用連接的數目。 **注意：** 這個效能計數器預設未啟用。 若要啟用這個效能計數器，請參閱[啟動依預設關閉的計數器](#ActivatingOffByDefault)。|  
  
### <a name="connection-pool-groups-and-connection-pools"></a>連接集區群組和連接集區  
 在使用「Windows 驗證」(整合式安全性) 時，必須同時監控 `NumberOfActiveConnectionPoolGroups` 和 `NumberOfActiveConnectionPools` 效能計數器。 原因是連接集區群組會對應至唯一的連接字串。 使用整合式安全性時，連接集區會對應至連接字串，並針對個別的 Windows 識別 (Identity) 額外建立獨立的集區。 例如，如果 Fred 和 Julie 位於相同的 AppDomain 內，且兩者都使用連接字串 `"Data Source=MySqlServer;Integrated Security=true"`，則會針對連接字串建立連接集區群組，並針對 Fred 和 Julie 建立兩個額外的集區。 如果 John 和 Martha 使用連接字串具有相同的 SQL Server 登入`"Data Source=MySqlServer;User Id=lowPrivUser;Password=Strong?Password"`，然後建立單一集區**lowPrivUser**身分識別。  
  
<a name="ActivatingOffByDefault"></a>   
### <a name="activating-off-by-default-counters"></a>啟動依預設關閉的計數器  
 效能計數器 `NumberOfFreeConnections`、`NumberOfActiveConnections`、`SoftDisconnectsPerSecond` 和 `SoftConnectsPerSecond` 預設會關閉。 請將下列資訊加入至應用程式的組態檔加以啟用：  
  
```xml  
<system.diagnostics>  
  <switches>  
    <add name="ConnectionPoolPerformanceCounterDetail"  
         value="4"/>  
  </switches>  
</system.diagnostics>  
```  
  
## <a name="retrieving-performance-counter-values"></a>擷取效能計數器值  
 下列主控台應用程式顯示如何在應用程式中擷取效能計數器值。 連接必須為開啟及使用中，才能傳回所有 ADO.NET 效能計數器的資訊。  
  
> [!NOTE]
>  此範例使用範例**AdventureWorks**隨附於 SQL Server 的資料庫。 範例程式碼中提供的連接字串假設該資料庫已安裝且可用於具有 SqlExpress 執行個體名稱的本機電腦上，而且您已建立符合連接字串中所提供登入的 SQL Server 登入。 如果伺服器是使用僅允許「Windows 驗證」的預設安全性設定而設定，則可能需要啟用 SQL Server 登入。 請視環境需要修改連接字串。  
  
### <a name="example"></a>範例  
  
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

## <a name="see-also"></a>另請參閱

- [連接資料來源](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)
- [OLE DB、ODBC 和 Oracle 連接共用](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md)
- [適用於 ASP.NET 的效能計數器](https://docs.microsoft.com/previous-versions/aspnet/fxk122b4(v=vs.100))
- [執行階段分析](../../../../docs/framework/debug-trace-profile/runtime-profiling.md)
- [監視效能臨界值簡介](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bd20x32d(v=vs.90))
- [ADO.NET 概觀](ado-net-overview.md)
