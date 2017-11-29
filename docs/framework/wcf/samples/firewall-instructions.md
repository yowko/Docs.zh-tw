---
title: "防火牆指示"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a7dc429f-65ac-4faf-974a-77d5fb977fe1
caps.latest.revision: "32"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0aac3a161b0482bad1a32f5223d2031402a632cc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="firewall-instructions"></a><span data-ttu-id="cb84d-102">防火牆指示</span><span class="sxs-lookup"><span data-stu-id="cb84d-102">Firewall Instructions</span></span>
<span data-ttu-id="cb84d-103">您必須啟用防火牆中的數個連接埠或程式，[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 範例才能運作。</span><span class="sxs-lookup"><span data-stu-id="cb84d-103">You must enable several ports or programs in the firewall so that the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] samples can function.</span></span> <span data-ttu-id="cb84d-104">許多範例都使用範圍 8000-8003 中的連接埠以及連接埠 9000 進行通訊。</span><span class="sxs-lookup"><span data-stu-id="cb84d-104">Many of the samples communicate by using ports in the range 8000-8003, and port 9000.</span></span> <span data-ttu-id="cb84d-105">防火牆預設為開啟狀態，可防止對這些連接埠的存取。</span><span class="sxs-lookup"><span data-stu-id="cb84d-105">The firewall is turned on by default and prevents access to these ports.</span></span> <span data-ttu-id="cb84d-106">若要為範例啟用防火牆，請視您的需求和安全性環境，完成下列其中一個程序：</span><span class="sxs-lookup"><span data-stu-id="cb84d-106">To enable the firewall for the samples, complete one of the following procedures, depending on your requirements and security environment:</span></span>  
  
-   <span data-ttu-id="cb84d-107">選項 1：執行時以互動方式啟用範例。</span><span class="sxs-lookup"><span data-stu-id="cb84d-107">Option 1: Interactively enable samples while running.</span></span> <span data-ttu-id="cb84d-108">不要對您的防火牆組態進行任何進階變更，並開始建置與執行範例。</span><span class="sxs-lookup"><span data-stu-id="cb84d-108">Make no advance changes to your firewall configuration and proceed to start building and running the samples.</span></span> <span data-ttu-id="cb84d-109">執行範例時， **Windows 安全性警訊** 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="cb84d-109">When a sample is run, a **Windows Security Alert** dialog box appears.</span></span> <span data-ttu-id="cb84d-110">接著，您就可以互動方式將範例新增至解除封鎖清單中。</span><span class="sxs-lookup"><span data-stu-id="cb84d-110">The sample program in question can then be added interactively to an unblocked list.</span></span> <span data-ttu-id="cb84d-111">使用這個程序時，您可能必須重新啟動範例。</span><span class="sxs-lookup"><span data-stu-id="cb84d-111">With this procedure, you may have to then restart the sample.</span></span>  
  
-   <span data-ttu-id="cb84d-112">選項 2：事先啟用範例程式。</span><span class="sxs-lookup"><span data-stu-id="cb84d-112">Option 2: Enable sample programs in advance.</span></span> <span data-ttu-id="cb84d-113">啟動**Windows 防火牆控制台** applet，並啟用範例程式您計劃執行。</span><span class="sxs-lookup"><span data-stu-id="cb84d-113">Start the **Windows Firewall Control Panel** applet and enable the sample programs you plan to run.</span></span> <span data-ttu-id="cb84d-114">您必須先建置程式，讓可執行檔存在。</span><span class="sxs-lookup"><span data-stu-id="cb84d-114">You must build the programs first so the executable files exist.</span></span> <span data-ttu-id="cb84d-115">接下來的程序中有更詳細的指示。</span><span class="sxs-lookup"><span data-stu-id="cb84d-115">You can find more detailed instructions in the following procedure.</span></span>  
  
