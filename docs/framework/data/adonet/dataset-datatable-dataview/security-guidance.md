---
title: DataSet 和 DataTable 安全性指引
ms.date: 07/14/2020
dev_langs:
- csharp
ms.openlocfilehash: f0fa43c467cc7866e69115acb5f807e6487fda7a
ms.sourcegitcommit: cbb19e56d48cf88375d35d0c27554d4722761e0d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2020
ms.locfileid: "88608530"
---
# <a name="dataset-and-datatable-security-guidance"></a>DataSet 和 DataTable 安全性指引

本文適用于：

* .NET Framework (所有版本) 
* .NET Core 和更新版本
* .NET 5.0 和更新版本

[DataSet](/dotnet/api/system.data.dataset)和[DataTable](/dotnet/api/system.data.datatable)類型是舊版 .net 元件，可將資料集表示為 managed 物件。 這些元件是在 .NET 1.0 中引進，作為原始 [ADO.NET 基礎結構](/dotnet/framework/data/adonet/dataset-datatable-dataview/)的一部分。 其目標是要提供關聯式資料集的 managed 視圖，並將資料的基礎來源抽象化為 XML、SQL 或其他技術。

如需 ADO.NET 的詳細資訊，包括更多新式資料檢視範例，請參閱 [ADO.NET 檔](/dotnet/framework/data/adonet/)。

## <a name="default-restrictions-when-deserializing-a-dataset-or-datatable-from-xml"></a>從 XML 還原序列化資料集或 DataTable 時的預設限制

在所有支援的 .NET Framework、.NET Core 和 .NET 版本上，並對已還原序列化 `DataSet` `DataTable` 的資料中可能存在的物件類型進行下列限制。 根據預設，此清單受限於：

* 基本和基本類型： `bool` 、 `char` 、 `sbyte` 、 `byte` 、 `short` 、 `ushort` 、 `int` 、、 `uint` `long` 、 `ulong` `float` `double` `decimal` `DateTime` `DateTimeOffset` `TimeSpan` `string` `Guid` `SqlBinary` `SqlBoolean` `SqlByte` `SqlBytes` `SqlChars` `SqlDateTime` `SqlDecimal` `SqlDouble` `SqlGuid` `SqlInt16` `SqlInt32` `SqlInt64` `SqlMoney` `SqlSingle` `SqlString` 、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、和。
* 常用的非基本： `Type` 、 `Uri` 和 `BigInteger` 。
* 常用的 _系統。繪圖_ 類型： `Color` 、 `Point` 、 `PointF` 、 `Rectangle` 、 `RectangleF` 、 `Size` 和 `SizeF` 。
* `Enum` 類型。
* 上述類型的陣列和清單。

如果傳入的 XML 資料包含的物件類型不在此清單中：

* 隨即擲回例外狀況。
* 還原序列化作業失敗。

將 XML 載入至現有的 `DataSet` 或 `DataTable` 實例時，也會將現有的資料行定義列入考慮。 如果資料表已經包含自訂類型的資料行定義，則該類型會暫時加入至 XML 還原序列化作業期間的允許清單中。

```cs
XmlReader xmlReader = GetXmlReader();

// Assume the XML blob contains data for type MyCustomClass.
// The following call to ReadXml fails because MyCustomClass isn't in the allowed types list.

DataTable table = new DataTable("MyDataTable");
table.ReadXml(xmlReader);

// However, the following call to ReadXml succeeds, since the DataTable instance
// already defines a column of type MyCustomClass.

DataTable table = new DataTable("MyDataTable");
table.Columns.Add("MyColumn", typeof(MyCustomClass));
table.ReadXml(xmlReader); // this call will succeed
```

使用還原序列化或的實例時，也適用物件類型限制 `XmlSerializer` `DataSet` `DataTable` 。 不過，當使用還原序列化或的實例時，它們可能不適用 `BinaryFormatter` `DataSet` `DataTable` 。

使用時，不會套用物件類型限制 `DataAdapter.Fill` ，例如， `DataTable` 直接從資料庫填入實例時，不會使用 XML 還原序列化 api。

### <a name="extend-the-list-of-allowed-types"></a>擴充允許類型的清單

除了上述內建類型之外，應用程式還可以擴充允許的類型清單，以包含自訂類型。 如果擴充允許的類型清單，則變更會_all_影響 `DataSet` `DataTable` 應用程式內的所有和實例。 類型無法從內建的允許類型清單中移除。

