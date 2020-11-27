---
title: 作法：讓 WCF 能夠存取 X.509 憑證
description: 瞭解如何讓 WCF 可以存取 x.509 憑證。 應用程式程式碼必須指定憑證存放區名稱和位置。 可能有其他需求。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- X.509 certificates [WCF]
- certificates [WCF], making X.509 certificates accessible to WCF
- X.509 certificates [WCF], making accessible to WCF
ms.assetid: a54e407c-c2b5-4319-a648-60e43413664b
ms.openlocfilehash: 06a6167f0ad352955eb6b764ef8bfdb1394f4ed9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96279736"
---
# <a name="how-to-make-x509-certificates-accessible-to-wcf"></a>作法：讓 WCF 能夠存取 X.509 憑證

若要讓 Windows Communication Foundation (WCF) 可以存取 x.509 憑證，應用程式程式碼必須指定憑證存放區名稱和位置。 在某些狀況下，處理序身分識別必須能夠存取包含與 X.509 憑證相關聯之私密金鑰的檔案。 若要取得與憑證存放區中的 x.509 憑證相關聯的私密金鑰，WCF 必須有許可權才能完成這項作業。 根據預設，只有擁有人和系統帳戶能夠存取憑證的私密金鑰。  
  
### <a name="to-make-x509-certificates-accessible-to-wcf"></a>讓 WCF 能夠存取 X.509 憑證  
  
1. 提供執行 WCF 的帳戶讀取權限，該檔案包含與 x.509 憑證相關聯的私密金鑰。  
  
    1. 判斷 WCF 是否需要 x.509 憑證之私密金鑰的讀取權限。  
  
         下表詳細列出在使用 X.509 憑證時是否必須要提供私密金鑰。  
  
        |X.509 憑證使用方式|私密金鑰|  
        |---------------------------|-----------------|  
        |數位簽署傳出的 SOAP 訊息。|Yes|  
        |確認傳入之 SOAP 訊息的簽章。|No|  
        |加密傳出的 SOAP 訊息。|No|  
        |解密傳入的 SOAP 訊息。|Yes|  
  
    2. 判斷憑證存放於其中的憑證存放區位置和名稱。  
  
         憑證存放於其中的憑證存放區會指定於應用程式程式碼或組態中。 例如，下列範例會指定憑證是位於名為 `CurrentUser` 的 `My` 憑證存放區中。  
  
         [!code-csharp[x509Accessible#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/x509accessible/cs/source.cs#1)]
         [!code-vb[x509Accessible#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/x509accessible/vb/source.vb#1)]  
  
    3. 使用 [FindPrivateKey](../samples/findprivatekey.md) 工具，判斷憑證的私密金鑰在電腦上的位置。  
  
         [FindPrivateKey](../samples/findprivatekey.md)工具需要憑證存放區名稱、憑證存放區位置，以及可唯一識別憑證的內容。 此工具會接受憑證的主體名稱或是其指紋來做為唯一識別項。 如需如何判斷憑證指紋的詳細資訊，請參閱 [如何：取出憑證的指紋](how-to-retrieve-the-thumbprint-of-a-certificate.md)。  
  
         下列程式碼範例會使用 [FindPrivateKey](../samples/findprivatekey.md) 工具來判斷儲存區中憑證之私密金鑰的位置，其 `My` `CurrentUser` 指紋為 `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d` 。  
  
        ```console
        findprivatekey.exe My CurrentUser -t "46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d" -a  
        ```  
  
    4. 判斷正在執行 WCF 的帳戶。  
  
         下表詳細說明 WCF 針對指定案例執行時所使用的帳戶。  
  
        |案例|處理序身分識別|  
        |--------------|----------------------|  
        |用戶端 (主控台或 WinForms 應用程式)。|目前登入的使用者。|  
        |自我裝載的服務。|目前登入的使用者。|  
        |裝載于 IIS 6.0 (Windows Server 2003) 或 IIS 7.0 (Windows Vista) 的服務。|NETWORK SERVICE|  
        |裝載于 IIS 5.x (Windows XP) 的服務。|由 Machine.config 檔中的 `<processModel>` 項目控制。 預設帳戶是 ASPNET。|  
  
    5. 使用 icacls.exe 之類的工具，將包含私密金鑰之私密金鑰的讀取權限授與執行 WCF 的帳戶。  
  
         下列程式碼範例會編輯指定檔案 (DACL) 的任意存取控制清單，以授與網路服務帳戶 read (： R) 存取檔案。  
  
        ```console
        icacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /grant "NETWORK SERVICE":R  
        ```  
  
## <a name="see-also"></a>另請參閱

- [FindPrivateKey](../samples/findprivatekey.md)
- [作法：擷取憑證的指紋](how-to-retrieve-the-thumbprint-of-a-certificate.md)
- [使用憑證](working-with-certificates.md)
