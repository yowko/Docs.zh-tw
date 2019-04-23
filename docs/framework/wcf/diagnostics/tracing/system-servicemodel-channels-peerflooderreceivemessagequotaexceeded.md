---
title: System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded
ms.date: 03/30/2017
ms.assetid: b8371d0a-843e-440b-b86a-6996db131cb0
ms.openlocfilehash: 0ca3d198ce225221348ac7b405ea91ad215cd298
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59190895"
---
# <a name="systemservicemodelchannelspeerflooderreceivemessagequotaexceeded"></a>System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded
訊息的傳入接收速率太高。  
  
## <a name="description"></a>描述  
 這個追蹤會發生在嘗試處理傳入訊息時。 訊息無法轉送到特定的芳鄰，因為已超過該芳鄰的配額設定。 這發生在沒有回應的芳鄰無法清除該芳鄰之擱置訊息的待辦項目。  
  
## <a name="troubleshooting"></a>疑難排解  
 降低訊息在 mesh 內傳送的速率。  
  
## <a name="see-also"></a>另請參閱

- [追蹤](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [使用追蹤為應用程式進行疑難排解](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [管理與診斷](../../../../../docs/framework/wcf/diagnostics/index.md)
