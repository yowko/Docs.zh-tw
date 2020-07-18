---
title: 資料集和 DataTable 安全性指引
ms.date: 07/14/2020
dev_langs:
- csharp
ms.openlocfilehash: 2fbac625ae0049fc4c363977dc1d3fbcfb376025
ms.sourcegitcommit: 3492dafceb5d4183b6b0d2f3bdf4a1abc4d5ed8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2020
ms.locfileid: "86416194"
---
# <a name="dataset-and-datatable-security-guidance"></a>資料集和 DataTable 安全性指引

本文適用于：

* .NET Framework （所有版本）
* .NET Core 和更新版本
* .NET 5.0 和更新版本

[DataSet](/dotnet/api/system.data.dataset)和[DataTable](/dotnet/api/system.data.datatable)類型是舊版的 .net 元件，可將資料集表示為 managed 物件。 這些元件是在 .NET 1.0 中引進，做為原始[ADO.NET 基礎結構](/dotnet/framework/data/adonet/dataset-datatable-dataview/)的一部分。 其目標是要提供關聯式資料集的受控視圖，並將資料的基礎來源抽象化為 XML、SQL 或其他技術。

如需 ADO.NET 的詳細資訊，包括更多現代化的資料檢視範例，請參閱[ADO.NET 檔](/dotnet/framework/data/adonet/)。

## <a name="default-restrictions-when-deserializing-a-dataset-or-datatable-from-xml"></a>從 XML 還原序列化 DataSet 或 DataTable 時的預設限制

在所有支援的 .NET Framework、.NET Core 和 .NET 版本上，針對還原序列化 `DataSet` `DataTable` 資料中可能出現的物件類型，施加下列限制。 根據預設，此清單僅限於：

* 基本和基本對等專案： `bool` 、 `char` 、 `sbyte` 、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、 `byte` `short` `ushort` `int` `uint` `long` `ulong` `float` `double` `decimal` `DateTime` `DateTimeOffset` `TimeSpan` `string` `Guid` `SqlBinary` `SqlBoolean` `SqlByte` `SqlBytes` `SqlChars` `SqlDateTime` `SqlDecimal` `SqlDouble` `SqlGuid` `SqlInt16` `SqlInt32` `SqlInt64` `SqlMoney` `SqlSingle` 和 `SqlString` 。
* 常用的非基本類型： `Type` 、 `Uri` 和 `BigInteger` 。
* 常用的_系統。繪圖_類型： `Color` 、 `Point` 、 `PointF` 、 `Rectangle` 、 `RectangleF` 、 `Size` 和 `SizeF` 。
* `Enum`各種.
* 上述類型的陣列和清單。

如果傳入的 XML 資料包含的物件的類型不在此清單中：

* 隨即擲回例外狀況。
* 還原序列化操作失敗。

將 XML 載入到現有的 `DataSet` 或 `DataTable` 實例時，也會將現有的資料行定義納入考慮。 如果資料表已經包含自訂類型的資料行定義，則該類型會暫時加入至 XML 還原序列化作業期間的允許清單。

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

當您使用來還原序列化或的實例時，也適用物件類型限制 `XmlSerializer` `DataSet` `DataTable` 。 不過，使用來還原序列化或的實例時，可能不適用這些限制 `BinaryFormatter` `DataSet` `DataTable` 。

使用時，不適用物件類型限制 `DataAdapter.Fill` ，例如 `DataTable` 直接從資料庫填入實例時，不使用 XML 還原序列化 api。

### <a name="extend-the-list-of-allowed-types"></a>擴充允許類型的清單

除了以上所列的內建類型之外，應用程式可以擴充允許的類型清單來包含自訂類型。 如果擴充允許的類型清單，變更會影響_all_ `DataSet` `DataTable` 應用程式內的所有和實例。 無法從內建的允許類型清單中移除類型。

#### <a name="extend-through-configuration-net-framework-40---48"></a>透過設定擴充（.NET Framework 4.0-4.8）

_App.config_可以用來擴充允許的類型清單。 若要擴充允許的類型清單：

* 使用專案 `<configSections>` ，將參考加入至_system.object_設定區段。
* 使用 `<system.data.dataset.serialization>` / `<allowedTypes>` 來指定其他類型。

每個 `<add>` 元素都只能使用其元件限定類型名稱來指定一個類型。 若要將其他類型新增至允許的類型清單，請使用多個 `<add>` 元素。

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

