---
title: System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
ms.date: 03/30/2017
ms.assetid: d75d39da-7502-4a6a-91b9-eaa05b8e24d5
ms.openlocfilehash: 0a28eec659b48d5add4c53bc8c16972892e65099
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="systemservicemodelchannelsmsmqmoveordeleteattemptfailed"></a>System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
無法移動或刪除訊息。  
  
## <a name="description"></a>描述  
 此追蹤表示嘗試移動、刪除或拒絕 MSMQ 訊息時，發生錯誤。  
  
 MSMQ 訊息被採用由 Windows Communication Foundation (WCF) （與 NetMsmqBinding 或 msmqintegrationbinding 配合使用） 時。這個追蹤所選擇的值與相關`ReceiveErrorHandling`NetMsmqBinding 或 MsmqIntegrationBinding 上的屬性。  
  
 此追蹤不代表整體系統失敗。 但是，它代表某個訊息的選定有害訊息處置作業失敗。 請參閱[有害訊息處理](http://go.microsoft.com/fwlink/?LinkID=99546)如需詳細資訊訊息何時變為有害，以及設定您的服務來適當處理這些。  
  
## <a name="see-also"></a>另請參閱  
 [追蹤](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [使用追蹤為應用程式進行疑難排解](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [管理與診斷](../../../../../docs/framework/wcf/diagnostics/index.md)
