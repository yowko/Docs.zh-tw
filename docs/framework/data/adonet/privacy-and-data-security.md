---
title: 隱私權和資料安全性
ms.date: 03/30/2017
ms.assetid: 46fa5839-adf7-4c7c-bce3-71e941fa7de9
ms.openlocfilehash: dd74abcd95faf27485efcefa1a0a76e830df60fe
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43508860"
---
# <a name="privacy-and-data-security"></a>隱私權和資料安全性
如何保護及管理 ADO.NET 應用程式中的機密資訊，是依據建立資訊時所使用的基礎產品及技術而定。 ADO.NET 並未直接針對資料的保護或加密提供服務。  
  
## <a name="cryptography-and-hash-codes"></a>加密和雜湊程式碼  
 您可以從 ADO.NET 應用程式使用 .NET Framework <xref:System.Security.Cryptography> 命名空間 (Namespace) 中的類別 (Class)，以防止未獲授權的第三方讀取或修改資料。 某些類別是 Unmanaged Microsoft CryptoAPI 的包裝函式，某些則是 Managed 實作 (Implementation)。 [Signature is Valid](https://msdn.microsoft.com/library/68a1e844-c63c-44af-9247-f6716eb23781)主題提供.NET Framework 中的密碼編譯概觀，說明如何實作密碼編譯，以及如何執行特定的密碼編譯工作。  
  
 加密可進行先加密再解密資料；而雜湊資料則是單向的處理序。 當您想要檢查資料未經改變，以防止他人篡改資料時，雜湊資料很有用：提供相同的輸入字串，雜湊演算法一定可以產生相同且簡短的輸出值，讓您輕鬆進行比較。 [使用雜湊程式碼確定資料完整性](../../../../docs/standard/security/ensuring-data-integrity-with-hash-codes.md)說明如何產生及驗證雜湊值。  
  
## <a name="encrypting-configuration-files"></a>加密組態檔  
 保護應用程式時的最重要目標之一就是保護資料來源的存取。 連接字串如果沒有受到保護，就可能造成安全性漏洞。 儲存在組態檔中的連接字串會儲存在標準的 XML 檔案中，.NET Framework 已為其定義了共用元素組。 受保護的組態可用於加密組態檔中的機密資訊。 雖然主要是針對 ASP.NET 應用程式所設計，但這項功能仍可用來加密 Windows 應用程式中的組態檔區段。 如需詳細資訊，請參閱[保護連線資訊](../../../../docs/framework/data/adonet/protecting-connection-information.md)。  
  
## <a name="securing-string-values-in-memory"></a>保護記憶體中的字串值  
 如果 <xref:System.String> 物件包含密碼、信用卡號或個人資料等機密資訊，則這些資訊有可能會在使用後洩漏，因為應用程式無法從電腦記憶體刪除這些資料。  
  
 <xref:System.String> 是不可變的；它的值一旦建立就無法修改。 看似修改字串值的變更，實際上是在記憶體中建立 <xref:System.String> 物件的新執行個體 (Instance) 並以純文字儲存資料。 此外也無法預測這些執行個體何時會從記憶體刪除。 字串的記憶體回收，是無法用 .NET 記憶體回收決定的。 如果資料真的十分機密，您應該避免使用 <xref:System.String> 和 <xref:System.Text.StringBuilder> 類別。  
  
 <xref:System.Security.SecureString> 類別提供加密文字的方法，可用於在記憶體中使用「資料保護 API」(DPAPI) 加密文字。 之後在不再需要字串時，就可以將它從記憶體刪除。 沒有可用於快速讀取 `ToString` 內容的 <xref:System.Security.SecureString> 方法。 您可以不使用任何值來初始化 `SecureString` 的新執行個體，或者將 <xref:System.Char> 物件陣列的指標傳送給該項目來進行初始化。 之後就可以使用該類別的各種方法來使用字串。 如需詳細資訊，請下載[SecureString 範例應用程式](https://go.microsoft.com/fwlink/?LinkId=120418)，其中示範如何使用`SecureString`類別。  
  
## <a name="see-also"></a>另請參閱  
 [設定 ADO.NET 應用程式的安全性](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [SQL Server 安全性](../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
