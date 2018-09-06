---
title: 使用 WCF 開發工具
ms.date: 03/30/2017
ms.assetid: 054adb87-c244-4d5a-83d1-0b2b44bd454b
ms.openlocfilehash: 3eb349fd795b2067d4d75ff138fd9b5922110bd3
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "44037873"
---
# <a name="using-the-wcf-development-tools"></a>使用 WCF 開發工具
本節說明可協助您開發 wcf 服務的 Visual Studio 開發工具。  
  
 您可以使用 Visual Studio 範本做為基礎，快速建置您自己的服務，然後使用 WCF 服務自動主機和 WCF 測試用戶端來偵錯和測試您的服務。 這些工具都提供了迅速完善的偵錯與測試循環，而且在早期階段不需要認可裝載模型。  
  
## <a name="the-wcf-developer-tools"></a>WCF 開發者工具  
 [WCF Visual Studio 範本](../../../docs/framework/wcf/wcf-vs-templates.md)  
  
 您可以使用 Visual Studio 中的預先定義的 Visual Studio 專案和項目範本，快速建置 WCF 服務和相關的應用程式。  
  
 [WCF 服務主機 (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
  
 WCF 服務自動主機 (WcfSvcHost.exe) 可讓您啟動 Visual Studio 偵錯工具 (F5) 來自動裝載並測試您已實作的服務。 然後，您可以測試使用 WCF 測試用戶端 (wcfTestClient.exe) 或您自己的用戶端來找出並修正任何潛在錯誤的服務。  
  
 [WCF 測試用戶端 (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)  
  
 WCF 測試用戶端 (WcfTestClient.exe) 是一種 GUI 工具，可讓您輸入任意型別的參數，將該服務，以及檢視服務的回應傳回輸入送出。 它提供了完善的服務測試經驗與 WCF 服務自動主機結合時。  
  
 [從 XML 產生資料類型類別](../../../docs/framework/wcf/generating-data-type-classes-from-xml.md)  
  
 儲存在剪貼簿中的 XML 資料可以貼到程式碼頁面上。 在資料中定義的類別將會轉換為程式碼型別。  
  
## <a name="using-the-tools-without-administrator-privilege"></a>在沒有系統管理員權限的情況下使用工具  
 若要啟用沒有系統管理員權限的使用者來開發 WCF 服務，ACL （存取控制清單） 建立命名空間"http://+:8731/Design_Time_Addresses"Visual Studio 安裝期間。 ACL 會設定為 (UI)，其中包含已登入電腦的所有互動使用者。 系統管理員可以在這個 ACL 中新增或移除使用者，或是開啟其他連接埠。這個 ACL 可讓 WCF 或 WF 範本傳送及接收其預設組態中的資料。 它也可讓使用者使用 WCF 服務自動主機 (wcfSvcHost.exe)，而不授與他們系統管理員權限。  
  
 您可以更高權限的系統管理員帳戶身分，使用 [!INCLUDE[wv](../../../includes/wv-md.md)] 中的 Netsh.exe 工具來修改存取權。 下列是使用 Netsh.exe 的範例。  
  
```  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 如需 Netsh.exe 的詳細資訊，請參閱[如何使用 Netsh.exe 工具和命令列參數](https://go.microsoft.com/fwlink/?LinkId=97877)。  
  
## <a name="see-also"></a>另請參閱  
 [WCF Visual Studio 範本](../../../docs/framework/wcf/wcf-vs-templates.md)  
 [WCF 服務主機 (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
 [WCF 測試用戶端 (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
