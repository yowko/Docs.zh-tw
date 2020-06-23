---
title: 安裝訊息佇列 (MSMQ)
description: 瞭解如何在一次性安裝程式中安裝訊息佇列4.0 和訊息佇列3.0，以與 WFC 範例搭配使用。
ms.date: 03/30/2017
ms.assetid: 7ddcd497-3e04-427e-bc04-3610ad98b01e
ms.openlocfilehash: 0d0cb87b40b1cb11eb7692c2fa1e890ec815b13d
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244461"
---
# <a name="installing-message-queuing-msmq"></a><span data-ttu-id="b1828-103">安裝訊息佇列 (MSMQ)</span><span class="sxs-lookup"><span data-stu-id="b1828-103">Installing Message Queuing (MSMQ)</span></span>
<span data-ttu-id="b1828-104">下列程序示範如何安裝 Message Queuing 4.0 和 Message Queuing 3.0。</span><span class="sxs-lookup"><span data-stu-id="b1828-104">The following procedures show how to install Message Queuing 4.0 and Message Queuing 3.0.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b1828-105">Windows XP 和 Windows Server 2003 無法使用訊息佇列4.0。</span><span class="sxs-lookup"><span data-stu-id="b1828-105">Message Queuing 4.0 is not available in Windows XP and Windows Server 2003.</span></span>  
  
#### <a name="to-install-message-queuing-40-on-windows-server-2008-or-windows-server-2008-r2"></a><span data-ttu-id="b1828-106">若要在 Windows Server 2008 或 Windows Server 2008 R2 上安裝 Message Queuing 4.0</span><span class="sxs-lookup"><span data-stu-id="b1828-106">To install Message Queuing 4.0 on Windows Server 2008 or Windows Server 2008 R2</span></span>  
  
1. <span data-ttu-id="b1828-107">在伺服器管理員中，按一下 [**功能**]。</span><span class="sxs-lookup"><span data-stu-id="b1828-107">In Server Manager, click **Features**.</span></span>  
  
2. <span data-ttu-id="b1828-108">在右側窗格的 [**功能摘要**] 底下，按一下 [**新增功能**]。</span><span class="sxs-lookup"><span data-stu-id="b1828-108">In the right-hand pane under **Features Summary**, click **Add Features**.</span></span>  
  
3. <span data-ttu-id="b1828-109">在產生的視窗中，展開 [**訊息佇列**]。</span><span class="sxs-lookup"><span data-stu-id="b1828-109">In the resulting window, expand **Message Queuing**.</span></span>  
  
4. <span data-ttu-id="b1828-110">展開 [**訊息佇列服務**]。</span><span class="sxs-lookup"><span data-stu-id="b1828-110">Expand **Message Queuing Services**.</span></span>  
  
5. <span data-ttu-id="b1828-111">按一下 [**目錄服務整合**] （針對加入網域的電腦），然後按一下 [ **HTTP 支援**]。</span><span class="sxs-lookup"><span data-stu-id="b1828-111">Click **Directory Services Integration** (for computers joined to a Domain), then click **HTTP Support**.</span></span>  
  
6. <span data-ttu-id="b1828-112">按 **[下一步]**，然後按一下 [**安裝**]。</span><span class="sxs-lookup"><span data-stu-id="b1828-112">Click **Next**,then click **Install**.</span></span>  
  
#### <a name="to-install-message-queuing-40-on-windows-7-or-windows-vista"></a><span data-ttu-id="b1828-113">若要在 Windows 7 或 Windows Vista 上安裝 Message Queuing 4.0</span><span class="sxs-lookup"><span data-stu-id="b1828-113">To install Message Queuing 4.0 on Windows 7 or Windows Vista</span></span>  
  
1. <span data-ttu-id="b1828-114">開啟 [ **控制台**]。</span><span class="sxs-lookup"><span data-stu-id="b1828-114">Open **Control Panel**.</span></span>  
  
2. <span data-ttu-id="b1828-115">按一下 [**程式**]，然後按一下 [**程式和功能**] 下**的 [開啟或關閉 Windows 功能**]。</span><span class="sxs-lookup"><span data-stu-id="b1828-115">Click **Programs** and then, under **Programs and Features**, click **Turn Windows Features on and off**.</span></span>  
  
