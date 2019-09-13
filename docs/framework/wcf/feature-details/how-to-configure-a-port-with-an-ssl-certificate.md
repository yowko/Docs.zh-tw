---
title: HOW TO：使用 SSL 憑證設定連接埠
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SSL
- WCF, security mode
- WCF, security
ms.assetid: b8abcc8e-a5f5-4317-aca5-01e3c40ab24d
ms.openlocfilehash: 6e21311802b0a3ce4e415b14686b101d31f18035
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2019
ms.locfileid: "70893308"
---
# <a name="how-to-configure-a-port-with-an-ssl-certificate"></a>作法：使用 SSL 憑證設定連接埠
使用傳輸安全性的<xref:System.ServiceModel.WSHttpBinding>類別建立自我裝載的 Windows Communication Foundation （WCF）服務時，您也必須使用 x.509 憑證設定埠。 如果您沒有建立自我裝載的服務，可以將您的服務裝載在 Internet Information Services (IIS) 上。 如需詳細資訊，請參閱[HTTP 傳輸安全性](../../../../docs/framework/wcf/feature-details/http-transport-security.md)。  
  
 若要設定連接埠，使用的工具取決於電腦上執行的作業系統。  
  
 如果您是執行 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] 或 [!INCLUDE[wxp](../../../../includes/wxp-md.md)]，請使用 HttpCfg.exe 工具。 這個工具會隨 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] 進行安裝。 有[!INCLUDE[wxp](../../../../includes/wxp-md.md)]了，您可以在[Windows XP Service Pack 2 支援工具](https://go.microsoft.com/fwlink/?LinkId=88606)下載此工具。 如需詳細資訊，請參閱[Httpcfg.exe 總覽](https://go.microsoft.com/fwlink/?LinkId=88605)。 [Windows 支援工具檔](https://go.microsoft.com/fwlink/?LinkId=94840)會說明 HTTPcfg.exe 工具的語法。  
  
 如果您是執行 [!INCLUDE[wv](../../../../includes/wv-md.md)]，可以使用已安裝的 Netsh.exe 工具。  
  
 本主題說明如何完成下列數個程序：  
  
- 判斷電腦目前的連接埠組態。  
  
- 取得憑證的指紋 (如此才能完成下列兩個程序)。  
  
- 將 SSL 憑證繫結至連接埠組態。  
  
- 將 SSL 憑證繫結至連接埠組態並支援用戶端憑證。  
  
- 從連接埠號碼刪除 SSL 憑證。  
  
 請注意，您必須具備系統管理員權限，才能修改儲存在電腦上的憑證。  
  
### <a name="to-determine-how-ports-are-configured"></a>決定如何設定連接埠  
  
1. 在[!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]或[!INCLUDE[wxp](../../../../includes/wxp-md.md)]中，使用 HTTPcfg.exe 工具來查看目前的埠設定，使用**查詢**和**ssl**參數，如下列範例所示。  
  
    ```console
    httpcfg query ssl  
    ```  
  
2. 在 [!INCLUDE[wv](../../../../includes/wv-md.md)] 中，使用 Netsh.exe 工具來檢視目前的連接埠組態，如下列範例所示。  
  
    ```console  
    netsh http show sslcert  
    ```  
  
### <a name="to-get-a-certificates-thumbprint"></a>若要取得憑證的指紋  
  
1. 使用憑證 MMC 嵌入式管理單元，尋找目的為用戶端驗證的 X.509 憑證。 如需詳細資訊，請參閱[如何：使用 MMC 嵌入式管理](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)單元來查看憑證。  
  
2. 存取憑證的指紋。 如需詳細資訊，請參閱[如何：取得憑證](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)的指紋。  
  
3. 將憑證的指紋複製到文字編輯器中，例如「記事本」。  
  
4. 移除十六進位字元之間的所有空格。 完成這項工作的方法之一是使用文字編輯器的尋找與取代功能，並使用 null 字元來取代各個空格。  
  
### <a name="to-bind-an-ssl-certificate-to-a-port-number"></a>繫結 SSL 憑證與連接埠號碼  
  
1. 在 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] 或 [!INCLUDE[wxp](../../../../includes/wxp-md.md)] 中，在 Secure Sockets Layer (SSL) 存放區上的 "set" 模式中使用 HttpCfg.exe 工具，將憑證繫結至連接埠號碼。 此工具是使用指紋來識別憑證，如下列範例所示。  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
    - **-I**參數具有`IP`：`port`的語法，並指示工具將憑證設定為電腦的埠8012。 或者，號碼前面的四個零也可以使用電腦的實際 IP 位址來取代。  
  
    - **-H**參數會指定憑證的指紋。  
  