若要取得類型的元件限定名稱，請使用[AssemblyQualifiedName](/dotnet/api/system.type.assemblyqualifiedname)屬性，如下列程式碼所示。

```cs
string assemblyQualifiedName = typeof(Fabrikam.CustomType).AssemblyQualifiedName;
```

<a name="etc"></a>

#### <a name="extend-through-configuration-net-framework-20---35"></a>透過設定擴充（.NET Framework 2.0-3.5）

如果您的應用程式以 .NET Framework 2.0 或3.5 為目標，您仍然可以使用上述_App.config_機制來擴充允許的類型清單。 不過，您 `<configSections>` 的元素看起來會稍有不同，如下列程式碼所示：

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

#### <a name="extend-programmatically-net-framework-net-core-net-50"></a>以程式設計方式擴充（.NET Framework、.NET Core、.NET 5.0 +）

您也可以使用_DataSetDefaultAllowedTypes_ [，以程式](/dotnet/api/system.appdomain.setdata)設計方式擴充允許的類型清單，如下列程式碼所示。

```cs
Type[] extraAllowedTypes = new Type[]
{
    typeof(Fabrikam.CustomType),
    typeof(Contoso.AdditionalCustomType)
};

AppDomain.CurrentDomain.SetData("System.Data.DataSetDefaultAllowedTypes", extraAllowedTypes);
```

如果使用延伸模組機制，則與金鑰_DataSetDefaultAllowedTypes_相關聯的值必須是類型 `Type[]` 。

在 .NET Framework 上，允許的類型清單可使用_App.config_和進行擴充 `AppDomain.SetData` 。 在此情況下， `DataSet` 和 `DataTable` 會允許將物件還原序列化為數據的一部分（如果其中一個清單中有其類型的話）。

### <a name="run-an-app-in-audit-mode-net-framework"></a>以 audit 模式執行應用程式（.NET Framework）

在 .NET Framework 中， `DataSet` 並 `DataTable` 提供「稽核模式」功能。 啟用 audit 模式時，會 `DataSet` 將 `DataTable` 傳入物件的類型與允許的類型清單進行比較。 不過，如果看到不允許其類型的物件，則**不**會擲回例外狀況。 相反 `DataSet` 地，和 `DataTable` 會通知任何附加的 `TraceListener` 實例有可疑的類型存在，讓 `TraceListener` 能夠記錄此資訊。 不會擲回任何例外狀況，而且還原序列化作業會繼續進行。

