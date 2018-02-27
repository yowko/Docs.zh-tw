---
title: "在 Windows 10、Windows 8.1 及 Windows 8 上安裝 .NET Framework 3.5"
description: "了解如何在 Windows 10、Windows 8.1 及 Windows 8 上安裝 .NET Framework 3.5。"
author: rlander
ms.author: mairaw
ms.date: 11/27/2017
ms.topic: article
ms.prod: .net-framework
ms.workload:
- dotnet
ms.openlocfilehash: e81008eca3019860789db548d40998a7a7565d31
ms.sourcegitcommit: cec0525b2121c36198379525e69aa5388266db5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="install-the-net-framework-35-on-windows-10-windows-81-and-windows-8"></a><span data-ttu-id="d4b0e-103">在 Windows 10、Windows 8.1 及 Windows 8 上安裝 .NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="d4b0e-103">Install the .NET Framework 3.5 on Windows 10, Windows 8.1, and Windows 8</span></span>

<span data-ttu-id="d4b0e-104">您可能需要 .NET Framework 3.5，才能在 Windows 10、Windows 8.1 及 Windows 8 上執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="d4b0e-104">You may need the .NET Framework 3.5 to run an app on Windows 10, Windows 8.1, and Windows 8.</span></span> <span data-ttu-id="d4b0e-105">這些指示也適用於較舊的 Windows 版本。</span><span class="sxs-lookup"><span data-stu-id="d4b0e-105">You can also use these instructions for earlier Windows versions.</span></span>

## <a name="install-the-net-framework-35-on-demand"></a><span data-ttu-id="d4b0e-106">視需要安裝 .NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="d4b0e-106">Install the .NET Framework 3.5 on Demand</span></span>

<span data-ttu-id="d4b0e-107">如果您嘗試執行需要 .NET Framework 3.5 的應用程式，可能會看到下列設定對話方塊。</span><span class="sxs-lookup"><span data-stu-id="d4b0e-107">You may see the following configuration dialog if you try to run an app that requires the .NET Framework 3.5.</span></span> <span data-ttu-id="d4b0e-108">請選擇 [安裝此功能] 來啟用 .NET Framework 3.5。</span><span class="sxs-lookup"><span data-stu-id="d4b0e-108">Choose **Install this feature** to enable the .NET Framework 3.5.</span></span> <span data-ttu-id="d4b0e-109">這個選項需要網際網路連線。</span><span class="sxs-lookup"><span data-stu-id="d4b0e-109">This option requires an Internet connection.</span></span>

![.NET Framework 安裝對話方塊](./media/dotnet-framework-installation-dialog.jpg)

## <a name="enable-the-net-framework-35-in-control-panel"></a><span data-ttu-id="d4b0e-111">在控制台中啟用 .NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="d4b0e-111">Enable the .NET Framework 3.5 in Control Panel</span></span>

<span data-ttu-id="d4b0e-112">您可以透過 Windows 的 [控制台] 啟用 .NET Framework 3.5。</span><span class="sxs-lookup"><span data-stu-id="d4b0e-112">You can enable the .NET Framework 3.5 through the Windows Control Panel.</span></span> <span data-ttu-id="d4b0e-113">這個選項需要網際網路連線。</span><span class="sxs-lookup"><span data-stu-id="d4b0e-113">This option requires an Internet connection.</span></span>

