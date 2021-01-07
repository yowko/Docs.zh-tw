---
title: 建立新的 ASP.NET Core gRPC 專案-gRPC （適用于 WCF 開發人員）
description: 瞭解如何使用 Visual Studio 或命令列來建立 gRPC 專案。
ms.date: 01/06/2021
ms.openlocfilehash: c9d66a773f0633c2ae93c42ce3ce53084032cd17
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970254"
---
# <a name="create-a-new-aspnet-core-grpc-project"></a>建立新的 ASP.NET Core gRPC 專案

.NET SDK 隨附強大的 CLI 工具，可 `dotnet` 讓您從命令列建立和管理專案和解決方案。 SDK 與 Visual Studio 緊密整合，因此您也可以透過熟悉的圖形化使用者介面來取得所有專案。 本章將說明建立新的 ASP.NET Core gRPC 專案的兩種方式。

## <a name="create-the-project-by-using-visual-studio"></a>使用 Visual Studio 建立專案

> [!IMPORTANT]
> 若要開發任何 ASP.NET Core 5.0 應用程式，您需要已安裝 **ASP.NET 和 網頁程式開發** 工作負載的 Visual Studio 2019 16.8 版或更新版本。

從 *空白解決方案* 範本建立稱為 **TraderSys** 的空白解決方案。 加入名為的方案資料夾 `src` 。 然後，在資料夾上按一下滑鼠右鍵，然後選擇 [**加入**  >  **新專案**]。 `grpc`在範本搜尋方塊中輸入，您應該會看到名為的專案範本 `gRPC Service` 。

![[加入新專案] 對話方塊的螢幕擷取畫面](media/create-project/new-grpc-project.png)

選取 **[下一步** ] 以繼續前往 [ **設定您的新專案** ] 對話方塊。 為專案命名 `TraderSys.Portfolios` ，並將 `src` 子目錄新增至該 **位置**。

![[設定您的新專案] 對話方塊的螢幕擷取畫面](media/create-project/configure-project.png)

選取 **[下一步** ] 繼續前往 [ **建立新的 gRPC 服務** ] 對話方塊。

![[建立新的 gRPC 服務] 對話方塊的螢幕擷取畫面](media/create-project/create-new-grpc-service-v2.png)

目前，您有限制的服務建立選項。 Docker 將于稍後推出，因此現在請將該選項保留為未選取狀態。 只需選取 [ **建立**]。 系統會產生您的第一個 ASP.NET Core 5.0 gRPC 專案，並將其新增至方案。 如果您不想要知道如何使用 `dotnet CLI` ，請跳至 [清除範例程式碼](#clean-up-the-example-code) 一節。

## <a name="create-the-project-by-using-the-net-cli"></a>使用 .NET CLI 建立專案

本節將說明如何從命令列建立方案和專案。

建立解決方案，如下列命令所示。 `-o` (或 `--output`) 旗標會指定在目前的目錄中建立的輸出目錄（如果尚未存在）。 方案與目錄具有相同的名稱： `TraderSys.sln` 。 您可以使用 `-n` (或) 旗標來提供不同的名稱 `--name` 。

```dotnetcli
dotnet new sln -o TraderSys
cd TraderSys
```

ASP.NET Core 5.0 隨附 gRPC services 的 CLI 範本。 使用此範本建立新的專案，並將其放入 `src` 子目錄中，作為 ASP.NET Core 專案的傳統方式。 `TraderSys.Portfolios.csproj`除非您使用旗標指定不同的名稱，否則專案會以目錄 () 來命名 `-n` 。

```dotnetcli
dotnet new grpc -o src/TraderSys.Portfolios
```

最後，使用下列命令將專案新增至方案 `dotnet sln` ：

```dotnetcli
dotnet sln add src/TraderSys.Portfolios
```

> [!TIP]
> 因為特定目錄只包含單一檔案 `.csproj` ，所以您可以只指定目錄來儲存鍵入。

您現在可以在 Visual Studio 2019、Visual Studio Code 或任何偏好的編輯器中開啟此方案。

## <a name="clean-up-the-example-code"></a>清除範例程式碼

您現在已使用 gRPC 範本建立了範例服務，此範本已在本書稍早審核。 這段程式碼在股票交易內容中並不實用，因此我們將編輯第一個專案的內容。

### <a name="rename-and-edit-the-proto-file"></a>重新命名和編輯 proto 檔案

繼續並將檔案重新命名 `Protos/greet.proto` 為 `Protos/portfolios.proto` ，並在編輯器中開啟檔案。 刪除該行之後的所有專案 `package` 。 然後變更 `option csharp_namespace` 、 `package` 和 `service` 名稱，然後移除預設 `SayHello` 服務。 程式碼現在看起來如下所示：

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys.Portfolios.Protos";

package PortfolioServer;

service Portfolios {
  // RPCs will go here
}
```

> [!TIP]
> 範本預設不會新增 `Protos` 命名空間元件，但新增它可讓您更輕鬆地將 gRPC 產生的類別和您自己的類別明確地分隔在程式碼中。

如果您 `greet.proto` 在整合式開發環境中重新命名檔案 (IDE) 例如 Visual Studio，則會自動更新檔案中的這個檔案參考 `.csproj` 。 但是在某些其他編輯器中（例如 Visual Studio Code），此參考不會自動更新，因此您需要手動編輯專案檔。

在 gRPC 組建目標中，有一個 `Protobuf` 專案專案可讓您指定 `.proto` 應該編譯哪些檔案，以及需要何種形式的程式碼產生 (也就是「伺服器」或「用戶端」 ) 。

```xml
<ItemGroup>
  <Protobuf Include="Protos\portfolios.proto" GrpcServices="Server" />
</ItemGroup>
```

### <a name="rename-the-greeterservice-class"></a>重新命名 `GreeterService` 類別

`GreeterService`類別位於 `Services` 資料夾中，並繼承自 `Greeter.GreeterBase` 。 將它重新命名為 `PortfolioService` ，並將基類變更為 `Portfolios.PortfoliosBase` 。 刪除 `override` 方法。

```csharp
public class PortfolioService : Portfolios.PortfoliosBase
{
}
```

在類別的方法中，有類別的參考 `GreeterService` `Configure` `Startup` 。 如果您使用重構來重新命名類別，則應該會自動更新此參考。 但是，如果您沒有這麼做，您需要手動進行編輯。

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

在下一節中，我們會將功能新增至這個新的服務。

>[!div class="step-by-step"]
>[上一個](migrate-wcf-to-grpc.md) 
>[下一步](migrate-request-reply.md)
