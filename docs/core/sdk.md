---
title: .NET Core SDK 概觀
description: 了解 .NET Core SDK 相關資訊，這是用來建立 .NET Core 專案的一組程式庫和工具。
ms.date: 07/31/2019
ms.technology: dotnet-cli
ms.openlocfilehash: 0231c08f780455c4956c044815a2e80cef4d827e
ms.sourcegitcommit: 8c6426a3d2adff5fbcbe1fed0f28eda718c15351
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/02/2019
ms.locfileid: "68733383"
---
# <a name="net-core-sdk-overview"></a>.NET Core SDK 概觀

.NET Core 軟體開發套件 (SDK) 是一組程式庫和工具，可讓開發人員建立 .NET Core 應用程式和程式庫。 其中包含用來建置並執行應用程式的下列元件：

- .NET Core CLI 工具。
- .NET core 程式庫和執行階段。
- `dotnet` [驅動程式](tools/index.md#driver)。

## <a name="acquiring-the-net-core-sdk"></a>取得 .NET Core SDK

擁有任何工具時，第一件事都是要將工具安裝到電腦上。 視您的案例而定，您可以使用下列方法之一安裝 SDK：

- 使用原生的安裝程式。
- 使用安裝 Shell 指令碼。

原生安裝程式主要是為了開發人員電腦而設計。 SDK 是使用每個支援平台的原生安裝機制所散發，例如 Ubuntu 的 DEB 套件或 Windows 的 MSI 套件組合。 這些安裝程式會視需要安裝並設定環境，以讓使用者在安裝後可立即使用 SDK。 不過，它們也需要電腦的系統管理權限。 您可以在 [.NET 下載](https://dotnet.microsoft.com/download)頁面上找到要安裝的 SDK。

另一方面，安裝指令碼不需要系統管理權限。 不過，它們也不會在電腦上安裝任何必要條件；您需要手動安裝所有必要條件。 指令碼大部分用於設定組建伺服器，或您想要安裝工具但沒有系統管理權限時 (請確實注意上述先決條件警告)。 您可在[安裝指令碼參考](tools/dotnet-install-script.md)一文中取得需詳細資訊。 如對如何在 CI 組建伺服器上設定 SDK 有興趣，請參閱[在持續整合 (CI) 中使用 .NET Core SDK 和工具](tools/using-ci-with-cli.md)一文。

根據預設，SDK 會以「並存」(SxS) 的形式安裝，這表示一部電腦上可以同時存在多個版本的 CLI 工具。 如需了解執行 CLI 命令時如何挑選版本的詳細說明，請參閱[選取要使用的 .NET Core 版本](versions/selection.md)一文。

## <a name="see-also"></a>另請參閱

- [.NET Core CLI](tools/index.md)
- [.NET Core 版本控制概觀](versions/index.md)
- [如何移除 .NET Core 執行階段和 SDK](versions/remove-runtime-sdk-versions.md)
- [選取要使用的 .NET Core 版本](versions/selection.md)
