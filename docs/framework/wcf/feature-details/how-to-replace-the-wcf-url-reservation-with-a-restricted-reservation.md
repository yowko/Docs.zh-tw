---
title: HOW TO：若要以受限的保留項目取代 WCF URL URL 保留項目
ms.date: 03/30/2017
ms.assetid: 2754d223-79fc-4e2b-a6ce-989889f2abfa
ms.openlocfilehash: b53596d7ac4e7e7c3748f6a98130492a96c0b48c
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2018
ms.locfileid: "46578862"
---
# <a name="how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation"></a>HOW TO：若要以受限的保留項目取代 WCF URL URL 保留項目
URL 保留項目可讓您限制誰可以接收來自某個 URL 或一組 URL 的訊息。 保留項目是由一個 URL 範本、一個存取控制清單 (ACL)，以及一組旗標所組成。 URL 範本會定義保留項目所影響的 URL。 如需有關如何處理 URL 範本的詳細資訊，請參閱 <<c0> [ 路由傳送連入要求](https://go.microsoft.com/fwlink/?LinkId=136764)。 ACL 會控制允許從指定之 URL 接收訊息的使用者或使用者群組。 旗標會指出保留項目是要提供使用者或群組直接在 URL 上接聽的權限，還是要委派接聽其他特定處理序的權限。  
  
 預設作業系統組態的一部分，Windows Communication Foundation (WCF) 建立連接埠 80，若要讓所有使用者執行使用雙重 HTTP 繫結進行雙工通訊的應用程式的全域存取保留項目。 此保留項目的 ACL 是攻所有人使用，因此，系統管理員無法明確地允許或不允許在一個 URL 或一組 URL 上接聽的權限。 本主題說明如何刪除此保留項目，以及如何使用受限的 ACL 重新建立保留項目。  
  
 在 [!INCLUDE[wv](../../../../includes/wv-md.md)] 或 [!INCLUDE[lserver](../../../../includes/lserver-md.md)] 上，您可以從更高權限的命令提示字元輸入 `netsh http show urlacl`，以檢視所有 HTTP URL 保留項目。  下列範例會示範 WCF URL 保留項目應該類似。  
  
```  
Reserved URL : http://+:80/Temporary_Listen_Addresses/  
        User: \Everyone  
            Listen: Yes  
            Delegate: No  
            SDDL: D:(A;;GX;;;WD)  
```  
  
 此保留項目所組成的 WCF 應用程式使用 HTTP 雙重繫結進行雙工通訊時使用的 URL 範本。 WCF 服務會使用此表單的 Url，將訊息傳回給 WCF 用戶端透過 HTTP 雙重繫結進行通訊時。 所有人都會得到在 URL 上接聽的權限，但沒有委派接聽其他處理序的權限。 最後，ACL 會以 Security Descriptor Definition Language (SSDL) 描述。 如需有關 SSDL 的詳細資訊，請參閱[SSDL](https://go.microsoft.com/fwlink/?LinkId=136789)  
  
### <a name="to-delete-the-wcf-url-reservation"></a>若要刪除 WCF URL 保留項目  
  
1.  按一下 **開始**，指向**所有程式**，按一下 **附屬應用程式**，以滑鼠右鍵按一下**命令提示字元**按一下**身分執行系統管理員**被人提起的操作功能表上。 按一下 **繼續**上可能會要求權限才能繼續 使用者帳戶控制 (UAC) 視窗。  
  
2.  在中輸入**netsh http delete urlacl =http://+:80/Temporary_Listen_Addresses/** 在命令提示字元 視窗中。  
  
3.  如果成功刪除保留項目，就會顯示下列訊息。 **已成功刪除的 URL 保留項目**  
  
## <a name="creating-a-new-security-group-and-new-restricted-url-reservation"></a>建立新的安全性群組與新的受限 URL 保留項目  
 若要以受限的保留項目取代 WCF URL 保留項目，您必須先建立新的安全性群組。 您可以從命令提示字元或電腦管理主控台執行這個動作。 您只需要選擇其中一種方式。  
  
#### <a name="to-create-a-new-security-group-from-a-command-prompt"></a>若要從命令提示字元建立新的安全性群組  
  
1.  按一下 **開始**，指向**所有程式**，按一下 **附屬應用程式**，以滑鼠右鍵按一下**命令提示字元**按一下**身分執行系統管理員**被人提起的操作功能表上。 按一下 **繼續**上可能會要求權限才能繼續 使用者帳戶控制 (UAC) 視窗。  
  
2.  輸入**net localgroup"\<安全性群組名稱 >"/ 註解:"\<安全性群組描述 >"/add**在命令提示字元。 取代**\<安全性的群組名稱 >** 具有您想要建立的安全性群組的名稱並**\<安全性群組描述 >** 使用適合的描述安全性群組。  
  
3.  如果成功建立安全性群組，就會顯示下列訊息。 **已成功完成命令。**  
  
#### <a name="to-create-a-new-security-group-from-the-computer-management-console"></a>若要從電腦管理主控台建立新的安全性群組  
  
1.  按一下 **開始**，按一下**控制台**，按一下**系統管理工具**，然後按一下**電腦管理**以開啟 電腦設定管理主控台。 按一下 **繼續**上可能會要求權限才能繼續 使用者帳戶控制 (UAC) 視窗。  
  
2.  按一下 **系統工具**，按一下**本機使用者和群組**，以滑鼠右鍵按一下**群組**資料夾，然後按一下**新增群組**的操作功能表上，會出現。 輸入所需**群組名稱**，**描述**和其他詳細資料，這個新的安全性群組，然後按一下**建立** 按鈕來建立的安全性群組。  
  
#### <a name="to-create-the-restricted-url-reservation"></a>若要建立受限的 URL 保留項目  
  
1.  按一下 **開始**，指向**所有程式**，按一下 **附屬應用程式**，以滑鼠右鍵按一下**命令提示字元**按一下**身分執行系統管理員**被人提起的操作功能表上。 按一下 **繼續**上可能會要求權限才能繼續 使用者帳戶控制 (UAC) 視窗。  
  
2.  在中輸入**netsh http add urlacl =http://+:80/Temporary_Listen_Addresses/使用者 ="\<電腦名稱 >\\< 安全性群組名稱\>** 在命令提示字元。 取代**\<電腦名稱 >** 必須建立群組所在的電腦名稱並**\<安全性群組名稱 >** 具有您所建立的安全性群組名稱先前。  
  
3.  如果成功建立保留項目，就會顯示下列訊息。 **URL 保留項目已成功新增**。
