---
title: 竄改
ms.date: 03/30/2017
ms.assetid: 3bad93be-60bb-4f89-96ab-a1c3dc7c0fad
ms.openlocfilehash: e618ab369a46d403aa8db26c4b472e2be3634785
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600707"
---
# <a name="tampering"></a>竄改
「*篡改*」是改變訊息的動作，或是訊息的傳遞，並使用修改過的訊息，做為其用途以外的目的。  
  
## <a name="do-not-disable-ws-addressing"></a>請勿停用 WS-Addressing  
 WS-Addressing 規格會提供每個訊息的位址標頭，允許訊息收件者驗證訊息的寄件者。 您可以將 <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> 屬性設為 <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>，藉此停用這個功能。  
  
 當安全性模式設為「訊息」，而 WS-Addressing 停用時，攻擊者可能會從用戶端取得要求，然後傳送給另一項服務，使該服務無法偵測來自原始用戶端的訊息。 如此一來，第一項服務就可在與第二項服務交談時假裝為用戶端。  
  
 為減少這種情況發生，絕不要將 <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> 屬性設為 <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>，同時避免使用 <xref:System.ServiceModel.Channels.MessageVersion>，例如靜態 <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> 屬性，這類屬性會將 <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> 屬性設為 <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>。  
  
## <a name="see-also"></a>請參閱

- [安全性考量](security-considerations-in-wcf.md)
- [資訊洩漏](information-disclosure.md)
- [權限提高](elevation-of-privilege.md)
- [拒絕服務](denial-of-service.md)
- [不支援的案例](unsupported-scenarios.md)
- [重新執行攻擊](replay-attacks.md)
