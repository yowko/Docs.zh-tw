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
ms.openlocfilehash: 90d5424e12bb770dc3da85e1b2738206f4777c0c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185100"
---
# <a name="how-to-configure-a-port-with-an-ssl-certificate"></a>HOW TO：使用 SSL 憑證設定連接埠

使用使用傳輸安全性<xref:System.ServiceModel.WSHttpBinding>的類創建自託管的 Windows 通信基礎 （WCF） 服務時，還必須配置具有 X.509 憑證的埠。 如果您沒有建立自我裝載的服務，可以將您的服務裝載在 Internet Information Services (IIS) 上。 有關詳細資訊，請參閱[HTTP 傳輸安全](../../../../docs/framework/wcf/feature-details/http-transport-security.md)。  
  
 若要設定連接埠，使用的工具取決於電腦上執行的作業系統。  
  
 如果您正在運行 Windows Server 2003，請使用 HttpCfg.exe 工具。 在 Windows 伺服器 2003 上，將安裝此工具。 有關詳細資訊，請參閱[Httpcfg 概述](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc787508(v=ws.10))。 [Windows 支援工具文檔](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc781601(v=ws.10))解釋了 Httpcfg.exe 工具的語法。  
  
 如果您正在運行 Windows Vista，請使用已安裝的 Netsh.exe 工具。
  
> [!NOTE]
> 修改存儲在電腦上的證書需要管理許可權。  
  
## <a name="determine-how-ports-are-configured"></a>確定埠的配置方式  
  
1. 在 Windows 伺服器 2003 或 Windows XP 中，使用 HttpCfg.exe 工具使用**查詢**和**ssl**開關查看當前埠配置，如以下示例所示。  
  
    ```console
    httpcfg query ssl  
    ```  
  
2. 在 Windows Vista 中，使用 Netsh.exe 工具查看當前埠配置，如以下示例所示。  
  
    ```console  
    netsh http show sslcert  
    ```  
  
## <a name="get-a-certificates-thumbprint"></a>獲取證書的指紋  
  
1. 使用憑證 MMC 嵌入式管理單元，尋找目的為用戶端驗證的 X.509 憑證。 如需詳細資訊，請參閱 [做法：使用 MMC 嵌入式管理單元檢視憑證](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)。  
  
2. 存取憑證的指紋。 如需詳細資訊，請參閱[做法：擷取憑證的指紋](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)。  
  
3. 將憑證的指紋複製到文字編輯器中，例如「記事本」。  
  
4. 移除十六進位字元之間的所有空格。 完成這項工作的方法之一是使用文字編輯器的尋找與取代功能，並使用 null 字元來取代各個空格。  
  
## <a name="bind-an-ssl-certificate-to-a-port-number"></a>將 SSL 憑證綁定到埠號  
  
1. 在 Windows 伺服器 2003 或 Windows XP 中，在安全通訊端層 （SSL） 存儲的"設置"模式下使用 HttpCfg.exe 工具將證書綁定到埠號。 此工具是使用指紋來識別憑證，如下列範例所示。  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
    - **-i**開關的語法為`IP`：`port`並指示工具將證書設置為電腦的埠 8012。 或者，號碼前面的四個零也可以使用電腦的實際 IP 位址來取代。  
  
    - **-h**開關指定證書的指紋。  
  
2. 在 Windows Vista 中，請使用 Netsh.exe 工具，如以下示例所示。  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF}
    ```  
  
    - **證書**參數指定證書的指紋。  
  
    - **ipport**參數指定 IP 位址和埠，其功能與描述的 Httpcfg.exe 工具的 **-i**開關類似。  
  
    - **appid**參數是一個 GUID，可用於標識所屬應用程式。  
  
## <a name="bind-an-ssl-certificate-to-a-port-number-and-support-client-certificates"></a>將 SSL 憑證綁定到埠號並支援用戶端憑證  
  
1. 在 Windows Server 2003 或 Windows XP 中，為了支援在傳輸層使用 X.509 憑證進行身份驗證的用戶端，請按照上述過程操作，但將附加命令列參數傳遞給 HttpCfg.exe，如以下示例所示。  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6 -f 2  
    ```  
  
     **-f**開關的語法`n`是 n 是介於 1 和 7 之間的數位。 值為 2 (如上一個範例所示) 會在傳輸層啟用用戶端憑證。 值為 3 會啟用用戶端憑證，並將這些憑證對應至 Windows 帳戶。 如需其他值的行為，請參閱 HttpCfg.exe 說明。  
  
2. 在 Windows Vista 中，為了支援在傳輸層使用 X.509 憑證進行身份驗證的用戶端，請遵循前面的過程，但使用附加參數，如以下示例所示。  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF} clientcertnegotiation=enable  
    ```  
  
## <a name="delete-an-ssl-certificate-from-a-port-number"></a>從埠號中刪除 SSL 憑證  
  
1. 使用 HttpCfg.exe 或 Netsh.exe 工具來查看電腦上所有繫結的連接埠和指紋。 要將資訊列印到磁片，請使用重定向字元">"，如以下示例所示。  
  
    ```console  
    httpcfg query ssl>myMachinePorts.txt  
    ```
  
2. 在 Windows 伺服器 2003 或 Windows XP 中，使用 HttpCfg.exe 工具**刪除和****ssl**關鍵字。 使用 **-i**開關指定`IP`：`port`編號和 **-h**開關來指定指紋。  
  
    ```console  
    httpcfg delete ssl -i 0.0.0.0:8005 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
3. 在 Windows Vista 中，請使用 Netsh.exe 工具，如以下示例所示。  
  
    ```console  
    Netsh http delete sslcert ipport=0.0.0.0:8005  
    ```  
  
## <a name="example"></a>範例  

 下列程式碼將示範如何使用設定為傳輸安全性的 <xref:System.ServiceModel.WSHttpBinding> 類別來建立自我裝載的服務。 當建立應用程式時，請在位址中指定連接埠號碼。  
  
 [!code-csharp[c_WsHttpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#3)]
 [!code-vb[c_WsHttpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#3)]  
  
## <a name="see-also"></a>另請參閱

- [HTTP 傳輸安全性](../../../../docs/framework/wcf/feature-details/http-transport-security.md)
