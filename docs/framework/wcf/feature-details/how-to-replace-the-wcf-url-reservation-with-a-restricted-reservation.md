---
title: "HOW TO：若要以受限的保留項目取代 WCF URL URL 保留項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2754d223-79fc-4e2b-a6ce-989889f2abfa
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e4cfae36dfcb65dfd93dfc4fb1d6b64ba01e1b11
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation"></a>HOW TO：若要以受限的保留項目取代 WCF URL URL 保留項目
URL 保留項目可讓您限制誰可以接收來自某個 URL 或一組 URL 的訊息。 保留項目是由一個 URL 範本、一個存取控制清單 (ACL)，以及一組旗標所組成。 URL 範本會定義保留項目所影響的 URL。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]如何處理的 URL 範本，請參閱[路由內送要求](http://go.microsoft.com/fwlink/?LinkId=136764)。 ACL 會控制允許從指定之 URL 接收訊息的使用者或使用者群組。 旗標會指出保留項目是要提供使用者或群組直接在 URL 上接聽的權限，還是要委派接聽其他特定處理序的權限。  
  
 As part of the default operating system configuration, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 會針對通訊埠 80 建立可全域存取的保留項目，讓所有使用者執行使用雙重 HTTP 繫結進行雙工通訊的應用程式。 此保留項目的 ACL 是攻所有人使用，因此，系統管理員無法明確地允許或不允許在一個 URL 或一組 URL 上接聽的權限。 本主題說明如何刪除此保留項目，以及如何使用受限的 ACL 重新建立保留項目。  
  
 在 [!INCLUDE[wv](../../../../includes/wv-md.md)] 或 [!INCLUDE[lserver](../../../../includes/lserver-md.md)] 上，您可以從更高權限的命令提示字元輸入 `netsh http show urlacl`，以檢視所有 HTTP URL 保留項目。  下列範例顯示應該類似的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] URL 保留項目。  
  
```  
Reserved URL : http://+:80/Temporary_Listen_Addresses/  
        User: \Everyone  
            Listen: Yes  
            Delegate: No  
            SDDL: D:(A;;GX;;;WD)  
```  
  
 保留項目是由 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式使用 HTTP 雙重繫結進行雙工通訊時所使用的 URL 範本所組成。 透過 HTTP 雙重繫結進行通訊時，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務會使用這種形式的 URL，將訊息傳回 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端。 所有人都會得到在 URL 上接聽的權限，但沒有委派接聽其他處理序的權限。 最後，ACL 會以 Security Descriptor Definition Language (SSDL) 描述。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]SSDL，請參閱[SSDL](http://go.microsoft.com/fwlink/?LinkId=136789)  
  
### <a name="to-delete-the-wcf-url-reservation"></a>若要刪除 WCF URL 保留項目  
  
1.  按一下**啟動**，指向 **所有程式**，按一下**附屬應用程式**，以滑鼠右鍵按一下**命令提示字元**按一下**身分執行系統管理員**上出現的操作功能表。 按一下**繼續**使用者帳戶控制 (UAC) 視窗可能會要求權限才能繼續。  
  
2.  在中輸入**netsh http 刪除 urlacl url = http: / / +:80/Temporary_Listen_Addresses/**在命令提示字元 視窗中。  
  
3.  如果成功刪除保留項目，就會顯示下列訊息。 **已成功刪除的 URL 保留項目**  
  
## <a name="creating-a-new-security-group-and-new-restricted-url-reservation"></a>建立新的安全性群組與新的受限 URL 保留項目  
 若要以受限的保留項目取代 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] URL 保留項目，您必須先建立一個新的安全性群組。 您可以從命令提示字元或電腦管理主控台執行這個動作。 您只需要選擇其中一種方式。  
  
#### <a name="to-create-a-new-security-group-from-a-command-prompt"></a>若要從命令提示字元建立新的安全性群組  
  
1.  按一下**啟動**，指向 **所有程式**，按一下**附屬應用程式**，以滑鼠右鍵按一下**命令提示字元**按一下**身分執行系統管理員**上出現的操作功能表。 按一下**繼續**使用者帳戶控制 (UAC) 視窗可能會要求權限才能繼續。  
  
2.  在中輸入**net localgroup"\<安全性群組名稱 >"/ 註解:"\<安全性群組描述 >"/ 加入**在命令提示字元。 取代**\<安全性群組名稱 >**具有您想要建立的安全性群組的名稱和**\<安全性群組描述 >**適合的描述安全性群組。  
  
3.  如果成功建立安全性群組，就會顯示下列訊息。 **已成功完成命令。**  
  
#### <a name="to-create-a-new-security-group-from-the-computer-management-console"></a>若要從電腦管理主控台建立新的安全性群組  
  
1.  按一下**啟動**，按一下**控制台**，按一下**系統管理工具**，然後按一下**電腦管理**若要開啟的電腦設定管理主控台。 按一下**繼續**使用者帳戶控制 (UAC) 視窗可能會要求權限才能繼續。  
  
2.  按一下**系統工具**，按一下 **本機使用者和群組**，以滑鼠右鍵按一下**群組**資料夾，然後按一下**新增群組**操作功能表上，隨即出現。 輸入所需**群組名稱**，**描述**和其他詳細資料，這個新的安全性群組，然後按一下**建立**按鈕以建立安全性群組。  
  
#### <a name="to-create-the-restricted-url-reservation"></a>若要建立受限的 URL 保留項目  
  
1.  按一下**啟動**，指向 **所有程式**，按一下**附屬應用程式**，以滑鼠右鍵按一下**命令提示字元**按一下**身分執行系統管理員**上出現的操作功能表。 按一下**繼續**使用者帳戶控制 (UAC) 視窗可能會要求權限才能繼續。  
  
2.  在中輸入**netsh http 新增 urlacl url = http: / / +: 80/Temporary_Listen_Addresses/使用者 ="\<機器名稱 >\\< 安全性群組名稱\>**在命令提示字元。 取代**\<機器名稱 >**必須建立群組所在的電腦名稱和**\<安全性群組名稱 >**具有您所建立的安全性群組名稱先前。  
  
3.  如果成功建立保留項目，就會顯示下列訊息。 **URL 保留項目成功加入**。
