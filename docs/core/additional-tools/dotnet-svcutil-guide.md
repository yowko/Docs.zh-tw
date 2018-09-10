---
title: Microsoft WCF dotnet-svcutil 工具
description: Microsoft WCF dotnet-svcutil 工具的概觀，此工具可新增 .NET Core 和 ASP.NET Core 專案功能，與 .NET Framework 專案的 WCF svcutil 工具類似。
author: mlacouture
ms.author: jralexander
ms.date: 08/20/2018
ms.openlocfilehash: bb4d8e5f3997318b720535b0f1e07fc33d13338a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43511882"
---
# <a name="microsoft-wcf-dotnet-svcutil-tool"></a><span data-ttu-id="98fde-103">Microsoft WCF dotnet-svcutil 工具</span><span class="sxs-lookup"><span data-stu-id="98fde-103">Microsoft WCF dotnet-svcutil tool</span></span>

<span data-ttu-id="98fde-104">Windows Communication Foundation (WCF) **dotnet-svcutil** 工具是一種 .NET Core CLI 工具，可從網路位置上的 Web 服務或從 WSDL 檔案擷取中繼資料，並產生包含可用來存取 Web 服務作業的用戶端 Proxy 方法的 WCF 類別。</span><span class="sxs-lookup"><span data-stu-id="98fde-104">The Windows Communication Foundation (WCF) **dotnet-svcutil** tool is a .NET Core CLI tool that retrieves metadata from a web service on a network location or from a WSDL file, and generates a WCF class containing client proxy methods that access the web service operations.</span></span>

