---
title: HOW TO：使用 MMC 嵌入式管理單元檢視憑證
ms.date: 02/25/2019
helpviewer_keywords:
- certificates [WCF], viewing with the MMC snap-in
ms.assetid: 2b8782aa-ebb4-4ee7-974b-90299e356dc5
ms.openlocfilehash: 69f79b64250ff46524e7b4720d13351774875a3f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59167501"
---
# <a name="how-to-view-certificates-with-the-mmc-snap-in"></a><span data-ttu-id="84711-102">HOW TO：使用 MMC 嵌入式管理單元檢視憑證</span><span class="sxs-lookup"><span data-stu-id="84711-102">How to: View certificates with the MMC snap-in</span></span>
<span data-ttu-id="84711-103">當您建立安全的用戶端或服務時，您可以使用[憑證](working-with-certificates.md)身分的認證。</span><span class="sxs-lookup"><span data-stu-id="84711-103">When you create a secure client or service, you can use a [certificate](working-with-certificates.md) as the credential.</span></span> <span data-ttu-id="84711-104">例如，常見的認證類型是 X.509 憑證，您建立與<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="84711-104">For example, a common type of credential is the X.509 certificate, which you create with the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType> method.</span></span> 

<span data-ttu-id="84711-105">有三種不同的類型，您可以檢查與 Microsoft Management Console (MMC) 在 Windows 系統上的憑證存放區：</span><span class="sxs-lookup"><span data-stu-id="84711-105">There are three different types of certificate stores that you can examine with the Microsoft Management Console (MMC) on Windows systems:</span></span>

- <span data-ttu-id="84711-106">本機電腦：本機裝置和裝置上的所有使用者通用存放區。</span><span class="sxs-lookup"><span data-stu-id="84711-106">Local computer: The store is local to the device and global to all users on the device.</span></span>

- <span data-ttu-id="84711-107">目前的使用者：存放區是目前的使用者帳戶，在裝置上的本機。</span><span class="sxs-lookup"><span data-stu-id="84711-107">Current user: The store is local to the current user account on the device.</span></span>

- <span data-ttu-id="84711-108">服務帳戶：存放區是在裝置上的特定服務的本機。</span><span class="sxs-lookup"><span data-stu-id="84711-108">Service account: The store is local to a particular service on the device.</span></span>

## <a name="view-certificates-in-the-mmc-snap-in"></a><span data-ttu-id="84711-109">在 MMC 嵌入式管理單元檢視憑證</span><span class="sxs-lookup"><span data-stu-id="84711-109">View certificates in the MMC snap-in</span></span> 

<span data-ttu-id="84711-110">下列程序示範如何檢查在您的本機裝置，以尋找適當的憑證存放區：</span><span class="sxs-lookup"><span data-stu-id="84711-110">The following procedure demonstrates how to examine the stores on your local device to find an appropriate certificate:</span></span> 
  
1. <span data-ttu-id="84711-111">選取 **執行**從**開始**功能表，然後輸入*mmc*。</span><span class="sxs-lookup"><span data-stu-id="84711-111">Select **Run** from the **Start** menu, and then enter *mmc*.</span></span> 

    <span data-ttu-id="84711-112">MMC 隨即出現。</span><span class="sxs-lookup"><span data-stu-id="84711-112">The MMC appears.</span></span> 
  
2. <span data-ttu-id="84711-113">從**檔案**功能表上，選取**新增/移除嵌入式管理單元**。</span><span class="sxs-lookup"><span data-stu-id="84711-113">From the **File** menu, select **Add/Remove Snap In**.</span></span> 
    
    <span data-ttu-id="84711-114">**新增或移除嵌入式管理單元** 視窗隨即出現。</span><span class="sxs-lookup"><span data-stu-id="84711-114">The **Add or Remove Snap-ins** window appears.</span></span>
  
3. <span data-ttu-id="84711-115">從**可用的嵌入式管理單元**清單中，選擇**憑證**，然後選取**新增**。</span><span class="sxs-lookup"><span data-stu-id="84711-115">From the **Available snap-ins** list, choose **Certificates**, then select **Add**.</span></span>  

    ![新增憑證嵌入式管理單元](./media/mmc-add-certificate-snap-in.png)
  
