---
title: 服務稽核行為
ms.date: 03/30/2017
ms.assetid: 59bf0cda-e496-4418-a3a1-2f0f6e85f8ce
ms.openlocfilehash: ae7ed2059b491a71de9c806e78f1fb784da197fa
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262563"
---
# <a name="service-auditing-behavior"></a>服務稽核行為

這個範例會示範如何使用 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> 以啟用稽核服務作業期間的安全性事件。 這個範例是以 [消費者入門](getting-started-sample.md)為基礎。 服務和用戶端已使用進行設定 [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) 。 的 `mode` 屬性已 [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) 設定為 `Message` ，且已 `clientCredentialType` 設定為 `Windows` 。 在這個範例中，用戶端是主控台應用程式 (.exe)，而服務則是由網際網路資訊服務 (IIS) 所裝載。  
  
> [!NOTE]
> 此範例的安裝程序與建置指示位於本主題的結尾。  
  
 服務組態檔會使用 `serviceSecurityAudit` 項目設定稽核。  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      ...  
<!-- serviceSecurityAudit allows specification of audit location   
     and whether to audit success, failure or both. This service   
     logs success and failure of messageAuthentication   
     to the default location -->  
     <serviceSecurityAudit auditLogLocation ="Default" messageAuthenticationAuditLevel = "SuccessOrFailure" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。 在主控台視窗中按 ENTER 鍵，即可關閉用戶端。  
  
 執行事件檢視器可看到結果稽核記錄。 根據預設，在 Windows XP 中，您可以在應用程式記錄檔中查看稽核事件，而在 Windows Server 2003 和 Windows Vista 中，則可以在安全性記錄檔中查看稽核事件。 在 Windows Server 2008 和 Windows 7 上，您可以在應用程式記錄檔和服務記錄檔中查看稽核事件。 您可以藉由將屬性設定為「應用程式」或「安全性」來指定 audit 事件的位置 `auditLogLocation` 。 如需詳細資訊，請參閱 how [to： Audit Security Events](../feature-details/how-to-audit-wcf-security-events.md)。 如果事件是寫入安全性記錄檔中，則必須針對「成功」和「失敗」設定 LocalSecurityPolicy > 啟用物件存取。  
  
 在查看事件記錄檔時，稽核事件的來源為 "ServiceModel Audit 3.0.0.0"。 訊息驗證審核記錄的分類為 "MessageAuthentication"，而服務授權審核記錄的分類為 "ServiceAuthorization"。  
  
 訊息驗證稽核事件的涵蓋範圍包括訊息是否遭人竄改、訊息是否已過期，以及用戶端是否可驗證服務。 這些事件可提供驗證是否成功或失敗、以及用戶端的身分識别、訊息傳送的目的端點，以及與訊息關聯的動作等相關訊息。  
  
 服務授權稽核事件的涵蓋範圍則是服務授權管理員決定的授權。 這些事件提供的訊息是關於授權是否成功或失敗以及用戶端的身分識别、訊息傳送的目的端點、與訊息相關聯的動作、由傳入訊息產生的授權內容識別碼，以及做出存取決策的授權管理員類型。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1. 確定您已 [針對 Windows Communication Foundation 範例執行一次性安裝程式](one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2. 若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的指示。  
  
3. 若要在單一或跨電腦的設定中執行範例，請遵循執行 [Windows Communication Foundation 範例](running-the-samples.md)中的指示。  
  
## <a name="see-also"></a>另請參閱

- [稽核](../feature-details/auditing-security-events.md)
- [作法：稽核安全性事件](../feature-details/how-to-audit-wcf-security-events.md)
