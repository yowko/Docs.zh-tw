---
title: ".NET Core SDK 概觀 | Microsoft Docs"
description: ".NET Core SDK 概觀"
keywords: .NET, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 26bc9822-e42b-48ec-b0d6-499dc604add7
ms.translationtype: Human Translation
ms.sourcegitcommit: 4437ce5d344cf06d30e31911def6287999fc6ffc
ms.openlocfilehash: 1b05b7e1a2d274f02cd1222c0a90a59583d37e92
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017

---

# .NET Core SDK 概觀
<a id="net-core-sdk-overview" class="xliff"></a> 

## 簡介
<a id="introduction" class="xliff"></a>
.NET Core 軟體開發套件 (SDK) 是一組程式庫和工具，可讓開發人員建立 .NET Core 應用程式和程式庫。 這是開發人員最可能取得的套件。 

它包含以下元件：

1. 用來建置應用程式的 .NET Core 命令列工具
2. 可建置及執行應用程式的 .NET Core (程式庫和執行階段)
3. 執行 [CLI 命令](tools/index.md) 與應用程式的 `dotnet` 驅動程式


## 取得 .NET Core SDK
<a id="acquiring-the-net-core-sdk" class="xliff"></a>
擁有任何工具時，第一件事都是要將工具安裝到電腦上。 您可以根據自己的案例，使用原生安裝程式來安裝 SDK，或使用安裝殼層指令碼。

原生安裝程式主要是為了開發人員電腦而設計。 SDK 是使用每個支援平台的原生安裝機制所散發 (例如 Ubuntu 上的 DEB 套件或 Windows 上的 MSI 套件組合)。 這些安裝程式會視需要安裝並設定環境，以讓使用者在安裝後可立即使用 SDK。 不過，它們也需要電腦的系統管理權限。 您可以檢視 [.NET Core installation guide](https://aka.ms/dotnetcoregs) (.NET Core 安裝指南) 上的安裝指示。

另一方面來看，安裝指令碼則不需要系統管理權限。 不過，它們也不會在電腦上安裝任何必要條件；您必須手動安裝所有必要條件。 指令碼大部分用於設定組建伺服器，或您想要安裝工具但沒有系統管理權限時 (請確實注意上述先決條件警告)。 如需詳細資訊，請參閱[安裝指令碼參考主題](tools/dotnet-install-script.md)。 如果您對如何在 CI 組建伺服器中設定 SDK 感興趣，可以查看 [CI 伺服器的 SDK](tools/using-ci-with-cli.md) 文件。 

根據預設，SDK 會以並存 (SxS) 方式進行安裝。 這表示在任何指定時間，單一電腦上可同時存在多個版本的 CLI 工具。 .NET Core 命令列工具主題的[驅動程式區段](tools/index.md#driver)中，有詳細說明如何使用正確的版本。

