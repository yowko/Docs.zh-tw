---
title: 安裝F#
description: 了解如何安裝F#根據您的環境。
ms.date: 08/28/2018
ms.openlocfilehash: 873d3021ba884ec81992469e5d0f3b7c18b1e0f4
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975247"
---
# <a name="install-f"></a>安裝 F\#

您可以安裝F#以多種方式，根據您的環境。

## <a name="install-f-with-visual-studio"></a>安裝F#使用 Visual Studio

如果您正在下載[Visual Studio](https://visualstudio.microsoft.com/)第一次，它會先安裝 Visual Studio 安裝程式。 安裝適當的 SKU 的 Visual Studio 安裝程式。 如果您已經安裝，請按一下**修改**。

接下來，您會看到一份工作負載。 選取  **ASP.NET 和 web 開發**安裝F#支援和.NET Core 支援 ASP.NET Core 專案。

接下來，按一下**修改**右手邊角。  這會安裝您所選取的所有項目。 接著，您就可以開啟 Visual Studio 2017F#語言支援，即可**啟動**。

## <a name="install-f-with-visual-studio-for-mac"></a>安裝F#使用 Visual Studio for Mac

F#根據預設，在已安裝[Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/)，無論哪種設定您選擇。

安裝完成後，選擇 [啟動 Visual Studio]。 您也可以啟動它透過搜尋工具在 macOS 上。

## <a name="install-f-with-visual-studio-code"></a>安裝F#使用 Visual Studio Code

您必須擁有[安裝 git](https://git-scm.com/download) ，可在您的路徑，請使用專案範本。 您可以確認它已正確安裝輸入`git --version`在命令提示字元並按下**Enter**。

### <a name="macostabmacos"></a>[macOS](#tab/macos)

[Mono](https://www.mono-project.com)使用於[F#互動式](../tutorials/fsharp-interactive/index.md)支援。 在 macOS 上安裝 Mono 的最簡單方式是透過 Homebrew。 只要您的終端機中輸入下列：

```console
brew install mono
```

也會安裝[.NET Core SDK](https://www.microsoft.com/net/download)。

### <a name="linuxtablinux"></a>[Linux](#tab/linux)

[Mono](https://www.mono-project.com)使用於[F#互動式](../tutorials/fsharp-interactive/index.md)支援。 如果您是在 Debian 或 Ubuntu 上，您可以使用下列項目：

```console
sudo apt-get update
sudo apt-get install mono-complete fsharp
```

也會安裝[.NET Core SDK](https://www.microsoft.com/net/download)。

### <a name="windowstabwindows"></a>[Windows](#tab/windows)

安裝[Visual Studio 中使用F#支援](#install-f-with-visual-studio)。 這會安裝所有必要的元件，來撰寫、 編譯及執行F#程式碼。

也會安裝[.NET Core SDK](https://www.microsoft.com/net/download/)。

---

然後您必須[Visual Studio Code](https://code.visualstudio.com)安裝。

接下來，按一下 擴充功能圖示並搜尋"Ionide 」:

唯一的外掛程式所需的F#支援在 Visual Studio Code [Ionide fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp)。 不過，您也可以安裝[Ionide FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE)若要取得[假](https://fsharp.github.io/FAKE/)支援並[Ionide Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket)取得[Paket](https://fsprojects.github.io/Paket/)支援。 假和 Paket 是其他F#建置專案，並分別管理相依性的社群工具。
