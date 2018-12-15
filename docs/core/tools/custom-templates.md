---
title: dotnet new 的自訂範本
description: 了解任何 .NET 專案或檔案類型的自訂範本。
author: guardrex
ms.author: mairaw
ms.date: 08/11/2017
ms.openlocfilehash: 4e5dd11df8204d86009b0ece108ef877dc54f23e
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53126259"
---
# <a name="custom-templates-for-dotnet-new"></a>dotnet new 的自訂範本

[.NET Core SDK](https://www.microsoft.com/net/download/core) 隨附許多預先安裝的範本，搭配 [`dotnet new` 命令](dotnet-new.md)一起使用。 從 .NET Core 2.0 開始，您可以建立任何專案類型的自訂範本，例如應用程式、服務、工具或類別庫。 您甚至可以建立會輸出一或多個獨立檔案的範本，例如組態檔。

您可以直接參考 NuGet *nupkg* 檔案，或指定包含範本的檔案系統目錄，從任何 NuGet 摘要的 NuGet 套件安裝自訂的範本。 範本引擎提供的功能，可讓您取代值、包含與排除檔案和檔案區域，以及在使用範本時執行自訂的處理作業。

範本引擎是開放原始碼，而線上程式碼存放庫位於 GitHub 的 [dotnet/templating](https://github.com/dotnet/templating/)。 如需範本範例，請瀏覽 [dotnet/dotnet-template-samples](https://github.com/dotnet/dotnet-template-samples) 存放庫。 GitHub 的 [Available templates for dotnet new](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new) (dotnet new 的可用範本) 中，有包括協力廠商範本在內的更多範本。 如需建立與使用自訂範本的詳細資訊，請參閱[如何建立您自己的 dotnet new 範本](https://blogs.msdn.microsoft.com/dotnet/2017/04/02/how-to-create-your-own-templates-for-dotnet-new/)以及 [dotnet/templating GitHub repo Wiki](https://github.com/dotnet/templating/wiki) (維基百科：dotnet/templating GitHub 存放庫)。

若要遵循逐步解說並建立範本，請參閱[建立 dotnet new 的自訂範本](~/docs/core/tutorials/create-custom-template.md)教學課程。

## <a name="configuration"></a>Configuration

範本是由下列元件組成：

- 來源檔案和資料夾
- 組態檔 (*template.json*)

### <a name="source-files-and-folders"></a>來源檔案和資料夾

來源檔案和資料夾包含執行 `dotnet new <TEMPLATE>` 命令時，您希望範本引擎使用的任何檔案和資料夾。 範本引擎的設計是將「可執行專案」用為原始程式碼以產生專案。 這有幾項優點：

- 範本引擎不需要您將特殊權杖插入專案的原始程式碼。
- 程式碼檔案不是特殊的檔案，也不使用範本引擎以任何方式修改。 因此，通常在處理專案時使用的工具也用來處理範本內容。
- 您會建置、執行和偵錯範本專案，就如同您對任何其他專案一樣。
- 您可以從現有的專案快速建立範本，只要將 *template.json* 組態檔新增至專案即可。

儲存在範本中的檔案和資料夾不限於正式的 .NET 專案類型，例如 .NET Core 或 .NET Framework 解決方案。 當使用範本時，來源檔案和資料夾可由任何您想要建立的內容組成，即使範本引擎只產生一個輸出檔，例如組態檔或方案檔。 例如，您可以建立包含 *web.config* 來源檔案的範本，並為已使用範本的專案建立修改過的 *web.config* 檔案。 根據您在 *template.json* 組態檔提供的邏輯和設定，以及使用者提供的值 (當成選項傳遞給 `dotnet new <TEMPLATE>` 命令)，修改來源檔案。

### <a name="templatejson"></a>template.json

*template.json* 檔案放在範本根目錄的 *.template.config* 資料夾中。 檔案向範本引擎提供組態資訊。 最小的組態需要下表顯示的成員，這即足以建立具有功能的範本。

| 成員            | 類型          | 說明 |
| ----------------- | ------------- | ----------- |
| `$schema`         | URI           | *template.json* 檔案的 JSON 結構描述。 支援 JSON 結構描述的編輯器，會在指定結構描述時，啟用 JSON 編輯功能。 例如，[Visual Studio Code](https://code.visualstudio.com/) 需要此成員才能啟用 IntelliSense。 使用 `http://json.schemastore.org/template` 的值。 |
| `author`          | 字串        | 範本的作者。 |
| `classifications` | array(string) | 搜尋範本時，使用者可能用來尋找範本的零或多個範本特性。 當它出現在使用 <code>dotnet new -l&#124;--list</code> 命令產生的範本清單中時，分類也會出現在「標記」資料行中。 |
| `identity`        | 字串        | 此範本的唯一名稱。 |
| `name`            | 字串        | 使用者應該會看到的範本名稱。 |
| `shortName`       | 字串        | 預設的速記，用於選取適用於環境的範本，在此環境中，範本名稱由使用者指定，不是透過 GUI 選取。 例如，從命令提示字元以 CLI 命令使用範本時，簡短名稱很有用。 |

#### <a name="example"></a>範例：

```json
{
  "$schema": "http://json.schemastore.org/template",
  "author": "Catalina Garcia",
  "classifications": [ "Common", "Console" ],
  "identity": "GarciaSoftware.ConsoleTemplate.CSharp",
  "name": "Garcia Software Console Application",
  "shortName": "garciaconsole"
}
```

*template.json* 檔案的完整結構描述位於 [JSON 結構描述存放區](http://json.schemastore.org/template)。

## <a name="net-default-templates"></a>.NET 預設範本

當您安裝 [.NET Core SDK](https://www.microsoft.com/net/download/core) 時，您會收到十多個用於建立專案和檔案的內建範本，包括主控台應用程式、類別庫、單元測試專案，ASP.NET Core 應用程式 (包括 [Angular](https://angular.io/) 和 [React](https://facebook.github.io/react/) 專案) 和組態檔。 若要列出內建範本，請執行 `dotnet new` 命令搭配 `-l|--list` 選項：

```console
dotnet new -l
```

## <a name="packing-a-template-into-a-nuget-package-nupkg-file"></a>將範本封裝在 NuGet 套件中 (nupkg 檔案)

目前，Windows 上的自訂範本使用 [nuget.exe](https://dist.nuget.org/win-x86-commandline/latest/nuget.exe) 封裝 (不是 [dotnet pack](dotnet-pack.md))。 跨平台的封裝請考慮使用 [NuGetizer 3000](https://github.com/NuGet/Home/wiki/NuGetizer-3000)。

將專案資料夾的內容及其 *.template.config/template.json* 檔案放入名為 *content* 的資料夾中。 在 *content* 資料夾旁邊，新增 [*nuspec* 檔案](/nuget/create-packages/creating-a-package)，它是 XML 資訊清單檔案，描述套件的內容及驅動建立 NuGet 套件的程序。 在 *nuspec* 檔案的 **\<packageTypes>** 項目內，包含 `name` 屬性值為 `Template` 的 **\<packageType>** 項目。 *content* 資料夾和 *nuspec* 檔案都應該位於相同的目錄中。 下表顯示將範本製作為 NuGet 套件所需之最小的 *nuspec* 檔案項目。

| 元素            | 類型   | 說明 |
| ------------------ | ------ | ----------- |
| **\<作者>**     | 字串 | 以逗號分隔的套件作者清單，與 nuget.org 上的設定檔名稱相符。這些作者會顯示在 nuget.org 的 NuGet 組件庫中，並用來交互參照相同作者的其他套件。 |
| **\<描述>** | 字串 | UI 顯示中的套件詳細描述。 |
| **\<識別碼>**          | 字串 | 不區分大小寫的套件識別碼，在整個 nuget.org 或套件所在的任何組件庫都必須是唯一的。 識別碼可能不包含對 URL 而言無效的空格或字元，而且通常會遵循 .NET 命名空間規則。 如需指導方針，請參閱[選擇唯一的套件識別碼並設定版本號碼](/nuget/create-packages/creating-a-package#choosing-a-unique-package-identifier-and-setting-the-version-number)。 |
| **\<packageType>** | 字串 | 將此項目放在 **\<metadata>** 項目中的 **\<packageTypes>** 項目內。 將 **\<packageType>** 項目的 `name` 屬性設定為 `Template`。 |
| **\<版本>**     | 字串 | 套件版本，遵循 major.minor.patch 模式。 版本號碼可以包含預先發行版本的後置詞，如[預先發行版本](/nuget/create-packages/prerelease-packages#semantic-versioning)主題中所述。 |

請參閱 [.nuspec 參考](/nuget/schema/nuspec)以取得完整的 *nuspec* 檔案結構描述。 範本的範例 *nuspec* 檔案會出現在[建立 dotnet new 的自訂範本](~/docs/core/tutorials/create-custom-template.md)教學課程中。

使用 `nuget pack <PATH_TO_NUSPEC_FILE>` 命令[建立套件](/nuget/create-packages/creating-a-package#creating-the-package)。

## <a name="installing-a-template"></a>安裝範本

直接參考 *nupkg* 檔案，或指定包含組態範本的檔案系統目錄，從任何 NuGet 摘要的 NuGet 套件安裝自訂的範本。 使用 `-i|--install` 選項與 [dotnet new](dotnet-new.md) 命令。

### <a name="to-install-a-template-from-a-nuget-package-stored-at-nugetorg"></a>從儲存在 nuget.org 的 NuGet 套件安裝範本

```console
dotnet new -i <NUGET_PACKAGE_ID>
```

### <a name="to-install-a-template-from-a-local-nupkg-file"></a>從本機 nupkg 檔案安裝範本

```console
dotnet new -i <PATH_TO_NUPKG_FILE>
```

### <a name="to-install-a-template-from-a-file-system-directory"></a>從檔案系統目錄安裝範本

`FILE_SYSTEM_DIRECTORY` 是包含專案和 *.template.config* 資料夾的專案資料夾：

```console
dotnet new -i <FILE_SYSTEM_DIRECTORY>
```

## <a name="uninstalling-a-template"></a>解除安裝範本

參考 NuGet 套件的 `id` 或指定包含組態範本的檔案系統目錄，解除安裝自訂的範本。 使用 `-u|--uninstall` 安裝選項與 [dotnet new](dotnet-new.md) 命令。

### <a name="to-uninstall-a-template-from-a-nuget-package-stored-at-nugetorg"></a>從儲存在 nuget.org 的 NuGet 套件解除安裝範本

```console
dotnet new -u <NUGET_PACKAGE_ID>
```

### <a name="to-uninstall-a-template-from-a-local-nupkg-file"></a>從本機 nupkg 檔案解除安裝範本

若要將範本解除安裝，請勿嘗試使用 *nupkg* 檔案的路徑。 使用 `dotnet new -u <PATH_TO_NUPKG_FILE>` 來嘗試將範本解除安裝會失敗。 依套件的 `id` 參考套件：

```console
dotnet new -u <NUGET_PACKAGE_ID>
```

### <a name="to-uninstall-a-template-from-a-file-system-directory"></a>從檔案系統目錄解除安裝範本

`FILE_SYSTEM_DIRECTORY` 是包含專案和 *.template.config* 資料夾的專案資料夾。 提供的路徑必須是絕對路徑。 使用相對路徑來嘗試將範本解除安裝會失敗。 如需詳細資訊，請參閱 [dotnet new](dotnet-new.md) 一文。

```console
dotnet new -u <FILE_SYSTEM_DIRECTORY>
```

## <a name="create-a-project-using-a-custom-template"></a>使用自訂範本建立專案

在安裝範本之後，如同處理任何其他預先安裝的範本一樣，執行 `dotnet new <TEMPLATE>` 命令使用範本。 您也可以指定 `dotnet new` 命令的[選項](dotnet-new.md#options)，包括您在範本設定中設定的範本特定選項。 直接將範本的簡短名稱提供給命令：

```console
dotnet new <TEMPLATE>
```

## <a name="see-also"></a>另請參閱

* [建立 dotnet new 的自訂範本 (教學課程)](../tutorials/create-custom-template.md)
* [dotnet/templating GitHub repo Wiki](https://github.com/dotnet/templating/wiki) (維基百科：dotnet/templating GitHub 存放庫)
* [dotnet/dotnet-template-samples GitHub repo](https://github.com/dotnet/dotnet-template-samples) (dotnet/dotnet-template-samples GitHub 存放庫)
* [如何建立您自己的 dotnet new 範本](https://blogs.msdn.microsoft.com/dotnet/2017/04/02/how-to-create-your-own-templates-for-dotnet-new/)
* [JSON 結構描述保存區的 *template.json* 結構描述](http://json.schemastore.org/template)
