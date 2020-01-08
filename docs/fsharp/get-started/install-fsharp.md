---
title: 安裝 F#
description: 瞭解如何以各種F#不同的方式安裝。
ms.date: 12/20/2019
ms.openlocfilehash: 302e04f7cf3271516dff88d9d5f18f620b6ede80
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346557"
---
# <a name="install-f"></a>安裝 F\#

您可以透過F#多種方式安裝，視您的環境而定。

## <a name="install-f-with-visual-studio"></a>使用F# Visual Studio 安裝

1. 如果您是第一次下載[Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ，它會先安裝 Visual Studio 安裝程式。 從安裝程式安裝適當版本的 Visual Studio。

   如果您已安裝 Visual Studio，請選擇您想要新增F#至的版本旁邊的 [修改]。

2. 在 [工作負載] 頁面上，選取 [ **ASP.NET 和 網頁程式開發**] F#工作負載，其中包含 ASP.NET CORE 專案的和 .net Core 支援。

3. 選擇右下角的 [**修改**]，以安裝您所選取的所有專案。

   然後在 Visual Studio 安裝程式中選擇 [ F# **啟動**]，即可開啟 Visual Studio。

## <a name="install-f-with-visual-studio-code"></a>使用F# Visual Studio Code 安裝

1. 請確定您已在您的路徑上安裝並使用[git](https://git-scm.com/download) 。 您可以在命令提示字元中輸入 `git --version`，然後按**enter**鍵，確認它已正確安裝。

2. 安裝[.NET Core SDK](https://dotnet.microsoft.com/download)和[Visual Studio Code](https://code.visualstudio.com)。

3. 選取 [延伸模組] 圖示，並搜尋 "Ionide"：

   Visual Studio Code 中F#支援的唯一外掛程式是[Ionide-fsharp.core](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp)。 不過，您也可以安裝[Ionide-假](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE)以取得[假](https://fake.build/)的支援和[Ionide Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) ，以取得[Paket](https://fsprojects.github.io/Paket/)支援。 假和 Paket 是用F#來分別建立專案和管理相依性的額外社區工具。

## <a name="install-f-with-visual-studio-for-mac"></a>使用F# Visual Studio for Mac 安裝

F#預設會安裝在[Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)中，不論您選擇哪一種設定。

安裝完成之後，請選擇 [**開始 Visual Studio**]。 您也可以透過 macOS 上的搜尋工具開啟 Visual Studio。

## <a name="install-f-on-a-build-server"></a>在F#組建伺服器上安裝

如果您是透過 .NET SDK 使用 .NET Core 或 .NET Framework，您只需要在組建伺服器上安裝 .NET SDK。 它包含您所需的所有專案。

如果您使用 .NET Framework，而您**未**使用 .net SDK，則必須將[Visual Studio Build Tools SKU](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16)安裝到您的 Windows 伺服器上。 在安裝程式中，選取 [ **.net 桌面組建工具**]，然後選取 [安裝程式] 功能表右側的 [  **F#編譯器**] 元件。
