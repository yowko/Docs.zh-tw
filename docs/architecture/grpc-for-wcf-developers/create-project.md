---
title: 為 WCF 開發人員建立新的 ASP.NET Core gRPC 專案 gRPC
description: 瞭解如何使用 Visual Studio 或從命令列建立 gRPC 專案。
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: a0fcc3f9c4e32e87260a6bc79205c909ea3800e0
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184565"
---
# <a name="create-a-new-aspnet-core-grpc-project"></a>建立新的 ASP.NET Core gRPC 專案

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

.Net Core 隨附功能強大的 CLI 工具， `dotnet`可讓您從命令列建立和管理專案和解決方案。 此工具與 Visual Studio 緊密整合，因此您也可以透過熟悉的 GUI 介面取得所有專案。 本章將示範兩種建立新 ASP.NET Core gRPC 專案的方式：先使用 Visual Studio，然後再加上 .NET Core CLI。

## <a name="create-the-project-using-visual-studio"></a>使用 Visual Studio 建立專案

> [!IMPORTANT]
> 若要開發任何 ASP.NET Core 3.0 應用程式，您需要已安裝**ASP.NET 和 網頁程式開發**工作負載的 Visual Studio 2019.3 或更新版本。

從*空白解決方案*範本建立名為**TraderSys**的空白解決方案。 新增名`src`為的方案資料夾，然後以滑鼠右鍵按一下該資料夾，然後從內容功能表選擇 [**加入** > **新專案**]。 在`grpc` [範本搜尋] 方塊中輸入，您應該會看到名`gRPC Service`為的專案範本。

![顯示 gRPC 服務專案範本的 [新增專案] 對話方塊](media/create-project/new-grpc-project.png)

按 **[下一步**] 以繼續前往 [**設定專案**] `TraderSys.Portfolios`對話方塊並為專案`src`命名，並將子目錄新增至該**位置**。

![[設定專案] 對話方塊](media/create-project/configure-project.png)

按 **[下一步**] 以繼續前往 [**新增 gRPC 專案**] 對話方塊。

![[新增 gRPC 專案] 對話方塊](media/create-project/create-new-grpc-service.png)

目前，服務建立有一些有限的選項。 Docker 稍後會在本書中引進，因此請不要勾選該核取方塊，只要按一下 [**建立**] 即可。 系統會產生您的第一個 ASP.NET Core 3.0 gRPC 專案，並將其新增至方案。 如果您不想要知道`dotnet CLI`如何使用，請跳至[清除範例程式碼](#clean-up-the-example-code)一節。

## <a name="create-the-project-using-the-net-core-cli"></a>使用 .NET Core CLI 建立專案

本節說明如何從命令列建立解決方案和專案。

建立解決方案，如下所示。 `-o` （或`--output`）旗標會指定輸出目錄，如果它不存在，則會在目前的目錄中建立。 方案的名稱會與目錄相同，例如`TraderSys.sln`。您可以使用`-n` （或`--name`）旗標來提供不同的名稱。

```dotnetcli
dotnet new sln -o TraderSys
cd TraderSys
```

ASP.NET Core 3.0 隨附 gRPC services 的 CLI 範本。 使用此範本建立新的專案，並將其放`src`入子目錄中，如同 ASP.NET Core 專案的慣例。 除非您`TraderSys.Portfolios.csproj` `-n`使用旗標指定不同的名稱，否則專案會以目錄（亦即）命名。

```dotnetcli
dotnet new grpc -o src/TraderSys.Portfolios
```

最後，使用`dotnet sln`命令將專案新增至方案。

```dotnetcli
dotnet sln add src/TraderSys.Portfolios
```

> [!TIP]
> 由於指定的目錄只包含單一`.csproj`檔案，因此您可以只指定目錄來儲存輸入。

您現在可以在 Visual Studio 2019、Visual Studio Code 或任何您偏好的編輯器中開啟此方案。

## <a name="clean-up-the-example-code"></a>清除範例程式碼

您現在已使用 gRPC 範本建立了範例服務，先前已在本書中進行檢查。 這在我們的股票交易內容中並不實用，因此我們將編輯第一個專案的事項。

### <a name="rename-and-edit-the-proto-file"></a>重新命名和編輯 proto 檔案

繼續進行，並將`Protos/greet.proto`檔案重新`Protos/portfolios.proto`命名為，並在編輯器中開啟它。 刪除`package`行之後的所有專案，然後`option csharp_namespace`變更、 `package`和`service`名稱，並移除預設`SayHello`服務，讓程式碼看起來像這樣。

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys.Portfolios.Protos";

package PortfolioServer;

service Portfolios {
  // RPCs will go here
}
```

> [!TIP]
> 範本預設不會新增`Protos`命名空間部分，但新增它可讓您更輕鬆地將 gRPC 產生的類別和您自己的類別明確分隔在程式碼中。

如果您在 Visual Studio `greet.proto`之類的整合式開發環境（IDE）中重新命名檔案，檔案中會自動更新`.csproj`此檔案的參考。 但是在某些其他編輯器（例如 Visual Studio Code）中，此參考不會自動更新，因此您必須手動編輯專案檔。

在 gRPC 組建目標中，有一個`Protobuf` item 專案，可讓您指定應該編譯的`.proto`檔案，以及需要產生哪一種程式碼（也就是「伺服器」或「用戶端」）。

```xml
<ItemGroup>
  <Protobuf Include="Protos\portfolios.proto" GrpcServices="Server" />
</ItemGroup>
```

### <a name="rename-the-greeterservice-class"></a>重新命名 GreeterService 類別

類別位於`Services`資料夾中，並繼承自`Greeter.GreeterBase`。 `GreeterService` 將它重新`PortfolioService`命名為，並將基類`Portfolios.PortfoliosBase`變更為。 `override`刪除方法。

```csharp
public class PortfolioService : Portfolios.PortfoliosBase
{
}
```

在`GreeterService` 類別`Startup`的`Configure`方法中，有類別的參考。 如果您使用重構來重新命名類別，此參考應該已自動更新。 不過，如果您沒有這麼做，則需要手動編輯它。

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
