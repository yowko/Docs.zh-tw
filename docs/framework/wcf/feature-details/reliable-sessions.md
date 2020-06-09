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
ms.openlocfilehash: 910ad952192243c6aa8a79417ad711d8c2a4ba2e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84590536"
---
# <a name="reliable-sessions"></a>可靠工作階段

本節說明什麼是 Windows Communication Foundation （WCF）可靠會話、用於哪些用途、使用方式和時機、哪些系結設定支援它，以及最佳做法的指標。 下表將針對本節重點與相關主題的詳細資料提供摘要說明。

可靠會話 WCF 提供的功能，可確保端點之間傳送的訊息會跨 SOAP 或傳輸媒介傳輸，而且只會傳遞一次，並選擇性地以其傳送的相同順序傳送。

若要使用與 WCF 應用程式的可靠會話，請在 WCF 中使用其中一個系統提供的系結，此系結預設會支援可靠會話，或做為選項，或建立您自己的自訂系結來支援會話。

## <a name="in-this-section"></a>本節內容

[可靠會話總覽](reliable-sessions-overview.md)描述可靠會話、使用時機、支援可靠會話的不同系結，以及它們的工作方式。

[如何：在可靠的會話內交換訊息](how-to-exchange-messages-within-a-reliable-session.md)說明如何使用設定中指定的自訂系結，透過 HTTP 建立可靠會話。

[如何：保護可靠會話內的訊息](how-to-secure-messages-within-reliable-sessions.md)說明如何保護可靠會話的安全。

How [to：使用 HTTPS 建立自訂可靠會話](how-to-create-a-custom-reliable-session-binding-with-https.md)系結說明如何透過 HTTPS 建立可靠會話。

[可靠會話的最佳做法](best-practices-for-reliable-sessions.md)說明一些與使用可靠會話相關聯的最佳作法。

## <a name="reference"></a>參考

<xref:System.ServiceModel.ReliableSession>

## <a name="see-also"></a>請參閱

- [佇列和可靠工作階段](queues-and-reliable-sessions.md)
- [工作階段、執行個體與並行](sessions-instancing-and-concurrency.md)
