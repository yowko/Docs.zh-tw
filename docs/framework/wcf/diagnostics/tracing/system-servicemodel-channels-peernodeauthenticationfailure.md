---
title: System.ServiceModel.Channels.PeerNodeAuthenticationFailure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b50f782-ca06-4a82-aa7f-71f78ddc5177
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 38abf80f81a8a885f719603bc93bf1b3687e9938
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="systemservicemodelchannelspeernodeauthenticationfailure"></a>System.ServiceModel.Channels.PeerNodeAuthenticationFailure
與未來芳鄰的安全性交換失敗。  
  
## <a name="description"></a>描述  
 在嘗試建立安全的芳鄰連線時，發生這個追蹤。 這可能是因為認證不足或不正確而導致。  
  
 PeerChannel 會辨認嚴密識別 (X.509 憑證) 的單一權杖類型，它會根據能夠實作的驗證與授權類型，提供嚴密的識別模型。 PeerChannel 也會透過使用密碼的方式提供簡單應用程式的支援。 密碼只能用來允許進入工作階段；而不能用來執行訊息驗證。 這是因為對等群組共享的對稱式權杖，如果使用在來源驗證方面會發生困難而且不適當。  
  
## <a name="troubleshooting"></a>疑難排解  
 請確認所有芳鄰都有適當的安全性認證。  
  
## <a name="see-also"></a>另請參閱  
 [對等通道安全性](../../../../../docs/framework/wcf/feature-details/peer-channel-security.md)  
 [追蹤](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [使用追蹤來疑難排解您的應用程式](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [管理與診斷](../../../../../docs/framework/wcf/diagnostics/index.md)
