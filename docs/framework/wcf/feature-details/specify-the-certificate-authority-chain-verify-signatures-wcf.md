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
# <a name="how-to-specify-the-certificate-authority-certificate-chain-used-to-verify-signatures-wcf"></a>HOW TO：指定用來驗證簽章的憑證授權單位憑證鏈結 (WCF)

當 Windows Communication Foundation (WCF) 接收使用 x.509 憑證簽署的 SOAP 訊息時，根據預設，它會確認 x.509 憑證是否由受信任的憑證授權單位單位所發出。 它會搜尋憑證存放區並判斷該憑證授權單位的憑證是否已指定為受信任來完成所有程序。 為了讓 WCF 做出這項判斷，憑證授權單位單位憑證鏈必須安裝在正確的憑證存放區中。  
  
### <a name="to-install-a-certification-authority-certificate-chain"></a>若要安裝憑證授權單位憑證鏈結  
  
- 針對 SOAP 訊息收件者想要信任所發出之 x.509 憑證的每個憑證授權單位單位，將憑證授權單位單位憑證鏈安裝到已設定為從中取出 x.509 憑證的憑證存放區中。  
  
     比方說，如果 SOAP 訊息收件者想要信任 Microsoft 發出的 x.509 憑證，則必須將 Microsoft 的憑證授權單位單位憑證鏈安裝在設定 WCF 的憑證存放區中，以尋找的 x.509 憑證。 WCF 尋找 x.509 憑證的憑證存放區可在程式碼或設定中指定。 例如，您可以在程式碼中使用 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> 方法或設定中的幾種方式來指定這項功能，包括 [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) 。  
  
     由於 Windows 在產品出貨時，預設會附上由受信任憑證授權單位所發行的憑證鏈結，您可能不需要針對所有憑證授權單位安裝其憑證鏈結。  
  
    1. 匯出憑證授權單位憑證鏈結。  
  
         每個憑證授權單位將有不同的執行方式。 如果憑證授權單位單位正在執行 Microsoft 憑證服務，請選取 [ **下載 ca 憑證、憑證鏈或 CRL**]，然後選擇 [ **下載 ca 憑證**]。  
  
    2. 匯入憑證授權單位憑證鏈結。  
  
         在 Microsoft Management Console (MMC) 中，開啟 [憑證] 嵌入式管理單元。 針對已設定為從中取出 x.509 憑證的憑證存放區，請選取 [**信任的跟****證書授權** 單位] 資料夾。 在 [ **信任的根憑證授權** 單位] 資料夾底下，以滑鼠右鍵按一下 [ **憑證** ] 資料夾，指向 [ **所有** 工作]，然後按一下 [匯 **入**]。 提供在步驟 a 中匯出的檔案。  
  
         如需有關使用 [憑證] 嵌入式管理單元與 MMC 的詳細資訊，請參閱 [如何：使用 mmc 嵌入式管理單元來查看憑證](how-to-view-certificates-with-the-mmc-snap-in.md)。  
  
## <a name="see-also"></a>另請參閱

- [使用憑證](working-with-certificates.md)