1. <span data-ttu-id="d4b0e-114">按下鍵盤上的 Windows 鍵 ![Windows 標誌](https://i-msdn.sec.s-msft.com/dynimg/IC721376.jpeg)，鍵入「Windows 功能」，然後按 Enter 鍵。</span><span class="sxs-lookup"><span data-stu-id="d4b0e-114">Press the Windows key Windows ![Windows logo](https://i-msdn.sec.s-msft.com/dynimg/IC721376.jpeg) on your keyboard, type "Windows Features", and press Enter.</span></span> <span data-ttu-id="d4b0e-115">[開啟或關閉 Windows 功能] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="d4b0e-115">The **Turn Windows features on or off** dialog box appears.</span></span>

2. <span data-ttu-id="d4b0e-116">選取 [.NET Framework 3.5 (包括 .NET 2.0 和 3.0)] 核取方塊，選取 [確定]，然後在出現提示時重新啟動電腦。</span><span class="sxs-lookup"><span data-stu-id="d4b0e-116">Select the **.NET Framework 3.5 (includes .NET 2.0 and 3.0)** check box, select **OK**, and reboot your computer if prompted.</span></span>

   ![使用控制台來安裝 .NET](./media/dotnet-control-panel.png)

   <span data-ttu-id="d4b0e-118">您不需要選取 [Windows Communication Foundation (WCF) HTTP 啟用] 和 [Windows Communication Foundation (WCF) 非 HTTP 啟用] 的子項目，除非您是需要這項功能的開發人員或伺服器系統管理員。</span><span class="sxs-lookup"><span data-stu-id="d4b0e-118">You don't need to select the child items for **Windows Communication Foundation (WCF) HTTP Activation** and **Windows Communication Foundation (WCF) Non-HTTP Activation** unless you're a developer or server administrator who requires this functionality.</span></span>

## <a name="troubleshoot-the-installation-of-the-net-framework-35"></a><span data-ttu-id="d4b0e-119">進行 .NET Framework 3.5 安裝的疑難排解</span><span class="sxs-lookup"><span data-stu-id="d4b0e-119">Troubleshoot the installation of the .NET Framework 3.5</span></span>

<span data-ttu-id="d4b0e-120">在安裝過程中，可能會出現錯誤 0x800f0906、0x800f0907、0x800f081f 或 0x800F0922，如果發生這種情況，請參考 [.NET Framework 3.5 安裝錯誤：0x800f0906、0x800f0907 或 0x800f081f](https://support.microsoft.com/help/2734782/net-framework-3-5-installation-error-0x800f0906--0x800f081f--0x800f09)，了解如何解決這些問題。</span><span class="sxs-lookup"><span data-stu-id="d4b0e-120">During installation, you may encounter error 0x800f0906, 0x800f0907, 0x800f081f, or 0x800F0922, in which case refer to [.NET Framework 3.5 installation error: 0x800f0906, 0x800f0907, or 0x800f081f](https://support.microsoft.com/help/2734782/net-framework-3-5-installation-error-0x800f0906--0x800f081f--0x800f09) to see how to resolve these issues.</span></span>

<span data-ttu-id="d4b0e-121">若上一篇文章中探討的任一方法失敗，或是您沒有網際網路連線，則必須使用 Windows 安裝媒體。</span><span class="sxs-lookup"><span data-stu-id="d4b0e-121">If any of the methods discussed in the previous article fail or if you don't have an Internet connection, it's necessary to use your Windows installation media.</span></span> <span data-ttu-id="d4b0e-122">如需詳細資訊，請參閱[使用部署映像服務與管理 (DISM) 部署 .NET Framework 3.5](/windows-hardware/manufacture/desktop/deploy-net-framework-35-by-using-deployment-image-servicing-and-management--dism)。</span><span class="sxs-lookup"><span data-stu-id="d4b0e-122">For more information, see [Deploy .NET Framework 3.5 by using Deployment Image Servicing and Management (DISM)](/windows-hardware/manufacture/desktop/deploy-net-framework-35-by-using-deployment-image-servicing-and-management--dism).</span></span> <span data-ttu-id="d4b0e-123">如果您沒有安裝媒體，請參閱[建立 Windows 的安裝媒體](https://support.microsoft.com/help/15088/windows-create-installation-media)。</span><span class="sxs-lookup"><span data-stu-id="d4b0e-123">If you don't have the installation media, see [Create installation media for Windows](https://support.microsoft.com/help/15088/windows-create-installation-media).</span></span>
