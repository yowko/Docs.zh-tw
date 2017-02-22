---
title: "dotnet-new 命令 | Microsoft Docs"
description: "dotnet-new 命令會在目前的目錄中建立新的 .NET Core 專案。"
keywords: "dotnet-new, CLI, CLI 命令, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 02/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: fcc3ed2e-9265-4d50-b59e-dc2e5c190b34
translationtype: Human Translation
ms.sourcegitcommit: 96fd8ea3e55ea33e0bdd0bf3c50a10d0de6db1a1
ms.openlocfilehash: f0c62647c5817db2057c60a7a95a62f08f7889a5

---
#<a name="dotnet-new-net-core-tools-rc4"></a>dotnet-new (.NET Core 工具 RC4)

> [!WARNING]
> 本主題適用於 .NET Core 工具 RC4。 .NET Core 工具 Preview 2 版本，請參閱 [dotnet-new](../../tools/dotnet-new.md) 主題。

## <a name="name"></a>名稱
dotnet-new - 在目前的目錄中建立新的 .NET Core 專案

## <a name="synopsis"></a>概要
```
dotnet new [template] [-lang|--language] [-n|--name] [-o|--output] [-h|--help]
dotnet new [template] [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```

## <a name="description"></a>說明
`dotnet new` 命令提供便利的方式來初始化有效的 .NET Core 專案和範例原始程式碼，以試用命令列介面 (CLI) 工具組。 

這個命令是在目錄的內容中叫用。 叫用時，命令會根據範本和傳遞到命令的選項，建立出資源和檔案。 

在此之後，專案即可進行編譯並 (或) 進一步編輯。 

## <a name="arguments"></a>引數
template - 要在叫用命令時執行個體化的範本。

命令包含預設的範本清單。使用 `dotnet new --help`。 

## <a name="options"></a>選項

`-l|--list`         

列出包含指定名稱的範本。

`-lang|--language`  

指定要建立的範本語言

`-n|--name`         

正在建立輸出的名稱。 如果未指定名稱，則會使用目前目錄的名稱。

`-o|--output`       

放置所產生輸出的位置。

`-all|--show-all`   

顯示特定專案類型的所有範本。

`-h|--help`

印出命令的說明。

## <a name="template-options"></a>範本選項
每個專案範本都可能會有其他可用的選項。 例如，核心範本會有下列各項。

**console、xunit、mstest**

`-f|--framework` - 指定要將哪個架構當成目標。 值：netcoreapp1.0 或 netcoreapp1.1 (預設值：netcoreapp1.0)

**web、webapi**

`-f|--framework` - 指定要將哪個架構當成目標。 值：netcoreapp1.0 或 netcoreapp1.1 (預設值：netcoreapp1.0)
 
**mvc**

`-f|--framework` - 指定要將哪個架構當成目標。 值：netcoreapp1.0 或 netcoreapp1.1 (預設值：netcoreapp1.0)

`-au|--authentication` -  要使用的驗證類型。 值︰無或個別 (預設值︰ 無)

`-uld|--use-local-db` - 是否要使用 LocalDB，而不是 SQLite。 值：true 或 false (預設值：false)

**classlib**

`-f|--framework` - 指定要將哪個架構當成目標。 值︰netcoreapp1.0、netcoreapp1.1 及 netstandard1.0 - 1.6 (預設值︰netstandard1.4)。

## <a name="examples"></a>範例

在目前的目錄中建立 F# 主控台應用程式專案：

`dotnet new console -lang f#` 
   
未經驗證即在目前的目錄中，建立以 .NET Core 1.0 為目標新的 ASP.NET Core C# MVC 應用程式專案：  

`dotnet new mvc -au None -f netcoreapp1.0`
 
建立以 .NET Core 1.1 為目標的新 XUnit 應用程式：

`dotnet new xunit --Framework netcoreapp1.1`

列出 MVC 可用的所有範本：

`dotnet new mvc -l`


<!--HONumber=Feb17_HO3-->


