---
title: "WCF 的驗證"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- authentication [WCF]
- security [WCF], authentication
ms.assetid: 9254d873-843d-4c6e-bea4-8184ac3e44f4
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 432ed9debeffad82125b567508ed46b46d4b8821
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="authentication-in-wcf"></a>WCF 的驗證
下列主題說明 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 中提供驗證的各種不同機制，例如，Windows 驗證、X.509 憑證以及使用者名稱與密碼。  
  
## <a name="in-this-section"></a>本節內容  
 [如何：使用 ASP.NET 成員資格提供者](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)  
 ASP.NET 功能包括成員資格及角色提供者、用來儲存驗證時比對的使用者名稱/密碼組合之資料庫，以及供授權的使用者角色。 這個主題會說明 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務如何能使用相同的資料庫對使用者驗證與授權。  
  
 [如何：使用自訂使用者名稱與密碼驗證程式](../../../../docs/framework/wcf/feature-details/how-to-use-a-custom-user-name-and-password-validator.md)  
 示範如何整合自訂使用者名稱與密碼驗證程式。  
  
 [服務身分識別和驗證](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 作為額外的保護，用戶端可以藉由指定預期的驗證服務*識別*的服務。 若預期識別與服務傳回的識別不符，則驗證失敗。  
  
 [安全性交涉與逾時](../../../../docs/framework/wcf/feature-details/security-negotiation-and-timeouts.md)  
 說明如何使用 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> 類別中的 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> 屬性。  
  
 [偵錯 Windows 驗證錯誤](../../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md)  
 焦點放在使用 Windows 驗證時，經常遇見的問題。  
  
## <a name="reference"></a>參考資料  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a>相關章節  
 [常見的安全性案例](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
  
## <a name="see-also"></a>請參閱  
 [安全性概觀](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Windows Server App Fabric 的安全性模型](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