-   <span data-ttu-id="cb84d-116">選項 3：事先啟用連接埠範圍。</span><span class="sxs-lookup"><span data-stu-id="cb84d-116">Option 3: Enable a port range in advance.</span></span> <span data-ttu-id="cb84d-117">啟動**Windows 防火牆****控制台** applet，並啟用連接埠 80、 443、 8000-8003 和 9000，所使用的範例。</span><span class="sxs-lookup"><span data-stu-id="cb84d-117">Start the **Windows Firewall** **Control Panel** applet and enable ports 80, 443, 8000-8003 and 9000, which are used by the samples.</span></span> <span data-ttu-id="cb84d-118">接下來的程序中有更詳細的指示。</span><span class="sxs-lookup"><span data-stu-id="cb84d-118">You can find more detailed instructions in the following procedure.</span></span> <span data-ttu-id="cb84d-119">這個選項的安全性最低，因為除了範例以外，它也允許其他程式使用這些連接埠。</span><span class="sxs-lookup"><span data-stu-id="cb84d-119">This option is less secure than the others because it allows any program to use these ports, not just the samples.</span></span>  
  
 <span data-ttu-id="cb84d-120">如果您不確定要使用哪一個程序，請選擇第一個選項。</span><span class="sxs-lookup"><span data-stu-id="cb84d-120">If you are unsure of which procedure to use, choose the first option.</span></span> <span data-ttu-id="cb84d-121">如果您執行的是其他廠商的防火牆，可能必須進行類似的變更。</span><span class="sxs-lookup"><span data-stu-id="cb84d-121">If you are running a firewall from another vendor, you might need to make similar changes.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="cb84d-122">變更防火牆組態會影響您的安全性。</span><span class="sxs-lookup"><span data-stu-id="cb84d-122">Changing your firewall configuration affects your security.</span></span> <span data-ttu-id="cb84d-123">建議您記下所做的變更，然後在使用完範例後，將這些變更移除。</span><span class="sxs-lookup"><span data-stu-id="cb84d-123">It is recommended that you record the changes you make and remove them when you are finished working with the samples.</span></span>  
  
### <a name="to-enable-samples-programs-in-advance"></a><span data-ttu-id="cb84d-124">若要事先啟用範例程式</span><span class="sxs-lookup"><span data-stu-id="cb84d-124">To enable samples programs in advance</span></span>  
  
1.  <span data-ttu-id="cb84d-125">建置 (Build) 範例。</span><span class="sxs-lookup"><span data-stu-id="cb84d-125">Build the sample.</span></span>  
  
2.  <span data-ttu-id="cb84d-126">按一下**啟動**，按一下 **執行**，然後輸入`firewall.cpl`。</span><span class="sxs-lookup"><span data-stu-id="cb84d-126">Click **Start**, click **Run**, and type `firewall.cpl`.</span></span> <span data-ttu-id="cb84d-127">這會開啟**Windows 防火牆控制台**小程式。</span><span class="sxs-lookup"><span data-stu-id="cb84d-127">This opens the **Windows Firewall Control Panel** applet.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="cb84d-128">您必須擁有變更防火牆設定的權限，才能執行需要透過 Windows 防火牆進行通訊之能力的範例。</span><span class="sxs-lookup"><span data-stu-id="cb84d-128">You must have permission to change the Firewall settings to run samples that require the ability to communicate through the Windows Firewall.</span></span> <span data-ttu-id="cb84d-129">如果無法使用某些防火牆設定，而且您的電腦已連線至某個網域，表示您的系統管理員可能正在透過「群組原則」控制這些設定。</span><span class="sxs-lookup"><span data-stu-id="cb84d-129">If some firewall settings are unavailable and your computer is connected to a domain, your system administrator might be controlling these settings through Group Policy.</span></span>  
  
