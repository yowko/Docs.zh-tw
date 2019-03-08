---
title: 可靠工作階段
ms.date: 03/30/2017
f1_keywords:
- Windows Communication Foundation, sessions and instances
- WCF, sessions and instances
- sessions and instances [WCF]
helpviewer_keywords:
- instances [WCF]
- sessions [WCF]
ms.assetid: 143951b3-3aa0-4540-b4b7-d33e77e874a1
ms.openlocfilehash: 9a2cd06c4c5a73d9fb5c4c7f09632e10c3eb0d87
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2019
ms.locfileid: "57679122"
---
# <a name="reliable-sessions"></a>可靠工作階段

本章節說明哪些 Windows Communication Foundation (WCF) 可靠的工作階段、 其用途，如何以及何時要使用其中一個，哪些繫結組態支援它，而最佳做法的指標。 下表將針對本節重點與相關主題的詳細資料提供摘要說明。

可靠工作階段 WCF 提供的功能，確保端點之間傳送的訊息會透過 SOAP 或傳輸媒介傳輸和傳遞一次，並選擇性地依照傳送的順序相同。

若要使用的 WCF 應用程式中的可靠工作階段，請使用其中一個系統提供繫結在 WCF 中支援可靠工作階段，根據預設，或選擇，或是建立您自己自訂的繫結支援工作階段。

## <a name="in-this-section"></a>本節內容

[可靠工作階段概觀](../../../../docs/framework/wcf/feature-details/reliable-sessions-overview.md)說明可靠工作階段，使用支援可靠工作階段的不同繫結的時機，以及其運作方式。

[如何：Exchange 訊息在可靠工作階段](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md)說明如何透過使用自訂繫結組態中指定的 HTTP 建立可靠工作階段。

[如何：保護可靠工作階段內的訊息](../../../../docs/framework/wcf/feature-details/how-to-secure-messages-within-reliable-sessions.md)說明如何保護可靠工作階段。

[如何：使用 HTTPS 建立自訂可靠工作階段繫結](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md)說明如何透過 HTTPS 建立可靠工作階段。

[最佳做法的可靠工作階段](../../../../docs/framework/wcf/feature-details/best-practices-for-reliable-sessions.md)說明一些與使用可靠工作階段相關聯的最佳作法。

## <a name="reference"></a>參考資料

<xref:System.ServiceModel.ReliableSession>

## <a name="see-also"></a>另請參閱

- [佇列和可靠工作階段](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md)
- [工作階段、執行個體與並行](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)
