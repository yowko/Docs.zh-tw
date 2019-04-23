---
title: 使用模擬搭配傳輸安全性
ms.date: 03/30/2017
ms.assetid: 426df8cb-6337-4262-b2c0-b96c2edf21a9
ms.openlocfilehash: 6209007b60effe5403caf3db8855f029d0c47a0e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59151433"
---
# <a name="using-impersonation-with-transport-security"></a>使用模擬搭配傳輸安全性
*模擬*是伺服器應用程式才會在用戶端的身分識別的能力。 對服務而言，驗證存取資源時使用模擬是很常見的。 伺服器應用程式使用服務帳戶執行，但是伺服器在接受用戶端連線會模擬用戶端，藉此使用用戶端的認證執行存取檢查。 傳輸安全性是一種用於傳遞認證與使用該認證保護通訊安全性的機制。 本主題描述使用傳輸安全性的設定，在 Windows Communication Foundation (WCF) 搭配模擬功能。 如需有關使用訊息安全性模擬的詳細資訊，請參閱[委派和模擬](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)。  
  
## <a name="five-impersonation-levels"></a>五個模擬等級  
 傳輸安全性運用如下表所述的五種模擬等級。  
  
|模擬等級|描述|  
|-------------------------|-----------------|  
|None|伺服器不嘗試模擬用戶端。|  
|匿名|伺服器應用程式可以根據用戶端的認證執行存取檢查，但不會接收任何有關用戶端身分識別的資訊。 模擬等級只對電腦上的通訊有意義，例如具名管道。 使用 `Anonymous` 搭配遠端連線將模擬等級提升至識別。|  
|識別|伺服器應用程式知道用戶端的身分，而且可以根據用戶端的認證執行存取驗證，但無法模擬用戶端。 識別是除非權杖提供者提供不同的模擬等級，WCF 中搭配 SSPI 認證使用的預設模擬等級。|  
|Impersonate|除了執行存取檢查外，伺服器應用程式可以存取做為用戶端的伺服器電腦上的資源。 伺服器應用程式無法使用用戶端識別存取遠端電腦上的資源，因為模擬的權杖沒有網路認證。|  
|Delegate - 委派|除了擁有與 `Impersonate` 相同的功能外，「委派」模擬等級也可以使用用戶端識別讓伺服器應用程式存取遠端電腦上的資訊，並且將識別傳遞到其他應用程式。<br /><br /> **重要**伺服器網域帳戶必須標示為受信任的網域控制站，才能使用這些額外的功能上的委派。 這個模擬等級無法搭配標示為敏感的用戶端網域帳戶使用。|  
  
 最常搭配傳輸安全性層級`Identify`和`Impersonate`。 不建議將 `None` 和 `Anonymous` 等級使用於一般用途，而且很多傳輸不支援使用這些等級進行驗證。 請小心使用 `Delegate` 等級的強大功能， 僅將委派憑證的使用權限提供給受信任的伺服器應用程式。  
  
 伺服器應用程式需要有 `Impersonate` 權限，才能在 `Delegate` 或 `SeImpersonatePrivilege` 等級使用模擬。 如果應用程式在管理員群組或有服務 SID (網路服務、本機服務或本機系統) 的帳戶上執行，該應用程式預設為擁有此權限。 伺服器不需要用戶端和伺服器的相互驗證。 有些支援模擬的驗證配置 (例如 NTLM) 無法搭配相互驗證使用。  
  
## <a name="transport-specific-issues-with-impersonation"></a>模擬的特定傳輸問題  
 在 WCF 中的傳輸選擇會影響模擬的可能選擇。 本章節描述的問題會影響標準 HTTP 與具名管道傳輸在 WCF 中。 自訂傳輸在支援模擬上有其限制。  
  
### <a name="named-pipe-transport"></a>具名管道傳輸  
 下列項目會與具名管道傳輸一併使用：  
  
-   命名管道傳輸僅供在本機電腦上使用。 在 WCF 中的具名的管道明確不允許跨電腦連接。  
  
-   具名管道無法搭配 `Impersonate` 或 `Delegate` 模擬等級使用。 具名管道無法在這些模擬等級強制執行電腦保證。  
  
 如需有關具名管道的詳細資訊，請參閱 <<c0> [ 選擇傳輸](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)。  
  
### <a name="http-transport"></a>HTTP 傳輸  
 使用 HTTP 傳輸的繫結 (<xref:System.ServiceModel.WSHttpBinding>並<xref:System.ServiceModel.BasicHttpBinding>) 中所述，支援數個驗證配置， [Understanding HTTP Authentication](../../../../docs/framework/wcf/feature-details/understanding-http-authentication.md)。 支援的模擬等級視驗證配置而定。 下列項目會與 HTTP 傳輸一併使用：  
  
-   `Anonymous` 驗證配置會忽略模擬。  
  
-   `Basic`驗證配置僅支援`Delegate`層級。 所有較低的模擬等級都會進行升級。  
  
-   `Digest` 驗證配置僅支援 `Impersonate` 和 `Delegate` 等級。  
  
-   可直接選擇或透過交涉選擇的 `NTLM` 驗證配置僅支援本機電腦上的 `Delegate` 等級。  
  
-   只能夠透過交涉選擇的 Kerberos 驗證配置可以搭配任何支援的模擬等級使用。  
  
 如需 HTTP 傳輸的詳細資訊，請參閱[選擇傳輸](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)。  
  
## <a name="see-also"></a>另請參閱

- [委派和模擬](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
- [授權](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)
- [如何：服務上模擬用戶端](../../../../docs/framework/wcf/how-to-impersonate-a-client-on-a-service.md)
- [了解 HTTP 驗證](../../../../docs/framework/wcf/feature-details/understanding-http-authentication.md)