#### <a name="extend-through-configuration-net-framework-40---48"></a>擴充到 configuration ( .NET Framework 4.0-4.8) 

_App.config_ 可以用來擴充允許的類型清單。 若要擴充允許的類型清單：

* 您可以使用專案 `<configSections>` ，將參考加入至 [ _system.object_ 設定] 區段。
* 用 `<system.data.dataset.serialization>` / `<allowedTypes>` 來指定其他類型。

每個專案都 `<add>` 只能使用其元件限定類型名稱來指定一種類型。 若要將其他類型加入至允許的類型清單，請使用多個 `<add>` 元素。

下列範例顯示如何藉由新增自訂類型來擴充允許的類型清單 `Fabrikam.CustomType` 。

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <sectionGroup name="system.data.dataset.serialization" type="System.Data.SerializationSettingsSectionGroup, System.Data, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="allowedTypes" type="System.Data.AllowedTypesSectionHandler, System.Data, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>
    </sectionGroup>
  </configSections>
  <system.data.dataset.serialization>
    <allowedTypes>
      <!-- <add type="assembly qualified type name" /> -->
      <add type="Fabrikam.CustomType, Fabrikam, Version=1.0.0.0, Culture=neutral, PublicKeyToken=2b3831f2f2b744f7" />
      <!-- additional <add /> elements as needed -->
    </allowedTypes>
  </system.data.dataset.serialization>
</configuration>
```

若要取出型別的元件限定名稱，請使用 [AssemblyQualifiedName](/dotnet/api/system.type.assemblyqualifiedname) 屬性，如下列程式碼所示。

```cs
string assemblyQualifiedName = typeof(Fabrikam.CustomType).AssemblyQualifiedName;
```

<a name="etc"></a>

#### <a name="extend-through-configuration-net-framework-20---35"></a>擴充到 configuration ( .NET Framework 2.0-3.5) 

如果您的應用程式是以 .NET Framework 2.0 或3.5 為目標，您仍然可以使用上述 _App.config_ 機制來擴充允許的類型清單。 不過，您 `<configSections>` 的專案看起來會稍微不同，如下列程式碼所示：

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <!-- The below <sectionGroup> and <section> are specific to .NET Framework 2.0 and 3.5. -->
    <sectionGroup name="system.data.dataset.serialization" type="System.Data.SerializationSettingsSectionGroup, System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="allowedTypes" type="System.Data.AllowedTypesSectionHandler, System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>
    </sectionGroup>
  </configSections>
  <system.data.dataset.serialization>
    <allowedTypes>
      <!-- <add /> elements, as demonstrated in the .NET Framework 4.0 - 4.8 sample code above. -->
    </allowedTypes>
  </system.data.dataset.serialization>
</configuration>
```

#### <a name="extend-programmatically-net-framework-net-core-net-50"></a>以程式設計方式擴充 ( .NET Framework、.NET Core、.NET 5.0 +) 

您也可以使用 [AppDomain](/dotnet/api/system.appdomain.setdata) 搭配已知的金鑰 _DataSetDefaultAllowedTypes_，以程式設計方式擴充允許的類型清單，如下列程式碼所示。

```cs
Type[] extraAllowedTypes = new Type[]
{
    typeof(Fabrikam.CustomType),
    typeof(Contoso.AdditionalCustomType)
};

AppDomain.CurrentDomain.SetData("System.Data.DataSetDefaultAllowedTypes", extraAllowedTypes);
```

如果使用延伸模組機制，則與金鑰 _DataSetDefaultAllowedTypes_ 相關聯的值必須為類型 `Type[]` 。

在 .NET Framework 上，可使用 _App.config_ 和來擴充允許類型的清單 `AppDomain.SetData` 。 在此情況下 `DataSet` ， `DataTable` 如果物件的類型存在於其中一個清單中，則會允許物件還原序列化為數據的一部分。

### <a name="run-an-app-in-audit-mode-net-framework"></a>在 audit 模式中執行應用程式 ( .NET Framework) 

