---
title: 遷移新式桌面應用程式
description: 針對新式桌面應用程式的遷移程式，您需要知道的一切。
ms.date: 01/19/2021
ms.openlocfilehash: b5bea6e601dc040adfd8ed410320a3416cb3372e
ms.sourcegitcommit: 632818f4b527e5bf3c48fc04e0c7f3b4bdb8a248
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2021
ms.locfileid: "98615759"
---
# <a name="migrating-modern-desktop-applications"></a>遷移新式桌面應用程式

在本章中，我們將探討將現有應用程式從 .NET Framework 遷移至 .NET 時，最常見的問題和挑戰。

複雜的桌面應用程式不會獨立運作，而且需要與可能位於本機電腦或遠端伺服器上之子系統的某種互動。 可能需要某種類型的資料庫，才能在本機或遠端連線為持續性儲存區。 隨著網際網路和服務導向架構的引發，您的應用程式通常會連線到位於遠端伺服器或雲端中的某種服務。 您可能需要存取電腦檔案系統，才能執行一些功能。 或者，您可能使用的功能是位於應用程式外部的 COM 物件內，如果您是在應用程式中整合 Office 元件，這是常見的情況。

此外，.NET Framework 和 .NET 公開的 API 介面有一些差異，而 .NET Framework 上提供的某些功能無法在 .NET 上使用。 因此，在規劃遷移時，請務必瞭解並納入考慮。

## <a name="configuration-files"></a>組態檔

設定檔可讓您儲存在執行時間讀取的屬性集，並影響應用程式的行為，例如尋找資料庫的位置，或執行迴圈的次數。 這項技術的優點是您可以修改應用程式的某些層面，而不需要重新編碼和重新編譯。 比方說，當相同的應用程式程式碼在具有一組特定設定值的開發環境中執行，且在生產環境中使用不同的應用程式程式碼時，這會很有用。

### <a name="configuration-on-net-framework"></a>.NET Framework 上的設定

如果您有工作 .NET Framework 桌面應用程式，您可能會有 <xref:System.Configuration.AppSettingsSection> 從命名空間透過類別存取的app.config檔案 `System.Configuration` 。

在 .NET Framework 基礎結構中，有一階層的設定檔會繼承其父代的屬性。 您可以找到 *machine.config* 檔案，該檔案會定義可以在任何子系設定檔中使用或覆寫的許多屬性和設定區段。

### <a name="configuration-on-net"></a>.NET 上的設定

在 .NET 世界中，沒有 *machine.config* 的檔案。 雖然您可以繼續使用舊的舊 <xref:System.Configuration> 命名空間，但您還是可以考慮改用新式，以 <xref:Microsoft.Extensions.Configuration> 提供很多的增強功能。

設定 API 支援設定提供者的概念，其定義要用來載入設定的資料來源。 有不同類型的內建提供者，例如：

- 記憶體內部 .NET 物件
- INI 檔案
- JSON 檔案
- XML 檔案
- 命令列引數
- 環境變數
- 加密的使用者存放區

 您也可以建立自己的版本。

新的設定允許可分組為多層級階層的成對名稱/值組清單。 任何儲存的值會對應至字串，且有內建的系結支援，可讓您將設定還原序列化為自訂的簡單 CLR 物件， (POCO) 物件。

<xref:Microsoft.Extensions.Configuration.ConfigurationBuilder>物件可讓您新增應用程式所需數量的設定提供者，並使用優先順序規則來解析喜好設定。 因此，您在程式碼中加入的最後一個提供者會覆寫其他提供者。 由於您可以針對開發、測試和生產環境定義不同的設定，並在程式碼內的單一函式上管理它們，因此這是管理不同環境來執行的絕佳功能。

### <a name="migrating-configuration-files"></a>正在遷移設定檔

您可以繼續使用現有的 app.config XML 檔案。 不過，您可以利用這個機會來遷移您的設定，以受益于 .NET 上的數個增強功能。

若要從舊樣式的 *app.config* 遷移至新的設定檔，您應該選擇 XML 格式和 JSON 格式。

如果您選擇 XML，則轉換很簡單。 因為內容相同，所以只要以 XML 形式儲存 *app.config* 檔案，做為類型。 然後，將參考 AppSettings 的程式碼變更為使用 `ConfigurationBuilder` 類別。 這種變更應該很簡單。

