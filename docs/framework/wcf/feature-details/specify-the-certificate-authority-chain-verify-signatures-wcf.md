---
title: HOW TO：指定用來驗證簽章的憑證授權單位憑證鏈結 (WCF)
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], specifying the certificate authority certificate chain
- certificates [WCF], verifying signatures
ms.assetid: 7c719355-aa41-4567-80d0-5115a8cf73fd
ms.openlocfilehash: 103d68d4ccb4cc243d28037260c1f9f380485ff6
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600305"
---
# <a name="how-to-specify-the-certificate-authority-certificate-chain-used-to-verify-signatures-wcf"></a>HOW TO：指定用來驗證簽章的憑證授權單位憑證鏈結 (WCF)
當 Windows Communication Foundation （WCF）收到使用 x.509 憑證簽署的 SOAP 訊息時，根據預設，它會確認 x.509 憑證是由信任的憑證授權單位單位所發行。 它會搜尋憑證存放區並判斷該憑證授權單位的憑證是否已指定為受信任來完成所有程序。 為了讓 WCF 能夠進行這項判斷，憑證授權單位單位憑證鏈必須安裝在正確的憑證存放區中。  
  
### <a name="to-install-a-certification-authority-certificate-chain"></a>若要安裝憑證授權單位憑證鏈結  
  
- 針對 SOAP 訊息收件者想要信任從發出的 x.509 憑證的每個憑證授權單位單位，將憑證授權單位單位憑證鏈安裝到 WCF 設定從其中抓取 x.509 憑證的憑證存放區。  
  
     例如，如果 SOAP 訊息收件者想要信任由 Microsoft 所發行的 x.509 憑證，則必須將 Microsoft 的憑證授權單位單位憑證鏈安裝在憑證存放區中，以供 WCF 設定來尋找中的 x.509 憑證。 WCF 尋找 x.509 憑證的憑證存放區可以在程式碼或設定中指定。 例如，您可以在程式碼中使用 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> 方法或在設定中以數種方式指定，包括 [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) 。  
  
     由於 Windows 在產品出貨時，預設會附上由受信任憑證授權單位所發行的憑證鏈結，您可能不需要針對所有憑證授權單位安裝其憑證鏈結。  
  
    1. 匯出憑證授權單位憑證鏈結。  
  
         每個憑證授權單位將有不同的執行方式。 如果憑證授權單位單位正在執行 Microsoft 憑證服務，請選取 [**下載 ca 憑證、憑證鏈或 CRL**]，然後選擇 [**下載 ca 憑證**]。  
  
    2. 匯入憑證授權單位憑證鏈結。  
  
         在 Microsoft Management Console (MMC) 中，開啟 [憑證] 嵌入式管理單元。 針對 WCF 設定為從中抓取 x.509 憑證的憑證存放區，請選取 [**信任的跟****證書授權**單位] 資料夾。 在 [**信任的根憑證授權**單位] 資料夾底下，以滑鼠右鍵按一下 [**憑證**] 資料夾，指向 [**所有**工作]，然後按一下 [匯**入**]。 提供在步驟 a 中匯出的檔案。  
  
         如需搭配 MMC 使用 [憑證] 嵌入式管理單元的詳細資訊，請參閱[如何：使用 mmc 嵌入式管理單元來查看憑證](how-to-view-certificates-with-the-mmc-snap-in.md)。  
  
## <a name="see-also"></a>請參閱

- [Working with Certificates](working-with-certificates.md)
