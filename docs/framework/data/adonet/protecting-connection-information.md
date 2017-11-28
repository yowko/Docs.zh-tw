---
title: "保護連接資訊"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1471f580-bcd4-4046-bdaf-d2541ecda2f4
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 31196697a606b3edbc0b3aa00b01e5eacb66cb03
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="protecting-connection-information"></a>保護連接資訊
保護應用程式時的最重要目標之一就是保護資料來源的存取。 連接字串如果沒有受到保護，就可能造成安全性漏洞。 以純文字儲存連接資訊，或在記憶體中保存連接資訊，都會危及整個系統的安全性。 連接字串內嵌在您的程式碼可以使用讀取[Ildasm.exe （IL 解譯器）](../../../../docs/framework/tools/ildasm-exe-il-disassembler.md)若要檢視已編譯的組件中的 Microsoft intermediate language (MSIL)。  
  
 涉及連接字串的安全性漏洞，可能會根據使用的驗證類型、連接字串在記憶體及磁碟中的保存方式，以及在執行階段用來建構連接字串的技巧而引發。  
  
## <a name="use-windows-authentication"></a>使用 Windows 驗證。  
 為了限制他人存取您的資料來源，您必須保護連線資訊，例如使用者 ID、密碼和資料來源名稱。 為了避免公開使用者資訊，我們建議使用 Windows 驗證 (有時稱為*整合式安全性*) 可能的情況下。 Windows 驗證是藉由 `Integrated Security` 或 `Trusted_Connection` 關鍵字指定於連接字串中，可免除使用使用者 ID 和密碼的需要。 在使用 Windows 驗證時，使用者會由 Windows 進行驗證，而對伺服器和資料庫資源的存取權則是藉由授權給 Windows 使用者和群組來決定。  
  
 在無法使用 WIndows 驗證時必須特別小心，因為使用者認證會在連接字串中公開。 在 ASP.NET 應用程式中，可以將 Windows 帳戶設定為用於連接到資料庫和其他網路資源的固定識別 (Identity)。 啟用中的身分識別元素的模擬**web.config**檔案，並指定使用者名稱和密碼。  
  
```xml  
<identity impersonate="true"   
        userName="MyDomain\UserAccount"   
        password="*****" />  
```  
  
 固定識別帳戶應該是低權限的帳戶，僅為其授與資料庫中的必要權限。 此外，您也應該將組態檔加密，讓使用者名稱和密碼不至於以純文字方式公開。  
  
## <a name="do-not-use-universal-data-link-udl-files"></a>不使用通用資料連結 (UDL) 檔  
 請避免將 <xref:System.Data.OleDb.OleDbConnection> 的連接字串儲存於「通用資料連結」(UDL) 檔案中。 UDL 會以純文字方式儲存且無法加密。 UDL 檔案是應用程式外部的檔案型資源，無法使用 .NET Framework 進行保護或加密。  
  
## <a name="avoid-injection-attacks-with-connection-string-builders"></a>使用連接字串產生器來避免插入式攻擊  
 當使用動態字串串連來根據使用者輸入建立連接字串時，就可能發生連接字串插入式攻擊。 如果使用者輸入未經驗證且未逸出惡意的文字或字元，攻擊者就可能得以存取伺服器上的機密資料或其他資源。 為了解決此問題，ADO.NET 2.0 導入了新的連接字串產生器 (Builder) 類別 (Class)，可用於驗證連接字串語法，並確保沒有導入其他的參數。 如需詳細資訊，請參閱[連接字串產生器](../../../../docs/framework/data/adonet/connection-string-builders.md)。  
  
## <a name="use-persist-security-infofalse"></a>使用 Persist Security Info=False  
 `Persist Security Info` 的預設值為 False；建議您在所有連接字串中都使用此預設值。 如果將 `Persist Security Info` 設定為 `true` 或 `yes`，則在開啟連接後，可透過連接取得安全機密資訊，包括使用者 ID 和密碼。 當 `Persist Security Info` 是設定為 `false` 或 `no` 時，安全性資訊會在用來開啟連接之後捨棄，以確保未受信任的來源無法存取安全機密資訊。  
  
## <a name="encrypt-configuration-files"></a>加密組態檔  
 連接字串也可以儲存在組態檔案中，這麼做可免除將連接字串嵌入應用程式程式碼的需要。 組態檔是標準的 XML 檔案，.NET Framework 已為其定義了共用元素組。 在組態檔中的連接字串通常會儲存在 **\<connectionStrings >**中的項目**app.config** Windows 應用程式，或**web.config** ASP.NET 應用程式檔案。 如需的基本概念的儲存，擷取和加密的連接字串從組態檔，請參閱[連接字串和組態檔](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md)。  
  
## <a name="see-also"></a>另請參閱  
 [設定 ADO.NET 應用程式的安全性](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [使用受保護的組態加密組態資訊](http://msdn.microsoft.com/library/51cdfe5b-9d82-458c-94ff-c551c4f38ed1)  
 [PAVE 機器碼和 .NET Framework 程式碼中的安全性](http://msdn.microsoft.com/en-us/bd61be84-c143-409a-a75a-44253724f784)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)