如果您想要使用 JSON 格式，而不想要手動遷移，可在 .NET 上使用稱為 [dotnet config2json](https://www.nuget.org/packages/dotnet-config2json/) 的工具，可將 *app.config* 檔案轉換為 JSON 設定檔。

使用 *machine.config* 檔中定義的設定區段時，您也可能會遇到一些問題。 例如，請考慮下列設定：

```xml
<configuration>
    <system.diagnostics>
        <switches>
            <add name="General" value="4" />
        </switches>
        <trace autoflush="true" indentsize="2">
            <listeners>
                <add name="myListener"
                     type="System.Diagnostics.TextWriterTraceListener,
                           System, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
                     initializeData="MyListener.log"
                     traceOutputOptions="ProcessId, LogicalOperationStack, Timestamp, ThreadId, Callstack, DateTime" />
            </listeners>
        </trace>
    </system.diagnostics>
</configuration>
```

如果您將此設定設為 .NET，您將會收到例外狀況：

> 無法辨識的設定區段系統診斷

發生此例外狀況是因為該區段和負責處理該區段的元件已定義于 *machine.config* 檔案中，但目前不存在。

若要輕鬆地修正此問題，您可以從舊的 *machine.config* 將區段定義複製到新的設定檔：

```xml
<configSections>
    <section name="system.diagnostics"
             type="System.Diagnostics.SystemDiagnosticsSection,
                   System, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>
</configSections>
```

## <a name="accessing-databases"></a>存取資料庫

幾乎所有的桌面應用程式都需要某種類型的資料庫。 針對桌面，通常會在桌面應用程式和 database engine 之間直接連線來尋找用戶端-伺服器架構。 這些資料庫可以是本機或遠端，視需要在不同使用者之間共用資訊的需求而定。

從程式碼的觀點來看，有許多技術和架構可讓開發人員連接、查詢及更新資料庫。

在談到 Windows 傳統型應用程式時，最常見的資料庫範例是 Microsoft Access 和 Microsoft SQL Server。 如果您在桌上型電腦上擁有20年以上的體驗程式設計，則會很熟悉 ODBC、OLEDB、RDO、ADO、ADO.NET、LINQ 和 Entity Framework 等名稱。

### <a name="odbc"></a>ODBC

因為 Microsoft 提供的連結 `System.Data.Odbc` 庫與 .NET Standard 2.0 相容，所以您可以繼續在 .net 上使用 ODBC。

### <a name="ole-db"></a>OLE DB

[OLE DB](/previous-versions/windows/desktop/ms722784(v=vs.85)) 是以一致的方式存取各種資料來源的絕佳方式。 但它是以 COM 為基礎，這是一種僅限 Windows 的技術，因此不適合用于跨平臺技術，例如 .NET。 SQL Server 版本2014和更新版本也不支援此功能。 基於這些原因，.NET 不支援 OLE DB。

### <a name="adonet"></a>ADO.NET

您仍然可以從 .NET 上現有的桌面程式碼使用 ADO.NET。 您只需要更新一些 NuGet 套件。

### <a name="ef-core-vs-ef6"></a>EF Core 與 EF6

目前支援兩種版本的 Entity Framework (EF) ，Entity Framework 6 (EF6) 和 EF Core。

在 .NET Framework 世界中發行的最新技術是 Entity Framework，6.4 是最新版本。 隨著 .NET Core 的推出，Microsoft 也會根據 Entity Framework 發行新的資料存取堆疊，並呼叫 Entity Framework Core。

您可以從 .NET Framework 和 .NET 使用 EF 6.4 和 EF Core。 那麼，有哪些決策驅動程式有助於決定兩者之間？

EF 6.3 是 EF6 的第一個版本，可在 .NET 上執行並跨平臺運作。 事實上，這個版本的主要目標是要讓您更輕鬆地將使用 EF6 的現有應用程式遷移至 .NET。

EF Core 旨在提供類似於 EF6 的開發人員體驗。 大部分的頂層 API 都維持不變，因此使用過 EF6 的開發人員會對 EF Core 感到熟悉。

雖然是相容的，但在進行決策之前，您應該檢查的實作為差異。
如需詳細資訊，請參閱 [比較 EF Core & EF6](/ef/efcore-and-ef6/)。

建議您在下列情況中使用 EF Core：

* 應用程式需要 .NET 的功能。
* EF Core 支援應用程式所需的所有功能。

如果下列兩個條件成立，請考慮使用 EF6：

* 應用程式將在 Windows 上執行，並 .NET Framework 4.0 或更新版本。
* EF6 支援應用程式所需的所有功能。

### <a name="relational-databases"></a>關聯式資料庫

#### <a name="sql-server"></a>SQL Server

如果您在幾年前開發桌上型電腦，SQL Server 就是其中一個選擇的資料庫。 使用 <xref:System.Data.SqlClient> .NET Framework 中的，您可以存取封裝的 SQL Server 版本，以封裝資料庫特定的通訊協定。

在 .NET 中，您可以找到新的 `SqlClient` 類別，與 .NET Framework 中現有的類別完全相容，但位於連結 <xref:Microsoft.Data.SqlClient> 庫中。 您只需要新增 [SqlClient](https://www.nuget.org/packages/Microsoft.Data.SqlClient/) NuGet 套件的參考，並對命名空間進行一些重新命名，一切應該都能如預期般運作。

#### <a name="microsoft-access"></a>Microsoft Access

當您不需要精密且可擴充的 SQL Server 時，會使用 Microsoft Access。 您仍然可以使用程式庫連接到 Microsoft Access <xref:System.Data.Odbc> 。

## <a name="consuming-services"></a>使用服務

隨著服務導向架構的引發，桌面應用程式會從用戶端-伺服器模型開始發展到三層式的方法。 在用戶端伺服器的方法中，直接資料庫連線是從保存商務邏輯的用戶端建立，通常是在單一 EXE 檔案內。 另一方面，三層式方法會建立一個中繼服務層，以實行商務邏輯和資料庫存取，以提供更佳的安全性、可調整性和重複使用性。 該層方法不會直接使用資料的資料集，而是依賴一組執行合約和類型物件的服務來執行資料傳輸。

如果您有使用 WCF 服務的桌面應用程式，而您想要將它遷移至 .NET，則需要考慮一些事項。

第一件事是如何解決設定以存取服務。 因為 .NET 上的設定不同，所以您必須在設定檔中進行一些更新。

其次，您必須使用 Visual Studio 2019 上的新工具，重新產生服務用戶端。 在此步驟中，您必須考慮啟用同步作業的產生，使用戶端與您現有的程式碼相容。

在遷移之後，如果您發現 .NET 上有您需要的程式庫，您可以新增對 [Microsoft 相容性](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) NuGet 套件的參考，並查看是否有遺漏的函式。

如果您使用 <xref:System.Net.WebRequest> 類別來執行 web 服務呼叫，可能會發現 .net 有一些差異。 建議您改為使用 HttpClient。

## <a name="consuming-a-com-object"></a>使用 COM 物件

目前沒有任何方法可將參考加入至 Visual Studio 2019 的 COM 物件，以搭配 .NET 使用。 因此，您必須手動修改專案檔。

`COMReference`在專案檔內插入結構，如下列範例所示：

```xml
<ItemGroup>
    <COMReference Include="MSHTML">
        <Guid>{3050F1C5-98B5-11CF-BB82-00AA00BDCE0B}\</Guid>
        <VersionMajor>4</VersionMajor>
        <VersionMinor>0</VersionMinor>
        <Lcid>0</Lcid>
        <WrapperTool>primary</WrapperTool>
        <Isolated>false</Isolated>
    </COMReference>
</ItemGroup>
```

## <a name="more-things-to-consider"></a>其他應考慮的事項

適用于 .NET Core 或 .NET 5 的 .NET Framework 程式庫可以使用數種技術。 如果您的程式碼相依于這些技術，請考慮本節所述的替代方法。

[Windows 相容性套件](../../core/porting/windows-compat-pack.md)可讓您存取先前僅供 .NET Framework 使用的 api。 它可以在 .NET Core 和 .NET Standard 專案上使用。

如需 API 相容性的詳細資訊，您可以在中找到有關重大變更和已淘汰/舊版 Api 的檔 <https://docs.microsoft.com/dotnet/core/compatibility/fx-core> 。

### <a name="appdomains"></a>AppDomain

應用程式定義域 (AppDomain) 可將應用程式互相隔離。 Appdomain 需要執行時間支援，而且很昂貴。 不支援建立其他應用程式網域。 若要隔離程式碼，建議使用不同的處理序或使用容器作為替代方法。 若要以動態方式載入組件，建議使用新的 <xref:System.Runtime.Loader.AssemblyLoadContext> 類別。

為了讓程式碼遷移 .NET Framework 更容易，.NET 會公開一些 `AppDomain` API 介面。 某些 API 會正常運作 (例如 <xref:System.AppDomain.UnhandledException?displayProperty=nameWithType>)，某些成員不會執行任何動作 (例如 <xref:System.AppDomain.SetCachePath%2A>)，而其中某些會擲回 <xref:System.PlatformNotSupportedException> (例如 <xref:System.AppDomain.CreateDomain%2A>)。

### <a name="remoting"></a>遠端

.NET 遠端處理是用於跨 AppDomain 通訊，但已不再支援。 此外，遠端處理需要執行階段支援，因此維護成本相當高昂。 基於這些理由，.NET 不支援 .net 遠端處理。

針對跨進程的通訊，您應該考慮 (IPC) 機制的處理序間通訊，作為遠端的替代方式，例如 <xref:System.IO.Pipes?displayProperty=nameWithType> 或 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> 類別。

針對跨機器通訊，請使用以網路為基礎的替代方案。 最好是使用低額外負荷的純文字通訊協定，例如 HTTP。 Kestrel Web 伺服器 \(英文\) 是 ASP.NET Core 所使用的 Web 伺服器，也是此情況下可考慮使用的選項。

### <a name="code-access-security-cas"></a>程式碼存取安全性 (CAS)

.NET 不支援沙箱（依賴執行時間或架構來限制受管理應用程式或程式庫所使用或執行的資源）。

使用作業系統所提供的安全性界限（例如虛擬化、容器或使用者帳戶），以最少的許可權集執行處理常式。

### <a name="security-transparency"></a>安全性透明度

與 CAS 類似，安全性透明度會以宣告方式區隔沙箱化程式碼和安全性關鍵程式碼，但已不再支援作為安全性界限。

使用作業系統所提供的安全性界限（例如虛擬化、容器或使用者帳戶），以最少的許可權來執行進程。

>[!div class="step-by-step"]
>[上一個](whats-new-dotnet.md ) 
>[下一步](windows-migration.md)
