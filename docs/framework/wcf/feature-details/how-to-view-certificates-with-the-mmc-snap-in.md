---
title: "HOW TO：使用 MMC 嵌入式管理單元來檢視憑證"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: certificates [WCF], viewing with the MMC snap-in
ms.assetid: 2b8782aa-ebb4-4ee7-974b-90299e356dc5
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5981e68ebe2870870fff5e92e87d7582ac2c42b5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-view-certificates-with-the-mmc-snap-in"></a><span data-ttu-id="481d0-102">HOW TO：使用 MMC 嵌入式管理單元來檢視憑證</span><span class="sxs-lookup"><span data-stu-id="481d0-102">How to: View Certificates with the MMC Snap-in</span></span>
<span data-ttu-id="481d0-103">常見的認證類型是 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="481d0-103">A common type of credential is the X.509 certificate.</span></span> <span data-ttu-id="481d0-104">當建立安全服務或用戶端時，您可以藉由使用像是 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> 方法，指定用來當做用戶端或服務認證的憑證。</span><span class="sxs-lookup"><span data-stu-id="481d0-104">When creating secure services or clients, you can specify a certificate be used as the client or service credential by using methods such as the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> method.</span></span> <span data-ttu-id="481d0-105">方法需要各種參數，例如儲存憑證的存放區，以及當搜尋憑證時要使用的值。</span><span class="sxs-lookup"><span data-stu-id="481d0-105">The method requires various parameters, such as the store where the certificate is stored and a value to use when searching for the certificate.</span></span> <span data-ttu-id="481d0-106">下列程序示範如何檢視電腦上的存放區，以尋找適當的憑證。</span><span class="sxs-lookup"><span data-stu-id="481d0-106">The following procedure demonstrates how to examine the stores on a computer to find an appropriate certificate.</span></span> <span data-ttu-id="481d0-107">尋找憑證指紋的範例，請參閱[How to： 擷取憑證的指紋](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)。</span><span class="sxs-lookup"><span data-stu-id="481d0-107">For an example of finding the certificate thumbprint, see [How to: Retrieve the Thumbprint of a Certificate](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
### <a name="to-view-certificates-in-the-mmc-snap-in"></a><span data-ttu-id="481d0-108">在 MMC 嵌入式管理單元中檢視憑證</span><span class="sxs-lookup"><span data-stu-id="481d0-108">To view certificates in the MMC snap-in</span></span>  
  
1.  <span data-ttu-id="481d0-109">開啟 [命令提示字元] 視窗。</span><span class="sxs-lookup"><span data-stu-id="481d0-109">Open a Command Prompt window.</span></span>  
  
2.  <span data-ttu-id="481d0-110">型別`mmc`按下 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="481d0-110">Type `mmc` and press the ENTER key.</span></span> <span data-ttu-id="481d0-111">請注意，若要檢視本機電腦存放區中的憑證，您必須是系統管理員的角色。</span><span class="sxs-lookup"><span data-stu-id="481d0-111">Note that to view certificates in the local machine store, you must be in the Administrator role.</span></span>  
  
3.  <span data-ttu-id="481d0-112">在**檔案**功能表上，按一下 **新增/移除嵌入式管理單元**。</span><span class="sxs-lookup"><span data-stu-id="481d0-112">On the **File** menu, click **Add/Remove Snap In**.</span></span>  
  
4.  <span data-ttu-id="481d0-113">按一下 [加入] 。</span><span class="sxs-lookup"><span data-stu-id="481d0-113">Click **Add**.</span></span>  
  
5.  <span data-ttu-id="481d0-114">在**新增獨立嵌入式管理單元**對話方塊中，選取**憑證**。</span><span class="sxs-lookup"><span data-stu-id="481d0-114">In the **Add Standalone Snap-in** dialog box, select **Certificates**.</span></span>  
  
6.  <span data-ttu-id="481d0-115">按一下 [加入] 。</span><span class="sxs-lookup"><span data-stu-id="481d0-115">Click **Add**.</span></span>  
  
7.  <span data-ttu-id="481d0-116">在**憑證嵌入式管理單元**對話方塊中，選取**電腦帳戶**按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="481d0-116">In the **Certificates snap-in** dialog box, select **Computer account** and click **Next**.</span></span> <span data-ttu-id="481d0-117">或者，您可以選取**我的使用者帳戶**或**服務帳戶**。</span><span class="sxs-lookup"><span data-stu-id="481d0-117">Optionally, you can select **My User account** or **Service account**.</span></span> <span data-ttu-id="481d0-118">如果您不是電腦的系統管理員，就只能夠管理您使用者帳戶的憑證。</span><span class="sxs-lookup"><span data-stu-id="481d0-118">If you are not an administrator of the computer, you can manage certificates only for your user account.</span></span>  
  
8.  <span data-ttu-id="481d0-119">在**選取電腦**對話方塊中，按一下 **完成**。</span><span class="sxs-lookup"><span data-stu-id="481d0-119">In the **Select Computer** dialog box, click **Finish**.</span></span>  
  
9. <span data-ttu-id="481d0-120">在**新增獨立嵌入式管理單元**對話方塊中，按一下 **關閉**。</span><span class="sxs-lookup"><span data-stu-id="481d0-120">In the **Add Standalone Snap-in** dialog box, click **Close**.</span></span>  
  
10. <span data-ttu-id="481d0-121">在**新增/移除嵌入式管理單元**對話方塊中，按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="481d0-121">On the **Add/Remove Snap-in** dialog box, click **OK**.</span></span>  
  
11. <span data-ttu-id="481d0-122">在**主控台根目錄**視窗中，按一下 **憑證 （本機電腦）**以檢視憑證存放區的電腦。</span><span class="sxs-lookup"><span data-stu-id="481d0-122">In the **Console Root** window, click **Certificates (Local Computer)** to view the certificate stores for the computer.</span></span>  
  
12. <span data-ttu-id="481d0-123">選擇項。</span><span class="sxs-lookup"><span data-stu-id="481d0-123">Optional.</span></span> <span data-ttu-id="481d0-124">若要檢視您帳戶的憑證，請重複步驟 3 到 6。</span><span class="sxs-lookup"><span data-stu-id="481d0-124">To view certificates for your account, repeat steps 3 to 6.</span></span> <span data-ttu-id="481d0-125">在步驟 7，而不是選取**電腦帳戶**，按一下 **我的使用者帳戶**並重複步驟 8 到 10。</span><span class="sxs-lookup"><span data-stu-id="481d0-125">In step 7, instead of selecting **Computer account**, click **My User account** and repeat steps 8 to 10.</span></span>  
  
13. <span data-ttu-id="481d0-126">選擇項。</span><span class="sxs-lookup"><span data-stu-id="481d0-126">Optional.</span></span> <span data-ttu-id="481d0-127">在**檔案**功能表上，按一下 **儲存**或**存**。</span><span class="sxs-lookup"><span data-stu-id="481d0-127">On the **File** menu, click **Save** or **Save As**.</span></span> <span data-ttu-id="481d0-128">儲存主控台檔案供稍後使用。</span><span class="sxs-lookup"><span data-stu-id="481d0-128">Save the console file for later reuse.</span></span>  
  
## <a name="viewing-certificates-with-internet-explorer"></a><span data-ttu-id="481d0-129">使用 Internet Explorer 檢視憑證</span><span class="sxs-lookup"><span data-stu-id="481d0-129">Viewing Certificates with Internet Explorer</span></span>  
 <span data-ttu-id="481d0-130">您也可以使用 Internet Explorer 檢視、匯出、匯入和刪除憑證。</span><span class="sxs-lookup"><span data-stu-id="481d0-130">You can also view, export, import, and delete certificates by using Internet Explorer.</span></span>  
  
#### <a name="to-view-certificates-with-internet-explorer"></a><span data-ttu-id="481d0-131">使用 Internet Explorer 檢視憑證</span><span class="sxs-lookup"><span data-stu-id="481d0-131">To view certificates with Internet Explorer</span></span>  
  
1.  <span data-ttu-id="481d0-132">在 Internet Explorer 中，按一下**工具**，然後按一下 [**網際網路選項**顯示**網際網路選項**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="481d0-132">In Internet Explorer, click **Tools**, then click **Internet Options** to display the **Internet Options** dialog box.</span></span>  
  
2.  <span data-ttu-id="481d0-133">按一下**內容** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="481d0-133">Click the **Content** tab.</span></span>  
  
3.  <span data-ttu-id="481d0-134">在下**憑證**，按一下 **憑證**。</span><span class="sxs-lookup"><span data-stu-id="481d0-134">Under **Certificates**, click **Certificates**.</span></span>  
  
4.  <span data-ttu-id="481d0-135">若要檢視任何憑證的詳細資料、 選取憑證按一下**檢視**。</span><span class="sxs-lookup"><span data-stu-id="481d0-135">To view details of any certificate, select the certificate and click **View**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="481d0-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="481d0-136">See Also</span></span>  
 [<span data-ttu-id="481d0-137">使用憑證</span><span class="sxs-lookup"><span data-stu-id="481d0-137">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="481d0-138">如何： 建立開發時使用的暫時憑證</span><span class="sxs-lookup"><span data-stu-id="481d0-138">How to: Create Temporary Certificates for Use During Development</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)  
 [<span data-ttu-id="481d0-139">如何： 擷取憑證的指紋</span><span class="sxs-lookup"><span data-stu-id="481d0-139">How to: Retrieve the Thumbprint of a Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)
