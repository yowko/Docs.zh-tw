---
title: HOW TO：指定用來驗證簽章的憑證授權單位憑證鏈結 (WCF)
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], specifying the certificate authority certificate chain
- certificates [WCF], verifying signatures
ms.assetid: 7c719355-aa41-4567-80d0-5115a8cf73fd
ms.openlocfilehash: 9e2ba9f3550442602cab217fec329e6c19efd3b3
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47080821"
---
# <a name="how-to-specify-the-certificate-authority-certificate-chain-used-to-verify-signatures-wcf"></a>HOW TO：指定用來驗證簽章的憑證授權單位憑證鏈結 (WCF)
當 Windows Communication Foundation (WCF) 收到透過 X.509 憑證簽署的 SOAP 訊息時，預設會確認 X.509 憑證已發行的受信任的憑證授權單位。 它會搜尋憑證存放區並判斷該憑證授權單位的憑證是否已指定為受信任來完成所有程序。 為了讓 WCF 來做出此判斷，憑證授權單位憑證鏈結必須安裝在正確的憑證存放區中。  
  
### <a name="to-install-a-certification-authority-certificate-chain"></a>若要安裝憑證授權單位憑證鏈結  
  
-   每個 SOAP 訊息收件者想要信任的憑證授權單位，從發行的 X.509 憑證會安裝憑證授權單位憑證鏈結，WCF 會設定為從其中擷取 X.509 憑證的憑證存放區。  
  
     比方說，如果 SOAP 訊息收件者想要信任由 Microsoft 所發行的 X.509 憑證，Microsoft 的憑證授權單位憑證鏈結必須安裝 WCF 設定搜尋從 X.509 憑證的憑證存放區。 WCF 尋找 X.509 憑證的憑證存放區可以在程式碼或組態中指定。 比方說，這可以指定在程式碼中使用<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A>方法或組態幾種方式，包括[ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) 。  
  
     由於 Windows 在產品出貨時，預設會附上由受信任憑證授權單位所發行的憑證鏈結，您可能不需要針對所有憑證授權單位安裝其憑證鏈結。  
  
    1.  匯出憑證授權單位憑證鏈結。  
  
         每個憑證授權單位將有不同的執行方式。 如果憑證授權單位執行 Microsoft 憑證服務，請選取**下載 CA 憑證、 憑證鏈結或 CRL**，然後選擇**下載 CA 憑證**。  
  
    2.  匯入憑證授權單位憑證鏈結。  
  
         在 Microsoft Management Console (MMC) 中，開啟 [憑證] 嵌入式管理單元。 憑證存放區擷取 X.509 憑證，選取設定該 WCF**受信任的根****憑證授權單位**資料夾。 底下**受信任的根憑證授權單位**資料夾中，以滑鼠右鍵按一下**憑證**資料夾，指向**所有工作**，然後按一下 **匯入**. 提供在步驟 a 中匯出的檔案。  
  
         如需使用 MMC 憑證嵌入式管理單元的詳細資訊，請參閱[如何： 使用 MMC 嵌入式管理單元檢視憑證](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)。  
  
## <a name="see-also"></a>另請參閱  
 [使用憑證](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
