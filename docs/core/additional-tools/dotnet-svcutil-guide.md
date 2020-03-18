---
title: WCF svcutil 工具概觀
description: Microsoft WCF dotnet-svcutil 工具的概觀，此工具可新增 .NET Core 和 ASP.NET Core 專案功能，與 .NET Framework 專案的 WCF svcutil 工具類似。
author: mlacouture
ms.date: 02/22/2019
ms.openlocfilehash: 0607c73935f319f2cc0d8d9f92d96a4c71c54edf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "76920941"
---
# <a name="wcf-dotnet-svcutil-tool-for-net-core"></a>適用於 .NET Core 的 WCF dotnet-svcutil 工具

Windows 通信基礎 （WCF） **dotnet-svcutil**工具是一個 .NET 工具，用於從網路位置或 WSDL 檔案中的 Web 服務檢索中繼資料，並生成包含訪問 Web 服務操作的用戶端代理方法的 WCF 類。

類似適用於 .NET Framework 專案的 [**Service Model Metadata - svcutil**](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) 工具，**dotnet-svcutil** 是一種命令列工具，可用來產生與 .NET Core 和 .NET Standard 專案相容的 Web 服務參考。

**dotnet-svcutil**工具是[**WCF Web 服務參考**](wcf-web-service-reference-guide.md)視覺化工作室連接服務提供者的替代方案，該服務提供者首次附帶了 Visual Studio 2017 版本 15.5。 作為 .NET 工具**的 dotnet-svcutil**工具在 Linux、macOS 和 Windows 上提供跨平臺版本。

> [!IMPORTANT]
> 您只應該參考來自信任來源的服務。 新增不信任來源的參考可能會危及安全性。

## <a name="prerequisites"></a>必要條件

<!-- markdownlint-disable MD025 -->

# <a name="dotnet-svcutil-2x"></a>[dotnet-svcutil 2.x](#tab/dotnetsvcutil2x)

- [.NET 核心 2.1 SDK](https://dotnet.microsoft.com/download)或更高版本
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

2. 使用以下命令在該目錄中創建新的[`dotnet new`](../tools/dotnet-new.md)C# Web 專案：

    ```dotnetcli
    dotnet new web
    ```

3. 將[`dotnet-svcutil`NuGet 包](https://nuget.org/packages/dotnet-svcutil)安裝為 CLI 工具： <!-- markdownlint-disable MD023 -->
    # <a name="dotnet-svcutil-2x"></a>[dotnet-svcutil 2.x](#tab/dotnetsvcutil2x)

    ```dotnetcli
    dotnet tool install --global dotnet-svcutil
    ```

    # <a name="dotnet-svcutil-1x"></a>[dotnet-svcutil 1.x](#tab/dotnetsvcutil1x)
    使用以下`HelloSvcutil.csproj`代碼在編輯器中打開專案檔案，`Project`編輯元素，並將[`dotnet-svcutil`NuGet 包](https://nuget.org/packages/dotnet-svcutil)添加為 CLI 工具參考：

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

產生的檔案會儲存為 _HelloSvcutil/ServiceReference/Reference.cs_。 _dotnet-svcutil_工具還會向專案添加代理代碼作為包引用所需的適當 WCF 包。

## <a name="using-the-service-reference"></a>使用服務參考

1. 使用命令還原 WCF[`dotnet restore`](../tools/dotnet-restore.md)包，如下所示：

    ```dotnetcli
    dotnet restore
    ```

2. 尋找您要使用的用戶端類別與作業名稱。 `Reference.cs` 會包含繼承自 `System.ServiceModel.ClientBase`的類別，並有可用來在服務上呼叫作業的方法。 在此例中，您想要呼叫 _SayHello_ 服務的 _Hello_ 作業。 `ServiceReference.SayHelloClient` 是用戶端類別的名稱，並有稱為 `HelloAsync` 的方法，可用來呼叫作業。

3. 在編輯器中開啟 `Startup.cs` 檔案，在頂端為服務參考命名空間新增 using 陳述式：

    ```csharp
    using ServiceReference;
    ```

4. 編輯 `Configure` 方法以叫用 Web 服務。 若要這樣做，請建立繼承自 `ClientBase` 的類別執行個體，然後在用戶端物件呼叫方法：

    ```csharp
    public void Configure(IApplicationBuilder app, IHostingEnvironment env)
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

5. 使用命令運行應用程式，[`dotnet run`](../tools/dotnet-run.md)如下所示：

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
