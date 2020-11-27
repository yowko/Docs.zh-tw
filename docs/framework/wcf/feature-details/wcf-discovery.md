---
title: WCF 探索
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], discovery
- Windows Communication Foundation [WCF], discovery
- discovery [WCF]
ms.assetid: 462c4913-f388-45a9-9042-28ae96a4e735
ms.openlocfilehash: 176e9760d98f9640bd9d1c7b059287dc29c0d666
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96289356"
---
# <a name="wcf-discovery"></a>WCF 探索

Windows Communication Foundation (WCF) 提供的支援，可讓服務在執行時間以可互通的方式使用 WS-Discovery 通訊協定來進行探索。 WCF 服務可以使用多播訊息或探索 proxy 伺服器，宣佈其對網路的可用性。 用戶端應用程式可搜尋網路或探索 Proxy 伺服器，來尋找符合整組準則的服務。 本節中的主題提供概要並詳細說明此功能的程式設計模型。  
  
## <a name="in-this-section"></a>本節內容  

 [WCF 探索概觀](wcf-discovery-overview.md)  
 提供 WCF 所提供 WS-Discovery 支援的總覽。  
  
 [WCF 探索物件模型](wcf-discovery-object-model.md)  
 說明物件模型中的類別以及 WS-Discovery 支援的擴充性。  
  
 [作法：以程式設計方式將探索能力新增至 WCF 服務與用戶端](how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)  
 示範如何讓 Windows Communication Foundation (WCF) 可探索的服務。  
  
 [實作探索 Proxy](implementing-a-discovery-proxy.md)  
 說明用來實作探索 Proxy 的必要步驟、使用探索 Proxy 註冊的可探索服務，以及使用探索 Proxy 來尋找服務的用戶端。  
  
 [探索版本控制](discovery-versioning.md)  
 簡要概述部分新探索功能的原型實作。 同時也概要說明如何選取要使用的探索版本。  
  
 [在組態檔中設定探索](configuring-discovery-in-a-configuration-file.md)  
 示範如何設定組態中的探索。  
  
 [使用探索用戶端通道](using-the-discovery-client-channel.md)  
 顯示如何在撰寫 WCF 用戶端應用程式時使用探索用戶端通道。
