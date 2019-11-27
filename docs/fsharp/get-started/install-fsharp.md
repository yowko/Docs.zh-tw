---
title: 安裝 F#
description: 瞭解如何根據您F#的環境安裝。
ms.date: 09/05/2019
ms.openlocfilehash: 592a4c7763266cee68809fca84f9604d7e96b8f1
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204879"
---
# <a name="install-f"></a>安裝 F\#

您可以透過F#多種方式安裝，視您的環境而定。

## <a name="install-f-with-visual-studio"></a>使用F# Visual Studio 安裝

如果您是第一次下載[Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) ，它會先安裝 Visual Studio 安裝程式。 從安裝程式安裝適當的 Visual Studio SKU。 如果您已經安裝它，請按一下 [**修改**]。

接下來，您會看到工作負載清單。 選取 [ **ASP.NET 和 網頁程式開發**]， F#這將會安裝 ASP.NET Core 專案的支援和 .net Core 支援。

接下來，按一下右下方的 [**修改**]。  這會安裝您所選取的所有專案。 接著，您可以按一下 [ F# **啟動**]，開啟具有語言支援的 Visual Studio 2017。

## <a name="install-f-with-visual-studio-code"></a>使用F# Visual Studio Code 安裝

首先，請確定您已在您的路徑上安裝並使用[git](https://git-scm.com/download) 。 您可以在命令提示字元中輸入 `git --version`，然後按**enter**鍵，確認是否已正確安裝。

接下來，安裝[.NET Core SDK](https://dotnet.microsoft.com/download)。

接著，您將需要安裝[Visual Studio Code](https://code.visualstudio.com) 。

接下來，按一下 [延伸模組] 圖示，然後搜尋 "Ionide"：

Visual Studio Code 中F#支援的唯一外掛程式是[Ionide-fsharp.core](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp)。 不過，您也可以安裝[Ionide-假](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE)以取得[假](https://fake.build/)的支援和[Ionide Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) ，以取得[Paket](https://fsprojects.github.io/Paket/)支援。 假和 Paket 是用F#來分別建立專案和管理相依性的額外社區工具。

## <a name="install-f-with-visual-studio-for-mac"></a>使用F# Visual Studio for Mac 安裝

F#預設會安裝在[Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)中，不論您選擇哪一種設定。

安裝完成之後，請選擇 [開始 Visual Studio]。 您也可以透過 macOS 上的搜尋工具來啟動它。

## <a name="install-f-on-a-build-server"></a>在F#組建伺服器上安裝

如果您是透過 .NET SDK 使用 .NET Core 或 .NET Framework，您只需要在組建伺服器上安裝 .NET SDK。 它包含您所需的所有專案。

如果您使用 .NET Framework，而您**未**使用 .net SDK，則必須將[Visual Studio Build Tools SKU](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16)安裝到您的 Windows 伺服器上。 在安裝程式中，選取 [ **.net 桌面組建工具**]，然後選取 [安裝程式] 功能表右側的 [  **F#編譯器**] 元件。
