---
title: WIF API 參考
ms.date: 03/30/2017
ms.assetid: a027d902-9314-4bfd-b172-4e81847b1d68
author: BrucePerlerMS
ms.openlocfilehash: 21b294a58efcad6c3eb7c74e643a2ac3e0ea23fd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54663592"
---
# <a name="wif-api-reference"></a>WIF API 參考
Windows Identity Foundation (WIF) 類別會分成下列組件：`mscorlib` (mscorlib.dll)、`System.IdentityModel` (System.IdentityModel.dll)、`System.IdentityModel.Services` (System.IdentityModel.Services.dll) 和 `System.ServiceModel` (System.ServiceModel.dll)。 本主題提供 WIF 命名空間的連結，以及每個命名空間所包含類別的簡短說明。  
  
> [!IMPORTANT]
>  下列 `System.IdentityModel` 命名空間包含的類別可實作 WCF 宣告式身分識別模型：<xref:System.IdentityModel.Claims?displayProperty=nameWithType>、<xref:System.IdentityModel.Policy?displayProperty=nameWithType> 和 <xref:System.IdentityModel.Selectors?displayProperty=nameWithType>。 從 .NET Framework 4.5 開始，WIF 已取代 WCF 宣告式身分識別模型。 在建置以 WIF 為基礎的方案時，您不應該使用這三個命名空間中的類別。  
  
 <xref:System.IdentityModel?displayProperty=nameWithType>  
 包含的類別代表 Cookie 轉換、安全性權杖服務，以及特定的 XML 字典讀取器。  
  
 <xref:System.IdentityModel.Configuration?displayProperty=nameWithType>  
 包含的類別可為使用 Windows Identity Foundation (WIF) 建置的應用程式和服務提供組態。 此命名空間中的類別代表 [\<identityConfiguration>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) 元素下的設定。  
  
 <xref:System.IdentityModel.Metadata?displayProperty=nameWithType>  
 包含的類別代表同盟中繼資料文件中的元素。  
  
 <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType>  
 包含的類別代表 WS-Trust 成品。  
  
 <xref:System.IdentityModel.Services?displayProperty=nameWithType>  
 包含的類別用於被動 (WS-同盟) 情節。 也包含一些代表 [\<system.identityModel.services>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) 元素下設定的類別。 此元素下的設定可用來設定應用程式的 WS-同盟。 `System.IdentityModel.Services.Configuration` 命名空間包含大部分用來設定 WS-同盟的類別。  
  
 <xref:System.IdentityModel.Services.Configuration?displayProperty=nameWithType>  
 包含的類別可為使用 WS-同盟通訊協定的 WIF 應用程式提供組態。 此命名空間中的類別代表 [\<system.identityModel.services>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) 元素下的設定。 `System.IdentityModel.Services` 命名空間也包含一些用來設定 WS-同盟的類別。  
  
 <xref:System.IdentityModel.Services.Tokens?displayProperty=nameWithType>  
 包含適用於 Web 伺服陣列情節的特定安全性權杖處理常式。  
  
 <xref:System.IdentityModel.Tokens?displayProperty=nameWithType>  
 包含的類別代表安全性權杖、安全性權杖處理常式，以及其他安全性權杖成品。  
  
 <xref:System.Security.Claims?displayProperty=nameWithType>  
 包含的類別代表宣告、宣告式身分識別、宣告式主體，以及其他宣告式身分識別模型成品。  
  
 <xref:System.ServiceModel.Security?displayProperty=nameWithType>  
 包含的類別代表 WCF 合約、通道、服務主機，以及主動 (WS-Trust) 情節中使用的其他成品。 此命名空間也包含專屬於 Windows Communication Foundation (WCF) 而不會由 WIF 使用的類別。  
  
## <a name="see-also"></a>另請參閱
- [WIF 組態參考](../../../docs/framework/security/wif-configuration-reference.md)
- [WIF 3.5 和 WIF 4.5 之間的命名空間對應](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md)
