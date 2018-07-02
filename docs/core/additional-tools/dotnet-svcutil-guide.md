---
title: Microsoft WCF dotnet-svcutil 工具
description: Microsoft WCF dotnet-svcutil 工具的概觀，此工具可新增 .NET Core 和 ASP.NET Core 專案功能，與 .NET Framework 專案的 WCF svcutil 工具類似。
author: mlacouture
ms.author: jralexander
ms.date: 06/04/2018
ms.openlocfilehash: c40dd9b437afe7381244b944228b6b2efe046eb2
ms.sourcegitcommit: d8bf4976eafe3289275be3811e7cb721bfff7e1e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34753418"
---
# <a name="microsoft-wcf-dotnet-svcutil-tool"></a>Microsoft WCF dotnet-svcutil 工具

Windows Communication Foundation (WCF) **dotnet-svcutil** 工具是一種 .NET Core CLI 工具，可從網路位置上的 Web 服務或從 WSDL 檔案擷取中繼資料，並產生包含可用來存取 Web 服務作業的用戶端 Proxy 方法的 WCF 類別。

類似適用於 .NET Framework 專案的 [**Service Model Metadata - svcutil**](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) 工具，**dotnet-svcutil** 是一種命令列工具，可用來產生與 .NET Core 和 .NET Standard 專案相容的 Web 服務參考。

**dotnet-svcutil** 工具是於 Visual Studio 2017 15.5 版首次推出之 [**WCF Web Service Reference**](wcf-web-service-reference-guide.md) Visual Studio 連線服務提供者的替代選項。 **dotnet-svcutil** 工具可當作 .NET Core CLI 工具，在 Linux、macOS 和 Windows 上跨平台使用。

> [!IMPORTANT]
> 您只應該參考來自信任來源的服務。 新增不信任來源的參考可能會危及安全性。

## <a name="prerequisites"></a>必要條件

* [.NET Core SDK](https://www.microsoft.com/net/download) \(英文\) 1.0.4 版或更新版本
* 您慣用的程式碼編輯器

## <a name="getting-started"></a>使用者入門

下列範例會引導您完成將 Web 服務參考新增到 .NET Core 主控台專案並叫用服務的必要步驟。 您將會建立名為 _HelloSvcutil_ 的 .NET Core 主控台應用程式，並將新增實作下列合約之 Web 服務的參考：

```csharp
[ServiceContract]
public interface ISayHello
{
    [OperationContract]
    string Hello(string name);
}
```

針對此範例，我們將假設 Web 服務裝載於下列位址：`http://contoso.com/SayHello.svc`

從 Windows、macOS 或 Linux 命令視窗執行下列步驟：

1. 為您的專案建立一個名為 _HelloSvcutil_ 的目錄，然後讓它成為您目前所在的目錄，如下列範例中所示：

```console
mkdir HelloSvcutil
cd HelloSvcutil
```

2. 使用 [`dotnet new`](../tools/dotnet-new.md) 命令在該目錄中建立新的 C# 主控台專案，如下所示：

```console
dotnet new console
```

3. 在您的編輯器中開啟 `HelloSvcutil.csproj` 專案檔，編輯 `Project` 元素，然後使用下列程式碼將 [`dotnet-svcutil`NuGet 套件](https://nuget.org/packages/dotnet-svcutil) \(英文\) 新增為 CLI 工具參考：

```xml
<ItemGroup>
  <DotNetCliToolReference Include="dotnet-svcutil" Version="1.0.0" />
</ItemGroup>
```

4. 使用 [`dotnet restore`](../tools/dotnet-restore.md) 命令還原 _dotnet-svcutil_ 套件，如下所示：

```console
dotnet restore
```

5. 搭配 _svcutil_ 命令執行 _dotnet_ 以產生 Web 服務參考檔案，如下所示：

```console
dotnet svcutil http://contoso.com/SayHello.svc
```
產生的檔案會儲存為 _HelloSvcutil/ServiceReference1/Reference.cs_。 _dotnet_svcutil_ 工具也會將 Proxy 程式碼所需的適當 WCF 套件，以套件參考的形式新增到專案。

6. 使用 [`dotnet restore`](../tools/dotnet-restore.md) 命令還原 WCF 套件，如下所示：

```console
dotnet restore
```

7. 在您的編輯器中開啟 `Program.cs` 檔案，編輯 `Main()` 方法，並以下列程式碼取代自動產生的程式碼來叫用 Web 服務：

```csharp
static void Main(string[] args)
{
    var client = new SayHelloClient();
    Console.WriteLine(client.HelloAsync("dotnet-svcutil").Result);
}
```

8. 使用 [`dotnet run`](../tools/dotnet-run.md) 命令執行應用程式，如下所示：

```console
dotnet run
```
您應該會看見下列輸出："Hello dotnet-svcutil!"

如需 `dotnet-svcutil` 工具參數的詳細說明，請依下列所示叫用工具並傳遞 help 參數：

```console
dotnet svcutil --help
```

## <a name="next-steps"></a>後續步驟

### <a name="feedback--questions"></a>意見反應和問題

如果您有任何問題或意見反應，請[在 GitHub 上開啟問題](https://github.com/dotnet/wcf/issues/new)。 您也可以[在 GitHub 的 WCF 存放庫](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling)檢閱任何現有問題或議題。

### <a name="release-notes"></a>版本資訊

* 如需已更新的版本資訊，請參閱[版本資訊](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md) (包含已知問題)。

### <a name="information"></a>資訊

* [dotnet-svcutil NuGet 套件](https://nuget.org/packages/dotnet-svcutil) \(英文\)
