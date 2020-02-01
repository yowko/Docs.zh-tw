---
title: 為 WCF 開發人員建立新的 ASP.NET Core gRPC 專案 gRPC
description: 瞭解如何使用 Visual Studio 或命令列來建立 gRPC 專案。
ms.date: 09/02/2019
ms.openlocfilehash: fbcc598cf503a5baeca941803ff8fa0d5fc99671
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2020
ms.locfileid: "76919404"
---
# <a name="create-a-new-aspnet-core-grpc-project"></a>建立新的 ASP.NET Core gRPC 專案

.NET Core SDK 隨附功能強大的 CLI 工具，`dotnet`，可讓您從命令列建立和管理專案和解決方案。 SDK 與 Visual Studio 緊密整合，因此您也可以透過熟悉的圖形化使用者介面取得所有專案。 本章說明建立新 ASP.NET Core gRPC 專案的兩種方式。

## <a name="create-the-project-by-using-visual-studio"></a>使用 Visual Studio 建立專案

> [!IMPORTANT]
> 若要開發任何 ASP.NET Core 3.0 應用程式，您需要已安裝**ASP.NET 和 網頁程式開發**工作負載的 Visual Studio 2019 16.3 或更新版本。

從*空白解決方案*範本建立名為**TraderSys**的空白解決方案。 新增名為 `src`的方案資料夾。 然後，在資料夾上按一下滑鼠右鍵，然後選擇 [**加入**] > [**新增專案**]。 在 [範本搜尋] 方塊中輸入 `grpc`，您應該會看到名為 `gRPC Service`的專案範本。

![[新增專案] 對話方塊的螢幕擷取畫面](media/create-project/new-grpc-project.png)

選取 **[下一步**] 以繼續前往 [**設定您的新專案**] 對話方塊。 將專案命名為 `TraderSys.Portfolios` 並將 `src` 子目錄新增至該**位置**。

![[設定您的新專案] 對話方塊的螢幕擷取畫面](media/create-project/configure-project.png)

選取 **[下一步**] 以繼續前往 [**建立新的 gRPC 服務**] 對話方塊。

![[建立新的 gRPC 服務] 對話方塊的螢幕擷取畫面](media/create-project/create-new-grpc-service.png)

目前，您的服務建立選項有限。 Docker 將會在稍後引進，因此現在請不要選取這個選項。 只需選取 [**建立**]。 系統會產生您的第一個 ASP.NET Core 3.0 gRPC 專案，並將其新增至方案。 如果您不想知道如何使用 `dotnet CLI`，請跳至[清除範例程式碼](#clean-up-the-example-code)一節。

## <a name="create-the-project-by-using-the-net-core-cli"></a>使用 .NET Core CLI 建立專案

本節說明如何從命令列建立解決方案和專案。

建立解決方案，如下列命令所示。 `-o` （或 `--output`）旗標會指定在目前目錄中建立的輸出目錄（如果尚未存在的話）。 此方案的名稱與目錄相同： `TraderSys.sln`。 您可以使用 `-n` （或 `--name`）旗標來提供不同的名稱。

```dotnetcli
dotnet new sln -o TraderSys
cd TraderSys
```

ASP.NET Core 3.0 隨附 gRPC services 的 CLI 範本。 使用此範本建立新的專案，並將其放入 `src` 子目錄中，如同傳統的 ASP.NET Core 專案。 除非您使用 `-n` 旗標指定不同的名稱，否則專案會以目錄（`TraderSys.Portfolios.csproj`）命名。

```dotnetcli
dotnet new grpc -o src/TraderSys.Portfolios
```

最後，使用 `dotnet sln` 命令，將專案新增至方案：

```dotnetcli
dotnet sln add src/TraderSys.Portfolios
```

> [!TIP]
> 因為特定目錄只包含單一 `.csproj` 檔案，所以您可以只指定目錄，以儲存輸入。

您現在可以在 Visual Studio 2019、Visual Studio Code 或任何您偏好的編輯器中開啟此方案。

## <a name="clean-up-the-example-code"></a>清除範例程式碼

您現在已使用 gRPC 範本建立了範例服務，先前已在本書中進行檢查。 這在我們的股票交易內容中並不實用，因此我們將編輯第一個專案的事項。

### <a name="rename-and-edit-the-proto-file"></a>重新命名和編輯 proto 檔案

繼續進行，並將 `Protos/greet.proto` 檔案重新命名為 `Protos/portfolios.proto`，然後在您的編輯器中開啟它。 刪除 `package` 行之後的所有內容。 然後，變更 `option csharp_namespace`、`package` 和 `service` 名稱，並移除預設的 `SayHello` 服務。 程式碼現在看起來如下所示：

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys.Portfolios.Protos";

package PortfolioServer;

service Portfolios {
  // RPCs will go here
}
```

> [!TIP]
> 範本預設不會新增 `Protos` 的命名空間部分，但新增它可讓您更輕鬆地將 gRPC 產生的類別和您自己的類別明確分隔在程式碼中。

如果您在類似 Visual Studio 的整合式開發環境（IDE）中重新命名 `greet.proto` 檔案，則會在 `.csproj` 檔案中自動更新此檔案的參考。 但是在某些其他編輯器（例如 Visual Studio Code）中，此參考不會自動更新，因此您必須手動編輯專案檔。

在 gRPC 組建目標中，有一個 `Protobuf` 專案元素，可讓您指定應該編譯的 `.proto` 檔，以及需要產生的程式碼形式（也就是「伺服器」或「用戶端」）。

```xml
<ItemGroup>
  <Protobuf Include="Protos\portfolios.proto" GrpcServices="Server" />
</ItemGroup>
```

### <a name="rename-the-greeterservice-class"></a>重新命名 `GreeterService` 類別

`GreeterService` 類別位於 `Services` 資料夾中，並繼承自 `Greeter.GreeterBase`。 將它重新命名為 `PortfolioService`，然後將基類變更為 `Portfolios.PortfoliosBase`。 刪除 `override` 方法。

```csharp
public class PortfolioService : Portfolios.PortfoliosBase
{
}
```

在 `Startup` 類別的 `Configure` 方法中，有 `GreeterService` 類別的參考。 如果您使用重構來重新命名類別，此參考應該已自動更新。 不過，如果您沒有這麼做，則需要手動編輯它。

```csharp
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    if (env.IsDevelopment())
    {
        app.UseDeveloperExceptionPage();
    }

    app.UseRouting();

    app.UseEndpoints(endpoints =>
    {
        endpoints.MapGrpcService<PortfolioService>();
    });
}
```

在下一節中，我們會新增新服務的功能。

>[!div class="step-by-step"]
>[上一頁](migrate-wcf-to-grpc.md)
>[下一頁](migrate-request-reply.md)
