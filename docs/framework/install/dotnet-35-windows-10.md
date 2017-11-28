---
title: "在 Windows 10、Windows 8.1 及 Windows 8 上安裝 .NET Framework 3.5"
description: "了解如何在 Windows 10、Windows 8.1 及 Windows 8 上安裝 .NET Framework 3.5。"
author: rlander
ms.author: mairaw
keywords: ".NET Framework, 安裝"
ms.date: 05/26/2017
ms.topic: article
ms.prod: .net-framework
ms.technology: vs-ide-deployment
ms.devlang: dotnet
ms.assetid: 67cda1d5-c6g4-4eb5-93e6-4f478de07ff7
ms.openlocfilehash: 85a3cada074714c24015d90c26d94551f4f411f2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="install-the-net-framework-35-on-windows-10-windows-81-and-windows-8"></a><span data-ttu-id="3b7dc-104">在 Windows 10、Windows 8.1 及 Windows 8 上安裝 .NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="3b7dc-104">Install the .NET Framework 3.5 on Windows 10, Windows 8.1, and Windows 8</span></span>

<span data-ttu-id="3b7dc-105">您可能需要 .NET Framework 3.5，才能在 Windows 10、Windows 8.1 及 Windows 8 上執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="3b7dc-105">You may need the .NET Framework 3.5 to run an app on Windows 10, Windows 8.1, and Windows 8.</span></span> <span data-ttu-id="3b7dc-106">這些指示也適用於較舊的 Windows 版本。</span><span class="sxs-lookup"><span data-stu-id="3b7dc-106">You can also use these instructions for earlier Windows versions.</span></span>

## <a name="install-the-net-framework-35-on-demand"></a><span data-ttu-id="3b7dc-107">視需要安裝 .NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="3b7dc-107">Install the .NET Framework 3.5 on Demand</span></span>

<span data-ttu-id="3b7dc-108">如果您嘗試執行需要 .NET Framework 3.5 的應用程式，可能會看到下列設定對話方塊。</span><span class="sxs-lookup"><span data-stu-id="3b7dc-108">You may see the following configuration dialog if you try to run an app that requires the .NET Framework 3.5.</span></span> <span data-ttu-id="3b7dc-109">請選擇 [安裝此功能] 來啟用 .NET Framework 3.5。</span><span class="sxs-lookup"><span data-stu-id="3b7dc-109">Choose **Install this feature** to enable the .NET Framework 3.5.</span></span> <span data-ttu-id="3b7dc-110">這個選項需要網際網路連線。</span><span class="sxs-lookup"><span data-stu-id="3b7dc-110">This option requires an Internet connection.</span></span>

![.NET Framework 安裝對話方塊](./media/dotnet-framework-installation-dialog.jpg)

## <a name="enable-the-net-framework-35-in-control-panel"></a><span data-ttu-id="3b7dc-112">在控制台中啟用 .NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="3b7dc-112">Enable the .NET Framework 3.5 in Control Panel</span></span>

<span data-ttu-id="3b7dc-113">您可以透過 Windows 的 [控制台] 啟用 .NET Framework 3.5。</span><span class="sxs-lookup"><span data-stu-id="3b7dc-113">You can enable the .NET Framework 3.5 through the Windows Control Panel.</span></span> <span data-ttu-id="3b7dc-114">這個選項需要網際網路連線。</span><span class="sxs-lookup"><span data-stu-id="3b7dc-114">This option requires an Internet connection.</span></span>

1. <span data-ttu-id="3b7dc-115">按下鍵盤上的 Windows 鍵 ![Windows 標誌](https://i-msdn.sec.s-msft.com/dynimg/IC721376.jpeg)，鍵入「Windows 功能」，然後按 Enter 鍵。</span><span class="sxs-lookup"><span data-stu-id="3b7dc-115">Press the Windows key Windows ![Windows logo](https://i-msdn.sec.s-msft.com/dynimg/IC721376.jpeg) on your keyboard, type "Windows Features", and press Enter.</span></span> <span data-ttu-id="3b7dc-116">[開啟或關閉 Windows 功能] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="3b7dc-116">The **Turn Windows features on or off** dialog box appears.</span></span>

2. <span data-ttu-id="3b7dc-117">選取 [.NET Framework 3.5 (包括 .NET 2.0 和 3.0)] 核取方塊，選取 [確定]，然後在出現提示時重新啟動電腦。</span><span class="sxs-lookup"><span data-stu-id="3b7dc-117">Select the **.NET Framework 3.5 (includes .NET 2.0 and 3.0)** check box, select **OK**, and reboot your computer if prompted.</span></span>

   ![使用控制台來安裝 .NET](./media/dotnet-control-panel.png)

   <span data-ttu-id="3b7dc-119">您不需要選取 [Windows Communication Foundation (WCF) HTTP 啟用] 和 [Windows Communication Foundation (WCF) 非 HTTP 啟用] 的子項目，除非您是需要這項功能的開發人員或伺服器系統管理員。</span><span class="sxs-lookup"><span data-stu-id="3b7dc-119">You don't need to select the child items for **Windows Communication Foundation (WCF) HTTP Activation** and **Windows Communication Foundation (WCF) Non-HTTP Activation** unless you're a developer or server administrator who requires this functionality.</span></span>
