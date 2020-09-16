---
ms.openlocfilehash: eb3fa768a491f6c0ff4b15479beabd71b0670338
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937266"
---
### <a name="hosting-https-redirection-enabled-for-iis-out-of-process-apps"></a>裝載：針對 IIS 跨進程應用程式啟用 HTTPS 重新導向

透過 IIS 跨進程裝載的 [ASP.NET Core 模組 (ANCM) ](/aspnet/core/host-and-deploy/aspnet-core-module) 的版本13.0.19218.0，可為 ASP.NET Core 3.0 和2.2 應用程式提供現有的 HTTPS 重新導向功能。

如需討論，請參閱 [dotnet/AspNetCore # 15243](https://github.com/dotnet/AspNetCore/issues/15243)。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

ASP.NET Core 2.1 專案範本首次推出 HTTPS 中介軟體方法的支援 <xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection%2A> ，例如和 <xref:Microsoft.AspNetCore.Builder.HstsBuilderExtensions.UseHsts%2A> 。 啟用 HTTPS 重新導向需要新增設定，因為開發中的應用程式不會使用預設通訊埠443。 只有當要求已在使用 HTTPS 時， [HTTP Strict Transport Security (HSTS) ](https://cheatsheetseries.owasp.org/cheatsheets/HTTP_Strict_Transport_Security_Cheat_Sheet.html)才會生效。 預設會略過 Localhost。

#### <a name="new-behavior"></a>新的行為

在 ASP.NET Core 3.0 中，已 [增強](https://github.com/dotnet/AspNetCore/pull/4685)IIS HTTPS 案例。 有了增強功能，應用程式就可以探索伺服器的 HTTPS 埠，並 `UseHttpsRedirection` 預設進行工作。 內含式元件已完成使用此功能的埠探索 `IServerAddresses` ，因為同進程程式庫是以 framework 建立版本，所以只會影響 ASP.NET Core 3.0 應用程式。 跨進程元件已變更為自動新增 `ASPNETCORE_HTTPS_PORT` 環境變數。 這項變更會影響 ASP.NET Core 2.2 和3.0 應用程式，因為跨進程元件是全域共用的。 ASP.NET Core 2.1 應用程式不會受到影響，因為它們預設使用舊版的 ANCM。

先前的行為已在 ASP.NET Core 3.0.1 和 3.1.0 Preview 3 中修改，以反轉 ASP.NET Core 2.x 中的行為變更。 這些變更只會影響 IIS 跨進程應用程式。

如上所述，安裝 ASP.NET Core 3.0.0 的副作用也會讓您 `UseHttpsRedirection` 在 ASP.NET Core 2.x 應用程式中啟用中介軟體。 ANCM 在 ASP.NET Core 3.0.1 和 3.1.0 Preview 3 中進行了變更，因此安裝這些專案不再對 ASP.NET Core 2.x 應用程式造成影響。 在 `ASPNETCORE_HTTPS_PORT` `ASPNETCORE_ANCM_HTTPS_PORT` ASP.NET Core 3.0.1 和 3.1.0 Preview 3 中，ANCM 填入 ASP.NET Core 3.0.0 的環境變數已變更為。 `UseHttpsRedirection` 也已在這些版本中更新，以瞭解新的和舊的變數。 ASP.NET Core 2.x 將不會更新。 因此，它會還原為先前預設停用的行為。

#### <a name="reason-for-change"></a>變更的原因

改進了 ASP.NET Core 3.0 功能。

#### <a name="recommended-action"></a>建議的動作

如果您想要讓所有用戶端使用 HTTPS，則不需要採取任何動作。 若要允許某些用戶端使用 HTTP，請執行下列其中一個步驟：

* `UseHttpsRedirection`從您的專案方法中移除對和的呼叫 `UseHsts` `Startup.Configure` ，然後重新部署應用程式。
* 在您的 *web.config* 檔案中，將 `ASPNETCORE_HTTPS_PORT` 環境變數設為空字串。 這種變更可以直接在伺服器上發生，而不需要重新部署應用程式。 例如：

    ```xml
    <aspNetCore processPath="dotnet" arguments=".\WebApplication3.dll" stdoutLogEnabled="false" stdoutLogFile="\\?\%home%\LogFiles\stdout" >
        <environmentVariables>
        <environmentVariable name="ASPNETCORE_HTTPS_PORT" value="" />
        </environmentVariables>
    </aspNetCore>
    ```

`UseHttpsRedirection` 仍然可以是：

* 在 ASP.NET Core 2.x 中手動啟動，方法是 `ASPNETCORE_HTTPS_PORT` 在大多數生產案例) 中將環境變數設為適當的埠號碼 (443。
* 以空字串值定義，在 ASP.NET Core 3.x 中停用 `ASPNETCORE_ANCM_HTTPS_PORT` 。 此值的設定方式與上述 `ASPNETCORE_HTTPS_PORT` 範例相同。

執行 ASP.NET Core 3.0.0 apps 的電腦應先安裝 ASP.NET Core 3.0.1 執行時間，再安裝 ASP.NET Core 3.1.0 Preview 3 ANCM。 這麼做可確保 `UseHttpsRedirection` ASP.NET Core 3.0 應用程式繼續如預期般運作。

在 Azure App Service 中，ANCM 會根據其全域性質，從執行時間部署個別的排程。 ANCM 已部署至 Azure，並在部署 ASP.NET Core 3.0.1 和3.1.0 之後進行這些變更。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

<xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection(Microsoft.AspNetCore.Builder.IApplicationBuilder)?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`M:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection(Microsoft.AspNetCore.Builder.IApplicationBuilder)`

-->
