---
title: "可靠工作階段"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Windows Communication Foundation, sessions and instances
- WCF, sessions and instances
- sessions and instances [WCF]
helpviewer_keywords:
- instances [WCF]
- sessions [WCF]
ms.assetid: 143951b3-3aa0-4540-b4b7-d33e77e874a1
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 659309ff5560480c423fc9b0adab5e93eac05ce5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="reliable-sessions"></a>可靠工作階段

本節說明該怎麼辦[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]可靠工作階段有用途，如何及何時使用其中一個，哪些繫結組態支援它，以及最佳做法的指標。 下表將針對本節重點與相關主題的詳細資料提供摘要說明。

可靠工作階段[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]提供 featrues 確保端點之間傳送的訊息會透過 SOAP 或傳輸媒介傳輸和傳遞一次，並選擇性地被傳送的順序相同。

若要配合 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式使用可靠工作階段，請使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中預設或選擇性支援可靠工作階段的其中一個系統提供繫結，或是自行建立支援工作階段的自訂繫結。

## <a name="in-this-section"></a>本章節內容

[可靠工作階段概觀](../../../../docs/framework/wcf/feature-details/reliable-sessions-overview.md)   
說明可靠工作階段、使用時機、支援可靠工作階段的各種不同繫結，以及這些工作階段的運作方式。

[如何： 在可靠工作階段中交換訊息](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md)   
說明如何使用組態中指定的自訂繫結，透過 HTTP 來建立可靠工作階段。

[如何： 保護可靠工作階段內的訊息](../../../../docs/framework/wcf/feature-details/how-to-secure-messages-within-reliable-sessions.md)   
說明如何保護可靠工作階段的安全。

[如何： 使用 HTTPS 建立自訂可靠工作階段繫結](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md)   
說明如何透過 HTTPS 建立可靠工作階段。

[可靠工作階段的最佳作法](../../../../docs/framework/wcf/feature-details/best-practices-for-reliable-sessions.md)   
說明一些與使用可靠工作階段相關的最佳做法。

## <a name="reference"></a>參考資料

<xref:System.ServiceModel.ReliableSession>

## <a name="see-also"></a>另請參閱

[佇列和可靠工作階段](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md)   
[工作階段中，執行個體與並行](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)
