---
title: 竄改
ms.date: 03/30/2017
ms.assetid: 3bad93be-60bb-4f89-96ab-a1c3dc7c0fad
ms.openlocfilehash: c2b0cae1dc57fac486122ca17fc8109ffe62f77d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96249796"
---
# <a name="tampering"></a>竄改

*篡改* 是指改變訊息、傳送訊息，以及使用改變的訊息，而不是它所用的用途。  
  
## <a name="do-not-disable-ws-addressing"></a>請勿停用 WS-Addressing  

 WS-Addressing 規格會提供每個訊息的位址標頭，允許訊息收件者驗證訊息的寄件者。 您可以將 <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> 屬性設為 <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>，藉此停用這個功能。  
  
 當安全性模式設為「訊息」，而 WS-Addressing 停用時，攻擊者可能會從用戶端取得要求，然後傳送給另一項服務，使該服務無法偵測來自原始用戶端的訊息。 如此一來，第一項服務就可在與第二項服務交談時假裝為用戶端。  
  
 為減少這種情況發生，絕不要將 <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> 屬性設為 <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>，同時避免使用 <xref:System.ServiceModel.Channels.MessageVersion>，例如靜態 <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> 屬性，這類屬性會將 <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> 屬性設為 <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>。  
  
## <a name="see-also"></a>另請參閱

- [安全性考量](security-considerations-in-wcf.md)
- [洩露資訊](information-disclosure.md)
- [提高權限](elevation-of-privilege.md)
- [拒絕服務](denial-of-service.md)
- [不支援的案例](unsupported-scenarios.md)
- [重新執行攻擊](replay-attacks.md)
