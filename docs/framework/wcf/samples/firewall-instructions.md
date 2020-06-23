---
title: 防火牆指示
description: 瞭解如何在防火牆中啟用 WCF 範例的埠或程式。 根據您的需求和安全性環境，使用其中一個程式。
ms.date: 03/30/2017
ms.assetid: a7dc429f-65ac-4faf-974a-77d5fb977fe1
ms.openlocfilehash: de55d067960b8f2096c129f6feaf037219e06a96
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246137"
---
# <a name="firewall-instructions"></a><span data-ttu-id="04110-104">防火牆指示</span><span class="sxs-lookup"><span data-stu-id="04110-104">Firewall instructions</span></span>

<span data-ttu-id="04110-105">您必須在防火牆中啟用數個通訊埠或程式，讓 Windows Communication Foundation （WCF）範例可以運作。</span><span class="sxs-lookup"><span data-stu-id="04110-105">You must enable several ports or programs in the firewall so that the Windows Communication Foundation (WCF) samples can function.</span></span> <span data-ttu-id="04110-106">許多範例都使用範圍 8000-8003 中的連接埠以及連接埠 9000 進行通訊。</span><span class="sxs-lookup"><span data-stu-id="04110-106">Many of the samples communicate by using ports in the range 8000-8003, and port 9000.</span></span> <span data-ttu-id="04110-107">防火牆預設為開啟狀態，可防止對這些連接埠的存取。</span><span class="sxs-lookup"><span data-stu-id="04110-107">The firewall is turned on by default and prevents access to these ports.</span></span> <span data-ttu-id="04110-108">若要為範例啟用防火牆，請視您的需求和安全性環境，完成下列其中一個程序：</span><span class="sxs-lookup"><span data-stu-id="04110-108">To enable the firewall for the samples, complete one of the following procedures, depending on your requirements and security environment:</span></span>

