---
ms.openlocfilehash: eb3fa768a491f6c0ff4b15479beabd71b0670338
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937266"
---
### <a name="hosting-https-redirection-enabled-for-iis-out-of-process-apps"></a>託管：為 IIS 進程外應用啟用 HTTPS 重定向

[ASP.NET核心模組 （ANCM）](/aspnet/core/host-and-deploy/aspnet-core-module)的 13.0.19218.0 版本通過 IIS 進程外託管，可為 ASP.NET Core 3.0 和 2.2 應用提供現有的 HTTPS 重定向功能。

有關討論，請參閱[點網/阿斯普內科#15243](https://github.com/dotnet/AspNetCore/issues/15243)。

#### <a name="version-introduced"></a>介紹的版本

3.0

#### <a name="old-behavior"></a>舊的行為

ASP.NET Core 2.1 專案範本首先引入了對 HTTPS 中間<xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection%2A>件<xref:Microsoft.AspNetCore.Builder.HstsBuilderExtensions.UseHsts%2A>方法（如 和） 的支援。 啟用 HTTPS 重定向需要添加配置，因為開發中的應用不使用預設埠 443。 [HTTP 嚴格傳輸安全 （HSTS）](https://cheatsheetseries.owasp.org/cheatsheets/HTTP_Strict_Transport_Security_Cheat_Sheet.html)僅在請求已在使用 HTTPS 時才處於活動狀態。 預設情況下，將跳過本地主機。

#### <a name="new-behavior"></a>新的行為

在 ASP.NET 核心 3.0 中，IIS HTTPS 方案[得到了增強](https://github.com/dotnet/AspNetCore/pull/4685)。 通過增強功能，應用可以發現伺服器的 HTTPS 埠，並在預設情況下`UseHttpsRedirection`工作時正常工作。 進程內元件使用`IServerAddresses`該功能完成了埠發現，該功能僅影響 ASP.NET Core 3.0 應用，因為進程內庫使用框架進行版本控制。 進程外元件更改為自動添加`ASPNETCORE_HTTPS_PORT`環境變數。 此更改ASP.NET酷睿 2.2 和 3.0 應用都受到影響，因為進程外元件全域共用。 ASP.NET Core 2.1 應用不受影響，因為它們預設使用以前的 ANCM 版本。

ASP.NET Core 3.0.1 和 3.1.0 預覽 3 中修改了上述行為，以反轉 ASP.NET Core 2.x 中的行為更改。 這些更改僅影響 IIS 進程外應用。

如上所述，安裝ASP.NET Core 3.0.0 具有啟動ASP.NET Core 2.x 應用程式中`UseHttpsRedirection`的中介軟體的副作用。 ASP.NET酷睿 3.0.1 和 3.1.0 預覽 3 中對 ANCM 進行了更改，以便安裝它們不再對 ASP.NET 酷睿 2.x 應用產生此影響。 ASP.NET `ASPNETCORE_HTTPS_PORT` Core 3.0.0 中填充的 ANCM 的環境`ASPNETCORE_ANCM_HTTPS_PORT`變數在 ASP.NET 酷 3.0.1 和 3.1.0 預覽 3 中更改為。 `UseHttpsRedirection`也在這些版本中更新，以瞭解新舊變數。 ASP.NET核心 2.x 不會更新。 因此，它將恢復為預設情況下禁用的前一個行為。

#### <a name="reason-for-change"></a>更改原因

改進了ASP.NET核心 3.0 功能。

#### <a name="recommended-action"></a>建議的動作

如果希望所有用戶端都使用 HTTPS，則無需執行任何操作。 要允許某些用戶端使用 HTTP，請執行以下步驟之一：

* 刪除對`UseHttpsRedirection`專案`UseHsts``Startup.Configure`方法的調用，然後重新部署應用。
* 在*Web.config 檔中*，將`ASPNETCORE_HTTPS_PORT`環境變數設置為空字串。 此更改可以直接在伺服器上發生，而無需重新部署應用。 例如：

    ```xml
    <aspNetCore processPath="dotnet" arguments=".\WebApplication3.dll" stdoutLogEnabled="false" stdoutLogFile="\\?\%home%\LogFiles\stdout" >
        <environmentVariables>
        <environmentVariable name="ASPNETCORE_HTTPS_PORT" value="" />
        </environmentVariables>
    </aspNetCore>
    ```

`UseHttpsRedirection`仍然可以：

* 通過將`ASPNETCORE_HTTPS_PORT`環境變數設置為相應的埠號（在大多數生產方案中為 443），在 ASP.NET Core 2.x 中手動啟動。
* 使用空字串值定義`ASPNETCORE_ANCM_HTTPS_PORT`ASP.NET Core 3.x 中停用。 此值的設置方式與前面的`ASPNETCORE_HTTPS_PORT`示例相同。

運行ASP.NET酷睿 3.0.0 應用的電腦在安裝 ASP.NET 酷睿 3.1.0 預覽 3 ANCM 之前，應安裝ASP.NET酷睿 3.0.1 運行時。 這樣做可確保`UseHttpsRedirection`繼續按預期運行ASP.NET酷睿 3.0 應用。

在 Azure 應用服務中，ANCM 由於其全域性，在獨立于運行時的計畫中部署。 在部署了ASP.NET Core 3.0.1 和 3.1.0 之後，ANCM 已部署到 Azure 中。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

<xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection(Microsoft.AspNetCore.Builder.IApplicationBuilder)?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`M:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection(Microsoft.AspNetCore.Builder.IApplicationBuilder)`

-->
