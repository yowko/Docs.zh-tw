---
title: .NET SDK 總覽
description: 瞭解 .NET SDK，這是用來建立 .NET 專案的一組程式庫和工具。
ms.date: 07/31/2019
ms.technology: dotnet-cli
ms.openlocfilehash: 5236d4abec5dcbf950059dd906958158cfb592fe
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2021
ms.locfileid: "99216137"
---
# <a name="net-sdk-overview"></a>.NET SDK 總覽

.NET SDK 是一組程式庫和工具，可讓開發人員建立 .NET 應用程式和程式庫。 其中包含用來建置並執行應用程式的下列元件：

- .NET CLI。
- .NET 程式庫和執行時間。
- `dotnet`[驅動程式](tools/index.md#driver)。

## <a name="acquiring-the-net-sdk"></a>取得 .NET SDK

使用任何工具時，第一件事都是要取得適合電腦的工具。 視您的案例而定，您可以使用下列方法之一安裝 SDK：

- 使用原生的安裝程式。
- 使用安裝 Shell 指令碼。

原生安裝程式主要是為了開發人員電腦而設計。 SDK 是使用每個支援平台的原生安裝機制所散發，例如 Ubuntu 的 DEB 套件或 Windows 的 MSI 套件組合。 這些安裝程式會視需要安裝並設定環境，以讓使用者在安裝後可立即使用 SDK。 不過，它們也需要電腦的系統管理權限。 您可以在 [.NET 下載](https://dotnet.microsoft.com/download)頁面上找到要安裝的 SDK。

另一方面，安裝指令碼不需要系統管理權限。 不過，它們也不會在電腦上安裝任何必要條件；您需要手動安裝所有必要條件。 指令碼大部分用於設定組建伺服器，或您想要安裝工具但沒有系統管理權限時 (請確實注意上述先決條件警告)。 您可在[安裝指令碼參考](tools/dotnet-install-script.md)一文中取得需詳細資訊。 如果您想瞭解如何在您的 CI 組建伺服器上設定 SDK，請參閱 [使用 .NET SDK 和持續整合 (CI 中的工具) ](tools/using-ci-with-cli.md) 文章。

根據預設，SDK 會以「並存」 (SxS) 方式安裝，這表示單一電腦上的任何指定時間都可以並存的多個版本。 當您執行 CLI 命令時，會在 [ [選取要使用的 .net 版本](versions/selection.md) ] 文章中更詳細地說明版本的選取方式。

## <a name="see-also"></a>另請參閱

- [.NET CLI 總覽](tools/index.md)
- [.NET 版本控制總覽](versions/index.md)
- [如何移除 .NET 執行時間和 SDK](install/remove-runtime-sdk-versions.md)
- [選取要使用的 .NET 版本](versions/selection.md)
