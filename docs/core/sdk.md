---
title: ".NET Core SDK 概觀"
description: "了解 .NET Core SDK 相關資訊，這是用來建立 .NET Core 專案的一組程式庫和工具。"
keywords: .NET, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 26bc9822-e42b-48ec-b0d6-499dc604add7
ms.openlocfilehash: 8f3d0f5b3bccdd1ca25fa1202c2c727e402fe668
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="net-core-sdk-overview"></a>.NET Core SDK 概觀 

## <a name="introduction"></a>簡介
.NET Core 軟體開發套件 (SDK) 是一組程式庫和工具，可讓開發人員建立 .NET Core 應用程式和程式庫。 這是開發人員最可能取得的套件。 

它包含以下元件：

1. 用來建置應用程式的 .NET Core 命令列工具
2. 可建置及執行應用程式的 .NET Core (程式庫和執行階段)
3. 執行 [CLI 命令](tools/index.md) 與應用程式的 `dotnet` 驅動程式


## <a name="acquiring-the-net-core-sdk"></a>取得 .NET Core SDK
擁有任何工具時，第一件事都是要將工具安裝到電腦上。 您可以根據自己的案例，使用原生安裝程式來安裝 SDK，或使用安裝殼層指令碼。

原生安裝程式主要是為了開發人員電腦而設計。 SDK 是使用每個支援平台的原生安裝機制所散發 (例如 Ubuntu 上的 DEB 套件或 Windows 上的 MSI 套件組合)。 這些安裝程式會視需要安裝並設定環境，以讓使用者在安裝後可立即使用 SDK。 不過，它們也需要電腦的系統管理權限。 您可以檢視 [.NET Core installation guide](https://aka.ms/dotnetcoregs) (.NET Core 安裝指南) 上的安裝指示。

另一方面來看，安裝指令碼則不需要系統管理權限。 不過，它們也不會在電腦上安裝任何必要條件；您必須手動安裝所有必要條件。 指令碼大部分用於設定組建伺服器，或您想要安裝工具但沒有系統管理權限時 (請確實注意上述先決條件警告)。 如需詳細資訊，請參閱[安裝指令碼參考主題](tools/dotnet-install-script.md)。 如果您對如何在 CI 組建伺服器中設定 SDK 感興趣，可以查看 [CI 伺服器的 SDK](tools/using-ci-with-cli.md) 文件。 

根據預設，SDK 會以並存 (SxS) 方式進行安裝。 這表示在任何指定時間，單一電腦上可同時存在多個版本的 CLI 工具。 .NET Core 命令列工具主題的[驅動程式區段](tools/index.md#driver)中，有詳細說明如何使用正確的版本。
