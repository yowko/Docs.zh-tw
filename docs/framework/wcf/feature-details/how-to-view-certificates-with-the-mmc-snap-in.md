---
title: 如何：使用 MMC 卡入式查看證書
ms.date: 02/25/2019
helpviewer_keywords:
- certificates [WCF], viewing with the MMC snap-in
ms.assetid: 2b8782aa-ebb4-4ee7-974b-90299e356dc5
ms.openlocfilehash: 35048c24e838c513909fae8bedcba287001f5cef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184776"
---
# <a name="how-to-view-certificates-with-the-mmc-snap-in"></a><span data-ttu-id="61489-102">如何：使用 MMC 卡入式查看證書</span><span class="sxs-lookup"><span data-stu-id="61489-102">How to: View certificates with the MMC snap-in</span></span>
<span data-ttu-id="61489-103">創建安全用戶端或服務時，可以使用[證書](working-with-certificates.md)作為憑據。</span><span class="sxs-lookup"><span data-stu-id="61489-103">When you create a secure client or service, you can use a [certificate](working-with-certificates.md) as the credential.</span></span> <span data-ttu-id="61489-104">例如，常用類型的憑據是 X.509 憑證，您可以使用 方法<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType>創建該證書。</span><span class="sxs-lookup"><span data-stu-id="61489-104">For example, a common type of credential is the X.509 certificate, which you create with the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="61489-105">在 Windows 系統上可以使用 Microsoft 管理主控台 （MMC） 檢查三種不同類型的憑證存放區：</span><span class="sxs-lookup"><span data-stu-id="61489-105">There are three different types of certificate stores that you can examine with the Microsoft Management Console (MMC) on Windows systems:</span></span>

- <span data-ttu-id="61489-106">本地電腦：存儲是設備的本機存放區，並且對設備上的所有使用者是全域的。</span><span class="sxs-lookup"><span data-stu-id="61489-106">Local computer: The store is local to the device and global to all users on the device.</span></span>

- <span data-ttu-id="61489-107">當前使用者：存儲是設備上當前使用者帳戶的本機存放區。</span><span class="sxs-lookup"><span data-stu-id="61489-107">Current user: The store is local to the current user account on the device.</span></span>

- <span data-ttu-id="61489-108">服務帳戶：存儲是設備上特定服務的本機存放區。</span><span class="sxs-lookup"><span data-stu-id="61489-108">Service account: The store is local to a particular service on the device.</span></span>

## <a name="view-certificates-in-the-mmc-snap-in"></a><span data-ttu-id="61489-109">在 MMC 管理單元中查看證書</span><span class="sxs-lookup"><span data-stu-id="61489-109">View certificates in the MMC snap-in</span></span>

<span data-ttu-id="61489-110">以下過程演示如何檢查本地設備上的存儲以查找適當的證書：</span><span class="sxs-lookup"><span data-stu-id="61489-110">The following procedure demonstrates how to examine the stores on your local device to find an appropriate certificate:</span></span>
  
1. <span data-ttu-id="61489-111">選擇"從**開始"** 功能表**中運行**，然後輸入*mmc*。</span><span class="sxs-lookup"><span data-stu-id="61489-111">Select **Run** from the **Start** menu, and then enter *mmc*.</span></span>

    <span data-ttu-id="61489-112">將顯示 MMC。</span><span class="sxs-lookup"><span data-stu-id="61489-112">The MMC appears.</span></span>
  
2. <span data-ttu-id="61489-113">從 **"檔**"功能表中，選擇 **"添加/刪除對齊入"。**</span><span class="sxs-lookup"><span data-stu-id="61489-113">From the **File** menu, select **Add/Remove Snap In**.</span></span>

    <span data-ttu-id="61489-114">將顯示 **"添加或刪除對齊"** 視窗。</span><span class="sxs-lookup"><span data-stu-id="61489-114">The **Add or Remove Snap-ins** window appears.</span></span>
  
3. <span data-ttu-id="61489-115">從 **"可用管理單元**"清單中，選擇 **"證書**"，然後選擇 **"添加**"。</span><span class="sxs-lookup"><span data-stu-id="61489-115">From the **Available snap-ins** list, choose **Certificates**, then select **Add**.</span></span>  

    ![添加證書管理單元](./media/mmc-add-certificate-snap-in.png)
  
4. <span data-ttu-id="61489-117">在 **"證書入駐"** 視窗中，選擇 **"電腦帳戶**"，然後選擇 **"下一步**"。</span><span class="sxs-lookup"><span data-stu-id="61489-117">In the **Certificates snap-in** window, select **Computer account**, and then select **Next**.</span></span>
  
    <span data-ttu-id="61489-118">或者，您可以選擇特定服務的當前使用者或服務**帳戶\*\*\*\*的"我的使用者帳戶**"。</span><span class="sxs-lookup"><span data-stu-id="61489-118">Optionally, you can select **My user account** for the current user or **Service account** for a particular service.</span></span>

    > [!NOTE]
    > <span data-ttu-id="61489-119">如果您不是設備的管理員，則只能管理使用者帳戶的證書。</span><span class="sxs-lookup"><span data-stu-id="61489-119">If you're not an administrator for your device, you can manage certificates only for your user account.</span></span>
  
