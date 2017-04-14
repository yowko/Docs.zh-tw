---
title: "延伸保護原則 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e2616a10-317e-4c34-8023-0c015a80a82f
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# 延伸保護原則
延伸保護是防止攔截式攻擊的一項安全性方案。  MITM 攻擊是一項安全性威脅，其方式為 MITM 取得用戶端的認證並將它轉送至伺服器。  
  
## 示範  
 延伸保護  
  
## 討論  
 當應用程式使用 Kerberos、Digest 或 NTLM 透過 HTTPS 進行驗證時，首先會建立傳輸層安全性 \(TLS\) 通道，然後使用這個安全的通道進行驗證。  但是，SSL 所產生的工作階段金鑰與驗證期間產生的工作階段金鑰之間並無任何繫結。  任何 MITM 都可以在用戶端和伺服器之間自行建立，並且開始從用戶端轉送要求，甚至是在傳輸通道本身是安全的情況下進行，因為伺服器無從得知安全的通道是從用戶端或 MITM 所建立。  這個案例中的解決方法是將外部 TLS 通道與內部驗證通道加以繫結，讓伺服器能夠偵測是否有 MITM。  
  
> [!NOTE]
>  這個範例只有在裝載於 IIS 上時才能運作，無法在 Cassini \(Visual Studio 程式開發伺服器\) 上運作，因為 Cassini 不支援 HTTPS。  
  
> [!NOTE]
>  這項功能目前僅於 Windows 7 上提供。  以下為 Windows 7 專屬步驟。  
  
#### 若要安裝、建置及執行範例  
  
1.  從 \[**控制台**\]、\[**新增\/移除程式**\]、\[**Windows 功能**\] 安裝 \[Internet Information Services\]。  
  
2.  在 \[**Windows 功能**\]、\[**Internet Information Services**\]、\[**全球資訊網服務**\]、\[**安全性**\]、\[**Windows 驗證**\] 中安裝 \[**Windows 驗證**\]。  
  
3.  在 \[**Windows 功能**\]、\[**Microsoft .NET Framework 3.5.1**\]、\[**Windows Communication Foundation HTTP 啟動**\] 中安裝 \[**Windows Communication Foundation HTTP 啟動**\]。  
  
4.  這個範例需由用戶端建立與伺服器之間的安全通道，所以必須有可從 Internet Information Services \(IIS\) 管理員進行安裝的伺服器憑證。  
  
    1.  開啟 \[IIS 管理員\]。  開啟 \[**伺服器憑證**\]，它會在選取根節點 \(電腦名稱\) 時出現在 \[**功能檢視**\] 索引標籤中。  
  
    2.  若要測試這個範例，請建立自我簽署憑證。  如果您不希望 Internet Explorer 出現憑證可能不安全的提示，請將此憑證安裝到 \[受信任的根憑證授權單位\] 存放區。  
  
5.  開啟預設網站的 \[**執行**\] 窗格。  依序按一下 \[**編輯站台**\]、\[**繫結**\]。  加入 HTTPS 做為類型 \(如果尚未存在\)，並且使用連接埠號碼 443。  指派上一個步驟中建立的 SSL 憑證。  
  
6.  建置服務。  這樣會在 IIS 中建立一個虛擬目錄，並且視需要複製 Web 主控服務的 .dll、.svc 和 .config 檔案。  
  
7.  開啟 \[IIS 管理員\]。  以滑鼠右鍵按一下上一個步驟中建立的虛擬目錄 \(\[**ExtendedProtection**\]\)。  選取 \[**轉換成應用程式**\]。  
  
8.  開啟此虛擬目錄在 \[IIS 管理員\] 中的 \[**驗證**\] 模組，然後啟用 \[**Windows 驗證**\]。  
  
9. 在 \[**Windows 驗證**\] 下開啟此虛擬目錄的 \[**進階設定**\]，然後將它設定為 \[**必要**\]。  
  
10. 您可以從瀏覽器視窗存取 HTTPS URL 來測試服務 \(提供完整網域名稱\)。  如果您想要從遠端電腦存取此 URL，請確定防火牆已開放所有傳入的 HTTP 和 HTTPS 連線。  
  
11. 開啟用戶端組態檔，並且為用戶端提供完整網域名稱，或是取代 `<<full_machine_name>>` 的端點位址屬性。  
  
12. 執行該用戶端。  用戶端將與服務進行通訊，該服務會建立安全通道並且使用延伸保護。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。  請先檢查下列 \(預設\) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[用於 .NET Framework 4 的 Windows Communication Foundation \(WCF\) 與 Windows Workflow Foundation \(WF\) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。  此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Security\ExtendedProtection`