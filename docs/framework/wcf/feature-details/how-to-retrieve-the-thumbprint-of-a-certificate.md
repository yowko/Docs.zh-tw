---
title: HOW TO：擷取憑證的指紋
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], retrieving thumbprint
ms.assetid: da3101aa-78cd-4c34-9652-d1f24777eeab
ms.openlocfilehash: f520e897ad467686e0dc151548a61ea8370eb07a
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/08/2018
ms.locfileid: "48873239"
---
# <a name="how-to-retrieve-the-thumbprint-of-a-certificate"></a><span data-ttu-id="af467-102">HOW TO：擷取憑證的指紋</span><span class="sxs-lookup"><span data-stu-id="af467-102">How to: Retrieve the Thumbprint of a Certificate</span></span>
<span data-ttu-id="af467-103">撰寫 Windows Communication Foundation (WCF) 應用程式所使用的 X.509 憑證進行驗證，時，通常必須指定在憑證中找到的宣告。</span><span class="sxs-lookup"><span data-stu-id="af467-103">When writing a Windows Communication Foundation (WCF) application that uses an X.509 certificate for authentication, it is often necessary to specify claims found in the certificate.</span></span> <span data-ttu-id="af467-104">例如，當您在 <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint> 方法中使用 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> 列舉時，就必須提供指紋宣告。</span><span class="sxs-lookup"><span data-stu-id="af467-104">For example, you must supply a thumbprint claim when using the <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint> enumeration in the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> method.</span></span> <span data-ttu-id="af467-105">尋找宣告值時，需要兩個步驟。</span><span class="sxs-lookup"><span data-stu-id="af467-105">Finding the claim value requires two steps.</span></span> <span data-ttu-id="af467-106">首先，開啟憑證的 Microsoft Management Console (MMC) 嵌入式管理單元</span><span class="sxs-lookup"><span data-stu-id="af467-106">First, open the Microsoft Management Console (MMC) snap-in for certificates.</span></span> <span data-ttu-id="af467-107">(請參閱 [如何：使用 MMC 嵌入式管理單元來檢視憑證](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md))。接著，如此處所描述，尋找適當的憑證並複製其指紋 (或其他宣告值)。</span><span class="sxs-lookup"><span data-stu-id="af467-107">(See [How to: View Certificates with the MMC Snap-in](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).) Second, as described here, find an appropriate certificate and copy its thumbprint (or other claim values).</span></span>  
  
 <span data-ttu-id="af467-108">如果您在服務驗證中使用憑證，則記下 [ **核發給** ] 欄位 (主控台中的第一欄) 之值是相當重要的。</span><span class="sxs-lookup"><span data-stu-id="af467-108">If you are using a certificate for service authentication, it is important to note the value of the **Issued To** column (the first column in the console).</span></span> <span data-ttu-id="af467-109">使用 Secure Sockets Layer (SSL) 做為傳輸安全性時，前幾項檢查其中完成的一項，就是比較服務之統一資源識別元 (URI) 的基底位址和 [ **核發給** ] 的值。</span><span class="sxs-lookup"><span data-stu-id="af467-109">When using Secure Sockets Layer (SSL) as a transport security, one of the first checks done is to compare the base address Uniform Resource Identifier (URI) of a service to the **Issued To** value.</span></span> <span data-ttu-id="af467-110">這些值必須相符，否則會中止驗證程序。</span><span class="sxs-lookup"><span data-stu-id="af467-110">The values must match or the authentication process is halted.</span></span>  
  
 <span data-ttu-id="af467-111">您也可以使用 Powershell 之 New-selfsignedcertificate cmdlet 來建立暫時憑證以用於只在開發期間。</span><span class="sxs-lookup"><span data-stu-id="af467-111">You can also use the Powershell New-SelfSignedCertificate cmdlet to create temporary certificates for use only during development.</span></span> <span data-ttu-id="af467-112">根據預設，不過，這類憑證不由憑證授權單位發行，並無法用於生產環境中使用。</span><span class="sxs-lookup"><span data-stu-id="af467-112">By default, however, such a certificate is not issued by a certification authority and is unusable for production purposes.</span></span> <span data-ttu-id="af467-113">如需詳細資訊，請參閱 <<c0> [ 如何： 建立開發期間使用的暫存憑證](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)。</span><span class="sxs-lookup"><span data-stu-id="af467-113">For more information, see [How to: Create Temporary Certificates for Use During Development](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md).</span></span>  
  
