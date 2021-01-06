---
title: 使用 .NET 設定適用于 Azure 開發的 Visual Studio Code
description: 本文可協助您設定 Azure 開發的 Visual Studio Code，包括在 VS Code 中安裝及設定正確的外掛程式。
ms.date: 11/30/2020
ms.topic: conceptual
ms.custom: devx-track-dotnet
ms.author: daberry
author: daberry
ms.openlocfilehash: 65ced99befe12d137062b4ea6a59a1ccd3099e0b
ms.sourcegitcommit: 3d6d6595a03915f617349781f455f838a44b0f44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2020
ms.locfileid: "97701105"
---
# <a name="configure-visual-studio-code-for-azure-development"></a>設定適用于 Azure 開發的 Visual Studio Code

如果您要使用 Visual Studio Code （不論是針對 .NET 開發）使用像是角度、回應或 Vue 等架構來建立單一頁面應用程式，或是以 Python 等其他語言撰寫應用程式，則您會想要設定 Azure 開發的 Visual Studio Code。

### <a name="download-visual-studio-code"></a>下載 Visual Studio Code

如果您已經安裝 Visual Studio Code，可以略過此步驟

> [!div class="nextstepaction"]
> [下載 Visual Studio Code](https://code.visualstudio.com/download)

### <a name="install-the-azure-tools-extension-pack"></a>安裝 Azure Tools 擴充功能套件

[Azure Tools 擴充套件](https://marketplace.visualstudio.com/items?itemName=ms-vscode.vscode-node-azure-pack)包含的延伸模組可搭配使用 Azure App Service、Azure Functions、Azure 儲存體、Cosmos DB 和 Azure 虛擬機器，全都放在一個方便的套件中。

若要從 Visual Studio Code 安裝延伸模組：

1. 按 <kbd>Ctrl + Shift + X</kbd> 以開啟 [ **擴充** 功能] 視窗。
1. 搜尋 *Azure Tools* 擴充功能。
1. 選取 [安裝] 按鈕。

![Visual Studio Code 的螢幕擷取畫面，其中顯示搜尋 Azure Tools 擴充功能套件的延伸模組面板](./media/visual-studio-code-azure-tools.png)

若要深入瞭解如何在 Visual Studio Code 中安裝擴充功能，請參閱 Visual Studio Code 網站上的 [延伸模組 Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery) 檔。

### <a name="sign-in-to-your-azure-account-with-azure-tools"></a>使用 Azure Tools 登入您的 Azure 帳戶

在左側面板上，您會看到 Azure 圖示。 選取此圖示，將會顯示 Azure 服務的控制台。 選擇 [登 **入 Azure ...** ] 下的任何服務，在 Visual Studio Code 中完成 azure 工具的驗證程式。

![顯示如何將 Azure tools 登入 Azure 的 Visual Studio Code 螢幕擷取畫面](./media/visual-studio-code-azure-login.png)

### <a name="next-steps"></a>後續步驟

接下來，您會想要在您的工作站上安裝 Azure CLI。

> [!div class="nextstepaction"]
> [安裝 Azure CLI](./install-azure-cli.md)