3.  <span data-ttu-id="cb84d-130">完成下列其中一個特定操作步驟，以允許程式通過 Windows 防火牆：</span><span class="sxs-lookup"><span data-stu-id="cb84d-130">Complete one of the following operating specific steps to allow a program through the Windows Firewall:</span></span>  
  
    -   <span data-ttu-id="cb84d-131">在 Windows 7 或 Windows Server 2008 r2 上，按一下 **允許程式或功能通過 Windows 防火牆**。</span><span class="sxs-lookup"><span data-stu-id="cb84d-131">On Windows 7 or Windows Server 2008 r2, click **Allow a program or feature through Windows Firewall**.</span></span> <span data-ttu-id="cb84d-132">按一下**變更設定**，允許**另一個程式...**.</span><span class="sxs-lookup"><span data-stu-id="cb84d-132">Click **Change Settings**, Allow **Another Program…**.</span></span>  
  
    -   <span data-ttu-id="cb84d-133">在[!INCLUDE[wv](../../../../includes/wv-md.md)]或[!INCLUDE[lserver](../../../../includes/lserver-md.md)]，按一下 **允許程式通過 Windows 防火牆**。</span><span class="sxs-lookup"><span data-stu-id="cb84d-133">On [!INCLUDE[wv](../../../../includes/wv-md.md)] or [!INCLUDE[lserver](../../../../includes/lserver-md.md)], click **Allow a program through Windows Firewall**.</span></span>  
  
4.  <span data-ttu-id="cb84d-134">在**例外狀況**索引標籤上，按一下 **新增程式**。</span><span class="sxs-lookup"><span data-stu-id="cb84d-134">On the **Exceptions** tab, click **Add Program**.</span></span>  
  
5.  <span data-ttu-id="cb84d-135">按一下**瀏覽**按鈕，然後選取想要執行此範例的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="cb84d-135">Click the **Browse** button and select the executable file of the sample you plan to run.</span></span>  
  
6.  <span data-ttu-id="cb84d-136">重複步驟 4 和 5，直到您已經新增所有想要執行這些範例可執行檔。</span><span class="sxs-lookup"><span data-stu-id="cb84d-136">Repeat steps 4 and 5 until you have added the executable files of all the samples you plan to run.</span></span>  
  
7.  <span data-ttu-id="cb84d-137">按一下**確定**以關閉防火牆 applet。</span><span class="sxs-lookup"><span data-stu-id="cb84d-137">Click **OK** to close the firewall applet.</span></span>  
  
### <a name="to-enable-a-port-range-in-advance"></a><span data-ttu-id="cb84d-138">若要事先啟用連接埠範圍</span><span class="sxs-lookup"><span data-stu-id="cb84d-138">To enable a port range in advance</span></span>  
  
1.  <span data-ttu-id="cb84d-139">按一下**啟動**，按一下 **執行**，然後輸入`firewall.cpl`。</span><span class="sxs-lookup"><span data-stu-id="cb84d-139">Click **Start**, click **Run**, and type `firewall.cpl`.</span></span> <span data-ttu-id="cb84d-140">這會開啟**Windows 防火牆控制台**小程式。</span><span class="sxs-lookup"><span data-stu-id="cb84d-140">This opens the **Windows Firewall Control Panel** applet.</span></span>  
  
2.  <span data-ttu-id="cb84d-141">在 Windows 7 或 Windows Server 2008 R2 上，按照以下步驟進行。</span><span class="sxs-lookup"><span data-stu-id="cb84d-141">On Windows 7 or Windows Server 2008 R2, follow these steps.</span></span>  
  
    1.  <span data-ttu-id="cb84d-142">按一下**進階設定**左側資料行 [Windows 防火牆] 視窗中。</span><span class="sxs-lookup"><span data-stu-id="cb84d-142">Click **Advanced settings** in the left column of the Windows Firewall window.</span></span>  
  
    2.  <span data-ttu-id="cb84d-143">按一下**輸入規則**左側資料行中。</span><span class="sxs-lookup"><span data-stu-id="cb84d-143">Click **Inbound Rules** in the left column.</span></span>  
  
    3.  <span data-ttu-id="cb84d-144">按一下**新規則**右欄中。</span><span class="sxs-lookup"><span data-stu-id="cb84d-144">Click **New Rules** in the right column.</span></span>  
  
    4.  <span data-ttu-id="cb84d-145">選取**連接埠**按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="cb84d-145">Select **Port** and click **next**.</span></span>  
  
    5.  <span data-ttu-id="cb84d-146">選取**TCP**輸入`8000, 8001, 8002, 8003, 9000, 80, 443`中**特定本機連接埠**欄位。</span><span class="sxs-lookup"><span data-stu-id="cb84d-146">Select **TCP** and enter `8000, 8001, 8002, 8003, 9000, 80, 443` in the **Specific local ports** field.</span></span>  
  
    6.  <span data-ttu-id="cb84d-147">按 [ **下一步**]。</span><span class="sxs-lookup"><span data-stu-id="cb84d-147">Click **Next**.</span></span>  
  
    7.  <span data-ttu-id="cb84d-148">選取**允許連線**，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="cb84d-148">Select **Allow the connection**, and click **Next** .</span></span>  
  
    8.  <span data-ttu-id="cb84d-149">選取**網域**和**私人**，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="cb84d-149">Select **Domain** and **Private**, and click **Next**.</span></span>  
  
    9. <span data-ttu-id="cb84d-150">將此規則命名`WCF-WF 4.0 Samples`，然後按一下**完成**。</span><span class="sxs-lookup"><span data-stu-id="cb84d-150">Name this rule `WCF-WF 4.0 Samples`, and click **Finish**.</span></span>  
  
    10. <span data-ttu-id="cb84d-151">按一下**輸出規則**並重複步驟 c 到 h。</span><span class="sxs-lookup"><span data-stu-id="cb84d-151">Click **Outbound Rules** and repeat steps c to h.</span></span>  
  
