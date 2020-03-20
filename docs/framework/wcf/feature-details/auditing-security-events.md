---
title: 稽核安全性事件
ms.date: 03/30/2017
helpviewer_keywords:
- auditing security events [WCF]
ms.assetid: 5633f61c-a3c9-40dd-8070-1c373b66a716
ms.openlocfilehash: 535f19741ff26e9472ce56ff06b670f7d0523be8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185460"
---
# <a name="auditing-security-events"></a>稽核安全性事件
使用 Windows 通信基礎 （WCF） 創建的應用程式可以使用審核功能記錄安全事件（成功、失敗或兩者）。 事件會寫入至 Windows 系統事件記錄檔，並且可以使用 [事件檢視器] 加以檢查。  
  
 稽核為系統管理員提供了一種方法，可偵測已發生或正在進行的攻擊。 此外，稽核可以協助開發人員偵錯安全性相關的問題。 例如，若授權的組態中出現錯誤，或是在檢查原則時不小心拒絕了某個授權使用者的存取，則開發人員可以藉由檢查事件日誌，快速地探索及隔離導致這個錯誤的原因。  
  
 有關 WCF 安全性的詳細資訊，請參閱[安全概述](../../../../docs/framework/wcf/feature-details/security-overview.md)。 有關程式設計 WCF 的詳細資訊，請參閱[基本 WCF 程式設計](../../../../docs/framework/wcf/basic-wcf-programming.md)。  
  
## <a name="audit-level-and-behavior"></a>稽核層級和行為  
 安全性稽核目前有兩種層級：  
  
- 服務授權層級，其中呼叫者已獲得授權。  
  
- 消息級別，其中 WCF 檢查消息有效性並驗證調用方。  
  
 可以檢查兩個審核級別的成功或失敗，這稱為*審核行為*。  
  
## <a name="audit-log-location"></a>稽核記錄檔的位置  
 決定稽核層級和行為後，您 (或系統管理員) 就可以指定稽核記錄檔的位置。 您有三種選擇，包括：預設、應用程式和安全性。 指定為 [預設] 時，實際的記錄檔取決於您所使用的系統，以及該系統是否支援寫入至安全性記錄檔。 有關詳細資訊，請參閱本主題後面的"作業系統"部分。  
  
 若要寫入安全性記錄檔，您必須具備 `SeAuditPrivilege`。 根據預設，只有本機系統帳戶和網路服務帳戶具有此權限。 若要管理安全性記錄函式 `read` 和 `delete`，您必須具備 `SeSecurityPrivilege`。 根據預設，只有系統管理員具有此權限。  
  
 相反地，通過驗證的使用者可以讀取及寫入應用程式記錄檔。 預設情況下，Windows XP 將審核事件寫入應用程式日誌。 記錄檔也可以包含個人資訊，所有通過驗證的使用者都可以檢視這些資訊。  
  
## <a name="suppressing-audit-failures"></a>隱藏稽核失敗  
 稽核期間可以使用的另一個選項為是否要隱藏任何稽核失敗。 根據預設，稽核失敗不會影響到應用程式。 不過，如果需要的話，您可以將選項設定為 `false`，如此便會擲回例外狀況。  
  
## <a name="programming-auditing"></a>程式設計稽核  
 您可以使用程式設計的方式或透過組態的方式指定稽核行為。  
  
### <a name="auditing-classes"></a>稽核類別  
 下表描述用來程式設計稽核行為的類別和屬性。  
  
