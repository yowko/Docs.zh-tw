---
title: "dotnet-new 命令 | .NET Core"
description: "dotnet-new 命令會在目前的目錄中建立新的 .NET Core 專案。"
keywords: "dotnet-new, CLI, CLI 命令, .NET Core"
author: mairaw
manager: wpickett
ms.date: 10/12/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 263c3d05-3a47-46a6-8023-3ca16b488410
translationtype: Human Translation
ms.sourcegitcommit: c6ee3f5663d0a3f62914e8de474cca4d15340c9d
ms.openlocfilehash: 29ccc12ff893d316c816d22da862f90bfc9334ff

---

#<a name="dotnetnew"></a>dotnet-new

## <a name="name"></a>名稱
dotnet-new -- 在目前的目錄中建立新的 .NET Core 專案

## <a name="synopsis"></a>概要
`dotnet new [--help] [--type] [--lang]`

## <a name="description"></a>描述
`dotnet new` 命令提供便利的方式來初始化有效的 .NET Core 專案和範例原始程式碼，以試用命令列介面 (CLI) 工具組。 

這個命令是在目錄的內容中叫用。 叫用時，這個命令會產生將放置到目前目錄的兩個主要成品︰ 

1. 包含範例 "Hello World" 程式的 `Program.cs` (或 `Program.fs`) 檔案。
2. 有效的 `project.json` 檔案。

在此之後，專案即可進行編譯並 (或) 進一步編輯。 

## <a name="options"></a>選項

`-h|--help`

印出命令的簡短說明。  

`-l|--lang <C#|F#>`

專案的語言。 預設值為 `C#`。 其他有效值為 `csharp`、`fsharp`、`cs` 和 `fs`。

`-t|--type`

專案的類型。 C# 的有效值為 `console`、`web`、`lib` 和 `xunittest`，而 F# 的有效值僅為 `console`。 

## <a name="examples"></a>範例

在目前的目錄中建立 C# 主控台應用程式專案：

`dotnet new` 或 `dotnet new --lang c#` 
   
在目前的目錄中建立 F# 主控台應用程式專案：

`dotnet new --lang f#`
  
在目前的目錄中建立新的 ASP.NET Core C# 應用程式專案：

`dotnet new -t web`


<!--HONumber=Nov16_HO1-->


