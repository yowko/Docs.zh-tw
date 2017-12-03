---
title: "聯合與信任"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: federation [WCF], and trust
ms.assetid: 4bdec4f2-f8a2-4512-bdcf-14ef54b5877a
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a5228ffaab43e24849d461080cdf3ef09b2fa6c0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="federation-and-trust"></a>聯合與信任
本主題涵蓋與聯合應用程式、信任界限和組態，以及在 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 內使用發行權杖相關的各個層面。  
  
## <a name="services-security-token-services-and-trust"></a>服務、安全性權杖服務和信任  
 公開聯合端點的服務，通常會預期用戶端使用特定簽發者所提供的權杖進行驗證。 以正確的簽發者認證設定服務是很重要的，否則該服務將無法確認發行權杖上的簽章，而用戶端將無法與服務通訊。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]在服務上設定簽發者認證，請參閱[How to： 設定聯合服務的認證](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)。  
  
 同樣地，在使用對稱金鑰時，由於該金鑰會為目標服務而加密，因此您必須為目標服務以正確的憑證設定安全性權杖服務，否則將無法為目標服務加密金鑰，而因此用戶端將無法與服務通訊。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]服務使用的值<xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A>屬性[SecurityBindingElement](../../../../docs/framework/wcf/diagnostics/wmi/securitybindingelement.md)允許的時鐘誤差用戶端與服務之間。 在聯合中，`MaxClockSkew` 設定會從用戶端取得的發行權杖，套用至用戶端和安全性權杖服務間的時鐘誤差。 因此，在設定發行權杖的有效性和到期時間時，安全性權杖服務不需要設定時鐘誤差的上限。  
  
> [!NOTE]
>  時鐘誤差的重要性隨著發行權杖的存留時間縮短而增加。 在大多數的情況下，如果權杖的存留時間為 30 分鐘 (含) 以上，則時鐘誤差就不是個嚴重的問題。 存留時間較短或需要精確驗證權杖時間的案例中，則請務必在設計時考量到時鐘誤差的問題。  
  
## <a name="federated-endpoints-and-time-outs"></a>聯合端點和逾時  
 當用戶端與聯合端點通訊時，必須先從安全性權杖服務取得適當的權杖。 如果安全性權杖服務公開了一個聯合端點，則用戶端必須先從該端點的簽發者取得權杖。 每個權杖的擷取都需要時間，而這些時間會隨著傳送實際訊息至最終端點的整個逾時而變動。  
  
 例如，用戶端通道上的逾時設定為 30 秒。 此時需要呼叫兩個權杖簽發者，以便在傳送訊息至最終端點之前擷取權杖，而每次發行權杖的時間需要 15 秒。 在此例中，此嘗試將會失敗，並會擲回 <xref:System.TimeoutException>。 因此，您必須將用戶端通道上的 <xref:System.ServiceModel.IContextChannel.OperationTimeout%2A> 值，設定為足以擷取所有發行權杖所需的時間。 在沒有為 <xref:System.ServiceModel.IContextChannel.OperationTimeout%2A> 屬性指定值的情形下，需要將 <xref:System.ServiceModel.Channels.Binding.OpenTimeout%2A> 屬性或 <xref:System.ServiceModel.Channels.Binding.SendTimeout%2A> 屬性 (或兩者同時) 的值設定為足以擷取所有發行權杖所需的時間。  
  
## <a name="token-lifetime-and-renewal"></a>權杖存留時間和更新  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端不需要在對服務建立初始要求時檢查發行權杖。  更確切地說，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 信任安全性權杖服務會發行具有適當有效性和到期時間的權杖。 如果用戶端快取了權杖並重複使用，則會在隨後要求時檢查權杖存留時間，而用戶端則會視需要自動更新權杖。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]權杖快取，請參閱[How to： 建立聯合用戶端](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)。  
  
 為發行權杖或安全性內容權杖指定較短的存留期間 (以 30 秒或小於 30 秒為例) 可能會導致交涉逾時，或者會在要求發行權杖或者在交涉或更新安全性內容權杖時，由 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端擲回其他例狀況。  
  
## <a name="issued-tokens-and-inclusionmode"></a>發行的權杖和 InclusionMode  
 從用戶端傳送至聯合端點的訊息中，其發行的權杖是否已序列化是由設定 <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.InclusionMode%2A> 類別的 <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters> 屬性所控制。 這個屬性可以設定為 <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode> 列舉值的其中一個值，但是這在大部分的聯合案例中沒有作用。 `SecurityTokenInclusionMode.Never` 和 `SecurityTokenInclusionMode.AlwaysToInitiator` 值會使用戶端將權杖參考，傳送給安全性權杖服務所發行給信賴憑證者的權杖。 除非信賴憑證者持有發行權杖的複本，否則驗證將會因為無法解析權杖參考而失敗。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會將 `SecurityTokenInclusionMode.Once` 視同為 `SecurityTokenInclusionMode.AlwaysToRecipient`。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>  
 [如何： 建立聯合用戶端](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [如何： 設定聯合服務認證](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 [如何： 建立 WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
