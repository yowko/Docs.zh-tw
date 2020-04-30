---
title: .NET Core SDK 概觀
description: 了解 .NET Core SDK 相關資訊，這是用來建立 .NET Core 專案的一組程式庫和工具。
ms.date: 07/31/2019
ms.technology: dotnet-cli
ms.openlocfilehash: 7eb06e4fd94ed2a73af2741e98e21e02728c27e4
ms.sourcegitcommit: d7666f6e49c57a769612602ea7857b927294ce47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2020
ms.locfileid: "82595737"
---
# <a name="net-core-sdk-overview"></a>.NET Core SDK 概觀

.NET Core SDK 是可讓開發人員建立 .NET Core 應用程式與程式庫的一組程式庫與工具。 其中包含用來建置並執行應用程式的下列元件：

- .NET Core CLI。
- .NET core 程式庫和執行階段。
- `dotnet` [驅動程式](tools/index.md#driver)。

## <a name="acquiring-the-net-core-sdk"></a>取得 .NET Core SDK

使用任何工具時，第一件事都是要取得適合電腦的工具。 視您的案例而定，您可以使用下列方法之一安裝 SDK：

- 使用原生的安裝程式。
- 使用安裝 Shell 指令碼。

原生安裝程式主要是為了開發人員電腦而設計。 SDK 是使用每個支援平台的原生安裝機制所散發，例如 Ubuntu 的 DEB 套件或 Windows 的 MSI 套件組合。 這些安裝程式會視需要安裝並設定環境，以讓使用者在安裝後可立即使用 SDK。 不過，它們也需要電腦的系統管理權限。 您可以在 [.NET 下載](https://dotnet.microsoft.com/download)頁面上找到要安裝的 SDK。

另一方面，安裝指令碼不需要系統管理權限。 不過，它們也不會在電腦上安裝任何必要條件；您需要手動安裝所有必要條件。 指令碼大部分用於設定組建伺服器，或您想要安裝工具但沒有系統管理權限時 (請確實注意上述先決條件警告)。 您可在[安裝指令碼參考](tools/dotnet-install-script.md)一文中取得需詳細資訊。 如對如何在 CI 組建伺服器上設定 SDK 有興趣，請參閱[在持續整合 (CI) 中使用 .NET Core SDK 和工具](tools/using-ci-with-cli.md)一文。

根據預設，SDK 會以「並存」（SxS）的方式安裝，這表示單一電腦上的任何指定時間都可以共存多個版本。 如需了解執行 CLI 命令時如何挑選版本的詳細說明，請參閱[選取要使用的 .NET Core 版本](versions/selection.md)一文。

## <a name="see-also"></a>另請參閱

- [.NET Core CLI 概觀](tools/index.md)
- [.NET Core 版本控制概觀](versions/index.md)
- [如何移除 .NET Core 執行時間和 SDK](install/remove-runtime-sdk-versions.md)
- [選取要使用的 .NET Core 版本](versions/selection.md)
