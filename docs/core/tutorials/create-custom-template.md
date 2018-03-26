---
title: 建立 dotnet new 的自訂範本
description: 了解如何在此好玩的教學課程中建立 dotnet new 命令的自訂範本。
keywords: .NET, .NET Core, 範本, 建立範本, 教學課程, dotnet new
author: guardrex
ms.author: mairaw
ms.date: 08/12/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 519b910a-6efe-4394-9b81-0546aa3e7462
ms.workload:
- dotnetcore
ms.openlocfilehash: 7830a437b46d2080efc65f43f9112503add4c305
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/26/2018
---
# <a name="create-a-custom-template-for-dotnet-new"></a>建立 dotnet new 的自訂範本

本教學課程會示範如何：

- 從現有的專案或新的主控台應用程式專案建立基本範本。
- 封裝範本，以在 nuget.org 或從本機 *nupkg* 檔案發佈。
- 從 nuget.org (本機 *nupkg* 檔案) 或本機檔案系統安裝範本。
- 解除安裝範本。

如果您偏好使用完整範例來進行教學課程，請下載[範例專案範本](https://github.com/dotnet/dotnet-template-samples/tree/master/16-nuget-package)。 範例範本是專為 NuGet 發佈所設定。

如果您希望使用下載的範例和檔案系統發佈，請執行下列作業：

- 將範例的 *content* 資料夾內容上移一層到 *GarciaSoftware.ConsoleTemplate.CSharp* 資料夾。
- 刪除空白的 *content* 資料夾。
- 刪除 *nuspec* 檔案。

## <a name="prerequisites"></a>必要條件

- 安裝 [.NET Core 2.0 SDK](https://www.microsoft.com/net/core) 或更新版本。
- 閱讀參考主題 [dotnet new 的自訂範本](../tools/custom-templates.md)。

## <a name="create-a-template-from-a-project"></a>從專案建立範本

使用您已確認編譯和執行的現有專案，或在硬碟的資料夾中建立新的主控台應用程式專案。 本教學課程假設專案資料夾的名稱為 *GarciaSoftware.ConsoleTemplate.CSharp*，儲存在使用者設定檔的 *Documents\Templates*。 教學課程專案範本名稱的格式為 \<公司名稱>.\<範本類型>.\<程式設計語言>，但是您可以依喜好隨意命名您的專案與範本。

1. 將資料夾新增至 *.template.config* 專案的根目錄。
1. 在 *.template.config* 資料夾中建立 *template.json* 檔案，以設定您的範本。 如需 *template.json* 檔案的詳細資訊和成員定義，請參閱 [dotnet new 的自訂範本](../tools/custom-templates.md#templatejson)主題和 [JSON 結構描述存放區的 *template.json* 結構描述](http://json.schemastore.org/template)。

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

已完成範本。 此時，您有兩個範本發佈的選項。 若要繼續本教學課程，請在兩個路徑中選擇其中之一：

1. [NuGet 發佈](#use-nuget-distribution)：從 NuGet 或從本機 *nupkg* 檔案安裝範本，並使用已安裝的範本。
2. [檔案系統發佈](#use-file-system-distribution)。

## <a name="use-nuget-distribution"></a>使用 NuGet 發佈

### <a name="pack-the-template-into-a-nuget-package"></a>將範本封裝至 NuGet 套件中

1. 建立 NuGet 套件的資料夾。 教學課程中使用 *GarciaSoftware.ConsoleTemplate.CSharp* 資料夾名稱，並在使用者設定檔的 *Documents\NuGetTemplates* 資料夾中建立此資料夾。 在新的範本資料夾內建立名為「內容」的資料夾，保留專案檔。
1. 將專案資料夾的內容以及其 *.template.config/template.json* 檔案複製到您建立的 *content* 資料夾。
1. 在 *content* 資料夾的旁邊，新增 [*nuspec* 檔案](/nuget/create-packages/creating-a-package)。 nuspec 檔案是 XML 資訊清單檔案，描述套件的內容及驅動建立 NuGet 套件的程序。
   
   ![目錄結構顯示 NuGet 套件的配置](./media/create-custom-template/nugetdirectorylayout.png)

1. 在 *nuspec* 檔案的 **\<packageTypes>** 項目內，包含 `name` 屬性值為 `Template` 的 **\<packageType>** 項目。 *content* 資料夾和 *nuspec* 檔案都應該位於相同的目錄中。 下表顯示將範本製作為 NuGet 套件所需之最小的 *nuspec* 檔案項目。

   | 項目            | 類型   | 描述 |
   | ------------------ | ------ | ----------- |
   | **\<作者>**     | 字串 | 以逗號分隔的套件作者清單，與 nuget.org 上的設定檔名稱相符。這些作者會顯示在 nuget.org 的 NuGet 組件庫中，並用來交互參照相同作者的其他套件。 |
   | **\<描述>** | 字串 | UI 顯示中的套件詳細描述。 |
   | **\<識別碼>**          | 字串 | 不區分大小寫的套件識別碼，在整個 nuget.org 或套件所在的任何組件庫都必須是唯一的。 識別碼可能不包含對 URL 而言無效的空格或字元，而且通常會遵循 .NET 命名空間規則。 如需指導方針，請參閱[選擇唯一的套件識別碼並設定版本號碼](/nuget/create-packages/creating-a-package#choosing-a-unique-package-identifier-and-setting-the-version-number)。 |
   | **\<packageType>** | 字串 | 將此項目放在 **\<metadata>** 項目中的 **\<packageTypes>** 項目內。 將 **\<packageType>** 項目的 `name` 屬性設定為 `Template`。 |
   | **\<版本>**     | 字串 | 套件版本，遵循 major.minor.patch 模式。 版本號碼可以包含預先發行版本的後置詞，如[預先發行版本](/nuget/create-packages/prerelease-packages#semantic-versioning)中所述。 |

   請參閱 [.nuspec 參考](/nuget/schema/nuspec)以取得完整的 *nuspec* 檔案結構描述。

   教學課程的 *nuspec* 檔案名為 *GarciaSoftware.ConsoleTemplate.CSharp.nuspec*，且包含下列內容：

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <package xmlns="http://schemas.microsoft.com/packaging/2012/06/nuspec.xsd">
     <metadata>
       <id>GarciaSoftware.ConsoleTemplate.CSharp</id>
       <version>1.0.0</version>
       <description>
         Creates the Garcia Software console app.
       </description>
       <authors>Catalina Garcia</authors>
       <packageTypes>
         <packageType name="Template" />
       </packageTypes>
     </metadata>
   </package>
   ```

1. 使用 `nuget pack <PATH_TO_NUSPEC_FILE>` 命令[建立套件](/nuget/create-packages/creating-a-package#creating-the-package)。 下列命令假設，保存 NuGet 資產的資料夾位於 *C:\Users\\\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp*。 但無論資料夾放在系統上的任何位置，`nuget pack` 命令都接受 *nuspec* 檔案的路徑：

   ```console
   nuget pack C:\Users\<USER>\Documents\NuGetTemplates\GarciaSoftware.ConsoleTemplate.CSharp\GarciaSoftware.ConsoleTemplate.CSharp.nuspec
   ```

### <a name="publishing-the-package-to-nugetorg"></a>將套件發佈至 nuget.org

若要發佈 NuGet 套件，請遵循[建立和發佈套件](/nuget/quickstart/create-and-publish-a-package#publish-the-package)主題中的指示。 不過，我們建議您不要將教學課程的範本發佈至 NuGet，因為它一旦發佈即永不刪除，只能取消列入。 既然已有 *nupkg* 檔案形式的 NuGet 套件，建議您遵循下列指示直接從本機 *nupkg* 檔案安裝範本。

### <a name="install-the-template-from-a-nuget-package"></a>從 NuGet 套件安裝範本

#### <a name="install-the-template-from-the-local-nupkg-file"></a>從本機 *nupkg* 檔案安裝範本

若要從您製作的 *nupkg* 檔案安裝範本，請使用 `dotnet new` 命令搭配 `-i|--install` 選項，然後提供 *nupkg* 檔案的路徑：

```console
dotnet new -i C:\Users\<USER>\GarciaSoftware.ConsoleTemplate.CSharp.1.0.0.nupkg
```

#### <a name="install-the-template-from-a-nuget-package-stored-at-nugetorg"></a>從儲存在 nuget.org 的 NuGet 套件安裝範本

如果您想要從儲存在 nuget.org 的 NuGet 套件安裝範本，請使用 `dotnet new` 命令搭配 `-i|--install` 選項，並提供 NuGet 套件的名稱：

```console
dotnet new -i GarciaSoftware.ConsoleTemplate.CSharp
```

> [!NOTE]
> 範例僅供示範之用。 nuget.org 沒有 `GarciaSoftware.ConsoleTemplate.CSharp` NuGet 套件，我們也不建議您發佈及使用來自 NuGet 的測試範本。 如果您執行命令，不會安裝任何範本。 不過，您可以直接參考本機檔案系統上的 *nupkg* 檔案，安裝尚未發佈至 nuget.org 的範本，如上一節[從本機 nupkg 檔案安裝範本](#install-the-template-from-the-local-nupkg-file)中所示。

如果您想要如何從 nuget.org 的套件安裝範本的即時範例，您可以使用 [NUnit 3 template for dotnet-new](https://www.nuget.org/packages/NUnit3.DotNetNew.Template/) (dotnet-new 的 NUnit 3 範本)。 此範本會設定專案使用 NUnit 單元測試。 使用下列命令來安裝：

```console
dotnet new -i NUnit3.DotNetNew.Template
```

當您列出範本與 `dotnet new -l` 時，您會在範本清單中看到 *NUnit 3 測試專案*的簡短名稱 *nunit*。 您已準備好在下一節中使用範本。

![顯示與其他已安裝範本一起列出之 NUnit 範本的主控台視窗](./media/create-custom-template/nunit1.png)

### <a name="create-a-project-from-the-template"></a>從範本建立專案

從 NuGet 安裝範本之後，從放置範本引擎輸出的目錄執行 `dotnet new <TEMPLATE>` 命令來使用範本 (除非您要使用 `-o|--output` 選項來指定特定的目錄)。 如需詳細資訊，請參閱[`dotnet new`選項](~/docs/core/tools/dotnet-new.md#options)。 直接將範本的簡短名稱提供給 `dotnet new` 命令。 若要從 NUnit 範本建立專案，請執行下列命令：

```console
dotnet new nunit
```

主控台會顯示專案已建立，且專案套件已還原。 命令執行之後，專案即可供使用。

![主控台視窗會在建立 NUnit 專案，以及還原專案相依性時，顯示 dotnet new 命令的輸出。](./media/create-custom-template/nunit2.png)

### <a name="to-uninstall-a-template-from-a-nuget-package-stored-at-nugetorg"></a>從儲存在 nuget.org 的 NuGet 套件解除安裝範本

```console
dotnet new -u GarciaSoftware.ConsoleTemplate.CSharp
```

> [!NOTE]
> 範例僅供示範之用。 nuget.org 沒有 `GarciaSoftware.ConsoleTemplate.CSharp` NuGet 套件，也未與 .NET Core SDK 一起安裝。 如果執行命令，但未解除安裝套件/範本，且收到下列例外狀況：
> 
> > 找不到稱為 'GarciaSoftware.ConsoleTemplate.CSharp' 要解除安裝的項目。

如已安裝 [NUnit 3 template for dotnet-new](https://www.nuget.org/packages/NUnit3.DotNetNew.Template/) (dotnet-new 的 NUnit 3 範本)，現在希望解除安裝，請使用下列命令：

```console
dotnet new -u NUnit3.DotNetNew.Template
```

### <a name="uninstall-the-template-from-a-local-nupkg-file"></a>從本機 nupkg 檔案解除安裝範本

當您想要解除安裝範本時，請勿嘗試使用 *nupkg* 檔案的路徑。 *嘗試使用 `dotnet new -u <PATH_TO_NUPKG_FILE>` 解除安裝範本失敗。* 依套件的 `id` 參考套件：

```console
dotnet new -u GarciaSoftware.ConsoleTemplate.CSharp.1.0.0
```

## <a name="use-file-system-distribution"></a>使用檔案系統發佈

若要發佈範本，請將專案範本資料夾放在網路上使用者能存取的位置。 使用 `dotnet new` 命令搭配 `-i|--install` 選項，並指定範本資料夾的路徑 (包含專案的專案資料夾和 *.template.config* 資料夾)。

教學課程假設專案範本是儲存在使用者設定檔的 *Documents/Templates* 資料夾中。 從該位置安裝範本，以下列命令取代 \<使用者> 和使用者的設定檔名稱：

```console
dotnet new -i C:\Users\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp
```

### <a name="create-a-project-from-the-template"></a>從範本建立專案

從檔案系統安裝範本之後，從放置範本引擎輸出的目錄執行 `dotnet new <TEMPLATE>` 命令來使用範本 (除非您要使用 `-o|--output` 選項來指定特定的目錄)。 如需詳細資訊，請參閱[`dotnet new`選項](~/docs/core/tools/dotnet-new.md#options)。 直接將範本的簡短名稱提供給 `dotnet new` 命令。

從在 *C:\Users\\\<USER>\Documents\Projects\MyConsoleApp* 建立的新專案資料夾，建立來自 `garciaconsole` 範本的專案：

```console
dotnet new garciaconsole
```

### <a name="uninstall-the-template"></a>解除安裝範本

如果在 *C:\Users\\\<USER>\Document\Templates\GarciaSoftware.ConsoleTemplate.CSharp* 的本機檔案系統上建立範本，請使用 `-u|--uninstall` 參數和範本資料夾路徑將其解除安裝：

```console
dotnet new -u C:\Users\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp
```

> [!NOTE]
> 若要將範本從您的本機檔案系統解除安裝，您需要使路徑成為完整路徑。 例如，*C:\Users\\\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp* 將有效，但來自包含資料夾的 *./GarciaSoftware.ConsoleTemplate.CSharp* 將無效。
> 此外，請勿在範本路徑中包含最終結尾目錄斜線。

## <a name="see-also"></a>另請參閱

[dotnet/templating GitHub repo Wiki](https://github.com/dotnet/templating/wiki) (維基百科：dotnet/templating GitHub 存放庫)  
[dotnet/dotnet-template-samples GitHub repo](https://github.com/dotnet/dotnet-template-samples) (dotnet/dotnet-template-samples GitHub 存放庫)  
[如何建立您自己的 dotnet new 範本](https://blogs.msdn.microsoft.com/dotnet/2017/04/02/how-to-create-your-own-templates-for-dotnet-new/)  
[JSON 結構描述保存區的 *template.json* 結構描述](http://json.schemastore.org/template)  
