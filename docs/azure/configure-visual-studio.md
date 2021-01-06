---
title: 使用 .NET 設定適用于 Azure 開發的 Visual Studio
description: 本文可協助您設定適用于 Azure 開發的 Visual Studio，包括將正確的工作負載安裝並連接 Visual Studio 至您的 Azure 帳戶
ms.date: 11/30/2020
ms.topic: conceptual
ms.custom: devx-track-dotnet
ms.author: daberry
author: daberry
ms.openlocfilehash: 986469bd07657d968045465803047dc21d76dd62
ms.sourcegitcommit: 3d6d6595a03915f617349781f455f838a44b0f44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2020
ms.locfileid: "97701108"
---
# <a name="configure-visual-studio-for-azure-development-with-net"></a>使用 .NET 設定適用于 Azure 開發的 Visual Studio

Visual Studio 包含可協助您在 Azure 上開發和部署應用程式的工具。  本指南將協助您確定已針對 Azure 開發正確設定 Visual Studio。

### <a name="download-visual-studio-2019"></a>下載 Visual Studio 2019

如果您已經安裝 Visual Studio 2019，可以略過此步驟。

> [!div class="nextstepaction"]
> [下載 Visual Studio 2019](https://www.visualstudio.com/downloads/)

### <a name="install-azure-workloads"></a>安裝 Azure 工作負載

啟動 **Visual Studio 安裝程式** ，並驗證您已安裝 **Azure 開發** 和 **ASP.NET 和 網頁程式開發** 的工作負載。  如果未安裝這些工作負載的其中一個，請選取這些工作負載來進行安裝。

![Visual Studio 安裝程式的螢幕擷取畫面，其中顯示已選取的 Azure 開發和 ASP.NET 和 Web 開發工作負載](./media/visual-studio-installer-azure-development.png)

### <a name="authenticate-visual-studio-with-azure"></a>使用 Azure 驗證 Visual Studio

透過 Visual Studio 來對應用程式進行偵錯工具時，Visual Studio 可以使用您的 Azure 帳戶來驗證和存取 Azure 資源。  當您直接從 Visual Studio 將應用程式發佈至 Azure 時，也會使用此帳戶。

若要從 Visual Studio 驗證您的 Azure 帳戶，請選取 [**工具**  >  **選項**] 功能表來啟動 [**選項**] 對話方塊。 流覽至 `Azure Service Authentication` 選項，然後使用您的 Azure 帳戶登入。

![顯示 Azure 登入之 [Visual Studio 選項] 對話方塊的螢幕擷取畫面](./media/visual-studio-azure-login-dialog.png)

### <a name="next-steps"></a>後續步驟

如果您也使用 [Visual Studio Code](https://code.visualstudio.com/) 在 .net 或任何其他語言中進行開發，您也應該 [設定適用于 Azure 開發的 Visual Studio Code](./configure-vs-code.md)。 否則，請繼續 [安裝 Azure CLI](./install-azure-cli.md)。
