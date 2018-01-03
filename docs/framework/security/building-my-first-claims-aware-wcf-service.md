---
title: "建置第一個宣告感知 WCF 服務"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e0e6d091-9a97-4888-8f2c-cbcee42d90ee
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: af39c3c5788db95eaee248ca8454534022cab659
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="building-my-first-claims-aware-wcf-service"></a>建置第一個宣告感知 WCF 服務
## <a name="applies-to"></a>適用於  
  
-   Windows Identity Foundation (WIF)  
  
-   Windows Communication Foundation (WCF)  
  
## <a name="overview"></a>概觀  
 本主題概述使用 WIF 建置宣告感知 WCF 服務的案例。 在一個宣告感知 Web 服務案例中，通常會有三個參與者：Web 服務本身、使用者和 Security Token Service (STS)。 下列圖將說明這個案例：  
  
 ![WIF 基本宣告感知 WCF 服務](../../../docs/framework/security/media/wifbasicclaimsawarewcfservice.gif "WIFBasicClaimsAwareWCFService")  
  
1.  WCF 服務用戶端 (有時稱為代理程式) 會使用 WIF 傳送認證至 STS，在驗證成功之後，STS 隨即發行權杖給代理程式。  
  
2.  代理程式隨即將 STS 發行的權杖傳送至 WCF 服務。  
  
3.  宣告感知 WCF 服務設定為信任 STS 和它發行的權杖。 宣告感知 WCF 服務會使用 WIF 驗證和剖析權杖。 開發人員可以使用適當的 WIF API 和類型 (例如 **ClaimsPrincipal**) 來滿足應用程式的需求 (例如為它實作授權)。  
  
 從 .NET 4.5 開始，WIF 是 .NET Framework 套件的一部分。 在架構中直接提供 WIF 類別可讓 .NET 中的宣告式身分識別的整合更加深入，讓您更容易使用宣告。 使用 WIF 4.5，您不必安裝任何超出範圍的元件就能開始開發宣告感知 Web 應用程式。 WIF 類別現在已廣泛存在於各種組件，主要的類別是 System.Security.Claims、System.IdentityModel 和 System.IdentityModel.Services。  
  
 STS 服務會在驗證成功後發行權杖。 Microsoft 提供兩項業界標準 STS：  
  
-   [Active Directory Federation Services (AD FS) 2.0](http://go.microsoft.com/fwlink/?LinkID=247516) (http://go.microsoft.com/fwlink/?LinkID=247516)  
  
-   [Windows Azure 存取控制服務 (ACS)](http://go.microsoft.com/fwlink/?LinkID=247517) (http://go.microsoft.com/fwlink/?LinkID=247517)。  
  
 AD FS 2.0 是 Windows Server R2 的一部分，可以當做供內部部署案例使用的 STS； Azure Active Directory 存取控制 (也稱為存取控制服務或 ACS) 是一項隨著 Microsoft Azure 提供的雲端服務。 此外，基於測試或教育目的，您也可以使用其他 STS 建立專屬宣告感知應用程式。 例如，您可以使用包含在 [Identity and Access Tool for Visual Studio](http://go.microsoft.com/fwlink/?LinkID=245849) (適用於 Visual Studio 的識別和存取工具) (http://go.microsoft.com/fwlink/?LinkID=245849) (可在線上免費取得) 中的本機開發 STS。  
  
 若要使用 WIF 建置您的第一個宣告感知 WCF 服務，請參閱[如何：使用 WIF 建置宣告感知 WCF 服務](http://msdn.microsoft.com/en-us/431e6415-62ed-4a9f-af03-f14d2b4dfe6d)。  
  
## <a name="see-also"></a>請參閱  
 [開始使用 WIF](../../../docs/framework/security/getting-started-with-wif.md)
