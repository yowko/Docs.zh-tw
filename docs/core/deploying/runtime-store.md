---
title: "執行階段套件存放區"
description: "本主題說明 .NET Core 所使用的執行階段套件存放區和目標資訊清單。"
keywords: ".NET, .NET Core, dotnet 存放區, 執行階段套件存放區"
author: bleroy
ms.author: mairaw
ms.date: 08/12/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 9521d8b4-25fc-412b-a65b-4c975ebf6bfd
ms.translationtype: HT
ms.sourcegitcommit: 57e9a2b8aa952860a380b60c44fd2df16ef6463c
ms.openlocfilehash: e039190b49b35bd2675a175c6ff3631d6d344e4a
ms.contentlocale: zh-tw
ms.lasthandoff: 08/14/2017

---
# <a name="runtime-package-store"></a>執行階段套件存放區

從 .NET Core 2.0 開始，可針對目標環境中存在的已知套件集合封裝和部署應用程式。 優點是部署更快、磁碟使用空間較少，而且啟動效能在某些情況下有所改善。

這項功能實作為「執行階段套件存放區」，這是套件儲存所在磁碟的目錄 (通常在 macOS/Linux 是 */usr/local/share/dotnet/store*，在 Windows 是 *C:/Program Files/dotnet/store*)。 在此目錄下，有架構和[目標 Framework](../../standard/frameworks.md) 的子目錄。 檔案配置類似於[磁碟上的 NuGet 資產配置](/nuget/create-packages/supporting-multiple-target-frameworks#framework-version-folder-structure)方式：

\dotnet   
&nbsp;&nbsp;\store   
&nbsp;&nbsp;&nbsp;&nbsp;\x64   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\net47   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\microsoft.applicationinsights   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\microsoft.aspnetcore   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;...   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\netcoreapp2.0   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\microsoft.applicationinsights   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\microsoft.aspnetcore   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;...   
&nbsp;&nbsp;&nbsp;&nbsp;\x86   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\net47   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\microsoft.applicationinsights   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\microsoft.aspnetcore   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;...   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\netcoreapp2.0   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\microsoft.applicationinsights   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\microsoft.aspnetcore   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;...   

「目標資訊清單」檔會列出執行階段套件存放區中的套件。 開發人員可在發佈其應用程式時，以此資訊清單為目標。 目標資訊清單通常是由目標生產環境的擁有者提供。

## <a name="preparing-a-runtime-environment"></a>準備執行階段環境

執行階段環境的系統管理員可以建置執行階段套件存放區和對應的目標資訊清單，以最佳化應用程式，取得更快的部署和較少的磁碟使用空間。

第一個步驟是建立「套件存放區資訊清單」，列出撰寫執行階段套件存放區的套件。 此檔案格式與專案檔格式 (*csproj*) 相容。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="<NUGET_PACKAGE>" Version="<VERSION>" />
    <!-- Include additional packages here -->
  </ItemGroup>
</Project>
```

**範例**

下例使用套件存放區資訊清單 (*packages.csproj*) 將 [`Newtonsoft.Json`](https://www.nuget.org/packages/Newtonsoft.Json/) 和 [`Moq`](https://www.nuget.org/packages/moq/) 新增至執行階段套件存放區：

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.3" />
    <PackageReference Include="Moq" Version="4.7.63" />
  </ItemGroup>
</Project>
```

執行 `dotnet store` 加上套件存放區資訊清單、執行階段和架構，佈建執行階段套件存放區：

```console
dotnet store --manifest <PATH_TO_MANIFEST_FILE> --runtime <RUNTIME_IDENTIFIER> --framework <FRAMEWORK>
```

**範例**

```console
dotnet store --manifest packages.csproj --runtime win10-x64 --framework netcoreapp2.0 --framework-version 2.0.0
```

您可以在命令中重複選項和路徑，將多個目標套件存放區資訊清單路徑傳遞至單一 [`dotnet store`](../tools/dotnet-store.md) 命令。

根據預設，命令的輸出位在使用者設定檔的 *.dotnet/store* 子目錄下的套件存放區中。 您可以使用 `--output <OUTPUT_DIRECTORY>` 選項指定不同的位置。 存放區的根目錄包含目標資訊清單 *artifact.xml* 檔案。 此檔案可供下載，並可供想要在發行時以此存放區為目標的應用程式作者使用。

**範例**

執行上例後，會產生以下 *artifact.xml* 檔案。 請注意，[`Castle.Core`](https://www.nuget.org/packages/Castle.Core/) 是 `Moq` 的相依性，因此會自動包含並出現在 *artifacts.xml* 資訊清單檔中。

```xml
<StoreArtifacts>
  <Package Id="newtonsoft.json" Version="10.0.3" />
  <Package Id="castle.core" Version="4.1.0" />
  <Package Id="moq" Version="4.7.63" />
</StoreArtifacts>
```

## <a name="publishing-an-app-against-a-target-manifest"></a>針對目標資訊清單發行應用程式

如果磁碟上有目標資訊清單檔案，您可在使用 [`dotnet publish`](../tools/dotnet-publish.md) 命令發佈應用程式時，指定檔案的路徑：

```console
dotnet publish --manifest <PATH_TO_MANIFEST_FILE>
```

**範例**

```console
dotnet publish --manifest manifest.xml
```

您會將所產生的已發行應用程式，部署到有目標資訊清單所述套件的環境中。 無法這樣做，會導致應用程式無法啟動。

重複選項和路徑 (例如 `--manifest manifest1.xml --manifest manifest2.xml`)，以在發行應用程式時，指定多個目標資訊清單。 當您這樣做時，會針對提供給命令的目標資訊清單檔中指定的套件聯集修剪應用程式。

## <a name="specifying-target-manifests-in-the-project-file"></a>在專案檔中指定目標資訊清單

以 [`dotnet publish`](../tools/dotnet-publish.md) 命令指定目標資訊清單的替代方式，是在專案檔中將它們指定為 **\<TargetManifestFiles>** 標記下的以分號分隔的路徑清單。

```xml
<PropertyGroup>
  <TargetManifestFiles>manifest1.xml;manifest2.xml</TargetManifestFiles>
</PropertyGroup>
```

只有當應用程式的目標環境為已知時，例如 .NET Core 專案，才在專案檔中指定目標資訊清單。 這不是開放原始碼專案的情況。 開放原始碼專案的使用者通常會將它部署到不同的生產環境中。 這些生產環境通常會有不同的預先安裝的套件集。 您不能對這類環境中的目標資訊清單進行假設，因此您應該使用 [`dotnet publish`](../tools/dotnet-publish.md) 的 `--manifest` 選項。

## <a name="aspnet-core-implicit-store"></a>ASP.NET Core 隱含存放區

當應用程式部署為[與 Framework 相依的部署 (FDD)](index.md#framework-dependent-deployments-fdd) 應用程式時，ASP.NET Core 應用程式會以隱含方式使用執行階段套件存放區功能。 [`Microsoft.NET.Sdk.Web`](https://github.com/aspnet/websdk) 中的目標包含參考目標系統上隱含套件存放區的資訊清單。 此外，任何相依於 `Microsoft.AspNetCore.All` 套件的 FDD 應用程式，都會造成已發行的應用程式只包含應用程式及其資產，不包含 `Microsoft.AspNetCore.All` 中繼套件列出的套件。 假設這些套件存在於目標系統上。

安裝 .NET Core SDK 時，執行階段套件存放區會安裝在主機上。 其他的安裝程式可能會提供執行階段套件存放區，包括 .NET Core SDK 的 Zip/tarball 安裝、`apt-get`、Red Hat Yum、.NET Core Windows Server 裝載組合，以及手動的執行階段套件存放區安裝。

部署[與 Framework 相依的部署 (FDD)](index.md#framework-dependent-deployments-fdd) 應用程式時，請確定目標環境已安裝 .NET Core SDK。 如果應用程式部署到不包含 ASP.NET Core 的環境，您可以像下例一樣在專案檔指定設為 `false` 的 **\<PublishWithAspNetCoreTargetManifest>**，從隱含的存放區選擇：

```xml
<PropertyGroup>
  <PublishWithAspNetCoreTargetManifest>false</PublishWithAspNetCoreTargetManifest>
</PropertyGroup>
```

> [!NOTE] 
> 若為[獨立部署 (SCD)](index.md#self-contained-deployments-scd) 應用程式，假設目標系統不必然包含必要的資訊清單套件。 因此，SCD 應用程式的 **\<PublishWithAspNetCoreTargetManifest>** 不能設定為 `true`。

如果您部署的應用程式具有存在於部署中的資訊清單相依性 (組件位於 *bin* 資料夾)，主機對該組件「不會使用」執行階段套件存放區。 無論主機的執行階段套件存放區是否有 *bin* 資料夾組件，都使用它。

資訊清單中指示的相依性版本，必須符合執行階段套件存放區中的相依性版本。 如果目標資訊清單中的相依性版本與執行階段套件存放區的版本不相符，而應用程式的部署中不包含必要的套件版本，則應用程式無法啟動。 例外狀況包含目標資訊清單的名稱，為執行階段套件存放區組件所稱呼的名稱，有利於針對不符合進行疑難排解。

於發行時「修剪」部署，已發行的輸出只保留您指定的資訊清單套件特定版本。 主機必須要有指定版本的套件，應用程式才能啟動。

## <a name="see-also"></a>另請參閱
 [dotnet-publish](../tools/dotnet-publish.md)   
 [dotnet-store](../tools/dotnet-store.md)   

