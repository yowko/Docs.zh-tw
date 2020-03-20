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
ms.openlocfilehash: 14f2242ab55795c74fa169382fef846bc0e60ace
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184901"
---
# <a name="how-to-make-x509-certificates-accessible-to-wcf"></a>HOW TO：讓 WCF 能夠存取 X.509 憑證
要使 X.509 憑證可供 Windows 通信基礎 （WCF） 訪問，應用程式代碼必須指定憑證存放區名稱和位置。 在某些狀況下，處理序身分識別必須能夠存取包含與 X.509 憑證相關聯之私密金鑰的檔案。 要獲取憑證存放區中與 X.509 憑證關聯的私密金鑰，WCF 必須具有執行此操作的許可權。 根據預設，只有擁有人和系統帳戶能夠存取憑證的私密金鑰。  
  
### <a name="to-make-x509-certificates-accessible-to-wcf"></a>讓 WCF 能夠存取 X.509 憑證  
  
1. 向 WCF 運行對包含與 X.509 憑證關聯的私密金鑰的檔的讀取存取許可權的帳戶。  
  
    1. 確定 WCF 是否需要對 X.509 憑證的私密金鑰進行讀取存取。  
  
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
  
    3. 使用[FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md)工具確定證書的私密金鑰位於電腦上的位置。  
  
         [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md)工具需要憑證存放區名稱、憑證存放區位置以及唯一標識證書的內容。 此工具會接受憑證的主體名稱或是其指紋來做為唯一識別項。 有關如何確定證書的指紋的詳細資訊，請參閱[如何：檢索證書的指紋](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)。  
  
         以下代碼示例使用[FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md)工具確定`My``CurrentUser`存儲中的證書的私密金鑰的位置，並帶有 的`46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`指紋。  
  
        ```console
        findprivatekey.exe My CurrentUser -t "46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d" -a  
        ```  
  
    4. 確定 WCF 正在運行的帳戶。  
  
         下表詳細介紹了為給定方案運行 WCF 的帳戶。  
  
        |狀況|處理序身分識別|  
        |--------------|----------------------|  
        |用戶端 (主控台或 WinForms 應用程式)。|目前登入的使用者。|  
        |自我裝載的服務。|目前登入的使用者。|  
        |託管在 IIS 6.0（Windows 伺服器 2003）或 IIS 7.0（Windows Vista）中的服務。|NETWORK SERVICE|  
        |在 IIS 5.X （Windows XP） 中託管的服務。|由 Machine.config 檔中的 `<processModel>` 項目控制。 預設帳戶是 ASPNET。|  
  
    5. 使用 icacls.exe 等工具授予對包含 WCF 運行帳戶的私密金鑰的檔的讀取存取許可權。  
  
         以下代碼示例編輯指定檔的可自由存取控制清單 （DACL）， 以授予網路服務帳戶對該檔的讀取 （：R） 存取權限。  
  
        ```console
        icacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /grant "NETWORK SERVICE":R  
        ```  
  
## <a name="see-also"></a>另請參閱

- [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md)
- [HOW TO：擷取憑證的指紋](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)
- [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
