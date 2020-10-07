---
title: .NET 簡介和總覽
description: 深入瞭解 .NET 這項免費的開放原始碼開發平臺，可用於建立許多種類的應用程式。
author: tdykstra
ms.date: 09/28/2020
ms.custom: updateeachrelease
ms.openlocfilehash: 2b339db769c283ff21e6ad48d5b672794e43a76b
ms.sourcegitcommit: 636af37170ae75a11c4f7d1ecd770820e7dfe7bd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2020
ms.locfileid: "91804792"
---
# <a name="introduction-to-net"></a>.NET 簡介

.NET 是免費的開放原始碼開發平臺，可用於建立許多種類的應用程式，例如：

* [Web 應用程式、web Api 和微服務](/aspnet/core/introduction-to-aspnet-core#recommended-learning-path)
* [雲端中的無伺服器函式](/azure/azure-functions/functions-create-first-function-vs-code?pivots=programming-language-csharp)
* [雲端原生應用程式](../architecture/cloud-native/index.md)
* [行動應用程式](https://dotnet.microsoft.com/learn/xamarin/hello-world-tutorial/intro)
* 傳統型應用程式
  * [Windows WPF](/dotnet/desktop/wpf/)
  * [Windows Forms](/dotnet/desktop/winforms/)
  * [通用 Windows 平台 (UWP)](/windows/uwp/get-started/create-a-hello-world-app-xaml-universal)
* [遊戲](https://dotnet.microsoft.com/learn/games/unity-tutorial/intro)
* [物聯網 (IoT)](https://dotnet.microsoft.com/apps/iot)
* [機器學習](../machine-learning/index.yml)
* [主控台應用程式](tutorials/with-visual-studio-code.md)
* [Windows 服務](/aspnet/core/host-and-deploy/windows-service)

使用 [類別庫](../standard/class-libraries.md)，在不同的應用程式和應用程式類型之間共用功能。

使用 .NET 時，無論您要建立哪種類型的應用程式，程式碼和專案檔的外觀和操作都會相同。 您可以使用每個應用程式存取相同的執行時間、API 和語言功能。

## <a name="cross-platform"></a>跨平台

您可以為許多作業系統建立 .NET 應用程式，包括：

* Windows
* macOS
* Linux
* Android
* iOS
* tvOS
* watchOS

支援的處理器架構包括：

* x64
* x86
* ARM32
* ARM64

.NET 可讓您使用平臺特定的功能，例如作業系統 Api。 範例包括 Windows 上的 Windows Forms 和 WPF，以及 Xamarin 的每個行動平臺的原生系結。

如需詳細資訊，請參閱 [支援的 OS 生命週期原則](https://github.com/dotnet/core/blob/master/os-lifecycle-policy.md) 和 [.net RID 目錄](rid-catalog.md)。

## <a name="open-source"></a>開放原始碼

.NET 是開放原始碼，使用 [MIT 和 Apache 2 授權](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT)。 .NET 是 [.Net Foundation](https://dotnetfoundation.org/)的專案。

如需詳細資訊，請參閱 [GitHub.com 上的專案存放庫清單](https://github.com/dotnet/core/blob/master/Documentation/core-repos.md)。

## <a name="support"></a>支援

Microsoft 在 Windows、macOS 和 Linux 上支援 .NET。 它會在每個月的第二個星期二定期更新安全性和品質。

Microsoft 的 .NET 二進位散發套件是在 Azure 中 Microsoft 維護的伺服器上建立和測試，並遵循 Microsoft 工程和安全性作法。

[Red Hat 支援](https://developers.redhat.com/topics/dotnet/) Red Hat Enterprise Linux 上的 .NET (RHEL) 。 Red Hat 與 Microsoft 共同作業以確保 .NET Core 可在 RHEL 上正確運作。

[Tizen 支援](https://developer.tizen.org/development/training/.net-application) Tizen 平臺上的 .net。

如需詳細資訊，請參閱 [支援原則](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)。

## <a name="tools-and-productivity"></a>工具和生產力

.NET 提供您選擇的語言、整合式開發環境 (Ide) 和其他工具。

### <a name="programming-languages"></a>程式語言

.NET 支援三種程式設計語言：

* [C#](../csharp/index.yml)

  C # (發音為「看清晰的」 ) 是新式、物件導向且型別安全的程式設計語言。 C# 源自於是 C 系列語言，使用 C、C++、Java 和 JavaScript 的程式設計人員會立即感到熟悉。

* [F#](../fsharp/index.yml)

  F # 語言支援功能性、物件導向和命令式程式設計模型。

* [Visual Basic](../visual-basic/index.yml)

  在 .NET 語言中，Visual Basic 的語法是最接近一般人類語言的語法，可讓您更輕鬆地學習。 不同于 c # 和 F #，Microsoft 正積極開發新功能，Visual Basic 的語言是穩定的。 Web 應用程式不支援 Visual Basic，但 web Api 支援此功能。

以下是 .NET 語言支援的一些功能：

* [型別安全](../standard/base-types/common-type-system.md)
* 型別推斷- [c #](../csharp/programming-guide/types/index.md#specifying-types-in-variable-declarations)、 [F #](../fsharp/language-reference/type-inference.md)、 [Visual Basic](../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
* [泛型類型](../standard/generics.md)
* [委派](../standard/delegates-lambdas.md)
* [Lambda](../standard/delegates-lambdas.md)
* [事件](../standard/events/index.md)
* [例外狀況](../standard/exceptions/index.md)
* [屬性](../standard/attributes/index.md)
* [非同步程式碼](../standard/async.md)
* [平行程式設計](../standard/parallel-programming/index.md)
* [程式碼分析器](../fundamentals/code-analysis/overview.md)

### <a name="ides"></a>IDE

適用于 .NET 的整合式開發環境包括：

* [Visual Studio](https://visualstudio.microsoft.com/vs/)

  只能在 Windows 上執行。 具有廣泛的內建功能，其設計目的是使用 .NET。 所有學生、開放原始碼參與者及個人均可免費取得此社區版。

* [Visual Studio Code](https://code.visualstudio.com/)

  在 Windows、macOS 和 Linux 上執行。 免費且開放的原始碼。 擴充功能可搭配 .NET 語言使用。

* [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/)

  只會在 macOS 上執行。 適用于開發適用于 iOS、Android 和 web 的 .NET 應用程式和遊戲。

* [GitHub Codespaces](https://github.com/features/codespaces)

  線上 Visual Studio Code 環境，目前為搶鮮版（Beta）。

### <a name="sdk-and-runtimes"></a>SDK 和執行時間

[.NET SDK](sdk.md)是用來開發及執行 .net 應用程式的一組程式庫和工具。

當您 [下載 .net](https://dotnet.microsoft.com/download/dotnet-core/)時，您可以選擇 SDK 或 *運行*時間，例如 .net 執行時間或 ASP.NET Core 執行時間。 在您想要準備執行 .NET 應用程式的電腦上安裝執行時間。 在您要用於開發的電腦上安裝 SDK。 當您下載 SDK 時，您會自動取得其執行時間。

SDK 下載包含下列元件：

* [.NET CLI](tools/index.md)。 您可以用於本機開發和連續整合腳本的命令列工具。
* `dotnet`[驅動程式](tools/index.md#driver)。 執行與架構相依的應用程式的 CLI 命令。
* [Roslyn](https://github.com/dotnet/roslyn)和[F #](https://github.com/microsoft/visualfsharp)程式設計語言編譯器。
* [MSBuild](/visualstudio/msbuild/msbuild)組建引擎。
* [.Net 運行](#clr)時間。 提供類型系統、元件載入、垃圾收集行程、原生 interop 及其他基本服務。
* [執行階段程式庫](#runtime-libraries)。 提供基本資料類型和基本公用程式。
* ASP.NET Core 執行時間。 為網際網路連線的應用程式（例如 web 應用程式、IoT 應用程式和行動後端）提供基本的服務。
* 桌面執行時間。 提供 Windows 傳統型應用程式的基本服務，包括 Windows Forms 和 WPF。

如需詳細資訊，請參閱下列資源：

* [.NET SDK 總覽](sdk.md)
* [.NET CLI 總覽](tools/index.md)
* [dotnet 命令](tools/dotnet.md)

### <a name="project-system-and-msbuild"></a>專案系統和 MSBuild

.NET 應用程式是使用 [MSBuild](/visualstudio/msbuild/msbuild)從原始程式碼建立的。 專案檔 (*.csproj*、 *>.fsproj*或 *. vbproj*) 指定負責編譯、封裝和發佈程式碼的[目標](/visualstudio/msbuild/msbuild-targets)[和相關聯](/visualstudio/msbuild/msbuild-tasks)工作。 有 SDK 識別碼可參考目標和工作的標準集合。 使用這些識別碼有助於讓專案檔變小且容易使用。 例如，以下是主控台應用程式的專案檔：

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net5.0</TargetFramework>
  </PropertyGroup>
</Project>
```

以下是 web 應用程式的其中一個：

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">
  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>
  </PropertyGroup>
</Project>
```

在這些範例中， `Sdk` 元素的屬性 `Project` 會指定一組 MSBuild 目標和工作，以建立專案。  `TargetFramework`元素會指定應用程式所相依的 .net 版本。 您可以編輯專案檔，以加入專案特定的其他目標和工作。

如需詳細資訊，請參閱 [.net 專案 SDK 總覽](project-sdk/overview.md) 和 [目標 framework](../standard/frameworks.md)。

### <a name="cicd"></a>CI/CD

MSBuild 和 .NET CLI 可以搭配各種持續整合工具和環境使用，例如：

* [GitHub 動作](https://github.com/features/actions)
* [Azure DevOps](/azure/devops/user-guide/what-is-azure-devops)
* [蛋糕](https://cakebuild.net/)
* [假](https://fake.build/)

如需詳細資訊，請參閱 [在持續整合 (CI 中使用 .NET SDK 和工具) ](tools/using-ci-with-cli.md)

### <a name="nuget"></a>NuGet

[NuGet](/nuget/what-is-nuget) 是專為 .net 設計的開放原始碼套件管理員。 NuGet 套件是副檔名為的 *.zip* 檔案，其中 `.nupkg` 包含已編譯的程式碼 (dll) 、與該程式碼相關的其他檔案，以及包含套件版本號碼等資訊的描述性資訊清單。 具有程式碼的開發人員可共用建立封裝，並將其發佈至 [nuget.org](https://nuget.org) 或私用主機。 如果開發人員想要使用共用程式碼，請將封裝新增至其專案，然後在其專案程式碼中呼叫封裝所公開的 API。

如需詳細資訊，請參閱 [NuGet 檔](/nuget/)集。

### <a name="net-interactive"></a>.NET 互動

.NET Interactive 是一組 CLI 工具和 Api，可讓使用者在 web、markdown 和筆記本之間建立互動式體驗。

如需詳細資訊，請參閱下列資源：

* [.NET 瀏覽器中教學課程](https://dotnet.microsoft.com/learn/dotnet/in-browser-tutorial/1)
* [在您的電腦上搭配 Jupyter 使用 .NET 筆記本](https://github.com/dotnet/interactive/blob/main/docs/NotebooksLocalExperience.md)
* [.NET 互動式檔](https://github.com/dotnet/interactive/blob/main/docs/README.md)

## <a name="execution-models"></a>執行模型

.NET 應用程式會在執行時間環境中執行 [managed 程式碼](../standard/managed-code.md) ，此環境稱為 Common Language RUNTIME (CLR) 。

### <a name="clr"></a>CLR

.NET [CLR](../standard/clr.md) 是一種跨平臺執行時間，包含對 Windows、MacOS 和 Linux 的支援。 CLR 會處理記憶體配置和管理。 CLR 也是虛擬機器，不僅會執行應用程式，也會使用及時 (JIT) 編譯器來產生和編譯器代碼。

如需詳細資訊，請參閱 [Common Language Runtime (CLR) 總覽](../standard/clr.md)。

### <a name="jit-compiler-and-il"></a>JIT 編譯程式和 IL

較高階的 .NET 語言 (例如 C#) 可向下編譯成硬體無從驗證的指令集，稱為中繼語言 (IL)。 當應用程式執行時，JIT 編譯程式會將 IL 轉譯為處理器瞭解的機器碼。 JIT 編譯發生在程式碼即將執行的同一部電腦上。

由於 JIT 編譯是在應用程式執行期間發生，編譯時間是執行時間的一部分。 因此，JIT 編譯程式必須將花費在優化程式碼的時間與產生的程式碼所能產生的節省時間進行平衡。 但是 JIT 編譯程式知道實際的硬體，而且可以讓開發人員不需要為不同的平臺送出不同的執行方式。

.NET JIT 編譯程式可以進行階層式 *編譯*，這表示它可以在執行時間重新編譯個別方法。 這項功能可讓它快速編譯，同時仍能針對常用的方法產生高度調整的程式碼版本。

如需詳細資訊，請參閱 [Managed 執行](../standard/managed-execution-process.md) 程式和階層式 [編譯](whats-new/dotnet-core-3-0.md#tiered-compilation)。

### <a name="aot-compiler"></a>AOT 編譯器

大部分 .NET 工作負載的預設體驗都是 JIT 編譯程式，但 .NET 提供兩種預先 (AOT) 編譯的形式：

* 某些案例需要 100% AOT 編譯。 例如 [iOS](/xamarin/ios/)。
* 在其他案例中，大部分的應用程式程式碼都是由 AOT 編譯，但有些則是 JIT 編譯的。 某些程式碼模式不適用於 AOT (例如泛型) 。 這種形式的 AOT 編譯範例是可 [立即執行](whats-new/dotnet-core-3-0.md#readytorun-images) 的發行選項。 這種形式的 AOT 可提供 AOT 的優點，而不會有其缺點。

### <a name="automatic-memory-management"></a>自動記憶體管理

*垃圾收集*行程 (GC) 管理應用程式的記憶體配置和釋放。 每當您的程式碼建立新的物件時，CLR 就會從 [managed 堆積](../standard/garbage-collection/fundamentals.md#the-managed-heap)設定物件的記憶體。 只要 Managed 堆積中有可供使用的位址空間，平台就會繼續為新的物件配置空間。 如果沒有足夠的可用位址空間，GC 就會檢查 managed 堆積中，應用程式不再使用的物件。 然後回收該記憶體。

GC 是可協助確保 *記憶體安全*的其中一個 CLR 服務。 如果程式只存取已配置的記憶體，就是記憶體安全。 例如，執行階段可確保應用程式不會存取陣列界限外已取消配置的記憶體。

如需詳細資訊，請參閱 [自動記憶體管理](../standard/automatic-memory-management.md) 和 [垃圾收集的基本](../standard/garbage-collection/fundamentals.md)概念。

### <a name="working-with-unmanaged-resources"></a>使用 Unmanaged 資源

有時候，程式碼需要參考 *未受管理的資源*。 Unmanaged 資源是指 .NET 執行階段不會自動維護的資源。 例如檔案控制程式碼就是 Unmanaged 資源。 <xref:System.IO.FileStream> 物件是Managed 物件，但會 Unmanaged 檔案控制代碼。 當您使用完成時 <xref:System.IO.FileStream> ，您必須明確釋放檔案控制代碼。

在.NET 中，參考 Unmanaged 資源的物件會實作 <xref:System.IDisposable> 介面。 當您完成使用此物件時，您可以呼叫物件的 <xref:System.IDisposable.Dispose> 方法來釋放任何 Unmanaged 資源。 .Net 語言提供了一個方便的 `using` 語句， ([c #](../csharp/language-reference/keywords/using.md)、 [F #](../fsharp/language-reference/resource-management-the-use-keyword.md)、 [VB](../visual-basic/language-reference/statements/using-statement.md)) ，可確保 `Dispose` 呼叫方法。

如需詳細資訊，請參閱 [清除非受控資源](../standard/garbage-collection/unmanaged.md)。

## <a name="deployment-models"></a>部署模型

.NET 應用程式可在兩種不同的模式下發行：

* 將應用程式發佈為 *獨立* 應用程式會產生可執行檔，其中包含 .net [運行](#sdk-and-runtimes) 時間和連結 [庫](#runtime-libraries)，以及應用程式及其相依性。 應用程式的使用者可以在未安裝 .NET 執行時間的電腦上執行它。 獨立應用程式是平臺專屬的應用程式，而且可以選擇性地使用 [AOT 編譯](#aot-compiler)形式來發佈。

* 將應用程式發行為與 *framework 相依* 的應用程式，會產生可執行檔和二進位檔案 (*.dll* 檔案，) 只包含應用程式本身及其相依性。 應用程式的使用者必須分別安裝 .NET [運行](#sdk-and-runtimes)時間。 可執行檔是平臺專屬的，但架構相依應用程式的 *.dll* 檔案是跨平臺。

  您可以並存安裝多個版本的執行時間，以執行以不同執行階段版本為目標的架構相依應用程式。 如需詳細資訊，請參閱 [目標 framework](../standard/frameworks.md)。

系統會針對特定的目標平臺產生可執行檔，您可以使用執行時間識別碼來指定 [ (RID) ](rid-catalog.md)。

如需詳細資訊，請參閱 [.net 應用程式發行總覽](deploying/index.md) 和 [.Net 和 Docker 簡介](docker/introduction.md)。

## <a name="runtime-libraries"></a>執行時間程式庫

.NET 有一組廣泛的標準類別庫。 核心集稱為「基類庫」（base class library）， (BCL) 。 完整的集合稱為執行時間程式庫或 framework 程式庫。 這些程式庫提供許多一般用途和工作負載特定類型和公用程式功能的實作為。

以下是執行時間程式庫中定義的一些類型範例：

* 基本類型，例如 <xref:System.Boolean?displayProperty=nameWithType> 和 <xref:System.Int32?displayProperty=nameWithType> 。
* 集合，例如 <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> 及 <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>。
* 資料類型，例如 <xref:System.Data.DataSet?displayProperty=nameWithType> 和 <xref:System.Data.DataTable?displayProperty=nameWithType> 。
* 網路公用程式類型，例如 <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> 。
* 檔案[和資料流程 i/o](../standard/io/index.md)公用程式類型，例如 <xref:System.IO.FileStream?displayProperty=nameWithType> 和 <xref:System.IO.TextWriter?displayProperty=nameWithType> 。
* [序列化](../standard/serialization/index.md) 公用程式類型，例如 <xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> 和 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> 。
* 高效能類型，例如 <xref:System.Span%601?displayProperty=nameWithType> 、 <xref:System.Numerics.Vector?displayProperty=nameWithType> 和 [管線](../standard/io/pipelines.md)。

如需詳細資訊，請參閱 [架構](../standard/framework-libraries.md) 程式庫和連結 [庫的原始程式碼](https://github.com/dotnet/runtime/tree/master/src/libraries)。

## <a name="microsoftextensions-libraries"></a>Microsoft Extensions 程式庫

某些常用應用程式功能的程式庫不包含在執行時間程式庫中，但可在 NuGet 套件中使用，如下所示：

| Nuget 套件 | 文件 |
|---------|---------|
| [Microsoft.Extensions.Hosting](https://www.nuget.org/packages/Microsoft.Extensions.Hosting) | [應用程式存留期管理 (一般主機) ](extensions/generic-host.md) |
| [DependencyInjection](https://www.nuget.org/packages/Microsoft.Extensions.DependencyInjection) | [相依性插入 (DI)](extensions/dependency-injection.md)
| [Microsoft.Extensions.Configuration](https://www.nuget.org/packages/Microsoft.Extensions.Configuration) | [設定](extensions/configuration.md) |
| [Microsoft.Extensions.Logging](https://www.nuget.org/packages/Microsoft.Extensions.Logging) | [Logging](extensions/logging.md) |
| [Microsoft. Extensions. 選項](https://www.nuget.org/packages/Microsoft.Extensions.Options) | [選項模式](extensions/options.md) |

如需詳細資訊，請參閱 [GitHub 上的 dotnet/extensions 存放庫](https://github.com/dotnet/extensions)。

## <a name="data-access"></a>資料存取

.NET 提供物件/關聯式對應程式 (ORM) 以及在程式碼中撰寫 SQL 查詢的方式。

### <a name="entity-framework-core"></a>Entity Framework Core

Entity Framework (EF) Core 是一個 [開放原始](https://github.com/aspnet/EntityFrameworkCore) 碼和跨平臺的資料存取技術，可作為 ORM。 EF Core 可讓您在程式碼中參考 .NET 物件來處理資料庫。 它可減少您需要撰寫和測試的資料存取程式碼數量。 EF Core 支援許多資料庫引擎。

如需詳細資訊，請參閱 [Entity Framework Core](/ef/core/) 和 [資料庫提供者](/ef/core/providers/)。

### <a name="linq"></a>LINQ

語言整合式查詢 (LINQ) 可讓您撰寫用來運算元據的宣告式程式碼。 資料可以是許多形式 (例如記憶體內部物件、SQL 資料庫或 XML 文件)，但您撰寫的 LINQ 程式碼在資料來源方面通常大同小異。

如需詳細資訊，請參閱 [LINQ (語言整合式查詢) 總覽](../standard/linq/index.md)。

## <a name="net-terminology"></a>.NET 術語

若要瞭解 .NET 檔，可協助您瞭解某些詞彙的使用方式如何隨時間而改變。

### <a name="net-core-and-net-5"></a>.NET Core 和 .NET 5

在2002中，Microsoft 發行了 [.NET Framework](../framework/get-started/overview.md)，這是用來建立 Windows 應用程式的開發平臺。 今天 .NET Framework 是4.8 版，而且 Microsoft 仍 [支援](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework)此版本。

在2014中，Microsoft 開始撰寫 .NET Framework 的跨平臺開放原始碼後續工作。 這項新的 .NET 實名為 .NET Core，直到它到達3.1 版為止。 .NET Core 3.1 之後的下一個版本是 .NET 5.0，目前為預覽狀態。 已略過第4版，以避免這種 .NET 的執行與 .NET Framework 4.8 的混淆。 已捨棄名稱 "Core"，以確定這現在是 .NET 的主要執行。

這篇文章是關於 .NET 5，但 .NET 5 的大部分檔仍有 ".NET Core" 或 ".NET Framework" 的參考。 此外，"Core" 會保留在名稱 [ASP.NET Core](/aspnet/core/) 和 [Entity Framework Core](/ef/core/)。

檔也會參考 .NET Standard。 [.NET Standard](../standard/net-standard.md)是一種 API 規格，可讓您開發適用于多個 .net 的類別庫。

如需詳細資訊，請參閱 [.net 架構元件](../standard/components.md)。

### <a name="overloaded-terms"></a>多載詞彙

適用于 .NET 的部分術語可能會造成混淆，因為相同的單字在不同的內容中使用不同的方式。 以下是一些比較顯著的實例：

* **執行階段**

  |Context  |「執行時間」表示 |
  |---------|---------|
  | [Common Language Runtime (CLR)](#clr)| 受管理程式的執行環境。 作業系統是執行時間環境的一部分，但不是 .NET 執行時間的一部分。 |
  | [.NET 下載頁面上的 .NET 執行時間](https://dotnet.microsoft.com/download/dotnet-core) | [CLR](#clr)與執行時間連結[庫](#runtime-libraries)，兩者共同提供執行[架構相依](#deployment-models)應用程式的支援。 此頁面也提供 ASP.NET Core server 應用程式和 Windows 桌面應用程式的執行時間選項。 |
  | [ (RID) 的執行時間識別碼 ](rid-catalog.md) | .NET 應用程式執行所在的 OS 平臺和 CPU 架構。 例如： Windows x64、Linux x64。 |

* **框架**

  |Context  | "framework" 意義 |
  |---------|---------------------|
  | .NET Framework | .NET 的原始、僅限 Windows 的實作為。 "Framework" 為大寫。 |
  | Target Framework - 目標 Framework | .NET 應用程式或程式庫依賴的 API 集合。 範例： .NET Core 3.1、.NET Standard 2。0 |
  | Target Framework Moniker (TFM)  | TFM 是標準化的權杖格式，用於指定 .NET 應用程式或程式庫的目標 framework。 範例： `net462` 適用于 .NET Framework 4.6.2。 |
  | 與 framework 相依的應用程式 | 只能在您從 [.net 下載頁面](https://dotnet.microsoft.com/download/dotnet-core)安裝執行時間的電腦上執行的應用程式。 此使用方式中的「架構」與您從 .NET 下載頁面下載的「執行時間」相同。 |
  
* **SDK**

  |Context  | "SDK" 意義 |
  |---------|---------------|
  | [.NET 下載頁面上的 SDK](#sdk-and-runtimes)  | 您下載並安裝以開發和執行 .NET 應用程式的工具和程式庫集合。 包括 CLI、MSBuild、.NET 執行時間和其他元件。|
  | [SDK 樣式專案](#project-system-and-msbuild) | 一組 MSBuild 目標和工作，可指定如何建立特定應用程式類型的專案。 此概念中的 SDK 是使用 `Sdk` 專案檔中專案的屬性所指定 `Project` 。 |

* **平台**

  |Context  | 「平臺」意義 |
  |---------|--------------------|
  | 跨平臺 | 在此詞彙中，「平臺」表示作業系統和其執行所在的硬體，例如 Windows、macOS、Linux、iOS 和 Android。 |
  | .NET 平臺 | 使用方式會有所不同。 參考可能是一種 .NET (的執行，例如 .NET Framework 或 .NET 5) 或 .NET 的整體概念，包括所有的實作為。 |

如需 .NET 術語的詳細資訊，請參閱 [.net 詞彙](../standard/glossary.md)。

## <a name="advanced-scenarios"></a>進階案例

下列各節說明一些適用于先進案例的 .NET 功能。

### <a name="native-interop"></a>原生 interop

每個作業系統都包含提供系統服務的應用程式開發介面 (API)。 .NET 提供幾種方式來呼叫這些 API。

與原生 Api 交互操作的主要方式是透過「平台叫用」或 P/Invoke （短）。 Linux 和 Windows 平臺之間支援 P/Invoke。 僅限 Windows 的交互操作方法稱為「COM interop」，可搭配 managed 程式碼中的 [COM 元件](/cpp/atl/introduction-to-com) 使用。 它是以 P/Invoke 基礎結構為建置基礎，但運作方式稍有不同。

如需詳細資訊，請參閱 [原生互通性](../standard/native-interop/index.md)。

### <a name="unsafe-code"></a>Unsafe 程式碼

CLR 可讓您根據語言支援透過 `unsafe` 程式碼存取原生記憶體及執行指標算術。 特定演算法和系統互通性需要這些作業。 雖然功能強大，但不建議使用 unsafe 程式碼，除非它必須與系統 Api 互通，或執行最有效率的演算法。 Unsafe 程式碼在不同的環境中執行時可能不盡相同，而且也會失去記憶體回收行程和型別安全的好處。 建議您盡可能限制和集中使用 Unsafe 程式碼，並徹底測試該程式碼。

如需詳細資訊，請參閱 [Unsafe 程式碼和指標](../csharp/programming-guide/unsafe-code-pointers/index.md)。

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
> [選擇 .NET 教學課程](tutorials/index.md)

> [!div class="nextstepaction"]
> [在您的瀏覽器中嘗試 .NET](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml)

> [!div class="nextstepaction"]
> [流覽 C#](../csharp/tour-of-csharp/index.md)

> [!div class="nextstepaction"]
> [流覽 F#](../fsharp/tour.md)
