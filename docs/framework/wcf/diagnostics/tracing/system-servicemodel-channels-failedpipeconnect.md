---
title: System.ServiceModel.Channels.FailedPipeConnect
ms.date: 03/30/2017
ms.assetid: 9a827e0f-fb91-46bb-bd54-926d4b74d8a6
ms.openlocfilehash: 790a15e5401850f2767cb06f5f321ad80c674f2b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84582409"
---
# <a name="systemservicemodelchannelsfailedpipeconnect"></a>System.ServiceModel.Channels.FailedPipeConnect
嘗試連接具名管道端點失敗。 在指定的逾時期間內，進行另一次嘗試。  
  
## <a name="description"></a>描述  
 這個告知性追蹤表示無法連接到具名通道端點。 如果具名通道端點找不到或忙碌中，可能就會發生這個問題。 進行額外的嘗試，每個嘗試之間相隔短暫的時間，直到成功或 OpenTimeout 到期為止。  
  
## <a name="see-also"></a>請參閱

- [追蹤](index.md)
- [使用追蹤來疑難排解應用程式](using-tracing-to-troubleshoot-your-application.md)
- [系統管理與診斷](../index.md)
