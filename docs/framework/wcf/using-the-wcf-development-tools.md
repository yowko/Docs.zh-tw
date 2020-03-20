---
title: 使用 WCF 開發工具
ms.date: 03/30/2017
ms.assetid: 054adb87-c244-4d5a-83d1-0b2b44bd454b
ms.openlocfilehash: 82bb7e225492bcdba4d2e611de405a09571355c0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183072"
---
# <a name="using-the-wcf-development-tools"></a>使用 WCF 開發工具
本節介紹視覺化工作室開發工具，這些工具可説明您開發 WCF 服務。  
  
 您可以使用 Visual Studio 範本作為基礎來快速構建您自己的服務，然後使用 WCF 服務自動主機和 WCF 測試用戶端來調試和測試服務。 這些工具都提供了迅速完善的偵錯與測試循環，而且在早期階段不需要認可裝載模型。  

 > [!NOTE]
 > 從 Visual Studio 2017 開始，預設情況下不會安裝 WCF 開發工具。 為了使用這些功能，必須確保在視覺化工作室安裝程式中選擇 Windows 通信基礎元件。
  
## <a name="the-wcf-developer-tools"></a>WCF 開發者工具  
 [WCF Visual Studio 範本](wcf-vs-templates.md)  
  
 您可以使用 Visual Studio 中預定義的 Visual Studio 專案和專案範本來快速構建 WCF 服務和周圍應用程式。  
  
 [WCF 服務主機 (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md)  
  
 WCF 服務自動主機 （WcfSvcHost.exe） 允許您啟動 Visual Studio 調試器 （F5） 以自動託管和測試您已實現的服務。 然後，您可以使用 WCF 測試用戶端 （wcfTestClient.exe） 或您自己的用戶端測試服務，以查找和修復任何潛在錯誤。  
  
 [WCF 測試用戶端 (WcfTestClient.exe)](wcf-test-client-wcftestclient-exe.md)  
  
 WCF 測試用戶端 （WcfTestClient.exe） 是一個 GUI 工具，允許您輸入任意類型的參數，將該輸入提交到服務，並查看服務發送回的回應。 與 WCF 服務自動主機結合使用時，可提供無縫的服務測試體驗。  
  
 [從 XML 產生資料類型類別](generating-data-type-classes-from-xml.md)  
  
 儲存在剪貼簿中的 XML 資料可以貼到程式碼頁面上。 在資料中定義的類別將會轉換為程式碼型別。  
  
## <a name="using-the-tools-without-administrator-privilege"></a>在沒有系統管理員權限的情況下使用工具  
 為了使沒有管理員許可權的使用者能夠開發 WCF 服務，在安裝 Visual Studio 期間為命名空間"http://+:8731/Design_Time_Addresses創建 ACL（存取控制清單）。 ACL 會設定為 (UI)，其中包含已登入電腦的所有互動使用者。 系統管理員可以在這個 ACL 中新增或移除使用者，或是開啟其他連接埠。這個 ACL 可讓 WCF 或 WF 範本傳送及接收其預設組態中的資料。 它還允許使用者使用 WCF 服務自動主機 （wcfSvcHost.exe），而無需授予管理員許可權。  
  
 您可以使用 Windows Vista 中的 Netsh.exe 工具在提升的管理員帳戶下修改存取權限。 下列是使用 Netsh.exe 的範例。  
  
```console  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 有關 Netsh.exe 的詳細資訊，請參閱[如何使用 Netsh.exe 工具和命令列開關](https://docs.microsoft.com/previous-versions/tn-archive/bb490939(v=technet.10))。  
  
## <a name="see-also"></a>另請參閱

- [WCF Visual Studio 範本](wcf-vs-templates.md)
- [WCF 服務主機 (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md)
- [WCF 測試用戶端 (WcfTestClient.exe)](wcf-test-client-wcftestclient-exe.md)
