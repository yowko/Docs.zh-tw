---
title: 安裝 F#
description: 瞭解如何根據您F#的環境安裝。
ms.date: 09/05/2019
ms.openlocfilehash: 18b660ff640904119d63f57405752a14f7673e0c
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400724"
---
# <a name="install-f"></a>安裝 F\#

您可以透過F#多種方式安裝，視您的環境而定。

## <a name="install-f-with-visual-studio"></a>使用F# Visual Studio 安裝

如果您是第一次下載[Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) ，它會先安裝 Visual Studio 安裝程式。 從安裝程式安裝適當的 Visual Studio SKU。 如果您已經安裝它，請按一下 [**修改**]。

接下來，您會看到工作負載清單。 選取 [ **ASP.NET 和 網頁程式開發**]， F#這將會安裝 ASP.NET Core 專案的支援和 .net Core 支援。

接下來，按一下右下方的 [**修改**]。  這會安裝您所選取的所有專案。 接著，您可以按一下 [ F# **啟動**]，開啟具有語言支援的 Visual Studio 2017。

## <a name="install-f-with-visual-studio-for-mac"></a>使用F# Visual Studio for Mac 安裝

F#預設會安裝在[Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)中，不論您選擇哪一種設定。

安裝完成之後，請選擇 [開始 Visual Studio]。 您也可以透過 macOS 上的搜尋工具來啟動它。

## <a name="install-f-with-visual-studio-code"></a>使用F# Visual Studio Code 安裝

您必須在路徑上安裝並使用[git](https://git-scm.com/download) ，才能利用專案範本。 您可以在命令提示字元中輸入`git --version`並按**enter**，確認它是否已正確安裝。

### <a name="macostabmacos"></a>[macOS](#tab/macos)

[Mono](https://www.mono-project.com)用於[ F#互動式](../tutorials/fsharp-interactive/index.md)支援。 在 macOS 上安裝 Mono 最簡單的方式是透過 Homebrew。 只要在您的終端機中輸入下列內容：

```console
brew install mono
```

也請安裝[.NET Core SDK](https://www.microsoft.com/net/download)。

### <a name="linuxtablinux"></a>[Linux](#tab/linux)

[Mono](https://www.mono-project.com)用於[ F#互動式](../tutorials/fsharp-interactive/index.md)支援。 如果您是在 Debian 或 Ubuntu 上，您可以使用下列各項：

```console
sudo apt-get update
sudo apt-get install mono-complete fsharp
```

也請安裝[.NET Core SDK](https://www.microsoft.com/net/download)。

### <a name="windowstabwindows"></a>[Windows](#tab/windows)

安裝[支援的F# Visual Studio](#install-f-with-visual-studio)。 這會安裝所有必要的元件來撰寫、編譯和執行F#程式碼。

也請安裝[.NET Core SDK](https://www.microsoft.com/net/download/)。

---

接著，您將需要安裝[Visual Studio Code](https://code.visualstudio.com) 。

接下來，按一下 [延伸模組] 圖示，然後搜尋 "Ionide"：

Visual Studio Code 中F#支援的唯一外掛程式是[Ionide-fsharp.core](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp)。 不過，您也可以安裝[Ionide-假](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE)以取得[假](https://fsharp.github.io/FAKE/)的支援和[Ionide Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) ，以取得[Paket](https://fsprojects.github.io/Paket/)支援。 假和 Paket 是用F#來分別建立專案和管理相依性的額外社區工具。

## <a name="install-f-on-a-build-server"></a>在F#組建伺服器上安裝

如果您是透過 .NET SDK 使用 .NET Core 或 .NET Framework，您只需要在組建伺服器上安裝 .NET SDK。 它包含您所需的所有專案。

如果您使用 .NET Framework，而您**未**使用 .net SDK，則必須將[Visual Studio Build Tools SKU](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16)安裝到您的 Windows 伺服器上。 在安裝程式中，選取 [ **.net 桌面組建工具**]，然後選取 [安裝程式] 功能表右側的 [  **F#編譯器**] 元件。
