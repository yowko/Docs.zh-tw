---
title: 應用程式發佈
description: 瞭解發佈 .NET Core 應用程式的方式。 .NET Core 可以發佈平臺特定或跨平臺應用程式。 您可以將應用程式發佈為獨立或與 framework 相依的應用程式。 每個模式都會影響使用者執行您應用程式的方式。
ms.date: 04/01/2020
ms.openlocfilehash: f343e184a7ccca66aaf94533b2d0262478f873f4
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656582"
---
# <a name="net-core-application-publishing-overview"></a>.NET Core 應用程式發行總覽

您使用 .NET Core 建立的應用程式可以在兩種不同的模式下發行，而此模式會影響使用者執行您應用程式的方式。

將您的應用程式發佈為 *獨立* 應用程式時，會產生包含 .net Core 執行時間和程式庫的應用程式，以及您的應用程式及其相依性。 應用程式的使用者可以在未安裝 .NET Core 執行時間的電腦上執行它。

將您的應用程式發佈為與 *framework 相依* 的專案，會產生只包含應用程式本身及其相依性的應用程式。 應用程式的使用者必須分別安裝 .NET Core 執行時間。

這兩種發行模式預設都會產生平臺特定的可執行檔。 您可以建立不含可執行檔的 Framework 相依應用程式，而這些應用程式會跨平臺。

當產生可執行檔時，您可以使用執行時間識別碼 (RID) 來指定目標平臺。 如需有關 Rid 的詳細資訊，請參閱 [.Net CORE RID 目錄](../rid-catalog.md)。

下表概述每個 SDK 版本用來將應用程式發佈為架構相依或獨立的命令：

