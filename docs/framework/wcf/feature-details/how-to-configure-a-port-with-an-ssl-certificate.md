---
title: "HOW TO：使用 SSL 憑證設定連接埠 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SSL"
  - "WCF, 安全性"
  - "WCF, 安全性模式"
ms.assetid: b8abcc8e-a5f5-4317-aca5-01e3c40ab24d
caps.latest.revision: 18
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 18
---
# HOW TO：使用 SSL 憑證設定連接埠
當以使用傳輸安全性的 <xref:System.ServiceModel.WSHttpBinding> 類別建立自我裝載的 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務時，也必須使用 X.509 憑證設定連接埠。  如果您沒有建立自我裝載的服務，可以將您的服務裝載在 Internet Information Services \(IIS\) 上。  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [HTTP 傳輸安全性](../../../../docs/framework/wcf/feature-details/http-transport-security.md).  
  
 若要設定連接埠，使用的工具取決於電腦上執行的作業系統。  
  
 如果您是執行 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] 或 [!INCLUDE[wxp](../../../../includes/wxp-md.md)]，請使用 HttpCfg.exe 工具。  這個工具會隨 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] 進行安裝。  如果您是使用 [!INCLUDE[wxp](../../../../includes/wxp-md.md)]，可以在 [Windows XP Service Pack 2 支援工具](http://go.microsoft.com/fwlink/?LinkId=88606)下載此工具。  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Httpcfg 概觀](http://go.microsoft.com/fwlink/?LinkId=88605)。  [Windows 支援工具文件](http://go.microsoft.com/fwlink/?LinkId=94840)會說明 Httpcfg.exe 工具的語法。  
  
 如果您是執行 [!INCLUDE[wv](../../../../includes/wv-md.md)]，可以使用已安裝的 Netsh.exe 工具。  
  
 本主題說明如何完成下列數個程序：  
  
-   判斷電腦目前的連接埠組態。  
  
-   取得憑證的指紋 \(如此才能完成下列兩個程序\)。  
  
-   將 SSL 憑證繫結至連接埠組態。  
  
-   將 SSL 憑證繫結至連接埠組態並支援用戶端憑證。  
  
-   從連接埠號碼刪除 SSL 憑證。  
  
 請注意，您必須具備系統管理員權限，才能修改儲存在電腦上的憑證。  
  
### 決定如何設定連接埠  
  
1.  在 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] 或 [!INCLUDE[wxp](../../../../includes/wxp-md.md)] 中，使用 HttpCfg.exe 工具檢視目前的連接埠組態，如下列範例所示使用 **query** 和 **ssl** 參數。  
  
    ```  
    httpcfg query ssl  
    ```  
  
2.  在 [!INCLUDE[wv](../../../../includes/wv-md.md)] 中，使用 Netsh.exe 工具來檢視目前的連接埠組態，如下列範例所示。  
  
    ```  
    netsh http show sslcert  
    ```  
  
### 若要取得憑證的指紋  
  
1.  使用憑證 MMC 嵌入式管理單元，尋找目的為用戶端驗證的 X.509 憑證。  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [HOW TO：使用 MMC 嵌入式管理單元來檢視憑證](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).  
  
2.  存取憑證的指紋。  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [HOW TO：擷取憑證的指紋](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).  
  
3.  將憑證的指紋複製到文字編輯器中，例如「記事本」。  
  
4.  移除十六進位字元之間的所有空格。  完成這項工作的方法之一是使用文字編輯器的尋找與取代功能，並使用 null 字元來取代各個空格。  
  
### 繫結 SSL 憑證與連接埠號碼  
  
1.  在 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] 或 [!INCLUDE[wxp](../../../../includes/wxp-md.md)] 中，在 Secure Sockets Layer \(SSL\) 存放區上的 "set" 模式中使用 HttpCfg.exe 工具，將憑證繫結至連接埠號碼。  此工具是使用指紋來識別憑證，如下列範例所示。  
  
    ```  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
    -   **\-i** 參數具有 `IP`：`port` 的語法，並指示工具將憑證設定為電腦的連接埠 8012。  或者，號碼前面的四個零也可以使用電腦的實際 IP 位址來取代。  
  
    -   **\-h**  參數會指定憑證的指紋。  
  
2.  在 [!INCLUDE[wv](../../../../includes/wv-md.md)] 中，使用 Netsh.exe 工具，如下列範例所示：  
  
    ```  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF}   
    ```  
  
    -   **certhash** 參數會指定憑證的指紋。  
  
    -   **ipport** 參數 \(Parameter\) 會指定 IP 位址和連接埠，作用就和上述 Httpcfg.exe 工具的 **\-i** 參數 \(Switch\) 一樣。  
  
    -   **appid** 參數是用來識別擁有端應用程式的 GUID。  
  
### 繫結 SSL 憑證與連接埠號碼並支援用戶端憑證  
  
1.  在 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] 或 [!INCLUDE[wxp](../../../../includes/wxp-md.md)] 中，若要支援在傳輸層使用 X.509 憑證驗證的用戶端，請依照前述程序執行，但將額外的命令列參數傳遞至 HttpCfg.exe，如下列範例所示。  
  
    ```  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6 -f 2  
    ```  
  
     **\-f** 參數具有 `n` 的語法，其中 n 是介於 1 和 7 之間的數字。  值為 2 \(如上一個範例所示\) 會在傳輸層啟用用戶端憑證。  值為 3 會啟用用戶端憑證，並將這些憑證對應至 Windows 帳戶。  如需其他值的行為，請參閱 HttpCfg.exe 說明。  
  
2.  在 [!INCLUDE[wv](../../../../includes/wv-md.md)] 中，若要支援在傳輸層使用 X.509 憑證驗證的用戶端，請依照前述程序執行，但是要加上額外的參數，如下列範例所示。  
  
    ```  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF} clientcertnegotiation=enable  
    ```  
  
### 從連接埠號碼刪除 SSL 憑證  
  
1.  使用 HttpCfg.exe 或 Netsh.exe 工具來查看電腦上所有繫結的連接埠和指紋。  若要將資訊列印至磁碟，請使用重新導向字元 "\>"，如下列範例所示。  
  
    ```  
    httpcfg query ssl>myMachinePorts.txt  
    ```  
  
2.  在 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] 或 [!INCLUDE[wxp](../../../../includes/wxp-md.md)] 中，使用 HttpCfg.exe 工具搭配 **delete** 和 **ssl** 關鍵字。  使用 **\-i** 參數來指定 `IP`：`port` 號碼，並使用 **\-h** 參數來指定指紋。  
  
    ```  
    httpcfg delete ssl -i 0.0.0.0:8005 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
3.  在 [!INCLUDE[wv](../../../../includes/wv-md.md)] 中，使用 Netsh.exe 工具，如下列範例所示：  
  
    ```  
    Netsh http delete sslcert ipport=0.0.0.0:8005  
    ```  
  
## 範例  
 下列程式碼將示範如何使用設定為傳輸安全性的 <xref:System.ServiceModel.WSHttpBinding> 類別來建立自我裝載的服務。  當建立應用程式時，請在位址中指定連接埠號碼。  
  
 [!code-csharp[c_WsHttpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#3)]
 [!code-vb[c_WsHttpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#3)]  
  
## 請參閱  
 [HTTP 傳輸安全性](../../../../docs/framework/wcf/feature-details/http-transport-security.md)