---
title: System.ServiceModel.Channels.PeerMaintainerActivity
ms.date: 03/30/2017
ms.assetid: ef28d086-d7fb-4e81-82e9-45a54647783b
ms.openlocfilehash: c1e82611bb776531ad3e3d60283d970602eb7f15
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96293022"
---
# <a name="systemservicemodelchannelspeermaintaineractivity"></a>System.ServiceModel.Channels.PeerMaintainerActivity

PeerMaintainer 模組正在執行特定作業 (追蹤訊息本文中會包含詳細資訊)。  
  
## <a name="description"></a>描述  

 會在各種 PeerMaintainer 作業期間發生此追蹤。  
  
 PeerMaintainer 是 PeerNode 的內部元件。 每一分鐘，或是每收到 32 個訊息，就會傳送 LinkUtility 訊息至鄰接項目，訊息內容包含已交換的訊息數目和有用訊息數目 (非重複、未遭竄改) 的統計資料。 這樣可幫助判斷特定鄰接項目的連結公用程式。 大約每五分鐘，維護程式就會檢查一次鄰接項目的連線狀態。 如果鄰接項目連線的數目超過理想數目，維護程式就會去除效用最低的連線。 如果連線數目不足，則維護程式會擷取新的連線。  
  
## <a name="see-also"></a>另請參閱

- [追蹤](index.md)
- [使用追蹤來疑難排解應用程式](using-tracing-to-troubleshoot-your-application.md)
- [系統管理與診斷](../index.md)