在 .NET Framework 中， `DataSet` 並 `DataTable` 提供「稽核模式」功能。 當啟用稽核模式時，會將 `DataSet` `DataTable` 傳入物件的類型與允許的類型清單進行比較。 但是，如果看不到類型為的物件，就 **不** 會擲回例外狀況。 相反 `DataSet` 地， `DataTable` 會通知任何附加的 `TraceListener` 實例有可疑的類型存在，讓 `TraceListener` 記錄這項資訊。 不會擲回例外狀況，而且還原序列化作業會繼續進行。

> [!WARNING]
> 在「audit 模式」中執行應用程式應該只是用於測試的暫時量值。 啟用稽核模式時， `DataSet` `DataTable` 不會強制執行類型限制，這可能會在您的應用程式中引進安全性漏洞。 如需詳細資訊，請參閱標題為移除[不受信任輸入](#swr)之[所有類型限制](#ratr)和安全性的章節。

您可以透過 _App.config_啟用 Audit 模式：

* 請參閱本檔中的「 [透過設定延伸](#etc) 」一節，以取得要為元素放置之適當值的相關資訊 `<configSections>` 。
* 使用 `<allowedTypes auditOnly="true">` 啟用 audit 模式，如下列標記所示。

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <!-- See the section of this document titled "Extending through configuration" for the appropriate
         <sectionGroup> and <section> elements to put here, depending on whether you're running .NET
         Framework 2.0 - 3.5 or 4.0 - 4.8. -->
  </configSections>
  <system.data.dataset.serialization>
    <allowedTypes auditOnly="true"> <!-- setting auditOnly="true" enables audit mode -->
      <!-- Optional <add /> elements as needed. -->
    </allowedTypes>
  </system.data.dataset.serialization>
</configuration>
```

啟用稽核模式之後，您就可以使用_App.config_ ，將您偏好的內 `TraceListener` `DataSet` `TraceSource.` 建追蹤來源的名稱_System.Data.DataSet_連接到 system.string。 下列範例示範如何將追蹤事件寫入主控台 _和_ 磁片上的記錄檔。

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.diagnostics>
    <sources>
      <source name="System.Data.DataSet"
              switchType="System.Diagnostics.SourceSwitch"
              switchValue="Warning">
        <listeners>
          <!-- write to the console -->
          <add name="console"
               type="System.Diagnostics.ConsoleTraceListener" />
          <!-- *and* write to a log file on disk -->
          <add name="filelog"
               type="System.Diagnostics.TextWriterTraceListener"
               initializeData="c:\logs\mylog.txt" />
        </listeners>
      </source>
    </sources>
  </system.diagnostics>
</configuration>
```

如需和的詳細資訊 `TraceSource` `TraceListener` ，請參閱檔 [如何：搭配追蹤接聽程式使用 TraceSource 和篩選](../../../debug-trace-profile/how-to-use-tracesource-and-filters-with-trace-listeners.md)。

> [!NOTE]
> 在 .NET Core 或 .NET 5.0 和更新版本中，無法使用以 audit 模式執行的應用程式。

<a name="ratr"></a>

### <a name="remove-all-type-restrictions"></a>移除所有類型限制

如果應用程式必須從和移除所有類型限制 `DataSet` 限制 `DataTable` ：

* 有幾個選項可隱藏類型限制限制。
* 可用的選項取決於應用程式的目標架構。

> [!WARNING]
> 移除所有類型限制可能會在應用程式中引進安全性漏洞。 使用這種機制時，請確定應用 **程式不會使用** `DataSet` 或 `DataTable` 讀取不受信任的輸入。 如需詳細資訊，請參閱有關未[受信任的輸入之安全性的](#swr) [CVE-2020-1147](https://portal.msrc.microsoft.com/en-us/security-guidance/advisory/CVE-2020-1147)和下一節。

#### <a name="through-appcontext-configuration-net-framework-46---48-net-core-21-and-later-net-50-and-later"></a>透過 AppCoNtext configuration ( .NET Framework 4.6-4.8、.NET Core 2.1 和更新版本、.NET 5.0 和更新版本) 

`AppContext` `Switch.System.Data.AllowArbitraryDataSetTypeInstantiation` 當設為時，參數會 `true` 從和移除所有類型限制 `DataSet` 限制 `DataTable` 。

在 .NET Framework 中，可以透過 _App.config_啟用此參數，如下列設定所示：

```xml
<configuration>
   <runtime>
      <!-- Warning: setting the following switch can introduce a security problem. -->
      <AppContextSwitchOverrides value="Switch.System.Data.AllowArbitraryDataSetTypeInstantiation=true" />
   </runtime>
</configuration>
```

在 ASP.NET 中， `<AppContextSwitchOverrides>` 無法使用元素。 相反地，您可以透過 _Web.config_啟用交換器，如下列設定所示：

```xml
<configuration>
    <appSettings>
        <!-- Warning: setting the following switch can introduce a security problem. -->
        <add key="AppContext.SetSwitch:Switch.System.Data.AllowArbitraryDataSetTypeInstantiation" value="true" />
    </appSettings>
</configuration>
```

如需詳細資訊，請參閱 [\<AppContextSwitchOverrides>](../../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 元素。

在 .NET Core、.NET 5 和 ASP.NET Core 中，此設定是由 _runtimeconfig.js_來控制，如下列 JSON 所示：

```json
{
  "runtimeOptions": {
    "configProperties": {
      "Switch.System.Data.AllowArbitraryDataSetTypeInstantiation": true
    }
  }
}
```

如需詳細資訊，請參閱「 [.Net Core 執行時間設定](/dotnet/core/run-time-config/)」。

`AllowArbitraryDataSetTypeInstantiation` 也可以透過 [AppCoNtext SetSwitch](/dotnet/api/system.appcontext.setswitch) 以程式設計方式設定，而不是使用設定檔，如下列程式碼所示：

```cs
// Warning: setting the following switch can introduce a security problem.
AppContext.SetSwitch("Switch.System.Data.AllowArbitraryDataSetTypeInstantiation", true);
```

 如果您選擇上述的程式設計方法，對的呼叫 `AppContext.SetSwitch` 應該會在應用程式啟動初期發生。

#### <a name="through-the-machine-wide-registry-net-framework-20---48"></a>透過整個電腦的登錄 ( .NET Framework 2.0-4.8) 

如果 `AppContext` 無法使用，則可以使用 Windows 登錄來停用類型限制檢查：

* 系統管理員必須設定登錄。
* 使用登錄是全電腦的變更，將會影響在電腦上執行的 _所有_ 應用程式。

| 類型  |  值 |
|---|---|
| **登錄機碼** | `HKLM\SOFTWARE\Microsoft\.NETFramework\AppContext` |
| **值名稱** | `Switch.System.Data.AllowArbitraryDataSetTypeInstantiation` |
| **值類型** | `REG_SZ` |
| **值資料** | `true` |

在64位的作業系統上，必須為上述的64位金鑰新增此值， (如上所示) 和32位金鑰。 32位金鑰位於 `HKLM\SOFTWARE\WOW6432Node\Microsoft\.NETFramework\AppContext` 。

如需使用登錄設定的詳細資訊 `AppContext` ，請參閱「連結 [庫取用者的 AppCoNtext](/dotnet/api/system.appcontext#appcontext-for-library-consumers)」。

<a name="swr"></a>

## <a name="safety-with-regard-to-untrusted-input"></a>不受信任輸入的安全性

雖然 `DataSet` 和 `DataTable` 的確會針對在還原序列化 XML 承載時允許出現的型別強加預設限制， __ `DataSet` 而且 `DataTable` 在填入未受信任的輸入時__，也不安全。 以下是 `DataSet` 或 `DataTable` 實例可能讀取未受信任之輸入的非詳盡清單。

* `DataAdapter`參考資料庫，並 `DataAdapter.Fill` 使用方法來填入 `DataSet` 資料庫查詢的內容。
* `DataSet.ReadXml`或 `DataTable.ReadXml` 方法是用來讀取包含資料行和資料列資訊的 XML 檔案。
* `DataSet`或 `DataTable` 實例會序列化為 ASP.NET (SOAP) web 服務或 WCF 端點的一部分。
* 序列化程式（例如） `XmlSerializer` 是用來將 `DataSet` `DataTable` XML 資料流程中的或實例還原序列化。
* 序列化程式（例如） `JsonConvert` 是用來 `DataSet` `DataTable` 從 JSON 資料流程還原序列化或實例。 `JsonConvert` 是受歡迎的協力廠商 [Newtonsoft.Js在](https://www.newtonsoft.com/json) 程式庫的方法。
* 序列化程式（例如） `BinaryFormatter` 是用來 `DataSet` `DataTable` 從原始位元組資料流程還原序列化或實例。

本檔討論上述案例的安全性考慮。

## <a name="use-dataadapterfill-to-populate-a-dataset-from-an-untrusted-data-source"></a>用 `DataAdapter.Fill` 來 `DataSet` 從不受信任的資料來源填入

您 `DataSet` 可以 `DataAdapter` 使用 [ `DataAdapter.Fill` 方法](/dotnet/api/system.data.common.dataadapter.fill)，從來填入實例，如下列範例所示。

```cs
// Assumes that connection is a valid SqlConnection object.  
string queryString =
  "SELECT CustomerID, CompanyName FROM dbo.Customers";  
SqlDataAdapter adapter = new SqlDataAdapter(queryString, connection);  
  
DataSet customers = new DataSet();  
adapter.Fill(customers, "Customers");
```

 (上述的程式碼範例是 [從 DataAdapter 填入資料集](../populating-a-dataset-from-a-dataadapter.md)的較大範例的一部分。 ) 

> 大部分的應用程式都可以簡化，並假設它們的資料庫層是受信任的。 但是，如果您習慣使用您的應用程式來 [建立威脅](https://www.microsoft.com/securityengineering/sdl/threatmodeling) 模型，則威脅模型可能會將應用程式 (用戶端) 和資料庫層之間的信任界限視為 (伺服器) 。 在用戶端與伺服器之間使用 [相互驗證](/sql/relational-databases/native-client/features/service-principal-name-spn-support-in-client-connections) 或 [AAD 驗證](/azure/azure-sql/database/authentication-aad-overview) 是協助解決與此相關的風險的一種方式。 本節的其餘部分將討論用戶端連接到不受信任的伺服器的可能結果。

`DataAdapter`在不受信任的資料來源中指向的結果，取決於本身的實 `DataAdapter` 。

### <a name="sqldataadapter"></a>SqlDataAdapter

針對內建類型 [SqlDataAdapter](/dotnet/api/microsoft.data.sqlclient.sqldataadapter)，參考不受信任的資料來源可能會導致拒絕服務 (DoS) 攻擊。 DoS 攻擊可能會導致應用程式變成沒有回應或損毀。 如果攻擊者可以與應用程式一起植入 DLL，它們也可以達成本機程式碼執行。

### <a name="other-dataadapter-types"></a>其他 DataAdapter 類型

協力廠商的 `DataAdapter` 執行必須自行評定其在不受信任的輸入時所提供的安全性保證。 .NET 無法針對這些執行提供任何安全保證。

<a name="dsrdtr"></a>

## <a name="datasetreadxml-and-datatablereadxml"></a>DataSet. ReadXml 和 DataTable. ReadXml

搭配 `DataSet.ReadXml` `DataTable.ReadXml` 未受信任的輸入使用時，和方法不安全。 強烈建議取用者改為考慮使用本檔稍後所述的其中一個替代方案。

和的實 `DataSet.ReadXml` 作為 `DataTable.ReadXml` 最初在序列化弱點之前建立的，是很容易理解的威脅類別。 因此，程式碼不會遵循目前的安全性最佳作法。 這些 Api 可以作為攻擊者用來對 web 應用程式執行 DoS 攻擊的向量。 這些攻擊可能會導致 web 服務沒有回應，或導致非預期的進程終止。 此架構不提供這些攻擊類別的緩和措施，而 .NET 會將此行為視為「依設計」。

.NET 已發行安全性更新，可減輕某些問題，例如和中的資訊洩漏或遠端程式碼執行 `DataSet.ReadXml` `DataTable.ReadXml` 。 .NET 安全性更新可能不會針對這些威脅類別提供完整的保護。 取用者應該評估其個別案例，並考慮其對這些風險的潛在風險。

取用者應該注意，在某些情況下，這些 Api 的安全性更新可能會影響應用程式相容性。 此外，也有可能會探索這些 Api 中的新穎弱點，而 .NET 無法實際發佈安全性更新。

我們建議這些 Api 的取用者可能：

* 請考慮使用本檔稍後所述的其中一個替代方案。
* 對其應用程式執行個別的風險評估。

消費者必須自行負責判斷是否要使用這些 Api。 取用者應該使用這些 Api 來評估任何安全性、技術和法律風險，包括法規需求。

## <a name="dataset-and-datatable-via-aspnet-web-services-or-wcf"></a>透過 ASP.NET web 服務或 WCF 的資料集和 DataTable

您可以接受 `DataSet` `DataTable` ASP.NET (SOAP) web 服務中的或實例，如下列程式碼所示：

```cs
using System.Data;
using System.Web.Services;

[WebService(Namespace = "http://contoso.com/")]
public class MyService : WebService
{
    [WebMethod]
    public string MyWebMethod(DataTable dataTable)
    {
        /* Web method implementation. */
    }
}
```

的變化不是接受 `DataSet` 或 `DataTable` 直接作為參數，而是在整體 SOAP 序列化物件圖形中接受它，如下列程式碼所示：

```cs
using System.Data;
using System.Web.Services;

[WebService(Namespace = "http://contoso.com/")]
public class MyService : WebService
{
    [WebMethod]
    public string MyWebMethod(MyClass data)
    {
        /* Web method implementation. */
    }
}

public class MyClass
{
    // Property of type DataTable, automatically serialized and
    // deserialized as part of the overall MyClass payload.
    public DataTable MyDataTable { get; set; }
}
```

或者，使用 WCF 而不是 ASP.NET web 服務：

```cs
using System.Data;
using System.ServiceModel;

[ServiceContract(Namespace = "http://contoso.com/")]
public interface IMyContract
{
    [OperationContract]
    string MyMethod(DataTable dataTable);
    [OperationContract]
    string MyOtherMethod(MyClass data);
}

public class MyClass
{
    // Property of type DataTable, automatically serialized and
    // deserialized as part of the overall MyClass payload.
    public DataTable MyDataTable { get; set; }
}
```

在上述所有情況下，威脅模型和安全性保證與 [ReadXml 和 DataTable. ReadXml 區段](#dsrdtr)相同。

## <a name="deserialize-a-dataset-or-datatable-via-xmlserializer"></a>透過 XmlSerializer 還原序列化 DataSet 或 DataTable

開發人員可以使用還原序列化 `XmlSerializer` `DataSet` 和 `DataTable` 實例，如下列程式碼所示：

```cs
using System.Data;
using System.IO;
using System.Xml.Serialization;

public DataSet PerformDeserialization1(Stream stream) {
    XmlSerializer serializer = new XmlSerializer(typeof(DataSet));
    return (DataSet)serializer.Deserialize(stream);
}

public MyClass PerformDeserialization2(Stream stream) {
    XmlSerializer serializer = new XmlSerializer(typeof(MyClass));
    return (MyClass)serializer.Deserialize(stream);
}

public class MyClass
{
    // Property of type DataTable, automatically serialized and
    // deserialized as part of the overall MyClass payload.
    public DataTable MyDataTable { get; set; }
}
```

在這些情況下，威脅模型和安全性保證與[ReadXml 和 DataTable. ReadXml 區段](#dsrdtr)相同。

## <a name="deserialize-a-dataset-or-datatable-via-jsonconvert"></a>透過 >jsonconvert.deserializeobject 還原序列化資料集或 DataTable

熱門的協力廠商 Newtonsoft 程式庫 [JSON.NET](https://www.newtonsoft.com/json) 可以用來還原序列化 `DataSet` 和 `DataTable` 實例，如下列程式碼所示：

```cs
using System.Data;
using Newtonsoft.Json;

public DataSet PerformDeserialization1(string json) {
    return JsonConvert.DeserializeObect<DataSet>(data);
}

public MyClass PerformDeserialization2(string json) {
    return JsonConvert.DeserializeObect<MyClass>(data);
}

public class MyClass
{
    // Property of type DataTable, automatically serialized and
    // deserialized as part of the overall MyClass payload.
    public DataTable MyDataTable { get; set; }
}
```

從不 `DataSet` 受信任的 JSON blob 還原序列化或以此 `DataTable` 方式並不安全。 這種模式很容易遭到阻絕服務攻擊。 這類攻擊可能會導致應用程式損毀，或使其無法回應。

> [!NOTE]
> Microsoft 不保證或支援協力廠商程式庫（例如 _Newtonsoft.Js_）的執行。 這項資訊是為了完整性而提供，而且在撰寫本文時，是正確的。

## <a name="deserialize-a-dataset-or-datatable-via-binaryformatter"></a>透過 BinaryFormatter 還原序列化資料集或 DataTable

開發人員絕不能使用 `BinaryFormatter` 、 `NetDataContractSerializer` 、 `SoapFormatter` 或相關的 ***unsafe*** 格式子， `DataSet` `DataTable` 從不受信任的承載還原序列化或實例：

* 這很容易受到完整的遠端程式碼執行攻擊。
* 使用自訂 `SerializationBinder` 並不足以防止這類攻擊。

## <a name="safe-replacements"></a>安全取代

針對下列任一項的應用程式：

* 接受 `DataSet` 或 `DataTable` 透過 .asmx SOAP 端點或 WCF 端點。
* 將不受信任的資料還原序列化為或的實例 `DataSet` `DataTable` 。

請考慮將物件模型取代為使用 [Entity Framework](/ef)。 Entity Framework：

* 是一種功能豐富、現代化的物件導向架構，可代表關聯式資料。
* 引進不同的資料庫提供者 [生態系統](/ef/core/providers/) ，讓您輕鬆地透過 Entity Framework 物件模型來投影資料庫查詢。
* 從不受信任的來源還原序列化資料時，提供內建的保護。

針對使用 SOAP 端點的應用程式 `.aspx` ，請考慮將這些端點變更為使用 [WCF](/dotnet/framework/wcf/)。 WCF 是 web 服務的功能更完整的取代 `.asmx` 。 您 [可以透過 SOAP 公開](../../../wcf/feature-details/how-to-expose-a-contract-to-soap-and-web-clients.md) WCF 端點，以與現有的呼叫端相容。

## <a name="code-analyzers"></a>程式碼分析器

編譯原始程式碼時所執行的程式碼分析器安全性規則，可協助您在 c # 和 Visual Basic 程式碼中找到與此安全性問題相關的弱點。 CodeAnalysis 將 microsoft.codeanalysis.fxcopanalyzers 是在 [nuget.org](https://www.nuget.org/)上散發之程式碼分析器的 NuGet 套件。

如需程式碼分析器的總覽，請參閱 [原始程式碼分析器的總覽](https://docs.microsoft.com/visualstudio/code-quality/roslyn-analyzers-overview)。

啟用下列 CodeAnalysis 規則：

- [CA2350](https://docs.microsoft.com/visualstudio/code-quality/ca2350)：不使用 DataTable. ReadXml ( # A1 與不受信任的資料
- [CA2351](https://docs.microsoft.com/visualstudio/code-quality/ca2351)：不使用資料集. ReadXml ( # A1 與不受信任的資料
- [CA2352](https://docs.microsoft.com/visualstudio/code-quality/ca2352)：可序列化類型的 Unsafe DataSet 或 DataTable 可能很容易受到遠端程式碼執行攻擊
- [CA2353](https://docs.microsoft.com/visualstudio/code-quality/ca2353)： serializable 類型中不安全的 DataSet 或 DataTable
- [CA2354](https://docs.microsoft.com/visualstudio/code-quality/ca2354)：還原序列化的物件圖形中不安全的資料集或 DataTable 可能很容易受到遠端程式碼執行攻擊
- [CA2355](https://docs.microsoft.com/visualstudio/code-quality/ca2355)：在還原序列化物件圖形中找到 Unsafe 資料集或 DataTable 類型
- [CA2356](https://docs.microsoft.com/visualstudio/code-quality/ca2356)： web 還原序列化物件圖形中不安全的資料集或 DataTable 類型
- [CA2361](https://docs.microsoft.com/visualstudio/code-quality/ca2361)：確定包含資料集的自動產生類別 ReadXml ( # A1 未與不受信任的資料搭配使用
- [CA2362](https://docs.microsoft.com/visualstudio/code-quality/ca2362)：自動產生的可序列化類型中不安全的資料集或 DataTable 可能很容易受到遠端程式碼執行攻擊

如需設定規則的詳細資訊，請參閱 [使用程式碼分析器](https://docs.microsoft.com/visualstudio/code-quality/use-roslyn-analyzers)。

下列 NuGet 套件中提供新的安全性規則：

- CodeAnalysis. 將 microsoft.codeanalysis.fxcopanalyzers 3.3.0：適用于 Visual Studio 2019 16.3 版或更新版本
- CodeAnalysis. 將 microsoft.codeanalysis.fxcopanalyzers 2.9.11：適用于 Visual Studio 2017 15.9 版或更新版本
