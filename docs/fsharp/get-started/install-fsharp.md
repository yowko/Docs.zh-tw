---
title: 安裝 F#
description: 瞭解如何以各種不同方式安裝 F#。
ms.date: 12/20/2019
ms.openlocfilehash: 302e04f7cf3271516dff88d9d5f18f620b6ede80
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400243"
---
# <a name="install-f"></a>安裝 F\#

您可以根據環境以多種方式安裝 F#。

## <a name="install-f-with-visual-studio"></a>使用視覺化工作室安裝 F#

1. 如果您是首次下載[視覺化工作室](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)，它將首先安裝視覺化工作室安裝程式。 從安裝程式安裝相應的視覺工作室版本。

   如果已安裝 Visual Studio，請選擇要向其添加 F# 的版本旁邊的 **"修改**"。

2. 在"工作負載"頁上，選擇**ASP.NET和 Web 開發**工作負載，其中包括 ASP.NET核心專案的 F# 和 .NET Core 支援。

3. 在右下角選擇 **"修改"** 以安裝您選擇的所有內容。

   然後，您可以通過選擇"在視覺化工作室安裝程式中**啟動"** 來打開帶有 F# 的視覺化工作室。

## <a name="install-f-with-visual-studio-code"></a>使用視覺化工作室代碼安裝 F#

1. 確保您已安裝[git](https://git-scm.com/download)並在您的 PATH 上可用。 您可以通過在命令提示符處輸入`git --version`並按**Enter**來驗證其安裝是否正確。

2. 安裝[.NET 核心 SDK](https://dotnet.microsoft.com/download)和[視覺化工作室代碼](https://code.visualstudio.com)。

3. 選擇"擴展"圖示並搜索"Ionide"：

   在視覺工作室代碼中 F# 支援的唯一外掛程式是[Ionide-fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp)。 但是，您也可以安裝[Ionide-FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE)以獲得[FAKE](https://fake.build/)支援和[Ionide-Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket)以獲得[Paket](https://fsprojects.github.io/Paket/)支援。 FAKE 和 Paket 是用於構建專案和管理依賴項的其他 F# 社區工具。

## <a name="install-f-with-visual-studio-for-mac"></a>安裝 F# 與 Mac 的視覺工作室

F# 預設安裝在[Mac 的 Visual Studio](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)中，無論您選擇哪種配置。

安裝完成後，選擇 **"開始視覺化工作室**"。 您還可以在 macOS 上通過 Finder 打開視覺工作室。

## <a name="install-f-on-a-build-server"></a>在生成伺服器上安裝 F#

如果您通過 .NET SDK 使用 .NET Core 或 .NET 框架，只需在生成伺服器上安裝 .NET SDK 即可。 它有你需要的一切。

如果您使用的是 .NET 框架，**並且沒有**使用 .NET SDK，則需要將[視覺化工作室構建工具 SKU](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16)安裝到 Windows 伺服器上。 在安裝程式中，選擇 **.NET 桌面生成工具**，然後在安裝程式功能表右側選擇**F# 編譯器**元件。
