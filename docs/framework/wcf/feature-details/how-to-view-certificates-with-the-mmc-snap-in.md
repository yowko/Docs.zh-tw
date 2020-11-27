---
title: 如何：使用 MMC 嵌入式管理單元來查看憑證
description: 安全的 WCF 用戶端或服務可以使用憑證作為認證。 瞭解您可以使用 MMC 外掛程式檢查的憑證存放區類型。
ms.date: 02/25/2019
helpviewer_keywords:
- certificates [WCF], viewing with the MMC snap-in
ms.assetid: 2b8782aa-ebb4-4ee7-974b-90299e356dc5
ms.openlocfilehash: 1f20384f16b3b5b898f926258d76a6a2773eaaa1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96280620"
---
# <a name="how-to-view-certificates-with-the-mmc-snap-in"></a><span data-ttu-id="2edd9-104">如何：使用 MMC 嵌入式管理單元來查看憑證</span><span class="sxs-lookup"><span data-stu-id="2edd9-104">How to: View certificates with the MMC snap-in</span></span>

<span data-ttu-id="2edd9-105">當您建立安全的用戶端或服務時，您可以使用 [憑證作為認證](working-with-certificates.md) 。</span><span class="sxs-lookup"><span data-stu-id="2edd9-105">When you create a secure client or service, you can use a [certificate](working-with-certificates.md) as the credential.</span></span> <span data-ttu-id="2edd9-106">例如，一般的認證類型是您使用方法建立的 x.509 憑證 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="2edd9-106">For example, a common type of credential is the X.509 certificate, which you create with the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="2edd9-107">您可以使用三種不同類型的憑證存放區來檢查 Windows 系統上的 Microsoft Management Console (MMC) ：</span><span class="sxs-lookup"><span data-stu-id="2edd9-107">There are three different types of certificate stores that you can examine with the Microsoft Management Console (MMC) on Windows systems:</span></span>

- <span data-ttu-id="2edd9-108">本機電腦：存放區是裝置的本機存放區，而且是裝置上所有使用者的全域存放區。</span><span class="sxs-lookup"><span data-stu-id="2edd9-108">Local computer: The store is local to the device and global to all users on the device.</span></span>

- <span data-ttu-id="2edd9-109">目前使用者：存放區是裝置上目前使用者帳戶的本機存放區。</span><span class="sxs-lookup"><span data-stu-id="2edd9-109">Current user: The store is local to the current user account on the device.</span></span>

- <span data-ttu-id="2edd9-110">服務帳戶：存放區是裝置上特定服務的本機存放區。</span><span class="sxs-lookup"><span data-stu-id="2edd9-110">Service account: The store is local to a particular service on the device.</span></span>

## <a name="view-certificates-in-the-mmc-snap-in"></a><span data-ttu-id="2edd9-111">在 MMC 嵌入式管理單元中查看憑證</span><span class="sxs-lookup"><span data-stu-id="2edd9-111">View certificates in the MMC snap-in</span></span>

<span data-ttu-id="2edd9-112">下列程式示範如何檢查本機裝置上的存放區，以尋找適當的憑證：</span><span class="sxs-lookup"><span data-stu-id="2edd9-112">The following procedure demonstrates how to examine the stores on your local device to find an appropriate certificate:</span></span>
  
1. <span data-ttu-id="2edd9-113">從 [**開始**] 功能表選取 [**執行**]，然後輸入 *mmc*。</span><span class="sxs-lookup"><span data-stu-id="2edd9-113">Select **Run** from the **Start** menu, and then enter *mmc*.</span></span>

    <span data-ttu-id="2edd9-114">MMC 隨即出現。</span><span class="sxs-lookup"><span data-stu-id="2edd9-114">The MMC appears.</span></span>
  
2. <span data-ttu-id="2edd9-115">**在 [檔案**] 功能表中，選取 [**新增/移除嵌入式管理單元**]。</span><span class="sxs-lookup"><span data-stu-id="2edd9-115">From the **File** menu, select **Add/Remove Snap In**.</span></span>

    <span data-ttu-id="2edd9-116">[ **新增或移除嵌入式管理單元** ] 視窗隨即出現。</span><span class="sxs-lookup"><span data-stu-id="2edd9-116">The **Add or Remove Snap-ins** window appears.</span></span>
  
3. <span data-ttu-id="2edd9-117">從 [ **可用的嵌入式管理單元** ] 清單中，選擇 [ **憑證**]，然後選取 [ **新增**]。</span><span class="sxs-lookup"><span data-stu-id="2edd9-117">From the **Available snap-ins** list, choose **Certificates**, then select **Add**.</span></span>  

    ![新增憑證嵌入式管理單元](./media/mmc-add-certificate-snap-in.png)
  
4. <span data-ttu-id="2edd9-119">在 [ **憑證** ] 嵌入式管理單元視窗中，選取 [ **電腦帳戶**]，然後選取 **[下一步**]。</span><span class="sxs-lookup"><span data-stu-id="2edd9-119">In the **Certificates snap-in** window, select **Computer account**, and then select **Next**.</span></span>
  
    <span data-ttu-id="2edd9-120">（選擇性）您可以為特定服務的目前使用者或 **服務帳戶** 選取 [**我的使用者帳戶**]。</span><span class="sxs-lookup"><span data-stu-id="2edd9-120">Optionally, you can select **My user account** for the current user or **Service account** for a particular service.</span></span>

    > [!NOTE]
    > <span data-ttu-id="2edd9-121">如果您不是裝置的系統管理員，您只能管理您的使用者帳戶的憑證。</span><span class="sxs-lookup"><span data-stu-id="2edd9-121">If you're not an administrator for your device, you can manage certificates only for your user account.</span></span>
  
