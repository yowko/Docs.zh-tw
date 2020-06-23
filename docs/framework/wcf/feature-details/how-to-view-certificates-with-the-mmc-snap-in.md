---
title: How to：使用 MMC 嵌入式管理單元來查看憑證
description: 安全的 WCF 用戶端或服務可以使用憑證做為認證。 瞭解您可以使用 MMC 外掛程式檢查的憑證存放區類型。
ms.date: 02/25/2019
helpviewer_keywords:
- certificates [WCF], viewing with the MMC snap-in
ms.assetid: 2b8782aa-ebb4-4ee7-974b-90299e356dc5
ms.openlocfilehash: e63034e48ae836f67f89b454829f7196c94610cd
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246671"
---
# <a name="how-to-view-certificates-with-the-mmc-snap-in"></a><span data-ttu-id="1ce7f-104">How to：使用 MMC 嵌入式管理單元來查看憑證</span><span class="sxs-lookup"><span data-stu-id="1ce7f-104">How to: View certificates with the MMC snap-in</span></span>
<span data-ttu-id="1ce7f-105">當您建立安全的用戶端或服務時，您可以使用[憑證做為認證。](working-with-certificates.md)</span><span class="sxs-lookup"><span data-stu-id="1ce7f-105">When you create a secure client or service, you can use a [certificate](working-with-certificates.md) as the credential.</span></span> <span data-ttu-id="1ce7f-106">例如，一般認證類型是您使用方法建立的 x.509 憑證 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="1ce7f-106">For example, a common type of credential is the X.509 certificate, which you create with the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="1ce7f-107">您可以使用 Windows 系統上的 Microsoft Management Console （MMC）來檢查三種不同類型的憑證存放區：</span><span class="sxs-lookup"><span data-stu-id="1ce7f-107">There are three different types of certificate stores that you can examine with the Microsoft Management Console (MMC) on Windows systems:</span></span>

- <span data-ttu-id="1ce7f-108">本機電腦：此存放區位於裝置的本機，而且裝置上的所有使用者都是全域的。</span><span class="sxs-lookup"><span data-stu-id="1ce7f-108">Local computer: The store is local to the device and global to all users on the device.</span></span>

- <span data-ttu-id="1ce7f-109">目前的使用者：此存放區位於裝置上目前使用者帳戶的本機。</span><span class="sxs-lookup"><span data-stu-id="1ce7f-109">Current user: The store is local to the current user account on the device.</span></span>

- <span data-ttu-id="1ce7f-110">服務帳戶：此存放區位於裝置上的特定服務的本機。</span><span class="sxs-lookup"><span data-stu-id="1ce7f-110">Service account: The store is local to a particular service on the device.</span></span>

## <a name="view-certificates-in-the-mmc-snap-in"></a><span data-ttu-id="1ce7f-111">在 MMC 嵌入式管理單元中查看憑證</span><span class="sxs-lookup"><span data-stu-id="1ce7f-111">View certificates in the MMC snap-in</span></span>

<span data-ttu-id="1ce7f-112">下列程式示範如何檢查本機裝置上的存放區，以尋找適當的憑證：</span><span class="sxs-lookup"><span data-stu-id="1ce7f-112">The following procedure demonstrates how to examine the stores on your local device to find an appropriate certificate:</span></span>
  
1. <span data-ttu-id="1ce7f-113">從 [**開始**] 功能表中選取 [**執行**]，然後輸入*mmc*。</span><span class="sxs-lookup"><span data-stu-id="1ce7f-113">Select **Run** from the **Start** menu, and then enter *mmc*.</span></span>

    <span data-ttu-id="1ce7f-114">MMC 隨即出現。</span><span class="sxs-lookup"><span data-stu-id="1ce7f-114">The MMC appears.</span></span>
  
2. <span data-ttu-id="1ce7f-115">從 [**檔案**] 功能表中，選取 [**新增/移除嵌入式管理單元**]。</span><span class="sxs-lookup"><span data-stu-id="1ce7f-115">From the **File** menu, select **Add/Remove Snap In**.</span></span>

    <span data-ttu-id="1ce7f-116">[**新增或移除嵌入式管理單元**] 視窗隨即出現。</span><span class="sxs-lookup"><span data-stu-id="1ce7f-116">The **Add or Remove Snap-ins** window appears.</span></span>
  
3. <span data-ttu-id="1ce7f-117">從 [**可用的嵌入式管理單元**] 清單中，選擇 [**憑證**]，然後選取 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="1ce7f-117">From the **Available snap-ins** list, choose **Certificates**, then select **Add**.</span></span>  

    ![新增憑證嵌入式管理單元](./media/mmc-add-certificate-snap-in.png)
  
4. <span data-ttu-id="1ce7f-119">在 [**憑證**] 嵌入式管理單元視窗中，選取 [**電腦帳戶**]，然後選取 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="1ce7f-119">In the **Certificates snap-in** window, select **Computer account**, and then select **Next**.</span></span>
  
    <span data-ttu-id="1ce7f-120">（選擇性）您可以選取 [**我的使用者帳戶**]，以取得特定服務的目前使用者或**服務帳戶**。</span><span class="sxs-lookup"><span data-stu-id="1ce7f-120">Optionally, you can select **My user account** for the current user or **Service account** for a particular service.</span></span>

    > [!NOTE]
    > <span data-ttu-id="1ce7f-121">如果您不是裝置的系統管理員，則只能管理您的使用者帳戶的憑證。</span><span class="sxs-lookup"><span data-stu-id="1ce7f-121">If you're not an administrator for your device, you can manage certificates only for your user account.</span></span>
  
