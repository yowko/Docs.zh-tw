---
title: "dotnet-test 命令 | Microsoft Docs"
description: "`dotnet test` 命令是用來在指定的專案中執行單元測試。"
keywords: "dotnet-test, CLI, CLI 命令, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 10/07/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 3a0fa917-eb0a-4d7e-9217-d06e65455675
translationtype: Human Translation
ms.sourcegitcommit: 796df1549a7553aa93158598d62338c02d4df73e
ms.openlocfilehash: 871a6f736272309f6fae74b06f437c7271df2321

---

#<a name="dotnet-test"></a>dotnet-test

> [!WARNING]
> 本主題適用於 .NET Core 工具 Preview 2。 .NET Core 工具 RC4 版本，請參閱 [dotnet-test (.NET Core 工具 RC4)](../preview3/tools/dotnet-test.md) 主題。

## <a name="name"></a>名稱

`dotnet-test` - 使用設定的測試執行器，來執行單元測試。

## <a name="synopsis"></a>概要

`dotnet test [project] [--help] 
    [--parentProcessId] [--port] [--configuration]   
    [--output] [--build-base-path] [--framework] [--runtime]
    [--no-build]`  

## <a name="description"></a>描述

`dotnet test` 命令是用來在指定的專案中執行單元測試。 單元測試是與單元測試架構 (例如 NUnit 或 xUnit) 具有相依性的類別庫專案，以及該單元測試架構的 dotnet test 執行器。 這些會封裝為 NuGet 套件，並還原為專案的一般相依性。

測試專案也需要在使用 "testRunner" 節點的 project.json 中指定測試執行器屬性。 這個值應該包含單元測試架構的名稱。

下列範例 project.json 顯示所需的屬性︰

```json
{
  "version": "1.0.0-*",
  "buildOptions": {
    "debugType": "portable"
  },
  "dependencies": {
    "System.Runtime.Serialization.Primitives": "4.1.1",
    "xunit": "2.1.0",
    "dotnet-test-xunit": "1.0.0-rc2-192208-24"
  },
  "testRunner": "xunit",
  "frameworks": {
    "netcoreapp1.0": {
      "dependencies": {
        "Microsoft.NETCore.App": {
          "type": "platform",
          "version": "1.0.0"
        }
      },
      "imports": [
        "dotnet5.4",
        "portable-net451+win8"
      ]
    }
  }
}
```

`dotnet test` 支援兩種執行模式︰

1. 主控台︰在主控台模式中，`dotnet test` 只會完整執行任何傳遞給它的命令，並輸出結果。 只要叫用未傳遞 --port 的 `dotnet test`，就會以主控台模式執行，而執行器接著會以主控台模式執行。
2. 設計階段︰用於其他工具的內容中 (例如編輯器或整合式開發環境 (IDE))。 您可以在 [dotnet-test 通訊協定](test-protocol.md)文件中深入了解這種模式。 

## <a name="options"></a>選項

`[project]`
    
指定測試專案的路徑。 如果省略，則會預設為目前目錄。

`-?|-h|--help`

印出命令的簡短說明。

`--parentProcessId`

IDE 用來指定其處理序識別碼。 如果父處理序結束，測試就會結束。

`--port`

IDE 用來指定要接聽連線的連接埠號碼。

`-c|--configuration <Debug|Release>`

用來建置的組態。 預設值是 `Release`。 

`-o|--output [OUTPUT_DIRECTORY]`

在其中尋找要執行的二進位檔的目錄。

`-b|--build-base-path <OUTPUT_DIRECTORY>`

在其中放置暫時輸出的目錄。

`-f|--framework [FRAMEWORK]`

尋找特定架構的測試二進位檔。

`-r|--runtime [RUNTIME_IDENTIFIER]`

尋找所指定執行階段的測試二進位檔。

`--no-build` 

請不要在執行之前建置測試專案。 

## <a name="examples"></a>範例

執行目前目錄之專案中的測試：

`dotnet test` 

執行 test1 專案中的測試︰

`dotnet test /projects/test1/project.json` 

## <a name="see-also"></a>請參閱

[dotnet-test 通訊協定](test-protocol.md)

[架構](../../standard/frameworks.md)

[執行階段識別項 (RID) 目錄](../rid-catalog.md)


<!--HONumber=Feb17_HO2-->


