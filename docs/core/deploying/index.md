---
title: 應用程式發行
description: 瞭解發行 .NET Core 應用程式的方式。 .NET Core 可以發佈平臺特定或跨平臺應用程式。 您可以將應用程式發佈為獨立或與執行時間相關聯。 每個模式都會影響使用者執行應用程式的方式。
ms.date: 04/01/2020
ms.openlocfilehash: 201363ad314373ec3be44eb8496f92a8e0c8e418
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164940"
---
# <a name="net-core-application-publishing-overview"></a>.NET Core 應用程式發行總覽

您使用 .NET Core 建立的應用程式可以在兩種不同的模式下發行，而此模式會影響使用者執行應用程式的方式。

將您的應用程式發佈為獨立式，*會產生一個*應用程式，其中包含 .net Core 執行時間和程式庫，以及您的應用程式及其相依性。 應用程式的使用者可以在未安裝 .NET Core 執行時間的電腦上執行它。

將您的應用程式發佈為與*執行時間相依*（先前稱為*framework 相依*）時，會產生僅包含應用程式本身和其相依性的應用程式。 應用程式的使用者必須分別安裝 .NET Core 執行時間。

這兩種發行模式預設都會產生平臺特定的可執行檔。 執行時間相依的應用程式可以在沒有可執行檔的情況下建立，而且這些應用程式會跨平臺。

當可執行檔產生時，您可以使用執行時間識別碼（RID）來指定目標平臺。 如需有關 Rid 的詳細資訊，請參閱[.Net CORE RID 目錄](../rid-catalog.md)。

下表概述用來將應用程式發佈為執行時間相依或獨立、每個 SDK 版本的命令：

