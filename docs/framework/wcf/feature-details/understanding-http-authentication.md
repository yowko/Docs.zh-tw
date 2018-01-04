---
title: "了解 HTTP 驗證"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9376309a-39e3-4819-b47b-a73982b57620
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 32d7df95c6acbe34a677cbd2951fd912466d015f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="understanding-http-authentication"></a>了解 HTTP 驗證
驗證是一種識別用戶端是否具備存取資源之資格的程序。 HTTP 通訊協定支援驗證作為存取安全資源的交涉方法。  
  
 用戶端的初始要求一般為匿名要求，不包含任何驗證資訊。 HTTP 伺服器應用程式可拒絕匿名要求，同時表示驗證是必要的。 伺服器應用程式會傳送 WWW-Authentication 標頭，表示支援的驗證配置。 這份文件描述 HTTP 的數種驗證配置，並在 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]中討論這些配置的支援。  
  
## <a name="http-authentication-schemes"></a>HTTP 驗證配置  
 伺服器可以指定多個用戶端從選擇的驗證配置。 下表描述一些常見的 Windows 應用程式的驗證配置。  
  
|驗證配置|描述|  
|---------------------------|-----------------|  
|匿名|匿名要求不包含任何驗證資訊。 這樣相當於授與所有人資源存取權。|  
|基本|基本驗證會為用戶端傳送包含使用者名稱和密碼的 Base64 編碼字串。 Base64 不是一種加密形式，這種方法所傳送的使用者名稱與密碼應視同為明文形式。 若需要保護資源，強烈建議考慮使用驗證配置而非基本驗證。|  
|摘要|摘要驗證是設計來取代基本驗證的挑戰/回應配置。 伺服器會傳送一串隨機資料稱為*nonce*至用戶端作為挑戰。 用戶端會回應包含使用者名稱、密碼與 Nonce 及其他資訊的雜湊。 使用這種驗證配置的交換所帶來的複雜性與資料雜湊，讓竊取與再利用使用者的認證更加困難。<br /><br /> 摘要驗證需要使用 Windows 網域帳號。 摘要*領域*是 Windows 網域名稱。 因此，您無法使用，不支援 Windows 網域，例如 Windows XP Home Edition、 摘要式驗證的作業系統上執行的伺服器。 相反地，當用戶端在不支援 Windows 網域的作業系統上執行，驗證期間必須特別指定網域帳號。|  
|NTLM|NT LAN Manager (NTLM) 驗證為摘要式驗證更安全的變異，是一種挑戰/回應配置。 NTLM 使用 Windows 認證轉換挑戰資料，而非未編碼的使用者名稱與密碼。 NTLM 驗證需要在用戶端與服務器之間進行多次交換。 伺服器與任何介入的 Proxy 必須支援持續性連線以成功完成驗證。|  
|交涉|交涉驗證會自動在 Kerberos 通訊協定與 NTLM 驗證之間選擇，依可用性而定。 如果 Kerberos 通訊協定可以使用，就選擇它；否則就會嘗試使用 NTLM。 Kerberos 驗證較 NTLM 更大幅改善。 Kerberos 驗證不僅較 NTLM 更快，而且允許使用交互驗證和對遠端機器認證的委派。|  
|Windows Live ID|基礎的 Windows HTTP 服務包括使用聯合通訊協定的驗證。 然而，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中的標準 HTTP 傳輸不支援使用同盟驗證配置，例如 Microsoft Windows Live ID。 目前可透過訊息安全性提供對此功能的支援。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][同盟與發行的權杖](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)。|  
  
## <a name="choosing-an-authentication-scheme"></a>選擇驗證配置  
 為 HTTP 伺服器選擇潛在驗證配置時，必須考量一些項目，包括：  
  
-   考量資源是否需要保護。 使用 HTTP 驗證需要傳輸更多資料，並且可限制與用戶端的互通性。 允許匿名存取不需要保護的資源。  
  
-   如果資源需要保護，則考慮何種驗證配置提供所需的安全性等級。 這裡所討論的驗證配置，最低標準是基礎驗證。 基礎驗證不會保護使用者的認證資訊。 最高標準驗證配置為交涉驗證，也就是 Kerberos 通訊協定。  
  
-   伺服器不應存在任何 (以 WWW-Authentication 標頭表示) 不預備接受或未能提供保護資源適當安全的配置。 用戶端可自行選擇任何伺服器提供的驗證配置。 有些用戶端預設選擇最薄弱的驗證配置，或是伺服器清單中第一項驗證配置。  
  
## <a name="see-also"></a>請參閱  
 [傳輸安全性概觀](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)  
 [使用模擬搭配傳輸安全性](../../../../docs/framework/wcf/feature-details/using-impersonation-with-transport-security.md)  
 [委派和模擬](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
