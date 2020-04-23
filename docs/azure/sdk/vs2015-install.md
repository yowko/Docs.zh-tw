---
title: Azure Tools For Visual Studio 2015
description: 取得工具，開始從 Visual Studio 2015 使用 Azure .NET 程式庫。
ms.date: 10/19/2017
ms.custom: azure-sdk-dotnet
ms.openlocfilehash: a29709d56f2debe04d49ee4eafdc27acd4ca480f
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2020
ms.locfileid: "82071924"
---
# <a name="azure-tools-for-visual-studio-2015"></a>Azure Tools For Visual Studio 2015

要安裝 **Azure SDK for Visual Studio 2015** 和 **Service Fabric SDK and Tools for Visual Studio 2015** 最快速且輕鬆的方式，是使用 [Web Platform Installer](https://www.microsoft.com/web/downloads/platform.aspx)。 Microsoft Web Platform Installer 是免費的工具，可簡化下載、安裝和更新一些 Microsoft Web Platform 的元件，包括 Azure tools for Visual Studio 2015。 也可從 [Azure 下載頁面](https://azure.microsoft.com/downloads/)下載這些 SDK，並安裝作為個別的元件。

## <a name="using-the-web-platform-installer"></a>使用 Web Platform Installer

1. 下載及執行此 [Web Platform Installer 啟動載入器](https://www.microsoft.com/web/handlers/webpi.ashx?command=getinstallerredirect&appid=VWDOrVs2015AzurePack;MicrosoftAzure-ServiceFabric-VS2015)。

2. 啟動載入器將會安裝 Web Platform Installer (如有需要)，並自動將最新版的 **Azure SDK for Visual Studio 2015** 和 **Service Fabric SDK and Tools for Visual Studio 2015** 項目放入 [要安裝的項目]** 清單。 按一下 [Install]  。

    ![Web Platform Installer](../media/sdk/vs2015-install/webpi.png)

3. 在下一個畫面上，按一下 [我接受]****。 Web PI 就會開始下載及安裝您選取的元件。

4. 安裝完成之後，會顯示確認畫面。 按一下 [完成]  。 您現在可以關閉 Web Platform Installer。

## <a name="verifying-the-installation"></a>驗證安裝

1. 在 Visual Studio 2015 中，按一下 [工具]**** 功能表，然後按一下 [擴充功能和更新...]****。

2. 顯示的清單會包含數個 Azure 工具，例如 **Microsoft Azure App Service 工具**、**已連線 Microsoft Azure 儲存體的服務**，和 **Service Fabric 工具**。

    ![擴充功能和更新](../media/sdk/vs2015-install/ext-tools.png)