| 類型                                                                                 | SDK 2.1 | SDK 3。x | Command |
| -----------------------------------------------------------------------------------  | ------- | ------- | ------- |
| 目前平臺的[執行時間相依可執行檔](#publish-runtime-dependent)。 |         | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |
| 特定平臺的[執行時間相依可執行檔](#publish-runtime-dependent)。  |         | ✔️      | [`dotnet publish -r <RID> --self-contained false`](../tools/dotnet-publish.md) |
| [執行時間相依的跨平臺二進位](#publish-runtime-dependent)檔。               | ✔️      | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |
| [獨立的可執行檔](#publish-self-contained)。                                | ✔️      | ✔️      | [`dotnet publish -r <RID>`](../tools/dotnet-publish.md) |

如需詳細資訊，請參閱[.Net Core dotnet publish 命令](../tools/dotnet-publish.md)。

## <a name="produce-an-executable"></a>產生可執行檔

可執行檔不是跨平臺。 它們是作業系統和 CPU 架構的特定。 發佈您的應用程式並建立可執行檔時，您可以將應用程式發佈為[獨立](#publish-self-contained)或[執行時間相依](#publish-runtime-dependent)。 以獨立方式發行應用程式包含應用程式的 .NET Core 執行時間，而應用程式的使用者在執行應用程式之前，不必擔心安裝 .NET Core。 發佈為執行時間相依的應用程式不包含 .NET Core 執行時間和程式庫;只包含應用程式和協力廠商相依性。

下列命令會產生可執行檔：

| 類型                                                                                 | SDK 2.1 | SDK 3。x | Command |
| ------------------------------------------------------------------------------------ | ------- | ------- | ------- |
| 目前平臺的[執行時間相依可執行檔](#publish-runtime-dependent)。 |         | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |
| 特定平臺的[執行時間相依可執行檔](#publish-runtime-dependent)。  |         | ✔️      | [`dotnet publish -r <RID> --self-contained false`](../tools/dotnet-publish.md) |
| [獨立的可執行檔](#publish-self-contained)。                                | ✔️      | ✔️      | [`dotnet publish -r <RID>`](../tools/dotnet-publish.md) |

## <a name="produce-a-cross-platform-binary"></a>產生跨平臺二進位檔

當您將應用程式發佈為與[執行時間相依](#publish-runtime-dependent)時，會以*dll*檔案的形式來建立跨平臺二進位檔。 *Dll*檔案會在您的專案之後命名。 例如，如果您有名為**word_reader**的應用程式，則會建立名為*word_reader.dll*的檔案。 以這種方式發佈的應用程式會使用 `dotnet <filename.dll>` 命令執行，而且可以在任何平臺上執行。

只要已安裝目標 .NET Core 執行時間，就可以在任何作業系統上執行跨平臺二進位檔。 如果未安裝目標 .NET Core 執行時間，當應用程式設定為向前復原時，應用程式可能會使用較新的執行時間來執行。 如需詳細資訊，請參閱[執行時間相依應用程式向前](../versions/selection.md#framework-dependent-apps-roll-forward)復原。

下列命令會產生跨平臺二進位檔：

| 類型                                                                                 | SDK 2.1 | SDK 3。x | Command |
| -----------------------------------------------------------------------------------  | ------- | ------- | ------- |
| [執行時間相依的跨平臺二進位](#publish-runtime-dependent)檔。               | ✔️      | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |

## <a name="publish-runtime-dependent"></a>發行執行時間相依

發佈為執行時間相依的應用程式會跨平臺，且不包含 .NET Core 執行時間。 需要應用程式的使用者，才能安裝 .NET Core 執行時間。

將應用程式發佈為執行時間相依會產生[跨平臺二進位](#produce-a-cross-platform-binary)檔做為*dll*檔，以及以目前平臺為目標的[平臺特定可執行](#produce-an-executable)檔。 *Dll*為跨平臺，而可執行檔不是。 例如，如果您發行名為**word_reader**和目標 Windows 的應用程式，則會隨著*word_reader.dll*建立*word_reader.exe*可執行檔。 以 Linux 或 macOS 為目標時，會隨*word_reader.dll*建立一個*word_reader*可執行檔。 如需有關 Rid 的詳細資訊，請參閱[.Net CORE RID 目錄](../rid-catalog.md)。

> [!IMPORTANT]
> 當您發佈應用程式執行時間相依時，.NET Core SDK 2.1 不會產生平臺特定的可執行檔。

您可以使用命令來執行應用程式的跨平臺二進位檔 `dotnet <filename.dll>` ，並可在任何平臺上執行。 如果應用程式使用具有平臺特定部署的 NuGet 套件，則所有平臺的相依性會連同應用程式一起複製到 [發佈] 資料夾。

您可以藉由將參數傳遞至命令，為特定平臺建立可執行檔 `-r <RID> --self-contained false` [`dotnet publish`](../tools/dotnet-publish.md) 。 `-r`省略參數時，會為您目前的平臺建立可執行檔。 任何具有目標平臺平臺特定相依性的 NuGet 套件，都會複製到 [發行] 資料夾。

### <a name="advantages"></a>優點

- **小型部署**\
只會散發您的應用程式及其相依性。 .NET Core 執行時間和程式庫是由使用者所安裝，而所有應用程式會共用執行時間。

- **跨平臺**\
您的應用程式和任何。以網路為基礎的程式庫會在其他作業系統上執行。 您不需要定義應用程式的目標平臺。 如需 .NET 檔案格式的詳細資訊，請參閱[.Net 元件檔案格式](../../standard/assembly/file-format.md)。

- **使用最新修補的執行時間**\
應用程式會使用安裝在目標系統上的最新執行時間（在目標主要-次要 .NET Core 系列內）。 這表示您的應用程式會自動使用最新修補版本的 .NET Core 執行時間。 可以覆寫這個預設行為。 如需詳細資訊，請參閱[執行時間相依應用程式向前](../versions/selection.md#framework-dependent-apps-roll-forward)復原。

### <a name="disadvantages"></a>缺點

- **需要預先安裝執行時間**\
只有在主機系統上已安裝您的應用程式目標版本的 .NET Core 時，您的應用程式才能執行。 您可以為應用程式設定向前復原行為，以要求特定版本的 .NET Core 或允許較新版本的 .NET Core。 如需詳細資訊，請參閱[執行時間相依應用程式向前](../versions/selection.md#framework-dependent-apps-roll-forward)復原。

- **.NET Core 可能會變更**\
.NET Core 執行時間和程式庫可能會在執行應用程式的電腦上更新。 在罕見的情況下，如果您使用 .NET Core 程式庫（大部分應用程式都有這麼做），這可能會變更應用程式的行為。 您可以設定應用程式使用較新版本 .NET Core 的方式。 如需詳細資訊，請參閱[執行時間相依應用程式向前](../versions/selection.md#framework-dependent-apps-roll-forward)復原。

下列缺點僅適用于 .NET Core 2.1 SDK。

- **使用 `dotnet` 命令來啟動應用程式**\
使用者必須執行 `dotnet <filename.dll>` 命令來啟動您的應用程式。 .NET Core 2.1 SDK 不會針對發佈執行時間相依的應用程式，產生平臺特定的可執行檔。

### <a name="examples"></a>範例

發佈與跨平臺執行時間相關的應用程式。 以目前平臺為目標的可執行檔會隨著*dll*檔案一起建立。

```dotnet
dotnet publish
```

發佈與跨平臺執行時間相關的應用程式。 Linux 64 位可執行檔會與*dll*檔案一併建立。 此命令無法與 .NET Core SDK 2.1 搭配使用。

```dotnet
dotnet publish -r linux-x64 --self-contained false
```

## <a name="publish-self-contained"></a>獨立發行

以獨立方式發行應用程式會產生平臺特定的可執行檔。 輸出發佈資料夾包含應用程式的所有元件，包括 .NET Core 程式庫和目標執行時間。 應用程式與其他 .NET Core 應用程式隔離，而且不會使用本機安裝的共用執行時間。 您應用程式的使用者不需要下載和安裝 .NET Core。

針對指定的目標平臺，會產生可執行檔二進位檔。 例如，如果您有一個名為**word_reader**的應用程式，而且您發行了獨立的可執行檔，則會建立*word_reader.exe*檔案。 發行 Linux 或 macOS 時，會建立*word_reader*檔案。 使用命令的參數指定目標平臺和架構 `-r <RID>` [`dotnet publish`](../tools/dotnet-publish.md) 。 如需有關 Rid 的詳細資訊，請參閱[.Net CORE RID 目錄](../rid-catalog.md)。

如果應用程式具有平臺特定的相依性（例如包含平臺特定相依性的 NuGet 套件），則這些相依性會連同應用程式一起複製到 [發佈] 資料夾。

### <a name="advantages"></a>優點

- **控制 .NET Core 版本**\
您可以控制哪個版本的 .NET Core 會與您的應用程式一起部署。

- **平臺特定目標**\
因為您必須為每個平臺發佈您的應用程式，所以您知道應用程式的執行位置。 如果 .NET Core 引進新的平臺，則在您發行以該平臺為目標的版本之前，使用者無法在該平臺上執行您的應用程式。 您可以在使用者于新平臺上執行應用程式之前，先測試應用程式的相容性問題。

### <a name="disadvantages"></a>缺點

- **較大的部署**\
因為您的應用程式包含 .NET Core 執行時間和您所有的應用程式相依性，所以所需的下載大小和硬碟空間會大於[執行時間相關](#publish-runtime-dependent)版本。

  > [!TIP]
  > 您可以使用 .NET Core[*全球化不變模式*](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md)，減少在 Linux 系統上部署的大小約 28 MB。 這會強制您的應用程式處理所有文化特性，例如不因[文化](xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType)特性而異。

- **難以更新 .NET Core 版本**\
.NET Core 執行時間（與您的應用程式一起散發）只能透過發行新版本的應用程式來進行升級。 您必須負責提供應用程式的更新版本，以取得 .NET Core 執行時間的安全性修補程式。

### <a name="examples"></a>範例

發行獨立的應用程式。 建立 macOS 64 位可執行檔。

```dotnet
dotnet publish -r osx-x64
```

發行獨立的應用程式。 建立 Windows 64 位可執行檔。

```dotnet
dotnet publish -r win-x64
```

## <a name="see-also"></a>另請參閱

- [使用 .NET Core CLI 部署 .NET Core 應用程式。](deploy-with-cli.md)
- [使用 Visual Studio 部署 .NET Core 應用程式。](deploy-with-vs.md)
- [.NET Core 執行時間識別碼（RID）目錄。](../rid-catalog.md)
- [選取要使用的 .NET Core 版本。](../versions/selection.md)
