---
title: 安裝 F#
description: '瞭解如何以各種不同的方式安裝 F #。'
ms.date: 12/20/2019
ms.openlocfilehash: 302e04f7cf3271516dff88d9d5f18f620b6ede80
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/20/2020
ms.locfileid: "92224290"
---
# <a name="install-f"></a>安裝 F\#

您可以用多種方式安裝 F #，視您的環境而定。

## <a name="install-f-with-visual-studio"></a>使用 Visual Studio 安裝 F #

1. 如果您是第一次下載 [Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ，它會先安裝 Visual Studio 安裝程式。 從安裝程式安裝適當的 Visual Studio 版本。

   如果您已經安裝 Visual Studio，請選擇您想要新增 F # 的版本旁的 [ **修改** ]。

2. 在 [工作負載] 頁面上，選取 [ **ASP.NET] 和 [網頁程式開發** ] 工作負載，其中包含 ASP.NET Core 專案的 F # 和 .net Core 支援。

3. 選擇右下角的 [ **修改** ]，以安裝您所選取的所有專案。

   然後，您可以在 Visual Studio 安裝程式中選擇 [ **啟動** ]，以 F # 開啟 Visual Studio。

## <a name="install-f-with-visual-studio-code"></a>使用 Visual Studio Code 安裝 F #

1. 確定您已在路徑上安裝並提供 [git](https://git-scm.com/download) 。 您可以 `git --version` 在命令提示字元中輸入，然後按 **enter**，確認它是否已正確安裝。

2. 安裝 [.NET Core SDK](https://dotnet.microsoft.com/download) 並 [Visual Studio Code](https://code.visualstudio.com)。

3. 選取擴充功能圖示，並搜尋 "Ionide"：

   Visual Studio Code 中 F # 支援所需的唯一外掛程式是 [Ionide-fsharp.core](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp)。 不過，您也可以安裝 [Ionide-假](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) 以取得 [假](https://fake.build/) 的支援和 [Ionide Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) ，以取得 [Paket](https://fsprojects.github.io/Paket/) 支援。 假和 Paket 是其他 F # 的工具，可分別用來建立專案和管理相依性。

## <a name="install-f-with-visual-studio-for-mac"></a>使用 Visual Studio for Mac 安裝 F #

依預設，F # 會安裝在 [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)中，不論您選擇哪一種設定。

安裝完成之後，請選擇 [ **開始 Visual Studio**]。 您也可以透過 macOS 上的搜尋工具開啟 Visual Studio。

## <a name="install-f-on-a-build-server"></a>在組建伺服器上安裝 F #

如果您是透過 .NET SDK 使用 .NET Core 或 .NET Framework，則只需要在您的組建伺服器上安裝 .NET SDK。 它具有您所需的一切。

如果您使用 .NET Framework 而 **不** 是使用 .net SDK，則您必須在 Windows Server 上安裝 [Visual Studio Build Tools SKU](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16) 。 在安裝程式中，選取 [ **.net 桌面 build tools**]，然後選取安裝程式功能表右邊的 **F # 編譯器** 元件。