5. <span data-ttu-id="61489-120">在 **"選擇電腦"** 視窗中，保持**本地電腦**選中狀態，然後選擇 **"完成**"。</span><span class="sxs-lookup"><span data-stu-id="61489-120">In the **Select Computer** window, leave **Local computer** selected, and then select **Finish**.</span></span>  
  
6. <span data-ttu-id="61489-121">在 **"添加或刪除對齊"** 視窗中，選擇 **"確定**"。</span><span class="sxs-lookup"><span data-stu-id="61489-121">In the **Add or Remove Snap-in** window, select **OK**.</span></span>  
  
    ![添加證書管理單元](./media/mmc-certificate-snap-in-selected.png)

7. <span data-ttu-id="61489-123">可選：從 **"檔**"功能表中，選擇 **"保存\*\*\*\*"或"保存為"** 以保存 MMC 主控台檔以供以後使用。</span><span class="sxs-lookup"><span data-stu-id="61489-123">Optional: From the **File** menu, select **Save** or **Save As** to save the MMC console file for later use.</span></span>  

8. <span data-ttu-id="61489-124">要在 MMC 管理單元中查看證書，請在左側窗格中選擇 **"主控台根"，** 然後展開**證書（本地電腦）。**</span><span class="sxs-lookup"><span data-stu-id="61489-124">To view your certificates in the MMC snap-in, select **Console Root** in the left pane, then expand **Certificates (Local Computer)**.</span></span>

    <span data-ttu-id="61489-125">將顯示每種類型的證書的目錄清單。</span><span class="sxs-lookup"><span data-stu-id="61489-125">A list of directories for each type of certificate appears.</span></span> <span data-ttu-id="61489-126">在每個證書目錄中，您可以查看、匯出、導入和刪除其證書。</span><span class="sxs-lookup"><span data-stu-id="61489-126">From each certificate directory, you can view, export, import, and delete its certificates.</span></span>

## <a name="view-certificates-with-the-certificate-manager-tool"></a><span data-ttu-id="61489-127">使用證書管理器工具查看證書</span><span class="sxs-lookup"><span data-stu-id="61489-127">View certificates with the Certificate Manager tool</span></span>

<span data-ttu-id="61489-128">您還可以使用證書管理器工具查看、匯出、導入和刪除證書。</span><span class="sxs-lookup"><span data-stu-id="61489-128">You can also view, export, import, and delete certificates by using the Certificate Manager tool.</span></span>

### <a name="to-view-certificates-for-the-local-device"></a><span data-ttu-id="61489-129">查看本地設備的證書</span><span class="sxs-lookup"><span data-stu-id="61489-129">To view certificates for the local device</span></span>

1. <span data-ttu-id="61489-130">選擇"**從開始"** 功能表**中運行**，然後輸入*certlm.msc*。</span><span class="sxs-lookup"><span data-stu-id="61489-130">Select **Run** from the **Start** menu, and then enter *certlm.msc*.</span></span>

    <span data-ttu-id="61489-131">將顯示本地設備的證書管理器工具。</span><span class="sxs-lookup"><span data-stu-id="61489-131">The Certificate Manager tool for the local device appears.</span></span>
  
2. <span data-ttu-id="61489-132">要查看證書，在左側窗格中的 **"證書 - 本地電腦**"下，請展開要查看的證書類型的目錄。</span><span class="sxs-lookup"><span data-stu-id="61489-132">To view your certificates, under **Certificates - Local Computer** in the left pane, expand the directory for the type of certificate you want to view.</span></span>

### <a name="to-view-certificates-for-the-current-user"></a><span data-ttu-id="61489-133">查看當前使用者的證書</span><span class="sxs-lookup"><span data-stu-id="61489-133">To view certificates for the current user</span></span>

1. <span data-ttu-id="61489-134">選擇"**從開始"** 功能表**中運行**，然後輸入*certmgr.msc*。</span><span class="sxs-lookup"><span data-stu-id="61489-134">Select **Run** from the **Start** menu, and then enter *certmgr.msc*.</span></span>

    <span data-ttu-id="61489-135">將顯示當前使用者的證書管理器工具。</span><span class="sxs-lookup"><span data-stu-id="61489-135">The Certificate Manager tool for the current user appears.</span></span>
  
2. <span data-ttu-id="61489-136">要查看證書，在左側窗格中的 **"證書 - 當前使用者**"下，請展開要查看的證書類型的目錄。</span><span class="sxs-lookup"><span data-stu-id="61489-136">To view your certificates, under **Certificates - Current User** in the left pane, expand the directory for the type of certificate you want to view.</span></span>

## <a name="see-also"></a><span data-ttu-id="61489-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="61489-137">See also</span></span>

- [<span data-ttu-id="61489-138">使用證書</span><span class="sxs-lookup"><span data-stu-id="61489-138">Working with certificates</span></span>](working-with-certificates.md)
- [<span data-ttu-id="61489-139">如何：創建臨時證書，供開發期間使用</span><span class="sxs-lookup"><span data-stu-id="61489-139">How to: Create temporary certificates for use during development</span></span>](how-to-create-temporary-certificates-for-use-during-development.md)
- [<span data-ttu-id="61489-140">如何：檢索證書的指紋</span><span class="sxs-lookup"><span data-stu-id="61489-140">How to: Retrieve the thumbprint of a certificate</span></span>](how-to-retrieve-the-thumbprint-of-a-certificate.md)