3. <span data-ttu-id="b1828-116">展開 [Microsoft Message Queue (MSMQ) 伺服器]，展開 [Microsoft Message Queue (MSMQ) 伺服器核心]，然後選取下列訊息佇列功能的核取方塊進行安裝：</span><span class="sxs-lookup"><span data-stu-id="b1828-116">Expand Microsoft Message Queue (MSMQ) Server, expand Microsoft Message Queue (MSMQ) Server Core, and then select the check boxes for the following Message Queuing features to install:</span></span>  
  
    - <span data-ttu-id="b1828-117">MSMQ Active Directory 網域服務整合 (針對加入網域的電腦)。</span><span class="sxs-lookup"><span data-stu-id="b1828-117">MSMQ Active Directory Domain Services Integration (for computers joined to a Domain).</span></span>  
  
    - <span data-ttu-id="b1828-118">MSMQ HTTP 支援。</span><span class="sxs-lookup"><span data-stu-id="b1828-118">MSMQ HTTP Support.</span></span>  
  
4. <span data-ttu-id="b1828-119">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="b1828-119">Click **OK**.</span></span>  
  
5. <span data-ttu-id="b1828-120">如果系統提示您重新開機電腦，請按一下 **[確定]** 以完成安裝。</span><span class="sxs-lookup"><span data-stu-id="b1828-120">If you are prompted to restart the computer, click **OK** to complete the installation.</span></span>  
  
#### <a name="to-install-message-queuing-30-on-windows-xp-and-windows-server-2003"></a><span data-ttu-id="b1828-121">若要在 Windows XP 和 Windows Server 2003 上安裝 Message Queuing 3.0</span><span class="sxs-lookup"><span data-stu-id="b1828-121">To install Message Queuing 3.0 on Windows XP and Windows Server 2003</span></span>  
  
1. <span data-ttu-id="b1828-122">開啟 [ **控制台**]。</span><span class="sxs-lookup"><span data-stu-id="b1828-122">Open **Control Panel**.</span></span>  
  
2. <span data-ttu-id="b1828-123">按一下 [新增] [**移除程式**]，然後按一下 [**新增 Windows 元件**]。</span><span class="sxs-lookup"><span data-stu-id="b1828-123">Click **Add Remove Programs** and then click **Add Windows Components**.</span></span>  
  
3. <span data-ttu-id="b1828-124">選取 [訊息佇列]，然後按一下 [**詳細資料**]。</span><span class="sxs-lookup"><span data-stu-id="b1828-124">Select Message Queuing and click **Details**.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="b1828-125">如果您執行的是 Windows Server 2003，請選取 [應用程式伺服器] 以存取訊息佇列。</span><span class="sxs-lookup"><span data-stu-id="b1828-125">If you are running Windows Server 2003, select Application Server to access Message Queuing.</span></span>  
  
4. <span data-ttu-id="b1828-126">確定在詳細資料頁面上選取 MSMQ HTTP 支援的選項。</span><span class="sxs-lookup"><span data-stu-id="b1828-126">Ensure that the option MSMQ HTTP Support is selected on the details page.</span></span>  
  
5. <span data-ttu-id="b1828-127">按一下 **[確定]** 以結束 [詳細資料] 頁面，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="b1828-127">Click **OK** to exit the details page, and then click **Next**.</span></span> <span data-ttu-id="b1828-128">完成安裝。</span><span class="sxs-lookup"><span data-stu-id="b1828-128">Complete the installation.</span></span>  
  
6. <span data-ttu-id="b1828-129">如果系統提示您重新開機電腦，請按一下 **[確定]** 以完成安裝。</span><span class="sxs-lookup"><span data-stu-id="b1828-129">If you are prompted to restart the computer, click **OK** to complete the installation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1828-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1828-130">See also</span></span>

- [<span data-ttu-id="b1828-131">設定指示</span><span class="sxs-lookup"><span data-stu-id="b1828-131">Set-Up Instructions</span></span>](set-up-instructions.md)
