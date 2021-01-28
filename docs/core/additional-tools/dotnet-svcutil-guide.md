---
title: WCF svcutil 工具概觀
description: Microsoft WCF dotnet-svcutil 工具的概觀，此工具可新增 .NET Core 和 ASP.NET Core 專案功能，與 .NET Framework 專案的 WCF svcutil 工具類似。
author: honggit
ms.date: 02/22/2019
ms.openlocfilehash: 9468a881fe3850b53d48945340127ac2c2d4c6c8
ms.sourcegitcommit: 7e42488c2f8f63f6d499b5f8fb1dec5bac9ad254
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2021
ms.locfileid: "98957919"
---
# <a name="wcf-dotnet-svcutil-tool-for-net-core"></a>適用於 .NET Core 的 WCF dotnet-svcutil 工具

Windows Communication Foundation (WCF) **dotnet-svcutil** tool 是一種 .net 工具，可從網路位置或 WSDL 檔案中的 web 服務取得中繼資料，並產生包含可存取 web 服務作業之用戶端 proxy 方法的 WCF 類別。

類似適用於 .NET Framework 專案的 [**Service Model Metadata - svcutil**](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) 工具，**dotnet-svcutil** 是一種命令列工具，可用來產生與 .NET Core 和 .NET Standard 專案相容的 Web 服務參考。

**Dotnet-svcutil** 工具是 [**WCF Web Service Reference**](wcf-web-service-reference-guide.md) Visual Studio 連線服務提供者的替代選項，第一次隨附于 Visual Studio 2017 15.5 版。 **Dotnet svcutil** tool 即為 .net 工具，可跨平臺在 Linux、MacOS 和 Windows 上使用。

> [!IMPORTANT]
> 您只應該參考來自信任來源的服務。 新增不信任來源的參考可能會危及安全性。

## <a name="prerequisites"></a>必要條件

<!-- markdownlint-disable MD025 -->

# <a name="dotnet-svcutil-2x"></a>[dotnet-svcutil 2.x](#tab/dotnetsvcutil2x)

