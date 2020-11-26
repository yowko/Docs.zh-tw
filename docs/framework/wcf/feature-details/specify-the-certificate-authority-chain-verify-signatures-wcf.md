---
title: HOW TO：指定用來驗證簽章的憑證授權單位憑證鏈結 (WCF)
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], specifying the certificate authority certificate chain
- certificates [WCF], verifying signatures
ms.assetid: 7c719355-aa41-4567-80d0-5115a8cf73fd
ms.openlocfilehash: 0a03902c9a0d36ebd6e2c38f4a827737cacec447
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96245028"
---
# <a name="how-to-specify-the-certificate-authority-certificate-chain-used-to-verify-signatures-wcf"></a><span data-ttu-id="2143b-102">HOW TO：指定用來驗證簽章的憑證授權單位憑證鏈結 (WCF)</span><span class="sxs-lookup"><span data-stu-id="2143b-102">How to: Specify the Certificate Authority Certificate Chain Used to Verify Signatures (WCF)</span></span>

<span data-ttu-id="2143b-103">當 Windows Communication Foundation (WCF) 接收使用 x.509 憑證簽署的 SOAP 訊息時，根據預設，它會確認 x.509 憑證是否由受信任的憑證授權單位單位所發出。</span><span class="sxs-lookup"><span data-stu-id="2143b-103">When Windows Communication Foundation (WCF) receives a SOAP message signed using an X.509 certificate, by default it verifies that the X.509 certificate was issued by a trusted certification authority.</span></span> <span data-ttu-id="2143b-104">它會搜尋憑證存放區並判斷該憑證授權單位的憑證是否已指定為受信任來完成所有程序。</span><span class="sxs-lookup"><span data-stu-id="2143b-104">This is done by looking in a certificate store and determining if the certificate for that certification authority has been designated as trusted.</span></span> <span data-ttu-id="2143b-105">為了讓 WCF 做出這項判斷，憑證授權單位單位憑證鏈必須安裝在正確的憑證存放區中。</span><span class="sxs-lookup"><span data-stu-id="2143b-105">In order for WCF to make this determination, the certification authority certificate chain must be installed in the correct certificate store.</span></span>  
  
### <a name="to-install-a-certification-authority-certificate-chain"></a><span data-ttu-id="2143b-106">若要安裝憑證授權單位憑證鏈結</span><span class="sxs-lookup"><span data-stu-id="2143b-106">To install a certification authority certificate chain</span></span>  
  
- <span data-ttu-id="2143b-107">針對 SOAP 訊息收件者想要信任所發出之 x.509 憑證的每個憑證授權單位單位，將憑證授權單位單位憑證鏈安裝到已設定為從中取出 x.509 憑證的憑證存放區中。</span><span class="sxs-lookup"><span data-stu-id="2143b-107">For each certification authority that a SOAP message recipient intends to trust X.509 certificates issued from, install the certification authority certificate chain into the certificate store that WCF is configured to retrieve X.509 certificates from.</span></span>  
  
     <span data-ttu-id="2143b-108">比方說，如果 SOAP 訊息收件者想要信任 Microsoft 發出的 x.509 憑證，則必須將 Microsoft 的憑證授權單位單位憑證鏈安裝在設定 WCF 的憑證存放區中，以尋找的 x.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="2143b-108">For instance, if a SOAP message recipient intends to trust X.509 certificates issued by Microsoft, the certification authority certificate chain for Microsoft must be installed in the certificate store that WCF is set up to look for X.509 certificates from.</span></span> <span data-ttu-id="2143b-109">WCF 尋找 x.509 憑證的憑證存放區可在程式碼或設定中指定。</span><span class="sxs-lookup"><span data-stu-id="2143b-109">The certificate store in which WCF looks for X.509 certificates can be specified in code or configuration.</span></span> <span data-ttu-id="2143b-110">例如，您可以在程式碼中使用 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> 方法或設定中的幾種方式來指定這項功能，包括 [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) 。</span><span class="sxs-lookup"><span data-stu-id="2143b-110">For example, this can be specified in code using the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> method or in configuration a few ways, including the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) .</span></span>  
  
     <span data-ttu-id="2143b-111">由於 Windows 在產品出貨時，預設會附上由受信任憑證授權單位所發行的憑證鏈結，您可能不需要針對所有憑證授權單位安裝其憑證鏈結。</span><span class="sxs-lookup"><span data-stu-id="2143b-111">Because Windows ships with a set of default certificate chains for trusted certificate authorities, it may not be necessary to install the certificate chain for all certificate authorities.</span></span>  
  
    1. <span data-ttu-id="2143b-112">匯出憑證授權單位憑證鏈結。</span><span class="sxs-lookup"><span data-stu-id="2143b-112">Export the certification authority certificate chain.</span></span>  
  
         <span data-ttu-id="2143b-113">每個憑證授權單位將有不同的執行方式。</span><span class="sxs-lookup"><span data-stu-id="2143b-113">Exactly how this is done depends on the certification authority.</span></span> <span data-ttu-id="2143b-114">如果憑證授權單位單位正在執行 Microsoft 憑證服務，請選取 [ **下載 ca 憑證、憑證鏈或 CRL**]，然後選擇 [ **下載 ca 憑證**]。</span><span class="sxs-lookup"><span data-stu-id="2143b-114">If the certification authority is running Microsoft Certificate Services, select **Download a CA certificate, certificate chain, or CRL**, and then choose **Download CA certificate**.</span></span>  
  
    2. <span data-ttu-id="2143b-115">匯入憑證授權單位憑證鏈結。</span><span class="sxs-lookup"><span data-stu-id="2143b-115">Import the certification authority certificate chain.</span></span>  
  
         <span data-ttu-id="2143b-116">在 Microsoft Management Console (MMC) 中，開啟 [憑證] 嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="2143b-116">In the Microsoft Management Console (MMC), open the Certificates snap-in.</span></span> <span data-ttu-id="2143b-117">針對已設定為從中取出 x.509 憑證的憑證存放區，請選取 [**信任的跟\*\*\*\*證書授權** 單位] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="2143b-117">For the certificate store that WCF is configured to retrieve X.509 certificates from, select the **Trusted Root** **Certification Authorities** folder.</span></span> <span data-ttu-id="2143b-118">在 [ **信任的根憑證授權** 單位] 資料夾底下，以滑鼠右鍵按一下 [ **憑證** ] 資料夾，指向 [ **所有** 工作]，然後按一下 [匯 **入**]。</span><span class="sxs-lookup"><span data-stu-id="2143b-118">Under the **Trusted Root Certification Authorities** folder, right-click the **Certificates** folder, point to **All Tasks**, and then click **Import**.</span></span> <span data-ttu-id="2143b-119">提供在步驟 a 中匯出的檔案。</span><span class="sxs-lookup"><span data-stu-id="2143b-119">Provide the file exported in step a.</span></span>  
  
         <span data-ttu-id="2143b-120">如需有關使用 [憑證] 嵌入式管理單元與 MMC 的詳細資訊，請參閱 [如何：使用 mmc 嵌入式管理單元來查看憑證](how-to-view-certificates-with-the-mmc-snap-in.md)。</span><span class="sxs-lookup"><span data-stu-id="2143b-120">For more information about using the Certificates snap-in with MMC, see [How to: View Certificates with the MMC Snap-in](how-to-view-certificates-with-the-mmc-snap-in.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2143b-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2143b-121">See also</span></span>

- [<span data-ttu-id="2143b-122">使用憑證</span><span class="sxs-lookup"><span data-stu-id="2143b-122">Working with Certificates</span></span>](working-with-certificates.md)