3.  <span data-ttu-id="cb84d-152">在 [!INCLUDE[wv](../../../../includes/wv-md.md)] 或 [!INCLUDE[lserver](../../../../includes/lserver-md.md)] 上，按照以下步驟進行。</span><span class="sxs-lookup"><span data-stu-id="cb84d-152">On [!INCLUDE[wv](../../../../includes/wv-md.md)] or [!INCLUDE[lserver](../../../../includes/lserver-md.md)], follow these steps.</span></span>  
  
    1.  <span data-ttu-id="cb84d-153">按一下**允許程式通過 Windows 防火牆**。</span><span class="sxs-lookup"><span data-stu-id="cb84d-153">Click **Allow a program through Windows Firewall**.</span></span>  
  
    2.  <span data-ttu-id="cb84d-154">在**例外狀況**索引標籤上，按一下 **新增連接埠**。</span><span class="sxs-lookup"><span data-stu-id="cb84d-154">On the **Exceptions** tab, click **Add Port**.</span></span>  
  
    3.  <span data-ttu-id="cb84d-155">輸入的名稱，輸入 8000 做為連接埠號碼，然後選取**TCP**選項。</span><span class="sxs-lookup"><span data-stu-id="cb84d-155">Enter a name, enter 8000 as the port number, and select the **TCP** option.</span></span>  
  
    4.  <span data-ttu-id="cb84d-156">按一下**變更領域**按鈕，選取**我的網路**（子網路） 唯一的選項，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="cb84d-156">Click the **Change Scope** button, select the **My Network** (subnet) only option, and click **OK**.</span></span>  
  
    5.  <span data-ttu-id="cb84d-157">為連接埠 8001、8002、8003、9000、80 和 443 重複步驟 b 到 d。</span><span class="sxs-lookup"><span data-stu-id="cb84d-157">Repeat steps b to d for ports 8001, 8002, 8003, 9000, 80, and 443.</span></span>  
  
4.  <span data-ttu-id="cb84d-158">按一下**確定**以關閉防火牆 applet。</span><span class="sxs-lookup"><span data-stu-id="cb84d-158">Click **OK** to close the firewall applet.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cb84d-159">當您使用完範例時，請移除任何防火牆例外狀況。</span><span class="sxs-lookup"><span data-stu-id="cb84d-159">Remove any firewall exceptions when you are finished working with the samples.</span></span> <span data-ttu-id="cb84d-160">若要這樣做，請開啟**Windows 防火牆控制台**小程式並移除任何程式或連接埠已由先前的程序新增的項目。</span><span class="sxs-lookup"><span data-stu-id="cb84d-160">To do so, open the **Windows Firewall Control Panel** applet and remove any programs or port entries that were added by the previous procedures.</span></span>
