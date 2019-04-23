---
title: 竄改
ms.date: 03/30/2017
ms.assetid: 3bad93be-60bb-4f89-96ab-a1c3dc7c0fad
ms.openlocfilehash: 7a4265c30a6713f9557de2b3d1e99c87b7dd3e58
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59107883"
---
# <a name="tampering"></a>竄改
*竄改*是改變一則訊息或傳遞的訊息，以及用於不該適用於使用修改的訊息動作。  
  
## <a name="do-not-disable-ws-addressing"></a>請勿停用 WS-Addressing  
 WS-Addressing 規格會提供每個訊息的位址標頭，允許訊息收件者驗證訊息的寄件者。 您可以將 <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> 屬性設為 <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>，藉此停用這個功能。  
  
 當安全性模式設為「訊息」，而 WS-Addressing 停用時，攻擊者可能會從用戶端取得要求，然後傳送給另一項服務，使該服務無法偵測來自原始用戶端的訊息。 如此一來，第一項服務就可在與第二項服務交談時假裝為用戶端。  
  
 為減少這種情況發生，絕不要將 <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> 屬性設為 <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>，同時避免使用 <xref:System.ServiceModel.Channels.MessageVersion>，例如靜態 <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> 屬性，這類屬性會將 <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> 屬性設為 <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>。  
  
## <a name="see-also"></a>另請參閱

- [安全性考量](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)
- [資訊洩漏](../../../../docs/framework/wcf/feature-details/information-disclosure.md)
- [權限提高](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)
- [阻絕服務](../../../../docs/framework/wcf/feature-details/denial-of-service.md)
- [不支援的案例](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
- [重新執行攻擊](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