4. <span data-ttu-id="84711-117">在 [**憑證嵌入式管理單元**視窗中，選取**電腦帳戶**，然後選取**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="84711-117">In the **Certificates snap-in** window, select **Computer account**, and then select **Next**.</span></span> 
  
    <span data-ttu-id="84711-118">或者，您可以選取**我的使用者帳戶**目前的使用者或**服務帳戶**針對特定服務。</span><span class="sxs-lookup"><span data-stu-id="84711-118">Optionally, you can select **My user account** for the current user or **Service account** for a particular service.</span></span> 

    > [!NOTE]
    > <span data-ttu-id="84711-119">如果您不是為您的裝置系統管理員，您可以只針對您的使用者帳戶來管理憑證。</span><span class="sxs-lookup"><span data-stu-id="84711-119">If you're not an administrator for your device, you can manage certificates only for your user account.</span></span>
  
5. <span data-ttu-id="84711-120">在 [**選取電腦**] 視窗中，保持**本機電腦**選取，然後按**完成**。</span><span class="sxs-lookup"><span data-stu-id="84711-120">In the **Select Computer** window, leave **Local computer** selected, and then select **Finish**.</span></span>  
  
6. <span data-ttu-id="84711-121">在 **新增或移除嵌入式管理單元**視窗中，選取**確定**。</span><span class="sxs-lookup"><span data-stu-id="84711-121">In the **Add or Remove Snap-in** window, select **OK**.</span></span>  
  
    ![新增憑證嵌入式管理單元](./media/mmc-certificate-snap-in-selected.png)

7. <span data-ttu-id="84711-123">選擇項：從**檔案**功能表上，選取**儲存**或是**另存新檔**儲存 MMC 主控台檔案供稍後使用。</span><span class="sxs-lookup"><span data-stu-id="84711-123">Optional: From the **File** menu, select **Save** or **Save As** to save the MMC console file for later use.</span></span>  

8. <span data-ttu-id="84711-124">若要檢視您的憑證 MMC 嵌入式管理單元中，選取**主控台根目錄**的左窗格中，然後展開**Certificates (Local Computer)**。</span><span class="sxs-lookup"><span data-stu-id="84711-124">To view your certificates in the MMC snap-in, select **Console Root** in the left pane, then expand **Certificates (Local Computer)**.</span></span>

    <span data-ttu-id="84711-125">每種類型的憑證的目錄清單隨即出現。</span><span class="sxs-lookup"><span data-stu-id="84711-125">A list of directories for each type of certificate appears.</span></span> <span data-ttu-id="84711-126">從每個憑證目錄中，您可以檢視、 匯出、 匯入，並刪除其憑證。</span><span class="sxs-lookup"><span data-stu-id="84711-126">From each certificate directory, you can view, export, import, and delete its certificates.</span></span>

## <a name="view-certificates-with-the-certificate-manager-tool"></a><span data-ttu-id="84711-127">使用憑證管理員工具檢視憑證</span><span class="sxs-lookup"><span data-stu-id="84711-127">View certificates with the Certificate Manager tool</span></span>

<span data-ttu-id="84711-128">您也可以檢視、 匯出、 匯入，並使用憑證管理員工具來刪除憑證。</span><span class="sxs-lookup"><span data-stu-id="84711-128">You can also view, export, import, and delete certificates by using the Certificate Manager tool.</span></span>

### <a name="to-view-certificates-for-the-local-device"></a><span data-ttu-id="84711-129">若要檢視本機裝置的憑證</span><span class="sxs-lookup"><span data-stu-id="84711-129">To view certificates for the local device</span></span>

1. <span data-ttu-id="84711-130">選取 **執行**從**開始**功能表，然後輸入*certlm.msc*。</span><span class="sxs-lookup"><span data-stu-id="84711-130">Select **Run** from the **Start** menu, and then enter *certlm.msc*.</span></span> 

    <span data-ttu-id="84711-131">憑證管理員工具的本機裝置會出現。</span><span class="sxs-lookup"><span data-stu-id="84711-131">The Certificate Manager tool for the local device appears.</span></span> 
  
2. <span data-ttu-id="84711-132">若要檢視您的憑證，在**憑證-本機電腦**在左窗格中，依序展開您想要檢視的憑證類型的目錄。</span><span class="sxs-lookup"><span data-stu-id="84711-132">To view your certificates, under **Certificates - Local Computer** in the left pane, expand the directory for the type of certificate you want to view.</span></span>

### <a name="to-view-certificates-for-the-current-user"></a><span data-ttu-id="84711-133">若要檢視目前的使用者憑證</span><span class="sxs-lookup"><span data-stu-id="84711-133">To view certificates for the current user</span></span>

1. <span data-ttu-id="84711-134">選取 **執行**從**開始**功能表，然後輸入*certmgr.msc*。</span><span class="sxs-lookup"><span data-stu-id="84711-134">Select **Run** from the **Start** menu, and then enter *certmgr.msc*.</span></span> 

    <span data-ttu-id="84711-135">目前使用者的憑證管理員工具隨即出現。</span><span class="sxs-lookup"><span data-stu-id="84711-135">The Certificate Manager tool for the current user appears.</span></span> 
  
2. <span data-ttu-id="84711-136">若要檢視您的憑證，在**憑證-目前使用者**在左窗格中，依序展開您想要檢視的憑證類型的目錄。</span><span class="sxs-lookup"><span data-stu-id="84711-136">To view your certificates, under **Certificates - Current User** in the left pane, expand the directory for the type of certificate you want to view.</span></span>

## <a name="see-also"></a><span data-ttu-id="84711-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84711-137">See also</span></span>

- [<span data-ttu-id="84711-138">使用憑證</span><span class="sxs-lookup"><span data-stu-id="84711-138">Working with certificates</span></span>](working-with-certificates.md)
- [<span data-ttu-id="84711-139">HOW TO：建立開發時要使用的暫時憑證</span><span class="sxs-lookup"><span data-stu-id="84711-139">How to: Create temporary certificates for use during development</span></span>](how-to-create-temporary-certificates-for-use-during-development.md)
- [<span data-ttu-id="84711-140">HOW TO：擷取憑證的指紋</span><span class="sxs-lookup"><span data-stu-id="84711-140">How to: Retrieve the thumbprint of a certificate</span></span>](how-to-retrieve-the-thumbprint-of-a-certificate.md)