> [!WARNING]
> 以「audit mode」執行應用程式應該只是用於測試的暫時量值。 啟用 audit 模式時， `DataSet` 並 `DataTable` 不會強制執行類型限制，這可能會在您的應用程式內引進安全性漏洞。 如需詳細資訊，請參閱標題為[不受信任的輸入](#swr)[移除所有類型限制](#ratr)和安全性的章節。

您可以透過_App.config_來啟用 Audit 模式：

* 請參閱本檔中的[擴充到](#etc)設定一節，以取得要為元素放置之適當值的相關資訊 `<configSections>` 。
* 使用 `<allowedTypes auditOnly="true">` 來啟用 audit 模式，如下列標記所示。

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

啟用 audit 模式之後，您就可以使用_App.config_ ，將慣用的 `TraceListener` 內建 `DataSet` `TraceSource.` 追蹤來源名稱連接到_system.web. Data. DataSet_。 下列範例示範如何將追蹤事件寫入主控台_和_磁片上的記錄檔。

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

如需和的詳細資訊 `TraceSource` `TraceListener` ，請參閱檔 how [To：搭配追蹤接聽項使用 TraceSource 和篩選](../../../debug-trace-profile/how-to-use-tracesource-and-filters-with-trace-listeners.md)。

> [!NOTE]
> .NET Core 或 .NET 5.0 和更新版本中不提供以 audit 模式執行應用程式的功能。

<a name="ratr"></a>

### <a name="remove-all-type-restrictions"></a>移除所有類型限制

如果應用程式必須從和移除所有類型限制 `DataSet` 限制 `DataTable` ：

* 有數個選項可隱藏類型限制限制。
* 可用的選項取決於應用程式的目標架構。

> [!WARNING]
> 移除所有類型的限制可能會在應用程式內引進安全性漏洞。 使用這種機制時，請確定應用**程式不會使用** `DataSet` 或 `DataTable` 來讀取不受信任的輸入。 如需詳細資訊，請參閱[CVE-2020-1147](https://portal.msrc.microsoft.com/en-us/security-guidance/advisory/CVE-2020-1147) ，以及[與不受信任的輸入有關](#swr)的下一節標題為安全。

#### <a name="through-appcontext-configuration-net-framework-46---48-net-core-21-and-later-net-50-and-later"></a>透過 AppCoNtext 設定（.NET Framework 4.6-4.8、.NET Core 2.1 和更新版本、.NET 5.0 和更新版本）

`AppContext` `Switch.System.Data.AllowArbitraryDataSetTypeInstantiation` 當設定為時，會 `true` 從和移除所有類型限制限制的參數 `DataSet` `DataTable` 。

在 .NET Framework 中，可以透過_App.config_啟用此交換器，如下列設定所示：

```xml
<configuration>
   <runtime>
      <!-- Warning: setting the following switch can introduce a security problem. -->
      <AppContextSwitchOverrides value="Switch.System.Data.AllowArbitraryDataSetTypeInstantiation=true" />
   </runtime>
</configuration>
```

在 ASP.NET 中， `<AppContextSwitchOverrides>` 無法使用元素。 相反地，您可以透過_Web.config_來啟用參數，如下列設定所示：

```xml
<configuration>
    <appSettings>
        <!-- Warning: setting the following switch can introduce a security problem. -->
        <add key="AppContext.SetSwitch:Switch.System.Data.AllowArbitraryDataSetTypeInstantiation" value="true" />
    </appSettings>
</configuration>
```

如需詳細資訊，請參閱 [\<AppContextSwitchOverrides>](../../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 元素。

在 .NET Core、.NET 5 和 ASP.NET Core 中，這項設定是由_上的runtimeconfig.js_所控制，如下列 JSON 所示：

```json
{
  "runtimeOptions": {
    "configProperties": {
      "Switch.System.Data.AllowArbitraryDataSetTypeInstantiation": true
    }
  }
}
```

如需詳細資訊，請參閱[.Net Core 執行時間設定](/dotnet/core/run-time-config/)值。

`AllowArbitraryDataSetTypeInstantiation`也可以透過[AppCoNtext](/dotnet/api/system.appcontext.setswitch)以程式設計方式設定，而不是使用設定檔，如下列程式碼所示：

```cs
// Warning: setting the following switch can introduce a security problem.
AppContext.SetSwitch("Switch.System.Data.AllowArbitraryDataSetTypeInstantiation", true);
```

 如果您選擇上述的程式設計方法，對的呼叫 `AppContext.SetSwitch` 應該會在應用程式啟動時提早發生。

#### <a name="through-the-machine-wide-registry-net-framework-20---48"></a>透過整部電腦的登錄（.NET Framework 2.0-4.8）

如果 `AppContext` 無法使用，可以使用 Windows 登錄來停用類型限制檢查：

* 系統管理員必須設定登錄。
* 使用登錄是全電腦的變更，將會影響在機器上執行的_所有_應用程式。

| 類型  |  值 |
|---|---|
| **登錄機碼** | `HKLM\SOFTWARE\Microsoft\.NETFramework\AppContext` |
| **值名稱** | `Switch.System.Data.AllowArbitraryDataSetTypeInstantiation` |
| **實值型別** | `REG_SZ` |
| **值資料** | `true` |

在64位的作業系統上，我需要為64位金鑰（如上所示）和32位金鑰新增這兩個值。 32位金鑰位於 `HKLM\SOFTWARE\WOW6432Node\Microsoft\.NETFramework\AppContext` 。

如需使用登錄進行設定的詳細資訊 `AppContext` ，請參閱「連結[庫取用者的 AppCoNtext](/dotnet/api/system.appcontext#appcontext-for-library-consumers)」。

<a name="swr"></a>

## <a name="safety-with-regard-to-untrusted-input"></a>與不受信任的輸入有關的安全性

雖然和會對在還原 `DataSet` `DataTable` 序列化 XML 裝載時允許出現的類型強加預設限制，但__ `DataSet` `DataTable` 在填入不受信任的輸入時，一般不安全。__ 以下是 `DataSet` 或 `DataTable` 實例可能會讀取不受信任的輸入之方式的不完整清單。

* `DataAdapter`會參考資料庫，而 `DataAdapter.Fill` 方法則是用來在中填入 `DataSet` 資料庫查詢的內容。
* `DataSet.ReadXml`或 `DataTable.ReadXml` 方法是用來讀取包含資料行和資料列資訊的 XML 檔案。
* `DataSet`或 `DataTable` 實例會序列化為 ASP.NET （SOAP） web 服務或 WCF 端點的一部分。
* 序列化程式（例如） `XmlSerializer` 是用來 `DataSet` `DataTable` 從 XML 資料流程還原序列化或實例。
* 序列化程式（例如） `JsonConvert` 是用來 `DataSet` `DataTable` 從 JSON 資料流程還原序列化或實例。 `JsonConvert`是常用的協力廠商[Newtonsoft.Js](https://www.newtonsoft.com/json)程式庫中的方法。
* 序列化程式（例如） `BinaryFormatter` 是用來 `DataSet` `DataTable` 從原始位元組資料流程還原序列化或實例。

本檔討論先前案例的安全性考慮。

## <a name="use-dataadapterfill-to-populate-a-dataset-from-an-untrusted-data-source"></a>用 `DataAdapter.Fill` 來 `DataSet` 從不受信任的資料來源填入

您 `DataSet` 可以 `DataAdapter` 使用[ `DataAdapter.Fill` 方法](/dotnet/api/system.data.common.dataadapter.fill)，從填入實例，如下列範例所示。

```cs
// Assumes that connection is a valid SqlConnection object.  
string queryString =
  "SELECT CustomerID, CompanyName FROM dbo.Customers";  
SqlDataAdapter adapter = new SqlDataAdapter(queryString, connection);  
  
DataSet customers = new DataSet();  
adapter.Fill(customers, "Customers");
```

（上述程式碼範例是在[從 DataAdapter 填入資料集中](../populating-a-dataset-from-a-dataadapter.md)找到之較大範例的一部分）。

> 大部分的應用程式都可以簡化並假設其資料庫層是受信任的。 不過，如果您的應用程式是[威脅](https://www.microsoft.com/securityengineering/sdl/threatmodeling)模型化的習慣，您的威脅模型可能會考慮到應用程式（用戶端）和資料庫層（伺服器）之間的信任界限。 使用[相互驗證](/sql/relational-databases/native-client/features/service-principal-name-spn-support-in-client-connections)或用戶端與伺服器之間的[AAD 驗證](/azure/azure-sql/database/authentication-aad-overview)，是協助解決與此相關聯之風險的一種方式。 本節的其餘部分將討論用戶端連接到不受信任的伺服器時可能產生的結果。

將指向 `DataAdapter` 不受信任資料來源的結果取決於本身的執行 `DataAdapter` 。

### <a name="sqldataadapter"></a>SqlDataAdapter

針對內建類型[SqlDataAdapter](/dotnet/api/microsoft.data.sqlclient.sqldataadapter)，參考不受信任的資料來源可能會導致拒絕服務（DoS）攻擊。 DoS 攻擊可能會導致應用程式變得沒有回應或損毀。 如果攻擊者可以將 DLL 與應用程式一起植入，他們也可以達到本機程式碼執行的能力。

### <a name="other-dataadapter-types"></a>其他 DataAdapter 類型

協力廠商的 `DataAdapter` 執行必須自行評估其在臉部不受信任的輸入時，所提供的安全性保證。 .NET 無法針對這些執行提供任何安全保證。

<a name="dsrdtr"></a>

## <a name="datasetreadxml-and-datatablereadxml"></a>ReadXml 和 DataTable. ReadXml

`DataSet.ReadXml`與不 `DataTable.ReadXml` 受信任的輸入搭配使用時，和方法不安全。 我們強烈建議取用者改為考慮使用本檔稍後所述的其中一種替代方案。

`DataSet.ReadXml`和的 `DataTable.ReadXml` 執行原本是在序列化弱點被視為很容易瞭解的威脅類別目錄之前建立的。 因此，此程式碼不會遵循目前的安全性最佳作法。 這些 Api 可用來做為攻擊者的向量，以對 web 應用程式執行 DoS 攻擊。 這些攻擊可能會使 web 服務無回應，或導致非預期的進程終止。 此架構不會提供這些攻擊類別的緩和措施，而 .NET 會將此行為視為「依設計」。

.NET 已發行安全性更新，以降低某些問題，例如和中的資訊洩漏或遠端程式碼執行 `DataSet.ReadXml` `DataTable.ReadXml` 。 .NET 安全性更新可能不會針對這些威脅類別提供完整的保護。 取用者應該評估其個別案例，並考慮其對這些風險的潛在風險。

取用者應該注意到，這些 Api 的安全性更新可能會影響應用程式在某些情況下的相容性。 此外，也有可能會發現這些 Api 中的 novel 弱點，而 .NET 無法實際發佈安全性更新。

我們建議這些 Api 的取用者為：

* 請考慮使用本檔稍後所述的其中一種替代方案。
* 對其應用程式執行個別風險評量。

取用者會自行負責判斷是否要使用這些 Api。 取用者應評估任何安全性、技術和法律風險，包括可能使用這些 Api 的法規需求。

## <a name="dataset-and-datatable-via-aspnet-web-services-or-wcf"></a>透過 ASP.NET web 服務或 WCF 的資料集和 DataTable

您可以 `DataSet` `DataTable` 在 ASP.NET （SOAP） web 服務中接受或實例，如下列程式碼所示：

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

這種方式的變化不是接受 `DataSet` 或 `DataTable` 直接作為參數，而是改為接受它做為整體 SOAP 序列化物件圖形的一部分，如下列程式碼所示：

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

或者，使用 WCF，而不是 ASP.NET web 服務：

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

在所有這些情況下，威脅模型和安全性保證與[ReadXml 和 DataTable. ReadXml 區段](#dsrdtr)相同。

## <a name="deserialize-a-dataset-or-datatable-via-xmlserializer"></a>透過 XmlSerializer 還原序列化 DataSet 或 DataTable

開發人員可以使用來還原序列化 `XmlSerializer` `DataSet` 和 `DataTable` 實例，如下列程式碼所示：

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

## <a name="deserialize-a-dataset-or-datatable-via-jsonconvert"></a>透過 Jsonconvert.deserializeobject 還原序列化 DataSet 或 DataTable

熱門的協力廠商 Newtonsoft 程式庫[JSON.NET](https://www.newtonsoft.com/json)可用於還原序列化 `DataSet` 和 `DataTable` 實例，如下列程式碼所示：

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

`DataSet` `DataTable` 以這種方式從不受信任的 JSON blob 還原序列化或是不安全的。 此模式很容易遭到阻絕服務攻擊。 這類攻擊可能會使應用程式損毀或呈現無回應。

> [!NOTE]
> Microsoft 不保證或不支援執行協力廠商程式庫，例如_上的Newtonsoft.Js_。 這項資訊是為了完整性而提供，而且在撰寫本文時是正確的。

## <a name="deserialize-a-dataset-or-datatable-via-binaryformatter"></a>透過 BinaryFormatter 還原序列化 DataSet 或 DataTable

開發人員絕對不能使用 `BinaryFormatter` 、 `NetDataContractSerializer` 、 `SoapFormatter` 或相關的***unsafe***格式子，將 `DataSet` 或 `DataTable` 實例從不受信任的承載還原序列化：

* 這很容易受到完整的遠端程式碼執行攻擊。
* 使用自訂 `SerializationBinder` 並不足以防止這類攻擊。

## <a name="safe-replacements"></a>安全取代

針對下列任一應用程式：

* 接受 `DataSet` 或 `DataTable` 透過 .asmx SOAP 端點或 WCF 端點。
* 將不受信任的資料還原序列化為或的實例 `DataSet` `DataTable` 。

請考慮取代物件模型，以使用[Entity Framework](/ef)。 Entity Framework：

* 是一種豐富、現代化、物件導向的架構，可以代表關聯式資料。
* 引進[了各種不同](/ef/core/providers/)的資料庫提供者生態系統，讓您可以輕鬆地透過 Entity Framework 物件模型來投影資料庫查詢。
* 從不受信任的來源還原序列化資料時，提供內建的保護功能。

針對使用 SOAP 端點的應用程式 `.aspx` ，請考慮將這些端點變更為使用[WCF](/dotnet/framework/wcf/)。 WCF 是一種功能更完整的 `.asmx` web 服務取代。 WCF 端點[可以透過 SOAP 公開](../../../wcf/feature-details/how-to-expose-a-contract-to-soap-and-web-clients.md)，以與現有的呼叫端相容。
