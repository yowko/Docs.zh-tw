---
title: 延伸保護原則
ms.date: 03/30/2017
ms.assetid: e2616a10-317e-4c34-8023-0c015a80a82f
ms.openlocfilehash: 00d1500b271625addde4499bc62b5ed4d689caf9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33504354"
---
# <a name="extended-protection-policy"></a>延伸保護原則
延伸保護是防止攔截式攻擊的一項安全性方案。 MITM 攻擊是一項安全性威脅，其方式為 MITM 取得用戶端的認證並將它轉送至伺服器。  
  
## <a name="demonstrates"></a>示範  
 延伸保護  
  
## <a name="discussion"></a>討論  
 當應用程式使用 Kerberos、Digest 或 NTLM 透過 HTTPS 進行驗證時，首先會建立傳輸層安全性 (TLS) 通道，然後使用這個安全的通道進行驗證。 但是，SSL 所產生的工作階段金鑰與驗證期間產生的工作階段金鑰之間並無任何繫結。 任何 MITM 都可以在用戶端和伺服器之間自行建立，並且開始從用戶端轉送要求，甚至是在傳輸通道本身是安全的情況下進行，因為伺服器無從得知安全的通道是從用戶端或 MITM 所建立。 這個案例中的解決方法是將外部 TLS 通道與內部驗證通道加以繫結，讓伺服器能夠偵測是否有 MITM。  
  
> [!NOTE]
>  這個範例只有在裝載於 IIS 上時才能運作，無法在 Cassini (Visual Studio 程式開發伺服器) 上運作，因為 Cassini 不支援 HTTPS。  
  
> [!NOTE]
>  這項功能目前僅於 Windows 7 上提供。 以下為 Windows 7 專屬步驟。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  安裝 Internet Information Services 從**控制台**，**新增/移除程式**， **Windows 功能**。  
  
2.  安裝**Windows 驗證**中**Windows 功能**， **Internet Information Services**， **World Wide Web 服務**， **安全性**，和**Windows 驗證**。  
  
3.  安裝**Windows Communication Foundation HTTP 啟動**中**Windows 功能**， **Microsoft.NET Framework 3.5.1**，和**Windows 通訊Foundation HTTP 啟動**。  
  
4.  這個範例需由用戶端建立與伺服器之間的安全通道，所以必須有可從 Internet Information Services (IIS) 管理員進行安裝的伺服器憑證。  
  
    1.  開啟 [IIS Manager]。 開啟**伺服器憑證**，會出現在**功能檢視**索引標籤上，選取根節點 （電腦名稱） 時。  
  
    2.  若要測試這個範例，請建立自我簽署憑證。 如果您不希望 Internet Explorer 出現憑證可能不安全的提示，請將此憑證安裝到 [受信任的根憑證授權單位] 存放區。  
  
5.  開啟**動作**窗格預設的網站。 按一下**編輯站台**，**繫結**。 加入 HTTPS 做為類型 (如果尚未存在)，並且使用連接埠號碼 443。 指派上一個步驟中建立的 SSL 憑證。  
  
6.  建置服務。 這樣會在 IIS 中建立一個虛擬目錄，並且視需要複製 Web 主控服務的 .dll、.svc 和 .config 檔案。  
  
7.  開啟 [IIS Manager]。 以滑鼠右鍵按一下虛擬目錄 (**ExtendedProtection**)，在上一個步驟中建立。 選取**轉換成應用程式**。  
  
8.  開啟**驗證**模組在 IIS 管理員中針對此虛擬目錄和啟用**Windows 驗證**。  
  
9. 開啟**進階設定**下**Windows 驗證**此虛擬目錄並將它設定為**需要**。  
  
10. 您可以從瀏覽器視窗存取 HTTPS URL 來測試服務 (提供完整網域名稱)。 如果您想要從遠端電腦存取此 URL，請確定防火牆已開放所有傳入的 HTTP 和 HTTPS 連線。  
  
11. 開啟用戶端組態檔，並且為用戶端提供完整網域名稱，或是取代 `<<full_machine_name>>` 的端點位址屬性。  
  
12. 執行該用戶端。 用戶端將與服務進行通訊，該服務會建立安全通道並且使用延伸保護。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Security\ExtendedProtection`