2. 在 [!INCLUDE[wv](../../../../includes/wv-md.md)] 中，使用 Netsh.exe 工具，如下列範例所示：  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF}   
    ```  
  
    - **Certhash**參數會指定憑證的指紋。  
  
    - **Ipport**參數會指定 IP 位址和埠，而函式就如同所述的 HTTPcfg.exe .exe 工具的 **-i**參數。  
  
    - **Appid**參數是可以用來識別擁有應用程式的 GUID。  
  
### <a name="to-bind-an-ssl-certificate-to-a-port-number-and-support-client-certificates"></a>繫結 SSL 憑證與連接埠號碼並支援用戶端憑證  
  
1. 在 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] 或 [!INCLUDE[wxp](../../../../includes/wxp-md.md)] 中，若要支援在傳輸層使用 X.509 憑證驗證的用戶端，請依照前述程序執行，但將額外的命令列參數傳遞至 HttpCfg.exe，如下列範例所示。  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6 -f 2  
    ```  
  
     **-F**參數具有的語法`n` ，其中 n 是介於1和7之間的數位。 值為 2 (如上一個範例所示) 會在傳輸層啟用用戶端憑證。 值為 3 會啟用用戶端憑證，並將這些憑證對應至 Windows 帳戶。 如需其他值的行為，請參閱 HttpCfg.exe 說明。  
  
2. 在 [!INCLUDE[wv](../../../../includes/wv-md.md)] 中，若要支援在傳輸層使用 X.509 憑證驗證的用戶端，請依照前述程序執行，但是要加上額外的參數，如下列範例所示。  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF} clientcertnegotiation=enable  
    ```  
  
### <a name="to-delete-an-ssl-certificate-from-a-port-number"></a>從連接埠號碼刪除 SSL 憑證  
  
1. 使用 HttpCfg.exe 或 Netsh.exe 工具來查看電腦上所有繫結的連接埠和指紋。 若要將資訊列印到磁片，請使用重新導向字元 ">"，如下列範例所示。  
  
    ```console  
    httpcfg query ssl>myMachinePorts.txt  
    ```
  
2. 在[!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]或[!INCLUDE[wxp](../../../../includes/wxp-md.md)]中，使用 HTTPcfg.exe 工具搭配**delete**和**ssl**關鍵字。 使用 **-i**參數指定`IP`：`port`號碼，並使用 **-h**參數指定指紋。  
  
    ```console  
    httpcfg delete ssl -i 0.0.0.0:8005 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
3. 在 [!INCLUDE[wv](../../../../includes/wv-md.md)] 中，使用 Netsh.exe 工具，如下列範例所示：  
  
    ```console  
    Netsh http delete sslcert ipport=0.0.0.0:8005  
    ```  
  
## <a name="example"></a>範例  
 下列程式碼將示範如何使用設定為傳輸安全性的 <xref:System.ServiceModel.WSHttpBinding> 類別來建立自我裝載的服務。 當建立應用程式時，請在位址中指定連接埠號碼。  
  
 [!code-csharp[c_WsHttpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#3)]
 [!code-vb[c_WsHttpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#3)]  
  
## <a name="see-also"></a>另請參閱

- [HTTP 傳輸安全性](../../../../docs/framework/wcf/feature-details/http-transport-security.md)
