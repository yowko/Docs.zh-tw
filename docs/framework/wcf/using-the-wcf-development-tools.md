---
title: 使用 WCF 開發工具
ms.date: 03/30/2017
ms.assetid: 054adb87-c244-4d5a-83d1-0b2b44bd454b
ms.openlocfilehash: adaad28fee5d27976df4bf20bb54f70aec5c2daf
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90544618"
---
# <a name="using-the-wcf-development-tools"></a>使用 WCF 開發工具
本節說明可協助您開發 WCFservice 的 Visual Studio 開發工具。  
  
 您可以使用 Visual Studio 範本作為基礎來快速建立您自己的服務，然後使用 WCF 服務自動主機和 WCF 測試用戶端來對您的服務進行 debug 錯和測試。 這些工具都提供了迅速完善的偵錯與測試循環，而且在早期階段不需要認可裝載模型。  

 > [!NOTE]
 > 從 Visual Studio 2017 開始，預設不會安裝 WCF 開發工具。 為了使用這些功能，您必須確定已在 Visual Studio 安裝程式中選取 Windows Communication Foundation 元件。
  
## <a name="the-wcf-developer-tools"></a>WCF 開發者工具  
 [WCF Visual Studio 範本](wcf-vs-templates.md)  
  
 您可以使用 Visual Studio 中預先定義的 Visual Studio 專案和專案範本，快速建立 WCF 服務和周圍的應用程式。  
  
 [WCF 服務主機 (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md)  
  
 WCF Service Auto Host ( # A0) 可讓您啟動 Visual Studio 偵錯工具 (F5) ，以自動裝載和測試您已執行的服務。 然後，您可以使用 WCF 測試用戶端 ( # A0) 或您自己的用戶端來測試服務，以尋找並修正任何可能的錯誤。  
  
 [WCF 測試用戶端 (WcfTestClient.exe)](wcf-test-client-wcftestclient-exe.md)  
  
 WCF 測試用戶端 ( # A0) 是一種 GUI 工具，可讓您輸入任意類型的參數、將該輸入提交至服務，以及查看服務傳回的回應。 它會在結合 WCF 服務自動主機時提供順暢的服務測試體驗。  
  
 [從 XML 產生資料型別類型](generating-data-type-classes-from-xml.md)  
  
 儲存在剪貼簿中的 XML 資料可以貼到程式碼頁面上。 在資料中定義的類別將會轉換為程式碼型別。  
  
## <a name="using-the-tools-without-administrator-privilege"></a>在沒有系統管理員權限的情況下使用工具  
 若要讓沒有系統管理員許可權的使用者開發 WCF 服務，安裝 Visual Studio 期間會為命名空間 "" 建立 ACL (存取控制清單) http://+:8731/Design_Time_Addresses 。 ACL 會設定為 (UI)，其中包含已登入電腦的所有互動使用者。 系統管理員可以在這個 ACL 中新增或移除使用者，或是開啟其他連接埠。這個 ACL 可讓 WCF 或 WF 範本傳送及接收其預設組態中的資料。 它也可讓使用者在不授與系統管理員許可權的情況下，使用 WCF Service Auto Host ( # A0) 。  
  
 您可以使用 Windows Vista 中的 [Netsh.exe] 工具，以提高許可權的系統管理員帳戶修改存取權。 下列是使用 Netsh.exe 的範例。  
  
```console  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 如需 Netsh.exe 的詳細資訊，請參閱 [如何使用 Netsh.exe 工具和命令列參數](/previous-versions/tn-archive/bb490939(v=technet.10))。  
  
## <a name="see-also"></a>另請參閱

- [WCF Visual Studio 範本](wcf-vs-templates.md)
- [WCF 服務主機 (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md)
- [WCF 測試用戶端 (WcfTestClient.exe)](wcf-test-client-wcftestclient-exe.md)