- [.Net Core 2.1 SDK](https://dotnet.microsoft.com/download) 或更新版本
- 您慣用的程式碼編輯器

# <a name="dotnet-svcutil-1x"></a>[dotnet-svcutil 1.x](#tab/dotnetsvcutil1x)

- [.NET Core 1.0.4 SDK](https://dotnet.microsoft.com/download) 或更新版本
- 您慣用的程式碼編輯器

---

## <a name="getting-started"></a>開始使用

下列範例會引導您完成將 Web 服務參考新增到 .NET Core Web 專案並叫用服務的必要步驟。 您建立名為 *HelloSvcutil* 的 .NET Core Web 應用程式，並對實作下列合約的 Web 服務新增參考：

```csharp
[ServiceContract]
public interface ISayHello
{
    [OperationContract]
    string Hello(string name);
}
```

對於此範例，我們假設 Web 服務裝載於下列位址：`http://contoso.com/SayHello.svc`

從 Windows、macOS 或 Linux 命令視窗執行下列步驟：

1. 為您的專案建立一個名為 _HelloSvcutil_ 的目錄，然後讓它成為您目前所在的目錄，如下列範例中所示：

    ```console
    mkdir HelloSvcutil
    cd HelloSvcutil
    ```

2. 使用命令在該目錄中建立新的 c # Web 專案，如下所示 [`dotnet new`](../tools/dotnet-new.md) ：

    ```dotnetcli
    dotnet new web
    ```

3. 以 CLI 工具的形式安裝[ `dotnet-svcutil` NuGet 套件](https://nuget.org/packages/dotnet-svcutil)： <!-- markdownlint-disable MD023 -->
    # <a name="dotnet-svcutil-2x"></a>[dotnet-svcutil 2.x](#tab/dotnetsvcutil2x)

    ```dotnetcli
    dotnet tool install --global dotnet-svcutil
    ```

    # <a name="dotnet-svcutil-1x"></a>[dotnet-svcutil 1.x](#tab/dotnetsvcutil1x)

    `HelloSvcutil.csproj`在編輯器中開啟專案檔、編輯 `Project` 元素，然後使用下列程式碼，將[ `dotnet-svcutil` NUGET 套件](https://nuget.org/packages/dotnet-svcutil)新增為 CLI 工具參考：

    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil" Version="1.0.*" />
    </ItemGroup>
    ```

    接著使用 [`dotnet restore`](../tools/dotnet-restore.md) 命令還原 _dotnet-svcutil_ 套件，如下所示：

    ```dotnetcli
    dotnet restore
    ```

    ---

4. 執行 _dotnet-svcutil_ 命令以產生 Web 服務參考檔案，如下所示：

    # <a name="dotnet-svcutil-2x"></a>[dotnet-svcutil 2.x](#tab/dotnetsvcutil2x)

    ```dotnetcli
    dotnet-svcutil http://contoso.com/SayHello.svc
    ```

    # <a name="dotnet-svcutil-1x"></a>[dotnet-svcutil 1.x](#tab/dotnetsvcutil1x)

    ```dotnetcli
    dotnet svcutil http://contoso.com/SayHello.svc
    ```

    ---

產生的檔案會儲存為 _HelloSvcutil/ServiceReference/Reference.cs_。 _Dotnet svcutil_ 工具也會將 proxy 程式碼所需的適當 WCF 封裝作為封裝參考新增至專案。

## <a name="using-the-service-reference"></a>使用服務參考

1. 使用命令來還原 WCF 封裝 [`dotnet restore`](../tools/dotnet-restore.md) ，如下所示：

    ```dotnetcli
    dotnet restore
    ```

2. 尋找您要使用的用戶端類別與作業名稱。 `Reference.cs` 會包含繼承自 `System.ServiceModel.ClientBase`的類別，並有可用來在服務上呼叫作業的方法。 在此例中，您想要呼叫 _SayHello_ 服務的 _Hello_ 作業。 `ServiceReference.SayHelloClient` 是用戶端類別的名稱，並有稱為 `HelloAsync` 的方法，可用來呼叫作業。

3. `Startup.cs`在編輯器中開啟檔案，並在 `using` 頂端為服務參考命名空間加入指示詞：

    ```csharp
    using ServiceReference;
    ```

4. 編輯 `Configure` 方法以叫用 Web 服務。 若要這樣做，請建立繼承自 `ClientBase` 的類別執行個體，然後在用戶端物件呼叫方法：

    ```csharp
    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        if (env.IsDevelopment())
        {
            app.UseDeveloperExceptionPage();
        }

        app.Run(async (context) =>
        {
            var client = new SayHelloClient();
            var response = await client.HelloAsync();
            await context.Response.WriteAsync(response);
        });
    }

    ```

5. 使用命令執行應用程式，如下所示 [`dotnet run`](../tools/dotnet-run.md) ：

    ```dotnetcli
    dotnet run
    ```

6. 在您的網頁瀏覽器中，瀏覽到主控台列出的 URL (例如 `http://localhost:5000`)。

您應該會看見下列輸出："Hello dotnet-svcutil!"

如需 `dotnet-svcutil` 工具參數的詳細說明，請依下列所示叫用工具並傳遞 help 參數：

# <a name="dotnet-svcutil-2x"></a>[dotnet-svcutil 2.x](#tab/dotnetsvcutil2x)

```dotnetcli
dotnet-svcutil --help
```

# <a name="dotnet-svcutil-1x"></a>[dotnet-svcutil 1.x](#tab/dotnetsvcutil1x)

```dotnetcli
dotnet svcutil --help
```

---

## <a name="feedback--questions"></a>意見反應和問題

如果您有任何問題或意見反應，請[在 GitHub 上開啟問題](https://github.com/dotnet/wcf/issues/new)。 您也可以[在 GitHub 的 WCF 存放庫](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling)檢閱任何現有問題或議題。

## <a name="release-notes"></a>版本資訊

- 如需已更新的版本資訊，請參閱[版本資訊](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md) (包含已知問題)。

## <a name="information"></a>資訊

- [dotnet-svcutil NuGet 套件](https://nuget.org/packages/dotnet-svcutil) \(英文\)