5. <span data-ttu-id="1ce7f-122">在 [**選取電腦**] 視窗中，保留選取 [**本機電腦**]，然後選取 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="1ce7f-122">In the **Select Computer** window, leave **Local computer** selected, and then select **Finish**.</span></span>  
  
6. <span data-ttu-id="1ce7f-123">在 [**新增或移除嵌入式管理單元**] 視窗中，選取 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="1ce7f-123">In the **Add or Remove Snap-in** window, select **OK**.</span></span>  
  
    ![新增憑證嵌入式管理單元](./media/mmc-certificate-snap-in-selected.png)

7. <span data-ttu-id="1ce7f-125">選擇性：**從 [檔案**] 功能表中，選取 [**儲存**] 或 [**另存**新檔] 以儲存 MMC 主控台檔案以供稍後使用。</span><span class="sxs-lookup"><span data-stu-id="1ce7f-125">Optional: From the **File** menu, select **Save** or **Save As** to save the MMC console file for later use.</span></span>  

8. <span data-ttu-id="1ce7f-126">若要在 MMC 嵌入式管理單元中查看憑證，請在左窗格中選取 [**主控台根目錄**]，然後展開 [**憑證（本機電腦）**]。</span><span class="sxs-lookup"><span data-stu-id="1ce7f-126">To view your certificates in the MMC snap-in, select **Console Root** in the left pane, then expand **Certificates (Local Computer)**.</span></span>

    <span data-ttu-id="1ce7f-127">每種憑證類型的目錄清單隨即出現。</span><span class="sxs-lookup"><span data-stu-id="1ce7f-127">A list of directories for each type of certificate appears.</span></span> <span data-ttu-id="1ce7f-128">您可以從每個憑證目錄中，查看、匯出、匯入和刪除其憑證。</span><span class="sxs-lookup"><span data-stu-id="1ce7f-128">From each certificate directory, you can view, export, import, and delete its certificates.</span></span>

## <a name="view-certificates-with-the-certificate-manager-tool"></a><span data-ttu-id="1ce7f-129">使用憑證管理員工具來查看憑證</span><span class="sxs-lookup"><span data-stu-id="1ce7f-129">View certificates with the Certificate Manager tool</span></span>

<span data-ttu-id="1ce7f-130">您也可以使用 [憑證管理員] 工具來查看、匯出、匯入和刪除憑證。</span><span class="sxs-lookup"><span data-stu-id="1ce7f-130">You can also view, export, import, and delete certificates by using the Certificate Manager tool.</span></span>

### <a name="to-view-certificates-for-the-local-device"></a><span data-ttu-id="1ce7f-131">若要查看本機裝置的憑證</span><span class="sxs-lookup"><span data-stu-id="1ce7f-131">To view certificates for the local device</span></span>

1. <span data-ttu-id="1ce7f-132">從 [**開始**] 功能表中選取 [**執行**]，然後輸入*certlm.msc*。</span><span class="sxs-lookup"><span data-stu-id="1ce7f-132">Select **Run** from the **Start** menu, and then enter *certlm.msc*.</span></span>

    <span data-ttu-id="1ce7f-133">本機裝置的 [憑證管理員] 工具隨即出現。</span><span class="sxs-lookup"><span data-stu-id="1ce7f-133">The Certificate Manager tool for the local device appears.</span></span>
  
2. <span data-ttu-id="1ce7f-134">若要查看您的憑證，請在左窗格中的 [**憑證-本機電腦**] 底下，展開您要查看之憑證類型的目錄。</span><span class="sxs-lookup"><span data-stu-id="1ce7f-134">To view your certificates, under **Certificates - Local Computer** in the left pane, expand the directory for the type of certificate you want to view.</span></span>

### <a name="to-view-certificates-for-the-current-user"></a><span data-ttu-id="1ce7f-135">若要查看目前使用者的憑證</span><span class="sxs-lookup"><span data-stu-id="1ce7f-135">To view certificates for the current user</span></span>

1. <span data-ttu-id="1ce7f-136">從 [**開始**] 功能表中選取 [**執行**]，然後輸入*certmgr.msc*。</span><span class="sxs-lookup"><span data-stu-id="1ce7f-136">Select **Run** from the **Start** menu, and then enter *certmgr.msc*.</span></span>

    <span data-ttu-id="1ce7f-137">目前使用者的 [憑證管理員] 工具隨即出現。</span><span class="sxs-lookup"><span data-stu-id="1ce7f-137">The Certificate Manager tool for the current user appears.</span></span>
  
2. <span data-ttu-id="1ce7f-138">若要查看您的憑證，請在左窗格中的 [**憑證-目前的使用者**] 底下，展開您要查看之憑證類型的目錄。</span><span class="sxs-lookup"><span data-stu-id="1ce7f-138">To view your certificates, under **Certificates - Current User** in the left pane, expand the directory for the type of certificate you want to view.</span></span>

## <a name="see-also"></a><span data-ttu-id="1ce7f-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ce7f-139">See also</span></span>

- [<span data-ttu-id="1ce7f-140">使用憑證</span><span class="sxs-lookup"><span data-stu-id="1ce7f-140">Working with certificates</span></span>](working-with-certificates.md)
- [<span data-ttu-id="1ce7f-141">如何：建立要在開發期間使用的暫時憑證</span><span class="sxs-lookup"><span data-stu-id="1ce7f-141">How to: Create temporary certificates for use during development</span></span>](how-to-create-temporary-certificates-for-use-during-development.md)
- [<span data-ttu-id="1ce7f-142">如何：取出憑證的指紋</span><span class="sxs-lookup"><span data-stu-id="1ce7f-142">How to: Retrieve the thumbprint of a certificate</span></span>](how-to-retrieve-the-thumbprint-of-a-certificate.md)
