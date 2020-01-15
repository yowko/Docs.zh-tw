---
title: 將C++/cli 專案遷移至 .net Core
description: 瞭解如何將C++/cli 專案移植到 .net Core。
author: mjrousos
ms.date: 01/10/2020
ms.openlocfilehash: eb03f2a5ff42e8279fd3ebd6ee6fb6d955f6798d
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964927"
---
# <a name="how-to-port-a-ccli-project-to-net-core"></a>如何將C++/cli 專案移植到 .net Core

從 .net core 3.1 和 Visual Studio 2019 16.4 版開始， [ C++/cli 專案](/cpp/dotnet/dotnet-programming-with-cpp-cli-visual-cpp)可以目標設為 .net core。 這種支援可讓您將 Windows 桌面應用程式C++與/cli interop 層移植到 .net Core。 本文說明如何將/Cli 專案C++從 .NET Framework 移植到 .net Core 3.1。

## <a name="ccli-net-core-limitations"></a>C++/CLI .NET Core 限制

相較于其他語言，將C++/cli 專案移植到 .net Core 時，有一些重要的限制：

* C++適用于 .NET Core 的/CLI 支援僅限 Windows。
* C++/CLI 專案不能以 .NET Standard 為目標，只有 .NET Core （或 .NET Framework）。
* C++/CLI 專案不支援新的 SDK 樣式專案檔案格式。 相反地，即使以 .NET Core 為C++目標，/cli 專案還是會使用現有的 .vcxproj 檔案格式。
* C++/CLI 專案無法使用多目標多個 .NET 平臺。 如果您需要為 .NET Framework 和C++.net Core 建立/cli 專案，請使用個別的專案檔。
* .NET Core 不支援 `-clr:pure` 或 `-clr:safe` 編譯，只有新的 `-clr:netcore` 選項（這相當於 .NET Framework 的 `-clr`）。

## <a name="port-a-ccli-project"></a>移植C++/cli 專案

若要將C++/cli 專案移植到 .net Core，請對 .vcxproj 檔案進行下列變更。 這些遷移步驟與其他專案類型所需的步驟不同， C++因為/cli 專案不會使用 SDK 樣式的專案檔。

1. 以 `<CLRSupport>NetCore</CLRSupport>`取代 `<CLRSupport>true</CLRSupport>` 的屬性。 這個屬性通常是在設定特定的屬性群組中，因此您可能需要在多個地方取代它。
2. 以 `<TargetFramework>netcoreapp3.1</TargetFramework>`取代 `<TargetFrameworkVersion>` 的屬性。
3. 移除任何 .NET Framework 參考（例如 `<Reference Include="System" />`）。 使用 `<CLRSupport>NetCore</CLRSupport>`時，會自動參考 .NET Core SDK 元件。
4. 視需要更新 cpp 檔案中的 API 使用方式，以移除 .NET Core 無法使用的 Api。 因為C++/cli 專案傾向于相當精簡的 interop 層，所以通常不需要進行許多變更。 [.Net 可攜性分析器](../../standard/analyzers/portability-analyzer.md)可以用來識別/cli 二進位檔所使用C++的不受支援 .net api，就像單純的受控二進位檔一樣。 連結[庫移植指引](./libraries.md#determine-portability)提供判斷程式碼可攜性和更新專案以使用 .Net Core api 的指導方針。

### <a name="wpf-and-windows-forms-usage"></a>WPF 和 Windows Forms 使用方式

.NET Core C++/cli 專案可以使用 WINDOWS FORMS 和 WPF api。 若要使用這些 Windows 桌面 Api，您必須將明確的架構參考新增至 UI 程式庫。 使用 Windows 桌面 Api 的 SDK 樣式專案會使用 `Microsoft.NET.Sdk.WindowsDesktop` SDK 自動參考必要的架構程式庫。 因為C++/cli 專案不會使用 SDK 樣式的專案格式，所以必須在以 .net Core 為目標時新增明確的架構參考。

若要使用 Windows Forms Api，請將此參考新增至 .vcxproj 檔案：

```xml
<!-- Reference all of Windows Forms -->
<FrameworkReference Include="Microsoft.WindowsDesktop.App.WindowsForms" />
```

若要使用 WPF Api，請將此參考新增至 .vcxproj 檔案：

```xml
<!-- Reference all of WPF -->
<FrameworkReference Include="Microsoft.WindowsDesktop.App.WPF" />
```

若要同時使用 Windows Forms 和 WPF Api，請將此參考新增至 .vcxproj 檔案：

```xml
<!-- Reference the entirety of the Windows desktop framework:
     Windows Forms, WPF, and the types that provide integration between them -->
<FrameworkReference Include="Microsoft.WindowsDesktop.App" />
```

目前，您無法使用 Visual Studio 的參考管理員來新增這些參考。 相反地，請手動更新專案檔。 這項更新可以在 Visual Studio 中完成，方法是卸載專案，然後編輯專案檔。 您也可以使用其他編輯器，如 VS Code。

## <a name="build-without-msbuild"></a>不含 MSBuild 的組建

您也可以建立C++/cli 專案，而不使用 MSBuild。 請遵循下列步驟，直接C++使用*cl*和*Link*建立適用于 .net Core 的/cli 專案：

1. 在編譯時，將 `-clr:netcore` 傳遞給*cl .exe*。
2. 參考必要的 .NET Core 參考元件。
3. 連結時，請提供 .NET Core 應用程式主機目錄做為 `LibPath` （如此即可找到*ijwhost* ）。
4. 將*ijwhost* （從 .net Core 應用程式主機目錄）複製到專案的輸出目錄。
5. 請確定將執行 managed 程式碼之應用程式的第一個元件有[.runtimeconfig.json。](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) 如果應用程式具有受控進入點，將會自動建立並複製 `runtime.config` 檔案。 不過，如果應用程式具有原生進入點，您就必須為第一個C++/cli 程式庫建立 `runtimeconfig.json` 檔案，才能使用 .net Core 執行時間。

## <a name="known-issues"></a>已知問題

使用以 .NET Core 為目標的C++/cli 專案時，有幾個已知問題需要注意。

* .NET Core C++/cli 專案中的 WPF 架構參考目前會造成一些關於無法匯入符號的無關警告。 這些警告可以放心忽略，而且應該很快就會修正。
* 如果應用程式具有原生進入點，則C++第一次執行 managed 程式碼的/cli 程式庫需要[.runtimeconfig.json json](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)檔案。 當 .NET Core 執行時間啟動時，會使用此設定檔。 C++/CLI 專案還不會在組建期間自動建立 `runtimeconfig.json` 檔案，因此必須手動產生檔案。 如果從C++managed 進入點呼叫/cli 程式庫，則C++/cli 程式庫不需要 `runtimeconfig.json` 檔案（因為進入點元件將會有一個在啟動執行時間時使用的檔案）。 簡單的範例 `runtimeconfig.json` 檔案如下所示。 如需詳細資訊，請參閱[GitHub 上的規格](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)。

    ```json
    {
          "runtimeOptions": {
             "tfm": "netcoreapp3.1",
             "framework": {
                "name": "Microsoft.NETCore.App",
                "version": "3.1.0"
             }
          }
    }
    ```