|類別|描述|  
|-----------|-----------------|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>|將稽核的設定選項啟用為服務行為。|  
|<xref:System.ServiceModel.AuditLogLocation>|用於指定寫入哪個記錄檔的列舉。 可能的值為 [預設]、[應用程式] 和 [安全性]。 當您選取 [預設] 時，作業系統會判斷實際的記錄檔位置。 如需詳細資訊，請參閱本主題稍後「應用程式或安全性事件記錄檔選擇」一節的說明。|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A>|指定要在訊息層級上稽核哪種訊息驗證事件的類型。 這些選擇有 `None`、`Failure`、`Success` 和 `SuccessOrFailure`。|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A>|指定要在服務層級上稽核哪種服務授權事件的類型。 這些選擇有 `None`、`Failure`、`Success` 和 `SuccessOrFailure`。|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A>|指定當稽核失敗時，用戶端要求會產生什麼變化。 例如，當服務嘗試寫入安全性記錄檔，但不具有 `SeAuditPrivilege` 時。 `true` 的預設值表示忽略該失敗，並且正常處理用戶端要求。|  
  
 有關設置應用程式以記錄審核事件的示例，請參閱[如何：審核安全事件](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md)。  
  
### <a name="configuration"></a>組態  
 您還可以使用配置來指定審核行為，通過在[\<行為>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)下添加[\<服務安全審核>。](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) 必須在[\<行為>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)下添加元素，如以下代碼所示。  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <behavior>  
        <!-- auditLogLocation="Application" or "Security" -->  
        <serviceSecurityAudit  
                  auditLogLocation="Application"  
                  suppressAuditFailure="true"  
                  serviceAuthorizationAuditLevel="Failure"  
                  messageAuthenticationAuditLevel="SuccessOrFailure" />
      </behavior>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 如果已啟用稽核，但未指定 `auditLogLocation`，則支援寫入至安全性記錄檔的平台會使用的預設記錄名稱為「安全性」記錄檔，否則便是「應用程式」記錄檔。 只有 Windows 伺服器 2003 和 Windows Vista 作業系統支援寫入安全性記錄檔。 有關詳細資訊，請參閱本主題後面的"作業系統"部分。  
  
## <a name="security-considerations"></a>安全性考量  
 如果惡意使用者得知已啟用稽核，攻擊者就可以傳送無效的訊息，而造成寫入稽核項目。 如果是因為這個方法而填滿稽核記錄檔，稽核系統就會失敗。 若要減輕這個威脅，請將 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> 屬性設定為 `true`，並使用 [事件檢視器] 的屬性來控制稽核行為。  
  
 寫入 Windows XP 上的應用程式日誌的審核事件對於任何經過身份驗證的使用者都可見。  
  
## <a name="choosing-between-application-and-security-event-logs"></a>在應用程式和安全性事件記錄檔之間選擇  
 下表提供可協助您選擇要記錄至應用程式或安全性事件記錄檔的詳細資訊。  
  
#### <a name="operating-system"></a>作業系統  
  
|系統|應用程式記錄|安全性記錄檔|  
|------------|---------------------|------------------|  
|Windows XP SP2 或更高版本|支援|不支援|  
|Windows 伺服器 2003 SP1 和 Windows Vista|支援|執行緒內容必須擁有 `SeAuditPrivilege`|  
  
#### <a name="other-factors"></a>其他因素  
 除了作業系統之外，下表描述其他控制記錄啟用的設定。  
  
|因數|應用程式記錄|安全性記錄檔|  
|------------|---------------------|------------------|  
|稽核原則管理|不適用。|安全性記錄檔也可以藉由本機安全性授權 (LSA) 原則與組態來加以控制。 您也必須啟用 [稽核物件存取] 類別。|  
|預設的使用者經驗|所有通過驗證的使用者都可以寫入應用程式記錄檔，因此不需要為應用程式處理序額外執行設定權限的步驟。|應用程式處理序 (內容) 必須具有 `SeAuditPrivilege`。|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
- <xref:System.ServiceModel.AuditLogLocation>
- [安全概述](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [基本 WCF 程式設計](../../../../docs/framework/wcf/basic-wcf-programming.md)
- [HOW TO：稽核安全性事件](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md)
- [\<服務安全審核>](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md)
- [\<行為>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)
- [Windows Server AppFabric 的資訊安全模型](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
