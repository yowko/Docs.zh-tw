---
title: "dotnet-migrate 命令 | .NET Core SDK"
description: "dotnet-migrate 命令會移轉專案及其所有相依性。"
keywords: "dotnet-migrate, CLI, CLI 命令, .NET Core"
author: mairaw
manager: wpickett
ms.date: 11/13/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 70285a83-4103-4617-be8b-d0e1e9a4a91d
translationtype: Human Translation
ms.sourcegitcommit: 1a84c694945fe0c77468eb77274ab46618bccae6
ms.openlocfilehash: 150d70e3f0a80f7f6e733abee3691a0fe420919f

---

#<a name="dotnet-migrate"></a>dotnet-migrate

## <a name="name"></a>名稱 
dotnet-migrate -- 將 Preview 2 .NET Core 專案移轉至 Preview 3 .NET Core 專案

## <a name="synopsis"></a>概要

`dotnet migrate [--help] [--template-file]  
    [--sdk-package-version] [--xproj-file]  
    [--skip-project-references]  [--report-file] [--format-report-file-json]
    [--skip-backup]
    [<arguments>]`

## <a name="description"></a>說明
`dotnet migrate` 命令將會移轉有效的 Preview 2 `project.json` 專案至有效 Preview 3 `csproj` 專案。 根據預設，命令將會移轉根專案和根專案包含的任何專案參考。 此行為可使用 `--skip-project-references` 選項在執行階段停用。 

移轉可在以下任一情況完成：

* 指定要移轉之 `project.json` 檔案的單一專案
* 於 `global.json` 檔案中指定的所有目錄，方法是傳遞 `global.json` 檔案的路徑
* 給定之目錄的所有遞迴子目錄 

移轉命令會在 `backup` 目錄中保留移轉的 `project.json` 檔案 (若檔案不存在則會建立)。 這可以使用 `--skip-backup` 選項覆寫。 

根據預設，移轉作業會將移轉程序的狀態輸出到標準輸出 (STDOUT)。 如果您使用 `--report-file` 選項，輸出也會儲存到您指定的檔案。 

截至 Preview 3 為止，`dotnet migrate` 命令只支援有效的 Preview 2 `project.json` 檔案。 這表示您無法使用它來將舊的 DNX 或 Preview 1 `project.json` 檔案直接移轉為 csproj；您必須先將它們移轉為 Preview 2 project.json 檔案，然後再移轉為 csproj 檔案。 在未來，我們將加入對 Preview 1 專案的支援。 

## <a name="options"></a>選項

`-h|--help`

印出命令的簡短說明。  

`-t|--template-file <TEMPLATE_FILE>`

要用於移轉的範本 csproj 檔案。 根據預設，將會使用 `dotnet new` 所置放的相同範本。 

`-v|--sdk-package-version <VERSION>`

將在已移轉之 App 中參考的 SDK 套件版本。 預設為 dotnet new 中的 SDK 版本。

`-x|--xproj-file <FILE>`

要使用之 xproj 檔案的路徑。 當專案目錄中有多個 xproj 時為必要。

`-s|--skip-project-references [Debug|Release]`

略過移轉專案參考。 根據預設，專案參考是以遞迴方式移轉。

`-r|--report-file <REPORT_FILE>`

除了主控台外，也將移轉報告輸出到檔案。

`--format-report-file-json <REPORT_FILE>`

將移轉報告檔案輸出為 json，而非使用者訊息。

`--skip-backup`

成功移轉後，略過將 project.json、global.json 和 \*.xproj 移動至 `backup` 目錄。

## <a name="examples"></a>範例

移轉目前目錄中的專案和所有其專案對專案相依性：

`dotnet migrate`

移轉 `global.json` 檔案指向的所有專案：

`dotnet migrate path/to/global.json`

只移轉目前的專案而不移轉專案對專案相依性，並使用特定的 SDK 版本：

`dotnet migrate -s -v 1.0.0-preview3`




<!--HONumber=Nov16_HO3-->