5. <span data-ttu-id="2edd9-122">在 [ **選取電腦** ] 視窗中，將 [ **本機電腦** ] 保持選取狀態，然後選取 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="2edd9-122">In the **Select Computer** window, leave **Local computer** selected, and then select **Finish**.</span></span>  
  
6. <span data-ttu-id="2edd9-123">在 [ **新增或移除嵌入式管理單元** ] 視窗中，選取 **[確定**]。</span><span class="sxs-lookup"><span data-stu-id="2edd9-123">In the **Add or Remove Snap-in** window, select **OK**.</span></span>  
  
    ![新增憑證嵌入式管理單元](./media/mmc-certificate-snap-in-selected.png)

7. <span data-ttu-id="2edd9-125">選擇性： **在 [檔案** ] 功能表中，選取 [ **儲存** ] 或 [ **另存** 新檔] 以儲存 MMC 主控台檔案以供稍後使用。</span><span class="sxs-lookup"><span data-stu-id="2edd9-125">Optional: From the **File** menu, select **Save** or **Save As** to save the MMC console file for later use.</span></span>  

8. <span data-ttu-id="2edd9-126">若要在 MMC 嵌入式管理單元中查看您的憑證，請選取左窗格中的 [ **主控台根目錄** ]，然後展開 [ **憑證 (本機電腦)**]。</span><span class="sxs-lookup"><span data-stu-id="2edd9-126">To view your certificates in the MMC snap-in, select **Console Root** in the left pane, then expand **Certificates (Local Computer)**.</span></span>

    <span data-ttu-id="2edd9-127">每種憑證類型的目錄清單隨即出現。</span><span class="sxs-lookup"><span data-stu-id="2edd9-127">A list of directories for each type of certificate appears.</span></span> <span data-ttu-id="2edd9-128">您可以從每個憑證目錄查看、匯出、匯入和刪除其憑證。</span><span class="sxs-lookup"><span data-stu-id="2edd9-128">From each certificate directory, you can view, export, import, and delete its certificates.</span></span>

## <a name="view-certificates-with-the-certificate-manager-tool"></a><span data-ttu-id="2edd9-129">使用憑證管理員工具來查看憑證</span><span class="sxs-lookup"><span data-stu-id="2edd9-129">View certificates with the Certificate Manager tool</span></span>

<span data-ttu-id="2edd9-130">您也可以使用憑證管理員工具來查看、匯出、匯入和刪除憑證。</span><span class="sxs-lookup"><span data-stu-id="2edd9-130">You can also view, export, import, and delete certificates by using the Certificate Manager tool.</span></span>

### <a name="to-view-certificates-for-the-local-device"></a><span data-ttu-id="2edd9-131">若要查看本機裝置的憑證</span><span class="sxs-lookup"><span data-stu-id="2edd9-131">To view certificates for the local device</span></span>

1. <span data-ttu-id="2edd9-132">從 [**開始**] 功能表選取 [**執行**]，然後輸入 *certlm.msc。*</span><span class="sxs-lookup"><span data-stu-id="2edd9-132">Select **Run** from the **Start** menu, and then enter *certlm.msc*.</span></span>

    <span data-ttu-id="2edd9-133">本機裝置的 [憑證管理員] 工具隨即出現。</span><span class="sxs-lookup"><span data-stu-id="2edd9-133">The Certificate Manager tool for the local device appears.</span></span>
  
2. <span data-ttu-id="2edd9-134">若要查看您的憑證，請在左窗格的 [ **憑證-本機電腦** ] 底下，展開您想要查看之憑證類型的目錄。</span><span class="sxs-lookup"><span data-stu-id="2edd9-134">To view your certificates, under **Certificates - Local Computer** in the left pane, expand the directory for the type of certificate you want to view.</span></span>

### <a name="to-view-certificates-for-the-current-user"></a><span data-ttu-id="2edd9-135">若要查看目前使用者的憑證</span><span class="sxs-lookup"><span data-stu-id="2edd9-135">To view certificates for the current user</span></span>

1. <span data-ttu-id="2edd9-136">從 [**開始**] 功能表選取 [**執行**]，然後輸入 *certmgr.msc。*</span><span class="sxs-lookup"><span data-stu-id="2edd9-136">Select **Run** from the **Start** menu, and then enter *certmgr.msc*.</span></span>

    <span data-ttu-id="2edd9-137">目前使用者的憑證管理員工具隨即出現。</span><span class="sxs-lookup"><span data-stu-id="2edd9-137">The Certificate Manager tool for the current user appears.</span></span>
  
2. <span data-ttu-id="2edd9-138">若要查看您的憑證，請在左窗格的 [ **憑證-目前的使用者** ] 底下，展開您想要查看之憑證類型的目錄。</span><span class="sxs-lookup"><span data-stu-id="2edd9-138">To view your certificates, under **Certificates - Current User** in the left pane, expand the directory for the type of certificate you want to view.</span></span>

## <a name="see-also"></a><span data-ttu-id="2edd9-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2edd9-139">See also</span></span>

- [<span data-ttu-id="2edd9-140">使用憑證</span><span class="sxs-lookup"><span data-stu-id="2edd9-140">Working with certificates</span></span>](working-with-certificates.md)
- [<span data-ttu-id="2edd9-141">如何：建立要在開發期間使用的暫時憑證</span><span class="sxs-lookup"><span data-stu-id="2edd9-141">How to: Create temporary certificates for use during development</span></span>](how-to-create-temporary-certificates-for-use-during-development.md)
- [<span data-ttu-id="2edd9-142">如何：取得憑證的指紋</span><span class="sxs-lookup"><span data-stu-id="2edd9-142">How to: Retrieve the thumbprint of a certificate</span></span>](how-to-retrieve-the-thumbprint-of-a-certificate.md)
