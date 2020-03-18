---
title: 應用程式發佈
description: 瞭解發佈 .NET Core 應用程式的方法。 .NET Core 可以發佈特定于平臺的應用或跨平臺應用。 您可以將應用發佈為自包含或與運行時相關。 每種模式都會影響使用者如何運行你的應用。
ms.date: 01/31/2020
ms.openlocfilehash: 3b9c3b7f29af12477874b7a31ef0de4750719de0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399060"
---
# <a name="net-core-application-publishing-overview"></a>.NET 核心應用程式發佈概述

使用 .NET Core 創建的應用程式可以在兩種不同的模式下發布，該模式會影響使用者運行應用的方式。

將應用發佈為*自包含*將生成一個應用程式，其中包含 .NET Core 運行時和庫以及應用程式及其依賴項。 應用程式的使用者可以在未安裝 .NET Core 運行時的電腦上運行它。

將應用發佈為*依賴于運行時*將生成僅包含應用程式本身及其依賴項的應用程式。 應用程式的使用者必須單獨安裝 .NET Core 運行時。

預設情況下，這兩種發佈模式都會生成特定于平臺的可執行檔。 無需可執行檔即可創建與運行時相關的應用程式，並且這些應用程式是跨平臺的。

生成可執行檔時，可以使用運行時識別碼 （RID） 指定目標平臺。 有關 RID 的詳細資訊，請參閱[.NET 核心 RID 目錄](../rid-catalog.md)。

下表概述了用於發佈應用為基於運行時或自包含的應用程式的命令，每個 SDK 版本：

