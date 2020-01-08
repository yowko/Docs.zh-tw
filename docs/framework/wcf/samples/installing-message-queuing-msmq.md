---
title: 安裝訊息佇列 (MSMQ)
ms.date: 03/30/2017
ms.assetid: 7ddcd497-3e04-427e-bc04-3610ad98b01e
ms.openlocfilehash: e6d6a3a2e1bc0a0c936e4b8594eab836b559e5a7
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344741"
---
# <a name="installing-message-queuing-msmq"></a><span data-ttu-id="7b2cf-102">安裝訊息佇列 (MSMQ)</span><span class="sxs-lookup"><span data-stu-id="7b2cf-102">Installing Message Queuing (MSMQ)</span></span>
<span data-ttu-id="7b2cf-103">下列程序示範如何安裝 Message Queuing 4.0 和 Message Queuing 3.0。</span><span class="sxs-lookup"><span data-stu-id="7b2cf-103">The following procedures show how to install Message Queuing 4.0 and Message Queuing 3.0.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7b2cf-104">[!INCLUDE[wxp](../../../../includes/wxp-md.md)] 和 Windows Server 2003 中無法使用訊息佇列4.0。</span><span class="sxs-lookup"><span data-stu-id="7b2cf-104">Message Queuing 4.0 is not available in [!INCLUDE[wxp](../../../../includes/wxp-md.md)] and Windows Server 2003.</span></span>  
  
#### <a name="to-install-message-queuing-40-on-windows-server-2008-or-windows-server-2008-r2"></a><span data-ttu-id="7b2cf-105">若要在 Windows Server 2008 或 Windows Server 2008 R2 上安裝 Message Queuing 4.0</span><span class="sxs-lookup"><span data-stu-id="7b2cf-105">To install Message Queuing 4.0 on Windows Server 2008 or Windows Server 2008 R2</span></span>  
  
1. <span data-ttu-id="7b2cf-106">在伺服器管理員中，按一下 [**功能**]。</span><span class="sxs-lookup"><span data-stu-id="7b2cf-106">In Server Manager, click **Features**.</span></span>  
  
2. <span data-ttu-id="7b2cf-107">在右側窗格的 [**功能摘要**] 底下，按一下 [**新增功能**]。</span><span class="sxs-lookup"><span data-stu-id="7b2cf-107">In the right-hand pane under **Features Summary**, click **Add Features**.</span></span>  
  
3. <span data-ttu-id="7b2cf-108">在產生的視窗中，展開 [**訊息佇列**]。</span><span class="sxs-lookup"><span data-stu-id="7b2cf-108">In the resulting window, expand **Message Queuing**.</span></span>  
  
4. <span data-ttu-id="7b2cf-109">展開 [**訊息佇列服務**]。</span><span class="sxs-lookup"><span data-stu-id="7b2cf-109">Expand **Message Queuing Services**.</span></span>  
  
5. <span data-ttu-id="7b2cf-110">按一下 [**目錄服務整合**] （針對加入網域的電腦），然後按一下 [ **HTTP 支援**]。</span><span class="sxs-lookup"><span data-stu-id="7b2cf-110">Click **Directory Services Integration** (for computers joined to a Domain), then click **HTTP Support**.</span></span>  
  
6. <span data-ttu-id="7b2cf-111">按 **[下一步]** ，然後按一下 [**安裝**]。</span><span class="sxs-lookup"><span data-stu-id="7b2cf-111">Click **Next**,then click **Install**.</span></span>  
  
#### <a name="to-install-message-queuing-40-on-windows-7-or-windows-vista"></a><span data-ttu-id="7b2cf-112">若要在 Windows 7 或 Windows Vista 上安裝 Message Queuing 4.0</span><span class="sxs-lookup"><span data-stu-id="7b2cf-112">To install Message Queuing 4.0 on Windows 7 or Windows Vista</span></span>  
  
1. <span data-ttu-id="7b2cf-113">開啟 [控制台]。</span><span class="sxs-lookup"><span data-stu-id="7b2cf-113">Open **Control Panel**.</span></span>  
  
2. <span data-ttu-id="7b2cf-114">按一下 [**程式**]，然後按一下 [**程式和功能**] 下**的 [開啟或關閉 Windows 功能**]。</span><span class="sxs-lookup"><span data-stu-id="7b2cf-114">Click **Programs** and then, under **Programs and Features**, click **Turn Windows Features on and off**.</span></span>  
  