<span data-ttu-id="98fde-105">類似適用於 .NET Framework 專案的 [**Service Model Metadata - svcutil**](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) 工具，**dotnet-svcutil** 是一種命令列工具，可用來產生與 .NET Core 和 .NET Standard 專案相容的 Web 服務參考。</span><span class="sxs-lookup"><span data-stu-id="98fde-105">Similar to the [**Service Model Metadata - svcutil**](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool for .NET Framework projects, the **dotnet-svcutil** is a command-line tool for generating a web service reference compatible with .NET Core and .NET Standard projects.</span></span>

<span data-ttu-id="98fde-106">**dotnet-svcutil** 工具是於 Visual Studio 2017 15.5 版首次推出之 [**WCF Web Service Reference**](wcf-web-service-reference-guide.md) Visual Studio 連線服務提供者的替代選項。</span><span class="sxs-lookup"><span data-stu-id="98fde-106">The **dotnet-svcutil** tool is an alternative option to the [**WCF Web Service Reference**](wcf-web-service-reference-guide.md) Visual Studio connected service provider that first shipped with Visual Studio 2017 v15.5.</span></span> <span data-ttu-id="98fde-107">**dotnet-svcutil** 工具可當作 .NET Core CLI 工具，在 Linux、macOS 和 Windows 上跨平台使用。</span><span class="sxs-lookup"><span data-stu-id="98fde-107">The **dotnet-svcutil** tool as a .NET Core CLI tool, is available cross-platform on Linux, macOS, and Windows.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="98fde-108">您只應該參考來自信任來源的服務。</span><span class="sxs-lookup"><span data-stu-id="98fde-108">You should only reference services from a trusted source.</span></span> <span data-ttu-id="98fde-109">新增不信任來源的參考可能會危及安全性。</span><span class="sxs-lookup"><span data-stu-id="98fde-109">Adding references from an untrusted source may compromise security.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="98fde-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="98fde-110">Prerequisites</span></span>

* <span data-ttu-id="98fde-111">[.NET Core SDK](https://www.microsoft.com/net/download) \(英文\) 1.0.4 版或更新版本</span><span class="sxs-lookup"><span data-stu-id="98fde-111">[.NET Core SDK](https://www.microsoft.com/net/download) v1.0.4 or later versions</span></span>
* <span data-ttu-id="98fde-112">您慣用的程式碼編輯器</span><span class="sxs-lookup"><span data-stu-id="98fde-112">Your favorite code editor</span></span>

## <a name="getting-started"></a><span data-ttu-id="98fde-113">使用者入門</span><span class="sxs-lookup"><span data-stu-id="98fde-113">Getting started</span></span>

<span data-ttu-id="98fde-114">下列範例會引導您完成將 Web 服務參考新增到 .NET Core 主控台專案並叫用服務的必要步驟。</span><span class="sxs-lookup"><span data-stu-id="98fde-114">The following example walks you through the steps required to add a web service reference to a .NET Core console project and invoke the service.</span></span> <span data-ttu-id="98fde-115">您將會建立名為 _HelloSvcutil_ 的 .NET Core 主控台應用程式，並將新增實作下列合約之 Web 服務的參考：</span><span class="sxs-lookup"><span data-stu-id="98fde-115">You will create a .NET Core console application named _HelloSvcutil_ and will add a reference to a web service that implements the following contract:</span></span>

```csharp
[ServiceContract]
public interface ISayHello
{
    [OperationContract]
    string Hello(string name);
}
```

<span data-ttu-id="98fde-116">針對此範例，我們將假設 Web 服務裝載於下列位址：`http://contoso.com/SayHello.svc`</span><span class="sxs-lookup"><span data-stu-id="98fde-116">For this example, the web service will be assumed to be hosted at the following address: `http://contoso.com/SayHello.svc`</span></span>

<span data-ttu-id="98fde-117">從 Windows、macOS 或 Linux 命令視窗執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="98fde-117">From a Windows, macOS, or Linux command window perform the following steps:</span></span>

1. <span data-ttu-id="98fde-118">為您的專案建立一個名為 _HelloSvcutil_ 的目錄，然後讓它成為您目前所在的目錄，如下列範例中所示：</span><span class="sxs-lookup"><span data-stu-id="98fde-118">Create a directory named _HelloSvcutil_ for your project and make it your current directory, as in the following example:</span></span>

```console
mkdir HelloSvcutil
cd HelloSvcutil
```

2. <span data-ttu-id="98fde-119">使用 [`dotnet new`](../tools/dotnet-new.md) 命令在該目錄中建立新的 C# 主控台專案，如下所示：</span><span class="sxs-lookup"><span data-stu-id="98fde-119">Create a new C# console project in that directory using the [`dotnet new`](../tools/dotnet-new.md) command as follows:</span></span>

```console
dotnet new console
```

3. <span data-ttu-id="98fde-120">在您的編輯器中開啟 `HelloSvcutil.csproj` 專案檔，編輯 `Project` 元素，然後使用下列程式碼將 [`dotnet-svcutil`NuGet 套件](https://nuget.org/packages/dotnet-svcutil) \(英文\) 新增為 CLI 工具參考：</span><span class="sxs-lookup"><span data-stu-id="98fde-120">Open the `HelloSvcutil.csproj` project file in your editor, edit the `Project` element, and add the [`dotnet-svcutil` NuGet package](https://nuget.org/packages/dotnet-svcutil) as a CLI tool reference, using the following code:</span></span>

```xml
<ItemGroup>
  <DotNetCliToolReference Include="dotnet-svcutil" Version="1.0.*" />
</ItemGroup>
```

4. <span data-ttu-id="98fde-121">使用 [`dotnet restore`](../tools/dotnet-restore.md) 命令還原 _dotnet-svcutil_ 套件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="98fde-121">Restore the _dotnet-svcutil_ package using the [`dotnet restore`](../tools/dotnet-restore.md) command as follows:</span></span>

```console
dotnet restore
```

5. <span data-ttu-id="98fde-122">搭配 _svcutil_ 命令執行 _dotnet_ 以產生 Web 服務參考檔案，如下所示：</span><span class="sxs-lookup"><span data-stu-id="98fde-122">Run _dotnet_ with the _svcutil_ command to generate the web service reference file as follows:</span></span>

```console
dotnet svcutil http://contoso.com/SayHello.svc
```
<span data-ttu-id="98fde-123">產生的檔案會儲存為 _HelloSvcutil/ServiceReference1/Reference.cs_。</span><span class="sxs-lookup"><span data-stu-id="98fde-123">The generated file is saved as _HelloSvcutil/ServiceReference1/Reference.cs_.</span></span> <span data-ttu-id="98fde-124">_dotnet_svcutil_ 工具也會將 Proxy 程式碼所需的適當 WCF 套件，以套件參考的形式新增到專案。</span><span class="sxs-lookup"><span data-stu-id="98fde-124">The _dotnet_svcutil_ tool also adds to the project the appropriate WCF packages required by the proxy code as package references.</span></span>

6. <span data-ttu-id="98fde-125">使用 [`dotnet restore`](../tools/dotnet-restore.md) 命令還原 WCF 套件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="98fde-125">Restore the WCF packages using the [`dotnet restore`](../tools/dotnet-restore.md) command as follows:</span></span>

```console
dotnet restore
```

7. <span data-ttu-id="98fde-126">在您的編輯器中開啟 `Program.cs` 檔案，編輯 `Main()` 方法，並以下列程式碼取代自動產生的程式碼來叫用 Web 服務：</span><span class="sxs-lookup"><span data-stu-id="98fde-126">Open the `Program.cs` file in your editor, edit the `Main()` method, and replace the auto-generated code with the following code to invoke the web service:</span></span>

```csharp
static void Main(string[] args)
{
    var client = new SayHelloClient();
    Console.WriteLine(client.HelloAsync("dotnet-svcutil").Result);
}
```

8. <span data-ttu-id="98fde-127">使用 [`dotnet run`](../tools/dotnet-run.md) 命令執行應用程式，如下所示：</span><span class="sxs-lookup"><span data-stu-id="98fde-127">Run the application using the [`dotnet run`](../tools/dotnet-run.md) command as follows:</span></span>

```console
dotnet run
```
<span data-ttu-id="98fde-128">您應該會看見下列輸出："Hello dotnet-svcutil!"</span><span class="sxs-lookup"><span data-stu-id="98fde-128">You should see the following output: "Hello dotnet-svcutil!"</span></span>

<span data-ttu-id="98fde-129">如需 `dotnet-svcutil` 工具參數的詳細說明，請依下列所示叫用工具並傳遞 help 參數：</span><span class="sxs-lookup"><span data-stu-id="98fde-129">For a detailed description of the `dotnet-svcutil` tool parameters, invoke the tool passing the help parameter as follows:</span></span>

```console
dotnet svcutil --help
```

## <a name="next-steps"></a><span data-ttu-id="98fde-130">後續步驟</span><span class="sxs-lookup"><span data-stu-id="98fde-130">Next steps</span></span>

### <a name="feedback--questions"></a><span data-ttu-id="98fde-131">意見反應和問題</span><span class="sxs-lookup"><span data-stu-id="98fde-131">Feedback & questions</span></span>

<span data-ttu-id="98fde-132">如果您有任何問題或意見反應，請[在 GitHub 上開啟問題](https://github.com/dotnet/wcf/issues/new)。</span><span class="sxs-lookup"><span data-stu-id="98fde-132">If you have any questions or feedback, [open an issue on GitHub](https://github.com/dotnet/wcf/issues/new).</span></span> <span data-ttu-id="98fde-133">您也可以[在 GitHub 的 WCF 存放庫](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling)檢閱任何現有問題或議題。</span><span class="sxs-lookup"><span data-stu-id="98fde-133">You can also review any existing questions or issues [at the WCF repo on GitHub](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).</span></span>

### <a name="release-notes"></a><span data-ttu-id="98fde-134">版本資訊</span><span class="sxs-lookup"><span data-stu-id="98fde-134">Release notes</span></span>

* <span data-ttu-id="98fde-135">如需已更新的版本資訊，請參閱[版本資訊](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md) (包含已知問題)。</span><span class="sxs-lookup"><span data-stu-id="98fde-135">Refer to the [Release notes](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md) for updated release information, including known issues.</span></span>

### <a name="information"></a><span data-ttu-id="98fde-136">資訊</span><span class="sxs-lookup"><span data-stu-id="98fde-136">Information</span></span>

* <span data-ttu-id="98fde-137">[dotnet-svcutil NuGet 套件](https://nuget.org/packages/dotnet-svcutil) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="98fde-137">[dotnet-svcutil NuGet Package](https://nuget.org/packages/dotnet-svcutil)</span></span>