| 類型                                                                                 | SDK 2.1 | SDK 3.x | Command |
| -----------------------------------------------------------------------------------  | ------- | ------- | ------- |
| 當前平臺[的運行時相關可執行檔](#publish-runtime-dependent)。 |         | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |
| 特定平臺[的與運行時相關的可執行檔](#publish-runtime-dependent)。  |         | ✔️      | [`dotnet publish -r <RID> --self-contained false`](../tools/dotnet-publish.md) |
| [與運行時相關的跨平臺二進位檔案](#publish-runtime-dependent)。               | ✔️      | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |
| [自包含可執行檔](#publish-self-contained)。                                | ✔️      | ✔️      | [`dotnet publish -r <RID>`](../tools/dotnet-publish.md) |

有關詳細資訊，請參閱[.NET 核心點網發佈命令](../tools/dotnet-publish.md)。

## <a name="produce-an-executable"></a>生成可執行檔

可執行檔不是跨平臺的。 它們特定于作業系統和 CPU 體系結構。 發佈應用並創建可執行檔時，可以將應用發佈為[自包含](#publish-self-contained)或[依賴于運行時](#publish-runtime-dependent)。 將應用發佈為自包含包括帶有應用的 .NET Core 運行時，應用使用者在運行應用之前不必擔心安裝 .NET Core。 發佈為與運行時相關的應用不包括 .NET Core 運行時和庫;因此，應用將包含 .NET Core 運行時和庫。僅包括應用和協力廠商依賴項。

以下命令生成可執行檔：

| 類型                                                                                 | SDK 2.1 | SDK 3.x | Command |
| ------------------------------------------------------------------------------------ | ------- | ------- | ------- |
| 當前平臺[的運行時相關可執行檔](#publish-runtime-dependent)。 |         | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |
| 特定平臺[的與運行時相關的可執行檔](#publish-runtime-dependent)。  |         | ✔️      | [`dotnet publish -r <RID> --self-contained false`](../tools/dotnet-publish.md) |
| [自包含可執行檔](#publish-self-contained)。                                | ✔️      | ✔️      | [`dotnet publish -r <RID>`](../tools/dotnet-publish.md) |

## <a name="produce-a-cross-platform-binary"></a>生成跨平臺二進位

當您以*dll*檔的形式將應用發佈為[依賴于運行時](#publish-runtime-dependent)的時，將創建跨平臺二進位檔案。 *dll*檔以專案命名。 例如，如果您有一個名為**word_reader**的應用，則將創建名為*word_reader.dll*的檔。 以這種方式發佈的應用使用 命令運行，`dotnet <filename.dll>`可以在任何平臺上運行。

只要已安裝目標 .NET Core 運行時，就可以在任何作業系統上運行跨平臺二進位檔案。 如果未安裝目標 .NET Core 運行時，則如果應用配置為向前滾動，則應用可能會使用較新的運行時運行。 有關詳細資訊，請參閱[與運行時相關的應用向前滾動](../versions/selection.md#framework-dependent-apps-roll-forward)。

以下命令生成跨平臺二進位檔案：

| 類型                                                                                 | SDK 2.1 | SDK 3.x | Command |
| -----------------------------------------------------------------------------------  | ------- | ------- | ------- |
| [與運行時相關的跨平臺二進位檔案](#publish-runtime-dependent)。               | ✔️      | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |

## <a name="publish-runtime-dependent"></a>發佈與運行時相關的發佈

發佈為依賴于運行時的應用是跨平臺的，不包括 .NET Core 運行時。 應用的使用者需要安裝 .NET Core 運行時。

將應用發佈為與運行時相關的應用將生成[跨平臺二進位檔案](#produce-a-cross-platform-binary)作為*dll*檔，以及針對當前平臺[的平臺特定可執行檔](#produce-an-executable)。 *dll*是跨平臺的，而可執行檔不是。 例如，如果發佈名為**word_reader**和目標 Windows 的應用，則將創建*word_reader.exe*可執行檔以及*word_reader.dll*。 當目標 Linux 或 macOS 時，將*word_reader.dll*一起創建*word_reader*可執行檔。 有關 RID 的詳細資訊，請參閱[.NET 核心 RID 目錄](../rid-catalog.md)。

> [!IMPORTANT]
> .NET Core SDK 2.1 在發佈依賴于應用運行時時不會生成特定于平臺的可執行檔。

應用的跨平臺二進位檔案可以使用 命令`dotnet <filename.dll>`運行，並且可以在任何平臺上運行。 如果應用使用的 NuGet 包具有特定于平臺的實現，則所有平臺的依賴項都將隨應用一起複製到發佈資料夾。

通過將參數傳遞給`-r <RID> --self-contained false`[`dotnet publish`](../tools/dotnet-publish.md)命令，可以為特定平臺創建可執行檔。 省略參數`-r`時，將為您的當前平臺創建一個可執行檔。 任何具有目標平臺特定于平臺的依賴項的任何 NuGet 包都將複製到發佈資料夾。

### <a name="advantages"></a>優點

- **小型部署**\
僅分發你的應用及其依賴項。 .NET Core 運行時和庫由使用者安裝，所有應用共用運行時。

- **跨平臺**\
你的應用和任何 。基於 NET 的庫在其他作業系統上運行。 您無需為應用定義目標平臺。 有關 .NET 檔案格式的資訊，請參閱[.NET 程式集檔案格式](../../standard/assembly/file-format.md)。

- **使用最新的修補運行時**\
該應用程式使用目標系統上安裝的最新運行時（在目標系統上安裝的目標主要次要類型 .NET Core）。 這意味著你的應用會自動使用 .NET Core 運行時的最新修補版本。 可以重寫此預設行為。 有關詳細資訊，請參閱[與運行時相關的應用向前滾動](../versions/selection.md#framework-dependent-apps-roll-forward)。

### <a name="disadvantages"></a>缺點

- **需要預先安裝運行時**\
僅當應用目標 .NET Core 的版本已在主機系統上安裝時，你的應用才能運行。 您可以為應用配置滾向行為，以需要 .NET Core 的特定版本或允許較新版本的 .NET Core。 有關詳細資訊，請參閱[與運行時相關的應用向前滾動](../versions/selection.md#framework-dependent-apps-roll-forward)。

- **.NET 核心可能更改**\
.NET Core 運行時和庫可以在運行應用的電腦上更新。 在極少數情況下，如果您使用 .NET Core 庫，這可能會更改應用的行為，大多數應用都這樣做。 您可以配置應用如何使用較新版本的 .NET Core。 有關詳細資訊，請參閱[與運行時相關的應用向前滾動](../versions/selection.md#framework-dependent-apps-roll-forward)。

以下缺點僅適用于 .NET 核心 2.1 SDK。

- **使用`dotnet`命令啟動應用**\
使用者必須運行該`dotnet <filename.dll>`命令才能啟動應用。 .NET Core 2.1 SDK 不會為發佈的依賴于運行時的應用生成特定于平臺的可執行檔。

### <a name="examples"></a>範例

發佈與應用跨平臺運行時相關的應用。 與*dll*檔一起創建針對當前平臺的可執行檔。

```dotnet
dotnet publish
```

發佈與應用跨平臺運行時相關的應用。 與*dll*檔一起創建 Linux 64 位可執行檔。 此命令與 .NET 核心 SDK 2.1 不起作用。

```dotnet
dotnet publish -r linux-x64 --self-contained false
```

## <a name="publish-self-contained"></a>發佈自包含

將應用發佈為自包含將會產生特定于平臺的可執行檔。 輸出發佈資料夾包含應用的所有元件，包括 .NET Core 庫和目標運行時。 該應用與其他 .NET Core 應用隔離，不使用本地安裝的共用運行時。 不需要應用的使用者下載和安裝 .NET Core。

可執行二進位檔案是為指定的目標平臺生成的。 例如，如果您有名為**word_reader**的應用，並且為 Windows 發佈了自包含可執行檔，則將創建*word_reader.exe*檔。 為 Linux 或 macOS 發佈，將創建*word_reader*檔。 目標平臺和體系結構使用`-r <RID>`[`dotnet publish`](../tools/dotnet-publish.md)命令的參數指定。 有關 RID 的詳細資訊，請參閱[.NET 核心 RID 目錄](../rid-catalog.md)。

如果應用具有特定于平臺的依賴項（如包含特定于平臺的依賴項的 NuGet 包），則這些依賴項將與應用一起複製到發佈資料夾。

### <a name="advantages"></a>優點

- **控制 .NET 核心版本**\
您可以控制隨應用一起部署 .NET Core 的哪個版本。

- **特定于平臺的目標**\
由於您必須為每個平臺發佈應用，因此知道應用將運行在何處。 如果 .NET Core 引入了一個新平臺，則在發佈面向該平臺的版本之前，使用者無法在該平臺上運行你的應用。 您可以在使用者在新平臺上運行應用之前測試應用的相容性問題。

### <a name="disadvantages"></a>缺點

- **更大的部署**\
由於你的應用包括 .NET Core 運行時和所有應用依賴項，因此所需的下載大小和硬碟空間大於[與運行時相關的](#publish-runtime-dependent)版本。

  > [!TIP]
  > 通過使用 .NET Core[*全球化不變模式*](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md)，您可以將在 Linux 系統上的部署大小減小了大約 28 MB。 這強制你的應用程式對待所有區域性，如[不變文化](xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType)。

- **更難更新 .NET 核心版本**\
.NET 核心運行時（隨應用一起分發）只能通過發佈應用的新版本進行升級。 您負責向 .NET 核心運行時提供應用程式的安全修補程式的更新版本。

### <a name="examples"></a>範例

發佈自包含的應用。 將創建 macOS 64 位可執行檔。

```dotnet
dotnet publish -r osx-x64
```

發佈自包含的應用。 將創建 Windows 64 位可執行檔。

```dotnet
dotnet publish -r win-x64
```

## <a name="see-also"></a>另請參閱

- [使用 .NET 核心 CLI 部署 .NET 核心應用。](deploy-with-cli.md)
- [使用視覺化工作室部署 .NET 核心應用。](deploy-with-vs.md)
- [包、元包和框架。](../packages.md)
- [.NET 核心運行時標識器 （RID） 目錄。](../rid-catalog.md)
- [選擇要使用的 .NET 核心版本。](../versions/selection.md)
