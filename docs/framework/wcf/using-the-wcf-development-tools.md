---
title: "使用 WCF 開發工具"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 054adb87-c244-4d5a-83d1-0b2b44bd454b
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f752d2aa2621ff650c864b2aca0928c5244c4917
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="using-the-wcf-development-tools"></a>使用 WCF 開發工具
本節說明可協助您開發 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 服務的 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)][!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 開發工具。  
  
 您可以使用 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)][!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 範本做為基礎，快速建置自己的服務，然後使用 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務自動主機和 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 測試用戶端來偵錯並測試您的服務。 這些工具都提供了迅速完善的偵錯與測試循環，而且在早期階段不需要認可裝載模型。  
  
## <a name="the-wcf-developer-tools"></a>WCF 開發者工具  
 [WCF Visual Studio 範本](../../../docs/framework/wcf/wcf-vs-templates.md)  
  
 您可以使用 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 中預先定義的 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)][!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 專案和項目範本，快速建置 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務和相關的應用程式。  
  
 [WCF 服務主機 (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務自動裝載 (WcfSvcHost.exe) 可讓您啟動 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 偵錯工具 (F5) 來自動裝載並測試您已實作的服務。 然後，您可以使用 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 測試用戶端 (wcfTestClient.exe) 或自己的用戶端來測試服務，以尋找並修正任何可能的錯誤。  
  
 [WCF 測試用戶端 (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 測試用戶端 (WcfTestClient.exe) 是一種 GUI 工具，可讓您輸入任意型別的參數、將該輸入送出至服務，以及檢視服務傳回的回應。 與 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務自動主機相結合時，這個用戶端也提供了完善的服務測試經驗。  
  
 [從 XML 產生資料類型類別](../../../docs/framework/wcf/generating-data-type-classes-from-xml.md)  
  
 儲存在剪貼簿中的 XML 資料可以貼到程式碼頁面上。 在資料中定義的類別將會轉換為程式碼型別。  
  
## <a name="using-the-tools-without-administrator-privilege"></a>在沒有系統管理員權限的情況下使用工具  
 為了讓沒有系統管理員權限的使用者能夠開發 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務，在安裝 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 期間會建立命名空間 "http://+:8731/Design_Time_Addresses" 的 ACL (存取控制清單)。 ACL 會設定為 (UI)，其中包含已登入電腦的所有互動使用者。 系統管理員可以在這個 ACL 中新增或移除使用者，或是開啟其他連接埠。這個 ACL 可讓 WCF 或 WF 範本傳送及接收其預設組態中的資料。 也可以讓使用者在未取得系統管理員權限的情況下使用 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務自動主機 (wcfSvcHost.exe)。  
  
 您可以更高權限的系統管理員帳戶身分，使用 [!INCLUDE[wv](../../../includes/wv-md.md)] 中的 Netsh.exe 工具來修改存取權。 下列是使用 Netsh.exe 的範例。  
  
```  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]Netsh.exe，請參閱[如何使用 Netsh.exe 工具和命令列參數](http://go.microsoft.com/fwlink/?LinkId=97877)。  
  
## <a name="see-also"></a>另請參閱  
 [WCF Visual Studio 範本](../../../docs/framework/wcf/wcf-vs-templates.md)  
 [WCF 服務主機 (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
 [WCF 測試用戶端 (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