| 類型                                                                                     | SDK 2.1 | SDK 3。x | Command |
| ---------------------------------------------------------------------------------------  | ------- | ------- | ------- |
| 適用于目前平臺的[framework 相依可執行檔](#publish-framework-dependent)。 |         | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |
| 特定平臺的[framework 相依可執行檔](#publish-framework-dependent)。  |         | ✔️      | [`dotnet publish -r <RID> --self-contained false`](../tools/dotnet-publish.md) |
| [framework 相依的跨平臺二進位](#publish-framework-dependent)檔。               | ✔️      | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |
| [獨立可執行檔](#publish-self-contained)。                                    | ✔️      | ✔️      | [`dotnet publish -r <RID>`](../tools/dotnet-publish.md) |

如需詳細資訊，請參閱 [.Net Core dotnet publish 命令](../tools/dotnet-publish.md)。

## <a name="produce-an-executable"></a>產生可執行檔

可執行檔不是跨平臺。 它們是專屬於作業系統和 CPU 架構所特有。 當您發行應用程式並建立可執行檔時，您可以將應用程式發佈為 [獨立](#publish-self-contained) 或與 [framework 相依](#publish-framework-dependent)的應用程式。 將應用程式發佈為獨立應用程式時，會包含 .NET Core 執行時間與應用程式，而應用程式的使用者在執行應用程式之前，不需要擔心安裝 .NET Core。 發佈為與 framework 相依的應用程式不包含 .NET Core 執行時間和程式庫;只會包含應用程式和協力廠商相依性。

下列命令會產生可執行檔：

| 類型                                                                                     | SDK 2.1 | SDK 3。x | Command |
| ---------------------------------------------------------------------------------------- | ------- | ------- | ------- |
| 適用于目前平臺的[framework 相依可執行檔](#publish-framework-dependent)。 |         | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |
| 特定平臺的[framework 相依可執行檔](#publish-framework-dependent)。  |         | ✔️      | [`dotnet publish -r <RID> --self-contained false`](../tools/dotnet-publish.md) |
| [獨立可執行檔](#publish-self-contained)。                                    | ✔️      | ✔️      | [`dotnet publish -r <RID>`](../tools/dotnet-publish.md) |

## <a name="produce-a-cross-platform-binary"></a>產生跨平臺二進位檔

當您將應用程式發佈為與 [framework 相依](#publish-framework-dependent)的應用程式時，會建立跨平臺二進位檔（以 *dll* 檔案的形式）。 *Dll*檔案會以您的專案命名。 例如，如果您有一個名為 **word_reader**的應用程式，則會建立名為 *word_reader.dll* 的檔案。 以這種方式發佈的應用程式會使用 `dotnet <filename.dll>` 命令執行，而且可以在任何平臺上執行。

只要已安裝目標 .NET Core 執行時間，就可以在任何作業系統上執行跨平臺二進位檔。 如果未安裝目標 .NET Core 執行時間，應用程式可以使用較新的執行時間執行（如果應用程式設定為向前復原）。 如需詳細資訊，請參閱 [與 framework 相依的應用程式向前](../versions/selection.md#framework-dependent-apps-roll-forward)復原。

下列命令會產生跨平臺二進位檔：

| 類型                                                                                 | SDK 2.1 | SDK 3。x | Command |
| -----------------------------------------------------------------------------------  | ------- | ------- | ------- |
| [framework 相依的跨平臺二進位](#publish-framework-dependent)檔。           | ✔️      | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |

## <a name="publish-framework-dependent"></a>發佈 framework 相依

發佈為與 framework 相依的應用程式是跨平臺，不包含 .NET Core 執行時間。 您應用程式的使用者必須安裝 .NET Core 執行時間。

將應用程式發佈為與 framework 相依的應用程式，會產生 [跨平臺二進位](#produce-a-cross-platform-binary) 檔做為 *dll* 檔案，以及以您目前平臺為目標的 [平臺特定可執行](#produce-an-executable) 檔。 *Dll*是跨平臺，而可執行檔則不是。 例如，如果您發行名為**word_reader**和目標 Windows 的應用程式，則會隨著*word_reader.dll*建立*word_reader.exe*可執行檔。 以 Linux 或 macOS 為目標時，會建立 *word_reader* 可執行檔以及 *word_reader.dll*。 如需有關 Rid 的詳細資訊，請參閱 [.Net CORE RID 目錄](../rid-catalog.md)。

> [!IMPORTANT]
> 當您發佈與應用程式架構相依的應用程式時，.NET Core SDK 2.1 不會產生平臺特定的可執行檔。

您可以使用命令來執行應用程式的跨平臺二進位檔 `dotnet <filename.dll>` ，並可在任何平臺上執行。 如果應用程式使用的 NuGet 套件具有平臺特定的執行，則所有平臺的相依性都會連同應用程式一起複製到 [發佈] 資料夾。

您可以藉由將參數傳遞至命令，為特定平臺建立可執行檔 `-r <RID> --self-contained false` [`dotnet publish`](../tools/dotnet-publish.md) 。 如果 `-r` 省略此參數，就會為您目前的平臺建立可執行檔。 任何具有目標平臺之平臺特定相依性的 NuGet 套件都會複製到 [發佈] 資料夾。

### <a name="advantages"></a>優點

- **小規模部署**\
只會發佈您的應用程式及其相依性。 使用者會安裝 .NET Core 執行時間和程式庫，而且所有應用程式會共用執行時間。

- **跨平臺**\
您的應用程式和任何。以網路為基礎的程式庫會在其他作業系統上執行。 您不需要為您的應用程式定義目標平臺。 如需 .NET 檔案格式的詳細資訊，請參閱 [.Net 元件檔案格式](../../standard/assembly/file-format.md)。

- **使用最新的修補執行時間**\
應用程式會使用最新的執行時間 (在目標系統上安裝之 .NET Core 的目標主要核心) 內。 這表示您的應用程式會自動使用 .NET Core 執行時間的最新修補版本。 您可以覆寫這個預設行為。 如需詳細資訊，請參閱 [與 framework 相依的應用程式向前](../versions/selection.md#framework-dependent-apps-roll-forward)復原。

### <a name="disadvantages"></a>缺點

- **需要預先安裝執行時間**\
只有當應用程式的目標 .NET Core 版本已安裝在主機系統上時，您的應用程式才能執行。 您可以將應用程式的向前復原行為設定為需要特定版本的 .NET Core，或允許較新版本的 .NET Core。 如需詳細資訊，請參閱 [與 framework 相依的應用程式向前](../versions/selection.md#framework-dependent-apps-roll-forward)復原。

- **.NET Core 可能會變更**\
您可以在執行應用程式的電腦上更新 .NET Core 執行時間和程式庫。 在罕見的情況下，如果您使用的是大部分應用程式所使用的 .NET Core 程式庫，這可能會變更您的應用程式行為。 您可以設定應用程式如何使用較新版本的 .NET Core。 如需詳細資訊，請參閱 [與 framework 相依的應用程式向前](../versions/selection.md#framework-dependent-apps-roll-forward)復原。

下列缺點僅適用于 .NET Core 2.1 SDK。

- **使用 `dotnet` 命令來啟動應用程式**\
使用者必須執行 `dotnet <filename.dll>` 命令以啟動您的應用程式。 .NET Core 2.1 SDK 不會針對已發佈 framework 相依的應用程式，產生平臺特定的可執行檔。

### <a name="examples"></a>範例

發佈跨平臺架構相依的應用程式。 以目前平臺為目標的可執行檔會與 *dll* 檔案一起建立。

```dotnet
dotnet publish
```

發佈跨平臺架構相依的應用程式。 Linux 64 位可執行檔會與 *dll* 檔案一起建立。 此命令不適用於 .NET Core SDK 2.1。

```dotnet
dotnet publish -r linux-x64 --self-contained false
```

## <a name="publish-self-contained"></a>獨立發行

將您的應用程式發佈為獨立應用程式，會產生平臺特定的可執行檔。 輸出發行資料夾包含應用程式的所有元件，包括 .NET Core 程式庫和目標執行時間。 應用程式會與其他 .NET Core 應用程式隔離，而且不會使用本機安裝的共用執行時間。 您應用程式的使用者不需要下載和安裝 .NET Core。

針對指定的目標平臺產生可執行檔二進位檔。 例如，如果您有一個名為 **word_reader**的應用程式，而且您發行了 Windows 的獨立可執行檔，則會建立 *word_reader.exe* 檔。 針對 Linux 或 macOS 發行，會建立 *word_reader* 檔案。 使用命令的參數指定目標平臺和架構 `-r <RID>` [`dotnet publish`](../tools/dotnet-publish.md) 。 如需有關 Rid 的詳細資訊，請參閱 [.Net CORE RID 目錄](../rid-catalog.md)。

如果應用程式具有平臺特定的相依性（例如包含平臺特定相依性的 NuGet 套件），則會將這些相依性連同應用程式一起複製到 [發佈] 資料夾。

### <a name="advantages"></a>優點

- **控制 .NET Core 版本**\
您可以控制您的應用程式所部署的 .NET Core 版本。

- **平臺特定目標**\
因為您必須為每個平臺發佈您的應用程式，所以您知道應用程式將執行的位置。 如果 .NET Core 引進新平臺，使用者將無法在該平臺上執行您的應用程式，除非您發行以該平臺為目標的版本。 您可以在使用者于新的平臺上執行應用程式之前，先測試應用程式的相容性問題。

### <a name="disadvantages"></a>缺點

- **較大型的部署**\
因為您的應用程式包含 .NET Core 執行時間和您所有的應用程式相依性，所以需要的下載大小和硬碟空間大於 [framework 相依](#publish-framework-dependent) 的版本。

  > [!TIP]
  > 您可以使用 .NET Core [*全球化*](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md)非變異模式，將 Linux 系統上的部署大小減少約 28 MB。 這會強制您的應用程式將所有文化特性視為不因 [文化](xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType)特性而異。

  > [!TIP]
  > 有一 [項預覽修剪功能](trim-self-contained.md) 可進一步減少部署的大小。

- **較難更新 .NET Core 版本**\
.NET Core 執行時間 (隨您的應用程式散發) 只能透過發行新版的應用程式來進行升級。 不過，.NET Core 會在應用程式執行所在的電腦中，視需要更新架構程式庫所需的重大安全性修補程式。 您必須負責進行此安全性修補程式案例的端對端驗證。

### <a name="examples"></a>範例

發行獨立應用程式。 建立 macOS 64 位可執行檔。

```dotnet
dotnet publish -r osx-x64
```

發行獨立應用程式。 建立 Windows 64 位可執行檔。

```dotnet
dotnet publish -r win-x64
```

## <a name="see-also"></a>請參閱

- [使用 .NET Core CLI 部署 .NET Core 應用程式。](deploy-with-cli.md)
- [使用 Visual Studio 部署 .NET Core 應用程式。](deploy-with-vs.md)
- [.NET Core 執行時間識別碼 (RID) 目錄。](../rid-catalog.md)
- [選取要使用的 .NET Core 版本。](../versions/selection.md)
