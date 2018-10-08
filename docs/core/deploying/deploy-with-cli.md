---
title: 使用 CLI 工具部署.NET Core 應用程式
description: 了解使用命令列介面 (CLI) 工具的 .NET Core 應用程式部署
author: rpetrusha
ms.author: ronpet
ms.date: 09/05/2018
dev_langs:
- csharp
- vb
ms.openlocfilehash: a7e810372d831699eae777186385e45fe65cdf45
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2018
ms.locfileid: "47208246"
---
# <a name="deploying-net-core-apps-with-command-line-interface-cli-tools"></a>使用命令列介面 (CLI) 工具部署 .NET Core 應用程式

您可以將 .NET Core 應用程式部署為「與 Framework 相依的部署」，其中包含您的應用程式二進位檔，但取決於目標系統上是否有 .NET Core 存在，也可以部署為「自封式部署」，其中包含您的應用程式和 .NET Core 二進位檔。 如需概觀，請參閱 [.NET Core 應用程式部署](index.md)。

下列各節顯示如何使用 [.NET Core 命令列介面工具](../tools/index.md)來建立下列類型的部署：

- 與 Framework 相依的部署
- 有協力廠商相依性的 Framework 相依部署
- 自封式部署
- 有協力廠商相依性的自封式部署

在命令列工作時，您可以使用您選擇的程式編輯器。 如果您的程式編輯器是 [Visual Studio Code](https://code.visualstudio.com)，您也可以在 Visual Studio 程式碼環境內選取 [檢視]  >  [整合式終端機] 來開啟命令主控台。

## <a name="framework-dependent-deployment"></a>與 Framework 相依的部署

部署無任何協力廠商相依性的 Framework 相依部署，只涉及建置、測試和發行應用程式。 以 C# 撰寫的簡單範例會說明此程序。

1. 建立專案目錄。

   建立專案的目錄，並將其設為您目前的目錄。

1. 建立專案。

   從命令列鍵入 [dotnet new 主控台](../tools/dotnet-new.md)，以建立新的 C# 主控台專案，或鍵入 [dotnet new 主控台 -lang vb](../tools/dotnet-new.md)，以在該目錄中建立新的 Visual Basic 主控台專案。

1. 新增應用程式的原始程式碼。

   在編輯器中開啟 *Program.cs* 或 *Program.vb* 檔案，並用下列程式碼取代自動產生的程式碼。 它會提示使用者輸入文字，並顯示使用者輸入的個別文字。 它會使用規則運算式 `\w+` 分隔輸入文字中的字詞。

   [!code-csharp[deployment#1](~/samples/snippets/core/deploying/cs/deployment-example.cs)]
   [!code-vb[deployment#1](~/samples/snippets/core/deploying/vb/deployment-example.vb)]

1. 更新專案的相依性和工具。

   執行 [dotnet restore](../tools/dotnet-restore.md) ([請參閱注意事項](#dotnet-restore-note)) 命令以還原專案中指定的相依性。

1. 建立應用程式的偵錯組建。

   使用 [dotnet build](../tools/dotnet-build.md) 命令來組建您的應用程式，或者使用 [dotnet run](../tools/dotnet-run.md) 命令來組建並執行它。

1. 部署應用程式。

   在您偵錯並測試程式之後，請使用下列命令來建立部署：

      ```console
      dotnet publish -f netcoreapp2.1 -c Release
      ```
   這會建立應用程式的發行 (而非偵錯) 版本。 產生的檔案會放在名為 *publish* 的目錄中，而該目錄位於您專案之 *bin* 目錄的子目錄中。

   隨著應用程式檔案一起，發佈程序會發出程式資料庫 (.pdb) 檔案，其中包含應用程式的偵錯資訊。 該檔案主要是用於例外狀況偵錯。 您可以選擇不與您的應用程式檔案一起將它發散。 不過，如果您要對應用程式的發行組建進行偵錯，則應該將其保存。

   您可以使用任何您想要的方式，部署整組應用程式檔案。 例如，您可以使用簡單的 `copy` 命令將它們封裝在 ZIP 檔案中，或與您選擇的任何安裝套件一起部署。

1. 執行應用程式

   安裝之後，使用者可以使用 `dotnet` 命令並提供應用程式的檔名 (例如，`dotnet fdd.dll`)，來執行您的應用程式。

   除了應用程式二進位檔之外，安裝程式也應該配套共用的 Framework 安裝程式，或勾選為必要條件當成應用程式安裝的一部分。  共用的 Framework 安裝需要系統管理員/根目錄存取權。

## <a name="framework-dependent-deployment-with-third-party-dependencies"></a>有協力廠商相依性的 Framework 相依部署

部署具有一或多個協力廠商相依性的 Framework 相依部署時，需要這些相依性都可供專案使用。 在執行 `dotnet restore` ([請參閱注意事項](#dotnet-restore-note)) 命令之前，需要執行兩個額外步驟：

1. 將任何協力廠商程式庫參考新增至您 *csproj* 檔案的 `<ItemGroup>` 區段。 下列 `<ItemGroup>` 區段會包含對 [Json.NET](http://www.newtonsoft.com/json) 的相依性作為協力廠商程式庫：

      ```xml
      <ItemGroup>
        <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
      </ItemGroup>
      ```

1. 如果尚未如此做，請下載包含協力廠商相依性的 NuGet 封裝。 若要下載套件，請在新增相依性後執行 `dotnet restore` ([請參閱注意事項](#dotnet-restore-note)) 命令。 因為相依性是在發行時於本機 NuGet 快取外解析，所以必須能在系統中取得。

請注意，具有協力廠商相依性的 Framework 相依部署，可攜性只與其協力廠商相依性一致。 例如，如果協力廠商程式庫只支援 macOS，則應用程式就無法攜至 Windows 系統。 如果協力廠商相依性本身依賴於原生程式碼，就會發生這種情況。 其中一個絶佳範例是 [Kestrel 伺服器](/aspnet/core/fundamentals/servers/kestrel)，它需要對 [libuv](https://github.com/libuv/libuv) 的原生相依性。 當具有這類協力廠商相依性的應用程式建立了 FDD 時，已發行輸出就會包含原生相依性支援的每個[執行階段識別碼 (RID)](../rid-catalog.md) 資料夾 (存在於其 NuGet 套件中)。

## <a name="simpleSelf"></a> 沒有協力廠商相依性的自封式部署

部署沒有協力廠商相依性的自封式部署，涉及建立專案、修改 *csproj* 檔案、組建、測試以及發行應用程式。 以 C# 撰寫的簡單範例會說明此程序。 此範例示範如何從命令列使用 [dotnet 公用程式](../tools/dotnet.md)建立自封式部署。

1. 建立專案的目錄。

   建立專案的目錄，並將其設為您目前的目錄。

1. 建立專案。

   從命令列鍵入 [dotnet new console](../tools/dotnet-new.md)，以在該目錄中建立新的 C# 主控台專案。

1. 新增應用程式的原始程式碼。

   在您的編輯器中開啟 *Program.cs* 檔案，並以下列程式碼取代自動產生的程式碼。 它會提示使用者輸入文字，並顯示使用者輸入的個別文字。 它會使用規則運算式 `\w+` 分隔輸入文字中的字詞。

   [!code-csharp[deployment#1](~/samples/snippets/core/deploying/cs/deployment-example.cs)]
   [!code-vb[deployment#1](~/samples/snippets/core/deploying/vb/deployment-example.vb)]
1. 定義您應用程式目標的平台。

   在定義應用程式目標平台之 *csproj* 檔案的 `<PropertyGroup>` 區段中建立 `<RuntimeIdentifiers>` 標記，並指定每個目標平台的執行階段識別碼 (RID)。 請注意，您也必須加上分號來分隔 RID。 如需執行階段識別碼清單，請參閱 [.NET Core RID 類別目錄](../rid-catalog.md)。

   例如，下列 `<PropertyGroup>` 區段指出應用程式在 64 位元 Windows 10 作業系統和 64 位元 OS X 版本 10.11 作業系統上執行。

     ```xml
     <PropertyGroup>
         <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
     </PropertyGroup>
     ```

   請注意，`<RuntimeIdentifiers>` 項目可以出現在 *csproj* 檔案的任何 `<PropertyGroup>` 中。 本節稍後會提供完整的 *csproj* 檔案範例。

1. 更新專案的相依性和工具。

   執行 [dotnet restore](../tools/dotnet-restore.md) ([請參閱注意事項](#dotnet-restore-note)) 命令以還原專案中指定的相依性。

1. 決定您是否想使用全域無差異模式。

   尤其當您的應用程式以 Linux 為目標時，使用全域無差異模式[能減少您部署的總大小](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md)。 全域無差異模式適用於非全域應用程式，其能使用格式化慣例、大小寫慣例及字串比較，還有不因文化特性而異的[排列次序](xref:System.Globalization.CultureInfo.InvariantCulture)。

   在您的專案 (而非解決方案) 點擊右鍵，進入 [方案總管]，然後選取 [Edit SCD.csproj] \(編輯 SCD.csproj\) 或 [Edit SCD.vbproj] \(編輯 SCD.vbproj\) 啟用非變異模式。 接著，將下列反白的幾行新增至檔案：

 [!code-xml[globalization-invariant-mode](~/samples/snippets/core/deploying/xml/invariant.csproj)]

1. 建立應用程式的偵錯組建。

   從命令列中，使用 [dotnet build](../tools/dotnet-build.md) 命令。

1. 在您偵錯並測試程式之後，請針對每個目標平台建立要隨應用程式一起部署的檔案。

   針對這兩個目標平台使用 `dotnet publish` 命令，如下所示：

      ```console
      dotnet publish -c Release -r win10-x64
      dotnet publish -c Release -r osx.10.11-x64
      ```

   這會建立每個目標平台的應用程式發行 (而非偵錯) 版本。 產生的檔案會放在名為 *publish* 的子目錄中，其位於您專案 *.\bin\Release\netcoreapp2.1\<runtime_identifier>* 子目錄的子目錄。 請注意，每個子目錄都包含啟動應用程式所需的一組完整檔案 (應用程式檔案和所有的 .NET Core 檔案)。

隨著應用程式檔案一起，發佈程序會發出程式資料庫 (.pdb) 檔案，其中包含應用程式的偵錯資訊。 該檔案主要是用於例外狀況偵錯。 您可以選擇不與您的應用程式檔案一起封裝它。 不過，如果您要對應用程式的發行組建進行偵錯，則應該將其保存。

請使用任何您想要的方式，部署已發行的檔案。 例如，您可以使用簡單的 `copy` 命令將它們封裝在 ZIP 檔案中，或與您選擇的任何安裝套件一起部署。

下面是此專案的完整 *csproj* 檔案。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

## <a name="self-contained-deployment-with-third-party-dependencies"></a>有協力廠商相依性的自封式部署

部署具有一或多個協力廠商相依性的自封式部署，涉及新增相依性。 在執行 `dotnet restore` ([請參閱注意事項](#dotnet-restore-note)) 命令之前，需要執行兩個額外步驟：

1. 將任何協力廠商程式庫參考新增至您 *csproj* 檔案的 `<ItemGroup>` 區段。 下列 `<ItemGroup>` 區段會使用 Json.NET 作為協力廠商程式庫。

    ```xml
      <ItemGroup>
        <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
      </ItemGroup>
    ```

1. 如果尚未如此做，請將包含協力廠商相依性的 NuGet 封裝下載至您的系統。 請在新增相依性後執行 `dotnet restore` ([請參閱注意](#dotnet-restore-note)) 命令，讓應用程式取得相依性。 因為相依性是在發行時於本機 NuGet 快取外解析，所以必須能在系統中取得。

下面是此專案的完整 *csproj* 檔案：

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
  </ItemGroup>
</Project>
```

當您部署應用程式時，應用程式中任何協力廠商相依性也包含在應用程式檔案中。 應用程式執行所在的系統上不需要協力廠商程式庫。

請注意，您只能將具有協力廠商程式庫的自封式部署，部署到該程式庫支援的平台上。 這類似於在與 Framework 相依的部署中擁有仰賴原生相依性的協力廠商相依性；在其中，原生相依性必須與部署應用程式的平台相容。

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

## <a name="see-also"></a>另請參閱

* [.NET Core 應用程式部署](index.md)
* [.NET Core 執行階段識別項 (RID) 目錄](../rid-catalog.md)