### <a name="to-retrieve-a-certificates-thumbprint"></a><span data-ttu-id="af467-114">若要擷取憑證的指紋</span><span class="sxs-lookup"><span data-stu-id="af467-114">To retrieve a certificate's thumbprint</span></span>  
  
1.  <span data-ttu-id="af467-115">開啟憑證的 Microsoft Management Console (MMC) 嵌入式管理單元</span><span class="sxs-lookup"><span data-stu-id="af467-115">Open the Microsoft Management Console (MMC) snap-in for certificates.</span></span> <span data-ttu-id="af467-116">(請參閱 [如何：使用 MMC 嵌入式管理單元來檢視憑證](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md))。</span><span class="sxs-lookup"><span data-stu-id="af467-116">(See [How to: View Certificates with the MMC Snap-in](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).)</span></span>  
  
2.  <span data-ttu-id="af467-117">在 [ **主控台根目錄** ] 視窗的左窗格中，按一下 [ **憑證 (本機電腦)**]。</span><span class="sxs-lookup"><span data-stu-id="af467-117">In the **Console Root** window's left pane, click **Certificates (Local Computer)**.</span></span>  
  
3.  <span data-ttu-id="af467-118">按一下 [ **個人** ] 資料夾以展開。</span><span class="sxs-lookup"><span data-stu-id="af467-118">Click the **Personal** folder to expand it.</span></span>  
  
4.  <span data-ttu-id="af467-119">按一下 [ **憑證** ] 資料夾以展開。</span><span class="sxs-lookup"><span data-stu-id="af467-119">Click the **Certificates** folder to expand it.</span></span>  
  
5.  <span data-ttu-id="af467-120">在憑證清單中，請記下 [ **使用目的** ] 的標題。</span><span class="sxs-lookup"><span data-stu-id="af467-120">In the list of certificates, note the **Intended Purposes** heading.</span></span> <span data-ttu-id="af467-121">尋找會將 [ **用戶端驗證** ] 列為使用目的之憑證。</span><span class="sxs-lookup"><span data-stu-id="af467-121">Find a certificate that lists **Client Authentication** as an intended purpose.</span></span>  
  
6.  <span data-ttu-id="af467-122">按兩下憑證。</span><span class="sxs-lookup"><span data-stu-id="af467-122">Double-click the certificate.</span></span>  
  
7.  <span data-ttu-id="af467-123">在 [ **憑證** ] 對話方塊中，按一下 [ **詳細資料** ] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="af467-123">In the **Certificate** dialog box, click the **Details** tab.</span></span>  
  
8.  <span data-ttu-id="af467-124">捲動欄位清單，並按一下 [ **指紋**]。</span><span class="sxs-lookup"><span data-stu-id="af467-124">Scroll through the list of fields and click **Thumbprint**.</span></span>  
  
9. <span data-ttu-id="af467-125">複製方塊中的十六進位字元。</span><span class="sxs-lookup"><span data-stu-id="af467-125">Copy the hexadecimal characters from the box.</span></span> <span data-ttu-id="af467-126">如果是針對 `X509FindType`在程式碼中使用此指紋，請移除十六進位數字之間的空格。</span><span class="sxs-lookup"><span data-stu-id="af467-126">If this thumbprint is used in code for the `X509FindType`, remove the spaces between the hexadecimal numbers.</span></span> <span data-ttu-id="af467-127">例如，在程式碼中應該將指紋 "a9 09 50 2d d8 2a e4 14 33 e6 f8 38 86 b0 0d 42 77 a3 2a 7b" 指定為 "a909502dd82ae41433e6f83886b00d4277a32a7b"。</span><span class="sxs-lookup"><span data-stu-id="af467-127">For example, the thumbprint "a9 09 50 2d d8 2a e4 14 33 e6 f8 38 86 b0 0d 42 77 a3 2a 7b" should be specified as "a909502dd82ae41433e6f83886b00d4277a32a7b" in code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af467-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="af467-128">See Also</span></span>  
 <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint>  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A>  
 [<span data-ttu-id="af467-129">如何：使用 SSL 憑證設定連接埠</span><span class="sxs-lookup"><span data-stu-id="af467-129">How to: Configure a Port with an SSL Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)  
 [<span data-ttu-id="af467-130">如何：使用 MMC 嵌入式管理單元來檢視憑證</span><span class="sxs-lookup"><span data-stu-id="af467-130">How to: View Certificates with the MMC Snap-in</span></span>](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)  
 [<span data-ttu-id="af467-131">如何：建立開發時要使用的暫時憑證</span><span class="sxs-lookup"><span data-stu-id="af467-131">How to: Create Temporary Certificates for Use During Development</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
