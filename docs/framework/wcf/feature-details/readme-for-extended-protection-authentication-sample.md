---
title: 延伸保護驗證之範例的讀我檔案
ms.date: 03/30/2017
ms.assetid: 80bf2e97-398d-4db5-9040-d96478a2ccab
ms.openlocfilehash: 53592db03c88e673d529ef04f2fbc6e182897457
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59319348"
---
# <a name="readme-for-extended-protection-authentication-sample"></a>延伸保護驗證之範例的讀我檔案
延伸的保護是一項安全性方案以防止攔截 (MITM) 攻擊，攻擊者 （"--攔截 」） 會攔截用戶端的認證和使用它們來存取用戶端想要的伺服器上的安全資源。  
  
 如需詳細資訊，請參閱 < [Extended Protection for Authentication 概觀](../../../../docs/framework/wcf/feature-details/extended-protection-for-authentication-overview.md)。  
  
> [!NOTE]
>  這個範例僅適用於由 IIS 裝載的情況。 Visual Studio 程式開發伺服器不支援 HTTPS，所以並不適用。  
  
## <a name="to-set-up-build-and-run-the-sample"></a>安裝設定、建置及執行範例  
  
1. 安裝 IIS 電腦上，從 新增/移除程式-> Windows 功能。  
  
2. 開啟 Windows 驗證，在 Windows 功能：網際網路資訊服務-> World Wide Web 服務-> 安全性-> Windows 驗證。  
  
3. 在 Windows 功能，以開啟 HTTP 啟動：Microsoft.NET Framework 3.5.1-> Windows Communication Foundation HTTP 啟動。  
  
4. 這個範例需由用戶端與伺服器建立安全通道，所以必須有可從 Internet Information Services (IIS) 管理員進行安裝的伺服器憑證。  
  
    1.  開啟 [IIS 管理員] -> [伺服器憑證] \(位於功能檢視索引標籤)。  
  
    2.  為了測試這個範例，您可以建立自我簽署憑證  (若不希望 Internet Explorer 出現憑證可能不安全的提示，可將此憑證安裝到 [受信任的根憑證授權單位] 存放區)。  
  
5. 移至 [預設的網站] 的 [執行] 窗格。 按一下 編輯站台-> 繫結。 新增 HTTPS 做為繫結類型 (如果沒有此項)，連接埠編號為 443，並指派上一個步驟所建立的 SSL 憑證。  
  
6. 建置服務。 這樣會建立一個 IIS 虛擬目錄 (透過專案屬性中指定的建置後動作)，並且視需要複製 Web 裝載服務的 dll、.svc 和 config 檔案。  
  
7. 開啟 [IIS 管理員]。 以滑鼠右鍵按一下先前步驟所建立的虛擬目錄 (ExtendedProtection)，選取 [轉換成應用程式]。  
  
8. 開啟此虛擬目錄在 [IIS 管理員] 中的驗證模組，然後啟用 Windows 驗證。  
  
9. 開啟此虛擬目錄 Windows 驗證的 [進階設定] 並將其設為 [必要]，因為這個範例中 ExtendedProtection 的相應設定是設為 [永遠]。  
  
10. 您可以從瀏覽器視窗存取 URL 來測試服務。 若想要從其他電腦存取此 URL，請確定防火牆已開放所有傳入的 HTTP 和 HTTPS 連線。  
  
11. 開啟用戶端組態檔，並提供完整電腦名稱\<用戶端 >-\<端點 >-address 屬性，取代 << full_machine_name >>。  
  
12. 執行該用戶端。 用戶端隨即建立安全通道，在延伸保護的庇護之下與服務通訊。
