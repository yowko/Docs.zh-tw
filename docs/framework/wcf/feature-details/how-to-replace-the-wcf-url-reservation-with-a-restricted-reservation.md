---
title: 作法：以受限的保留項目取代 WCF URL 保留項目
ms.date: 03/30/2017
ms.assetid: 2754d223-79fc-4e2b-a6ce-989889f2abfa
ms.openlocfilehash: 981c4890b11130b937e176da78f378340c0d3894
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991655"
---
# <a name="how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation"></a>HOW TO：以受限的保留項目取代 WCF URL 保留項目
URL 保留項目可讓您限制誰可以接收來自某個 URL 或一組 URL 的訊息。 保留項目是由一個 URL 範本、一個存取控制清單 (ACL)，以及一組旗標所組成。 URL 範本會定義保留項目所影響的 URL。 如需如何處理 URL 範本的詳細資訊，請參閱[路由傳入要求](https://go.microsoft.com/fwlink/?LinkId=136764)。 ACL 會控制允許從指定之 URL 接收訊息的使用者或使用者群組。 旗標會指出保留項目是要提供使用者或群組直接在 URL 上接聽的權限，還是要委派接聽其他特定處理序的權限。  
  
 作為預設作業系統設定的一部分，Windows Communication Foundation （WCF）會為埠80建立可全域存取的保留專案，讓所有使用者執行使用雙重 HTTP 系結進行雙工通訊的應用程式。 此保留項目的 ACL 是攻所有人使用，因此，系統管理員無法明確地允許或不允許在一個 URL 或一組 URL 上接聽的權限。 本主題說明如何刪除此保留項目，以及如何使用受限的 ACL 重新建立保留項目。  
  
 在 [!INCLUDE[wv](../../../../includes/wv-md.md)] 或 [!INCLUDE[lserver](../../../../includes/lserver-md.md)] 上，您可以從更高權限的命令提示字元輸入 `netsh http show urlacl`，以檢視所有 HTTP URL 保留項目。  下列範例會顯示 WCF URL 保留專案的外觀。  

```
Reserved URL : http://+:80/Temporary_Listen_Addresses/  
        User: \Everyone  
            Listen: Yes  
            Delegate: No  
            SDDL: D:(A;;GX;;;WD)  
```

 保留專案是由 WCF 應用程式使用 HTTP 雙重系結進行雙工通訊時所使用的 URL 範本所組成。 在透過 HTTP 雙重系結進行通訊時，WCF 服務會使用此表單的 Url，將訊息傳回給 WCF 用戶端。 所有人都會得到在 URL 上接聽的權限，但沒有委派接聽其他處理序的權限。 最後，ACL 會以 Security Descriptor Definition Language (SSDL) 描述。 如需 SSDL 的詳細資訊，請參閱[ssdl](https://go.microsoft.com/fwlink/?LinkId=136789)  
  
## <a name="to-delete-the-wcf-url-reservation"></a>若要刪除 WCF URL 保留項目  
  
1. 按一下 [**開始**]，指向 [**所有程式**]，按一下 [**附屬**應用程式]，以滑鼠右鍵按一下**命令提示**字元，然後在出現的內容功能表上按一下 [以**系統管理員身分執行**] 在可能會要求許可權繼續的 [使用者帳戶控制（UAC）] 視窗上，按一下 [**繼續**]。  
  
2. 在 [命令提示字元] 視窗中輸入**netsh HTTP delete urlacl http://+:80/Temporary_Listen_Addresses/ url =** 。  
  
3. 如果成功刪除保留項目，就會顯示下列訊息。 **已成功刪除 URL 保留專案**  
  
## <a name="creating-a-new-security-group-and-new-restricted-url-reservation"></a>建立新的安全性群組與新的受限 URL 保留項目  
 若要以受限的保留專案取代 WCF URL 保留專案，您必須先建立新的安全性群組。 您可以從命令提示字元或電腦管理主控台執行這個動作。 您只需要選擇其中一種方式。  
  
### <a name="to-create-a-new-security-group-from-a-command-prompt"></a>若要從命令提示字元建立新的安全性群組  
  
1. 按一下 [**開始**]，指向 [**所有程式**]，按一下 [**附屬**應用程式]，以滑鼠右鍵按一下**命令提示**字元，然後在出現的內容功能表上按一下 [以**系統管理員身分執行**] 在可能會要求許可權繼續的 [使用者帳戶控制（UAC）] 視窗上，按一下 [**繼續**]。  
  
2. 輸入 **net localgroup"\<安全性群組名稱 >"/ 註解:"\<安全性群組描述 >"/add** 在命令提示字元。 以您想要建立的安全性群組名稱取代 **\<安全性群組名稱 >** ，並 **\<** 以安全性群組的適當描述來取代安全性群組描述 >。  
  
3. 如果成功建立安全性群組，就會顯示下列訊息。 **命令已順利完成。**  
  
### <a name="to-create-a-new-security-group-from-the-computer-management-console"></a>若要從電腦管理主控台建立新的安全性群組  
  
1. 依序按一下 [**開始**]、[**控制台**]、[系統管理**工具**] 和 [**電腦管理**]，以開啟 [電腦管理] 主控台。 在可能會要求許可權繼續的 [使用者帳戶控制（UAC）] 視窗上，按一下 [**繼續**]。  
  
2. 按一下 [**系統工具**]，按一下 [**本機使用者和群組**]，以滑鼠右鍵按一下 [**群組**] 資料夾，然後在出現的內容功能表上按一下 [**新增群組**]。 輸入所需的 [**組名**]、[**描述**] 和這個新安全性群組的其他詳細資料，然後按一下 [**建立**] 按鈕來建立安全性群組。  
  
### <a name="to-create-the-restricted-url-reservation"></a>若要建立受限的 URL 保留項目  
  
1. 按一下 [**開始**]，指向 [**所有程式**]，按一下 [**附屬**應用程式]，以滑鼠右鍵按一下**命令提示**字元，然後在出現的內容功能表上按一下 [以**系統管理員身分執行**] 在可能會要求許可權繼續的 [使用者帳戶控制（UAC）] 視窗上，按一下 [**繼續**]。  
  
2. 在中輸入 **netsh http add urlacl =http://+:80/Temporary_Listen_Addresses/ 使用者 ="\< 電腦名稱 >\\ < 安全性群組名稱\>** 在命令提示字元。 以您先前建立的安全性群組名稱取代 **\<電腦名稱稱 >** 和群組必須建立的電腦名稱稱，以及 **\<安全性群組名稱 >** 。  
  
3. 如果成功建立保留項目，就會顯示下列訊息。 **已成功新增 URL 保留**專案。
