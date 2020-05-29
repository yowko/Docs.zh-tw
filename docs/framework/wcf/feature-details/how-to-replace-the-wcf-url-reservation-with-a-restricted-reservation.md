---
title: HOW TO：若要以受限的保留項目取代 WCF URL URL 保留項目
ms.date: 03/30/2017
ms.assetid: 2754d223-79fc-4e2b-a6ce-989889f2abfa
ms.openlocfilehash: 780a2c7fe240ed624ff106e8157661f8b76b32bd
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202366"
---
# <a name="how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation"></a>HOW TO：若要以受限的保留項目取代 WCF URL URL 保留項目

URL 保留項目可讓您限制誰可以接收來自某個 URL 或一組 URL 的訊息。 保留項目是由一個 URL 範本、一個存取控制清單 (ACL)，以及一組旗標所組成。 URL 範本會定義保留項目所影響的 URL。 如需如何處理 URL 範本的詳細資訊，請參閱[路由傳入要求](/windows/win32/http/routing-incoming-requests)。 ACL 會控制允許從指定之 URL 接收訊息的使用者或使用者群組。 旗標會指出保留項目是要提供使用者或群組直接在 URL 上接聽的權限，還是要委派接聽其他特定處理序的權限。  
  
 作為預設作業系統設定的一部分，Windows Communication Foundation （WCF）會為埠80建立可全域存取的保留專案，讓所有使用者執行使用雙重 HTTP 系結進行雙工通訊的應用程式。 此保留項目的 ACL 是攻所有人使用，因此，系統管理員無法明確地允許或不允許在一個 URL 或一組 URL 上接聽的權限。 本主題說明如何刪除此保留項目，以及如何使用受限的 ACL 重新建立保留項目。  
  
在 Windows Vista 或 Windows Server 2008 上，您可以藉由輸入，從提升許可權的命令提示字元中，查看所有的 HTTP URL 保留專案 `netsh http show urlacl` 。 下列範例會顯示 WCF URL 保留專案的外觀：

```
Reserved URL : http://+:80/Temporary_Listen_Addresses/  
        User: \Everyone  
            Listen: Yes  
            Delegate: No  
            SDDL: D:(A;;GX;;;WD)  
```

 保留專案是由 WCF 應用程式使用 HTTP 雙重系結進行雙工通訊時所使用的 URL 範本所組成。 在透過 HTTP 雙重系結進行通訊時，WCF 服務會使用此表單的 Url，將訊息傳回給 WCF 用戶端。 所有人都會得到在 URL 上接聽的權限，但沒有委派接聽其他處理序的權限。 最後，ACL 會以 Security Descriptor Definition Language (SSDL) 描述。 如需 SSDL 的詳細資訊，請參閱[ssdl](/windows/win32/secauthz/security-descriptor-definition-language)  
  
## <a name="to-delete-the-wcf-url-reservation"></a>若要刪除 WCF URL 保留項目  
  
1. 按一下 [**開始**]，指向 [**所有程式**]，按一下 [**附屬**應用程式]，以滑鼠右鍵按一下**命令提示**字元，然後在出現的內容功能表上按一下 [以**系統管理員身分執行**] 在可能會要求許可權繼續的 [使用者帳戶控制（UAC）] 視窗上，按一下 [**繼續**]。  
  
2. `netsh http delete urlacl url=http://+:80/Temporary_Listen_Addresses/`在 [命令提示字元] 視窗中輸入。  
  
3. 如果成功刪除保留項目，就會顯示下列訊息。 **URL 保留項目已成功刪除**  
  
## <a name="creating-a-new-security-group-and-new-restricted-url-reservation"></a>建立新的安全性群組與新的受限 URL 保留項目  
 若要以受限的保留專案取代 WCF URL 保留專案，您必須先建立新的安全性群組。 您可以從命令提示字元或電腦管理主控台執行這個動作。 您只需要選擇其中一種方式。  
  
### <a name="to-create-a-new-security-group-from-a-command-prompt"></a>若要從命令提示字元建立新的安全性群組  
  
1. 按一下 [**開始**]，指向 [**所有程式**]，按一下 [**附屬**應用程式]，以滑鼠右鍵按一下**命令提示**字元，然後在出現的內容功能表上按一下 [以**系統管理員身分執行**] 在可能會要求許可權繼續的 [使用者帳戶控制（UAC）] 視窗上，按一下 [**繼續**]。  
  
2. 在命令提示字元中輸入 `net localgroup "<security group name>" /comment:"<security group description>" /add` 。 將取代為 **\<security group name>** 您想要建立的安全性群組名稱，並 **\<security group description>** 使用適當的安全性群組描述。  
  
3. 如果成功建立安全性群組，就會顯示下列訊息。 **命令已順利完成。**  
  
### <a name="to-create-a-new-security-group-from-the-computer-management-console"></a>若要從電腦管理主控台建立新的安全性群組  
  
1. 依序按一下 [**開始**]、[**控制台**]、[系統管理**工具**] 和 [**電腦管理**]，以開啟 [電腦管理] 主控台。 在可能會要求許可權繼續的 [使用者帳戶控制（UAC）] 視窗上，按一下 [**繼續**]。  
  
2. 按一下 [**系統工具**]，按一下 [**本機使用者和群組**]，以滑鼠右鍵按一下 [**群組**] 資料夾，然後在出現的內容功能表上按一下 [**新增群組**]。 輸入所需的 [**組名**]、[**描述**] 和這個新安全性群組的其他詳細資料，然後按一下 [**建立**] 按鈕來建立安全性群組。  
  
### <a name="to-create-the-restricted-url-reservation"></a>若要建立受限的 URL 保留項目  
  
1. 按一下 [**開始**]，指向 [**所有程式**]，按一下 [**附屬**應用程式]，以滑鼠右鍵按一下**命令提示**字元，然後在出現的內容功能表上按一下 [以**系統管理員身分執行**] 在可能會要求許可權繼續的 [使用者帳戶控制（UAC）] 視窗上，按一下 [**繼續**]。  
  
2. 在命令提示字元中輸入 `netsh http add urlacl url=http://+:80/Temporary_Listen_Addresses/ user="<machine name>\<security group name>` 。 取代 **\<machine name>** 為必須建立群組的電腦名稱稱，以及 **\<security group name>** 您先前建立的安全性群組名稱。  
  
3. 如果成功建立保留項目，就會顯示下列訊息。 **已成功新增 URL 保留**專案。
