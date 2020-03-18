---
title: 將C++/CLI 專案遷移到 .NET 核心
description: 瞭解有關將C++/CLI 專案移植到 .NET Core。
author: mjrousos
ms.date: 01/10/2020
ms.openlocfilehash: eb03f2a5ff42e8279fd3ebd6ee6fb6d955f6798d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75964927"
---
# <a name="how-to-port-a-ccli-project-to-net-core"></a>如何將C++/CLI 專案移植到 .NET Core

從 .NET 核心 3.1 和 Visual Studio 2019 版本 16.4 開始[，C++/CLI 專案](/cpp/dotnet/dotnet-programming-with-cpp-cli-visual-cpp)可以定位 .NET Core。 通過這種支援，可以使用C++/CLI 互通層將 Windows 桌面應用程式移植到 .NET Core。 本文介紹如何將C++/CLI 專案從 .NET 框架移植到 .NET Core 3.1。

## <a name="ccli-net-core-limitations"></a>C++/CLI .NET 核心限制

與其他語言相比，將C++/CLI 專案移植到 .NET Core 有一些重要限制：

* C++/CLI 支援 .NET Core 僅支援 Windows。
* C++/CLI 專案不能針對 .NET 標準，只能定位 .NET 核心（或 .NET 框架）。
* C++/CLI 專案不支援新的 SDK 樣式的專案檔案格式。 相反，即使以 .NET Core 為目標，C++/CLI 專案也使用現有的 vcxproj 檔案格式。
* C++/CLI 專案不能多目標多個 .NET 平臺。 如果需要為 .NET 框架和 .NET Core 構建C++/CLI 專案，請使用單獨的專案檔案。
* .NET Core 不支援或`-clr:pure``-clr:safe`編譯，僅支援新`-clr:netcore`選項（相當於`-clr`.NET 框架）。

## <a name="port-a-ccli-project"></a>移植C++/CLI 專案

要將C++/CLI 專案移植到 .NET Core，對 vcxproj 檔進行以下更改。 這些遷移步驟與其他專案類型所需的步驟不同，因為C++/CLI 專案不使用 SDK 樣式的專案檔案。

1. 將`<CLRSupport>true</CLRSupport>`屬性替換為`<CLRSupport>NetCore</CLRSupport>`。 此屬性通常位於特定于配置的屬性組中，因此您可能需要在多個位置替換它。
2. 將`<TargetFrameworkVersion>`屬性替換為`<TargetFramework>netcoreapp3.1</TargetFramework>`。
3. 刪除任何 .NET 框架引用`<Reference Include="System" />`（如 ）。 .NET 核心 SDK 程式集在使用`<CLRSupport>NetCore</CLRSupport>`時會自動引用。
4. 根據需要更新 cpp 檔中的 API 使用方式，以刪除對 .NET Core 不可用的 API。 由於C++/CLI 專案往往相當薄的交互操作層，因此通常不需要太多的更改。 [.NET 可攜性分析器](../../standard/analyzers/portability-analyzer.md)可用於識別C++/CLI 二進位檔案使用的不支援的 .NET API，就像與純託管二進位檔案一樣。 [庫移植指南](./libraries.md#determine-portability)中提供了確定代碼可攜性和更新專案以使用 .NET Core API 的指南。

### <a name="wpf-and-windows-forms-usage"></a>WPF 和 Windows 表單使用方式

.NET 核心C++/CLI 專案可以使用 Windows 表單和 WPF API。 要使用這些 Windows 桌面 API，您需要向 UI 庫添加顯式框架引用。 使用 Windows 桌面 API 的 SDK 樣式專案使用`Microsoft.NET.Sdk.WindowsDesktop`SDK 自動引用必要的框架庫。 由於C++/CLI 專案不使用 SDK 風格的專案格式，因此在定位 .NET Core 時，需要添加顯式框架引用。

要使用 Windows 表單 API，添加此引用到 vcxproj 檔：

```xml
<!-- Reference all of Windows Forms -->
<FrameworkReference Include="Microsoft.WindowsDesktop.App.WindowsForms" />
```

要使用 WPF API，添加此引用到 vcxproj 檔：

```xml
<!-- Reference all of WPF -->
<FrameworkReference Include="Microsoft.WindowsDesktop.App.WPF" />
```

要同時使用 Windows 表單和 WPF API，請使用此引用添加到 vcxproj 檔：

```xml
<!-- Reference the entirety of the Windows desktop framework:
     Windows Forms, WPF, and the types that provide integration between them -->
<FrameworkReference Include="Microsoft.WindowsDesktop.App" />
```

目前，無法使用 Visual Studio 的參考管理器添加這些引用。 而是手動更新專案檔案。 此更新可以通過卸載專案然後編輯專案檔案在 Visual Studio 中完成。 您還可以使用其他編輯器，如 VS 代碼。

## <a name="build-without-msbuild"></a>無需 MSBuild 即可生成

無需使用 MSBuild 即可構建C++/CLI 專案。 按照以下步驟直接使用*cl.exe*和*link.exe*為 .NET Core 構建C++/CLI 專案：

1. 編譯時，將傳遞給`-clr:netcore` *cl.exe*。
2. 引用必需 .NET 核心引用程式集。
3. 連結時，將 .NET Core 應用主機目錄`LibPath`作為 （以便可以找到*ijwhost.lib）* 。
4. 將*ijwhost.dll（* 從 .NET Core 應用主機目錄）複製到專案的輸出目錄。
5. 確保運行託管代碼的應用程式的第一個元件存在[運行時 config.json](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)檔。 如果應用程式具有託管進入點，將自動創建和`runtime.config`複製檔。 但是，如果應用程式具有本機進入點，則需要為第一個C++/CLI 庫創建一個`runtimeconfig.json`檔才能使用 .NET Core 運行時。

## <a name="known-issues"></a>已知問題

在以 .NET Core 為目標C++/CLI 專案時，有幾個已知問題需要關注。

* .NET Core C++/CLI 專案中的 WPF 框架引用當前會導致一些有關無法導入符號的無關警告。 可以安全地忽略這些警告，並且應該儘快修復。
* 如果應用程式具有本機進入點，則首先執行託管代碼C++/CLI 庫需要[運行時 config.json](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)檔。 當 .NET 核心運行時啟動時，使用此設定檔。 C++/CLI 專案尚未在生成`runtimeconfig.json`時自動創建檔，因此必須手動生成該檔。 如果從託管進入點調用C++/CLI 庫，則C++/CLI 庫不需要`runtimeconfig.json`檔（因為進入點程式集將在啟動運行時時使用）。 下面顯示了一`runtimeconfig.json`個簡單的示例檔。 有關詳細資訊，請參閱[GitHub 上的規範](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)。

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