- <span data-ttu-id="04110-109">選項 1：執行時以互動方式啟用範例。</span><span class="sxs-lookup"><span data-stu-id="04110-109">Option 1: Interactively enable samples while running.</span></span> <span data-ttu-id="04110-110">不要對您的防火牆組態進行任何進階變更，並開始建置與執行範例。</span><span class="sxs-lookup"><span data-stu-id="04110-110">Make no advance changes to your firewall configuration and proceed to start building and running the samples.</span></span> <span data-ttu-id="04110-111">執行範例時，會出現 [ **Windows 安全性警示**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="04110-111">When a sample is run, a **Windows Security Alert** dialog box appears.</span></span> <span data-ttu-id="04110-112">接著，您就可以互動方式將範例新增至解除封鎖清單中。</span><span class="sxs-lookup"><span data-stu-id="04110-112">The sample program in question can then be added interactively to an unblocked list.</span></span> <span data-ttu-id="04110-113">使用這個程序時，您可能必須重新啟動範例。</span><span class="sxs-lookup"><span data-stu-id="04110-113">With this procedure, you may have to then restart the sample.</span></span>

- <span data-ttu-id="04110-114">選項 2：事先啟用範例程式。</span><span class="sxs-lookup"><span data-stu-id="04110-114">Option 2: Enable sample programs in advance.</span></span> <span data-ttu-id="04110-115">啟動 [ **Windows 防火牆控制台**] applet，並啟用您計畫執行的範例程式。</span><span class="sxs-lookup"><span data-stu-id="04110-115">Start the **Windows Firewall Control Panel** applet and enable the sample programs you plan to run.</span></span> <span data-ttu-id="04110-116">您必須先建置程式，讓可執行檔存在。</span><span class="sxs-lookup"><span data-stu-id="04110-116">You must build the programs first so the executable files exist.</span></span> <span data-ttu-id="04110-117">接下來的程序中有更詳細的指示。</span><span class="sxs-lookup"><span data-stu-id="04110-117">You can find more detailed instructions in the following procedure.</span></span>

- <span data-ttu-id="04110-118">選項 3：事先啟用連接埠範圍。</span><span class="sxs-lookup"><span data-stu-id="04110-118">Option 3: Enable a port range in advance.</span></span> <span data-ttu-id="04110-119">啟動 [ **Windows 防火牆控制台**] 小程式，並啟用範例所使用的埠80、443、8000-8003 和9000。</span><span class="sxs-lookup"><span data-stu-id="04110-119">Start the **Windows Firewall Control Panel** applet and enable ports 80, 443, 8000-8003 and 9000, which are used by the samples.</span></span> <span data-ttu-id="04110-120">接下來的程序中有更詳細的指示。</span><span class="sxs-lookup"><span data-stu-id="04110-120">You can find more detailed instructions in the following procedure.</span></span> <span data-ttu-id="04110-121">這個選項的安全性最低，因為除了範例以外，它也允許其他程式使用這些連接埠。</span><span class="sxs-lookup"><span data-stu-id="04110-121">This option is less secure than the others because it allows any program to use these ports, not just the samples.</span></span>

<span data-ttu-id="04110-122">如果您不確定要使用哪一個程序，請選擇第一個選項。</span><span class="sxs-lookup"><span data-stu-id="04110-122">If you are unsure of which procedure to use, choose the first option.</span></span> <span data-ttu-id="04110-123">如果您執行的是其他廠商的防火牆，可能必須進行類似的變更。</span><span class="sxs-lookup"><span data-stu-id="04110-123">If you are running a firewall from another vendor, you might need to make similar changes.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="04110-124">變更防火牆組態會影響您的安全性。</span><span class="sxs-lookup"><span data-stu-id="04110-124">Changing your firewall configuration affects your security.</span></span> <span data-ttu-id="04110-125">建議您記下所做的變更，然後在使用完範例後，將這些變更移除。</span><span class="sxs-lookup"><span data-stu-id="04110-125">It is recommended that you record the changes you make and remove them when you are finished working with the samples.</span></span>

## <a name="enable-samples-programs-in-advance"></a><span data-ttu-id="04110-126">事先啟用範例程式</span><span class="sxs-lookup"><span data-stu-id="04110-126">Enable samples programs in advance</span></span>

1. <span data-ttu-id="04110-127">建置範例。</span><span class="sxs-lookup"><span data-stu-id="04110-127">Build the sample.</span></span>

2. <span data-ttu-id="04110-128">選擇 [**開始**  >  **執行**]，然後輸入 `firewall.cpl` 。</span><span class="sxs-lookup"><span data-stu-id="04110-128">Choose **Start** > **Run**, and enter `firewall.cpl`.</span></span> <span data-ttu-id="04110-129">這會開啟 [ **Windows 防火牆控制台**] 小程式。</span><span class="sxs-lookup"><span data-stu-id="04110-129">This opens the **Windows Firewall Control Panel** applet.</span></span>

    > [!NOTE]
    > <span data-ttu-id="04110-130">您必須擁有變更防火牆設定的權限，才能執行需要透過 Windows 防火牆進行通訊之能力的範例。</span><span class="sxs-lookup"><span data-stu-id="04110-130">You must have permission to change the Firewall settings to run samples that require the ability to communicate through the Windows Firewall.</span></span> <span data-ttu-id="04110-131">如果無法使用某些防火牆設定，而且您的電腦已連線至某個網域，表示您的系統管理員可能正在透過「群組原則」控制這些設定。</span><span class="sxs-lookup"><span data-stu-id="04110-131">If some firewall settings are unavailable and your computer is connected to a domain, your system administrator might be controlling these settings through Group Policy.</span></span>

3. <span data-ttu-id="04110-132">完成下列其中一項操作特定的步驟，以允許程式通過 Windows 防火牆：</span><span class="sxs-lookup"><span data-stu-id="04110-132">Complete one of the following operating-specific steps to allow a program through the Windows Firewall:</span></span>

    - <span data-ttu-id="04110-133">在 Windows 7 或 Windows Server 2008 R2 上，按一下 [**允許程式或功能通過 Windows 防火牆**]。</span><span class="sxs-lookup"><span data-stu-id="04110-133">On Windows 7 or Windows Server 2008 R2, click **Allow a program or feature through Windows Firewall**.</span></span> <span data-ttu-id="04110-134">按一下 [**變更設定**] [  >  **允許其他程式**]。</span><span class="sxs-lookup"><span data-stu-id="04110-134">Click **Change Settings** > **Allow Another Program**.</span></span>

    - <span data-ttu-id="04110-135">在 Windows Vista 或 Windows Server 2008 上，按一下 [**允許程式通過 Windows 防火牆**]。</span><span class="sxs-lookup"><span data-stu-id="04110-135">On Windows Vista or Windows Server 2008, click **Allow a program through Windows Firewall**.</span></span>

4. <span data-ttu-id="04110-136">在 [**例外**] 索引標籤上，按一下 [**新增程式**]。</span><span class="sxs-lookup"><span data-stu-id="04110-136">On the **Exceptions** tab, click **Add Program**.</span></span>

5. <span data-ttu-id="04110-137">按一下 [**流覽]** 按鈕，然後選取您打算執行之範例的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="04110-137">Click the **Browse** button and select the executable file of the sample you plan to run.</span></span>

6. <span data-ttu-id="04110-138">重複步驟4和5，直到您已新增您打算執行之所有範例的可執行檔為止。</span><span class="sxs-lookup"><span data-stu-id="04110-138">Repeat steps 4 and 5 until you have added the executable files of all the samples you plan to run.</span></span>

7. <span data-ttu-id="04110-139">按一下 **[確定]** 以關閉防火牆小程式。</span><span class="sxs-lookup"><span data-stu-id="04110-139">Click **OK** to close the firewall applet.</span></span>

## <a name="enable-a-port-range-in-advance"></a><span data-ttu-id="04110-140">預先啟用埠範圍</span><span class="sxs-lookup"><span data-stu-id="04110-140">Enable a port range in advance</span></span>

1. <span data-ttu-id="04110-141">選擇 [**開始**  >  **執行**]，然後輸入 `firewall.cpl` 。</span><span class="sxs-lookup"><span data-stu-id="04110-141">Choose **Start** > **Run**, and enter `firewall.cpl`.</span></span> <span data-ttu-id="04110-142">這會開啟 [ **Windows 防火牆控制台**] 小程式。</span><span class="sxs-lookup"><span data-stu-id="04110-142">This opens the **Windows Firewall Control Panel** applet.</span></span>

2. <span data-ttu-id="04110-143">在 Windows 7 或 Windows Server 2008 R2 上，按照以下步驟進行。</span><span class="sxs-lookup"><span data-stu-id="04110-143">On Windows 7 or Windows Server 2008 R2, follow these steps.</span></span>

    1. <span data-ttu-id="04110-144">在 [Windows 防火牆] 視窗的左欄中，按一下 [ **Advanced settings** ]。</span><span class="sxs-lookup"><span data-stu-id="04110-144">Click **Advanced settings** in the left column of the Windows Firewall window.</span></span>

    2. <span data-ttu-id="04110-145">按一下左側資料行中的 [**輸入規則**]。</span><span class="sxs-lookup"><span data-stu-id="04110-145">Click **Inbound Rules** in the left column.</span></span>

    3. <span data-ttu-id="04110-146">按一下右側資料行中的 [**新增規則**]。</span><span class="sxs-lookup"><span data-stu-id="04110-146">Click **New Rules** in the right column.</span></span>

    4. <span data-ttu-id="04110-147">選取 [**埠**] 並按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="04110-147">Select **Port** and click **next**.</span></span>

    5. <span data-ttu-id="04110-148">選取 [ **TCP** ]，然後 `8000, 8001, 8002, 8003, 9000, 80, 443` 在 [**特定本機埠**] 欄位中輸入。</span><span class="sxs-lookup"><span data-stu-id="04110-148">Select **TCP** and enter `8000, 8001, 8002, 8003, 9000, 80, 443` in the **Specific local ports** field.</span></span>

    6. <span data-ttu-id="04110-149">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="04110-149">Click **Next**.</span></span>

    7. <span data-ttu-id="04110-150">選取 **[允許連接**]，然後按 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="04110-150">Select **Allow the connection**, and click **Next** .</span></span>

    8. <span data-ttu-id="04110-151">選取 [**網域**和**私人**]，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="04110-151">Select **Domain** and **Private**, and click **Next**.</span></span>

    9. <span data-ttu-id="04110-152">為此規則命名 `WCF-WF 4.0 Samples` ，然後按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="04110-152">Name this rule `WCF-WF 4.0 Samples`, and click **Finish**.</span></span>

    10. <span data-ttu-id="04110-153">按一下 [**輸出規則**]，然後重複步驟 c 到 h。</span><span class="sxs-lookup"><span data-stu-id="04110-153">Click **Outbound Rules** and repeat steps c to h.</span></span>

3. <span data-ttu-id="04110-154">在 Windows Vista 或 Windows Server 2008 上，請遵循下列步驟。</span><span class="sxs-lookup"><span data-stu-id="04110-154">On Windows Vista or Windows Server 2008, follow these steps.</span></span>

    1. <span data-ttu-id="04110-155">按一下 [**允許程式通過 Windows 防火牆**]。</span><span class="sxs-lookup"><span data-stu-id="04110-155">Click **Allow a program through Windows Firewall**.</span></span>

    2. <span data-ttu-id="04110-156">在 [**例外**] 索引標籤上，按一下 [**新增埠**]。</span><span class="sxs-lookup"><span data-stu-id="04110-156">On the **Exceptions** tab, click **Add Port**.</span></span>

    3. <span data-ttu-id="04110-157">輸入 [名稱]，輸入8000做為埠號碼，然後選取 [ **TCP** ] 選項。</span><span class="sxs-lookup"><span data-stu-id="04110-157">Enter a name, enter 8000 as the port number, and select the **TCP** option.</span></span>

    4. <span data-ttu-id="04110-158">按一下 [**變更領域**] 按鈕，選取 [僅限**我的網路**（子網）] 選項，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="04110-158">Click the **Change Scope** button, select the **My Network** (subnet) only option, and click **OK**.</span></span>

    5. <span data-ttu-id="04110-159">為連接埠 8001、8002、8003、9000、80 和 443 重複步驟 b 到 d。</span><span class="sxs-lookup"><span data-stu-id="04110-159">Repeat steps b to d for ports 8001, 8002, 8003, 9000, 80, and 443.</span></span>

4. <span data-ttu-id="04110-160">按一下 **[確定]** 以關閉防火牆小程式。</span><span class="sxs-lookup"><span data-stu-id="04110-160">Click **OK** to close the firewall applet.</span></span>

> [!NOTE]
> <span data-ttu-id="04110-161">當您使用完範例時，請移除任何防火牆例外狀況。</span><span class="sxs-lookup"><span data-stu-id="04110-161">Remove any firewall exceptions when you are finished working with the samples.</span></span> <span data-ttu-id="04110-162">若要這麼做，請開啟 [ **Windows 防火牆控制台**] applet，並移除先前程式所新增的任何程式或埠專案。</span><span class="sxs-lookup"><span data-stu-id="04110-162">To do so, open the **Windows Firewall Control Panel** applet and remove any programs or port entries that were added by the previous procedures.</span></span>