3. <span data-ttu-id="7b2cf-115">依序展開 [Microsoft Message Queue (MSMQ) 伺服器] 和 [Microsoft Message Queue (MSMQ) 伺服器核心]，然後選取下列訊息佇列功能的核取方塊進行安裝：</span><span class="sxs-lookup"><span data-stu-id="7b2cf-115">Expand Microsoft Message Queue (MSMQ) Server, expand Microsoft Message Queue (MSMQ) Server Core, and then select the check boxes for the following Message Queuing features to install:</span></span>  
  
    - <span data-ttu-id="7b2cf-116">MSMQ Active Directory 網域服務整合 (針對加入網域的電腦)。</span><span class="sxs-lookup"><span data-stu-id="7b2cf-116">MSMQ Active Directory Domain Services Integration (for computers joined to a Domain).</span></span>  
  
    - <span data-ttu-id="7b2cf-117">MSMQ HTTP 支援。</span><span class="sxs-lookup"><span data-stu-id="7b2cf-117">MSMQ HTTP Support.</span></span>  
  
4. <span data-ttu-id="7b2cf-118">按一下 [ **確定**]。</span><span class="sxs-lookup"><span data-stu-id="7b2cf-118">Click **OK**.</span></span>  
  
5. <span data-ttu-id="7b2cf-119">如果系統提示您重新開機電腦，請按一下 **[確定]** 以完成安裝。</span><span class="sxs-lookup"><span data-stu-id="7b2cf-119">If you are prompted to restart the computer, click **OK** to complete the installation.</span></span>  
  
#### <a name="to-install-message-queuing-30-on-windows-xp-and-windows-server-2003"></a><span data-ttu-id="7b2cf-120">若要在 Windows XP 和 Windows Server 2003 上安裝 Message Queuing 3.0</span><span class="sxs-lookup"><span data-stu-id="7b2cf-120">To install Message Queuing 3.0 on Windows XP and Windows Server 2003</span></span>  
  
1. <span data-ttu-id="7b2cf-121">開啟 [控制台]。</span><span class="sxs-lookup"><span data-stu-id="7b2cf-121">Open **Control Panel**.</span></span>  
  
2. <span data-ttu-id="7b2cf-122">按一下 [新增] [**移除程式**]，然後按一下 [**新增 Windows 元件**]。</span><span class="sxs-lookup"><span data-stu-id="7b2cf-122">Click **Add Remove Programs** and then click **Add Windows Components**.</span></span>  
  
3. <span data-ttu-id="7b2cf-123">選取 [訊息佇列]，然後按一下 [**詳細資料**]。</span><span class="sxs-lookup"><span data-stu-id="7b2cf-123">Select Message Queuing and click **Details**.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="7b2cf-124">如果您執行的是 Windows Server 2003，請選取 [應用程式伺服器] 以存取訊息佇列。</span><span class="sxs-lookup"><span data-stu-id="7b2cf-124">If you are running Windows Server 2003, select Application Server to access Message Queuing.</span></span>  
  
4. <span data-ttu-id="7b2cf-125">確定在詳細資料頁面上選取 MSMQ HTTP 支援的選項。</span><span class="sxs-lookup"><span data-stu-id="7b2cf-125">Ensure that the option MSMQ HTTP Support is selected on the details page.</span></span>  
  
5. <span data-ttu-id="7b2cf-126">按一下 **[確定]** 以結束 [詳細資料] 頁面，然後按 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="7b2cf-126">Click **OK** to exit the details page, and then click **Next**.</span></span> <span data-ttu-id="7b2cf-127">完成安裝。</span><span class="sxs-lookup"><span data-stu-id="7b2cf-127">Complete the installation.</span></span>  
  
6. <span data-ttu-id="7b2cf-128">如果系統提示您重新開機電腦，請按一下 **[確定]** 以完成安裝。</span><span class="sxs-lookup"><span data-stu-id="7b2cf-128">If you are prompted to restart the computer, click **OK** to complete the installation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b2cf-129">請參閱</span><span class="sxs-lookup"><span data-stu-id="7b2cf-129">See also</span></span>

- [<span data-ttu-id="7b2cf-130">設定指示</span><span class="sxs-lookup"><span data-stu-id="7b2cf-130">Set-Up Instructions</span></span>](../../../../docs/framework/wcf/samples/set-up-instructions.md)
