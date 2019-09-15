---
title: HOW TO：讓 WCF 能夠存取 X.509 憑證
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- X.509 certificates [WCF]
- certificates [WCF], making X.509 certificates accessible to WCF
- X.509 certificates [WCF], making accessible to WCF
ms.assetid: a54e407c-c2b5-4319-a648-60e43413664b
ms.openlocfilehash: 401371bf01a62a20f2834cb76df19d9ddaacf83d
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972359"
---
# <a name="how-to-make-x509-certificates-accessible-to-wcf"></a>HOW TO：讓 WCF 能夠存取 X.509 憑證
若要讓 Windows Communication Foundation （WCF）可以存取 x.509 憑證，應用程式代碼必須指定憑證存放區名稱和位置。 在某些狀況下，處理序身分識別必須能夠存取包含與 X.509 憑證相關聯之私密金鑰的檔案。 若要取得與憑證存放區中的 x.509 憑證相關聯的私密金鑰，WCF 必須擁有執行這項操作的許可權。 根據預設，只有擁有人和系統帳戶能夠存取憑證的私密金鑰。  
  
### <a name="to-make-x509-certificates-accessible-to-wcf"></a>讓 WCF 能夠存取 X.509 憑證  
  
1. 授與執行 WCF 所用的帳戶，其中包含與 x.509 憑證相關聯的私密金鑰之檔案的讀取權限。  
  
    1. 判斷 WCF 是否需要 x.509 憑證之私密金鑰的讀取權限。  
  
         下表詳細列出在使用 X.509 憑證時是否必須要提供私密金鑰。  
  
        |X.509 憑證使用方式|私密金鑰|  
        |---------------------------|-----------------|  
        |數位簽署傳出的 SOAP 訊息。|是|  
        |確認傳入之 SOAP 訊息的簽章。|否|  
        |加密傳出的 SOAP 訊息。|否|  
        |解密傳入的 SOAP 訊息。|是|  
  
    2. 判斷憑證存放於其中的憑證存放區位置和名稱。  
  
         憑證存放於其中的憑證存放區會指定於應用程式程式碼或組態中。 例如，下列範例會指定憑證是位於名為 `CurrentUser` 的 `My` 憑證存放區中。  
  
         [!code-csharp[x509Accessible#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/x509accessible/cs/source.cs#1)]
         [!code-vb[x509Accessible#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/x509accessible/vb/source.vb#1)]  
  
    3. 使用[FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md)工具，判斷憑證的私密金鑰位於電腦上的哪個位置。  
  
         [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md)工具需要憑證存放區名稱、憑證存放區位置，以及可唯一識別憑證的內容。 此工具會接受憑證的主體名稱或是其指紋來做為唯一識別項。 如需如何判斷憑證指紋的詳細資訊，請參閱[如何：取得憑證](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)的指紋。  
  
         下列程式碼範例會使用[FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md)工具，以的指紋`My` `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`，判斷存放區中`CurrentUser`之憑證的私密金鑰位置。  
  
        ```console
        findprivatekey.exe My CurrentUser -t "46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d" -a  
        ```  
  
    4. 判斷正在執行 WCF 的帳戶。  
  
         下表詳細說明針對指定案例執行 WCF 所使用的帳戶。  
  
        |狀況|處理序身分識別|  
        |--------------|----------------------|  
        |用戶端 (主控台或 WinForms 應用程式)。|目前登入的使用者。|  
        |自我裝載的服務。|目前登入的使用者。|  
        |裝載於 IIS 6.0 ([!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]) 或 IIS 7.0 ([!INCLUDE[wv](../../../../includes/wv-md.md)]) 中的服務。|網路服務|  
        |裝載於 IIS 5.X ([!INCLUDE[wxp](../../../../includes/wxp-md.md)]) 中的服務。|由 Machine.config 檔中的 `<processModel>` 項目控制。 預設帳戶是 ASPNET。|  
  
    5. 使用像是 icacls 的工具，將包含私密金鑰之檔案的讀取權限授與執行 WCF 的帳戶。  
  
         下列程式碼範例會編輯指定檔案的任意存取控制清單（DACL），以將檔案的讀取（： R）存取權授與網路服務帳戶。  
  
        ```console 
        icacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /grant "NETWORK SERVICE":R  
        ```  
  
## <a name="see-also"></a>另請參閱

- [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md)
- [如何：取得憑證的指紋](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)
- [使用憑證](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
