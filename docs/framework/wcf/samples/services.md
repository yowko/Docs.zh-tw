---
title: 服務範例-WCF
ms.date: 03/30/2017
ms.assetid: 462a2218-f8c6-4fb7-95bc-64765459c429
ms.openlocfilehash: 3fbca09a7b50a15299cb8e805ac84c60e4b78fa7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61967540"
---
# <a name="services"></a>服務

本節包含示範 Windows Communication Foundation (WCF) 服務的範例。

## <a name="in-this-section"></a>本節內容

- [裝載](../../../../docs/framework/wcf/feature-details/hosting.md)\
示範裝載 WCF 服務。

- [服務互通性](service-interoperability.md)\
示範 WCF 與其他服務技術之間的互動。

- [行為](behaviors.md)\
示範 WCF 服務行為。

- [服務安全性](service-security.md)\
示範 WCF 服務安全性。

- [WCF 服務的簡化的組態](simplified-configuration-for-wcf-services.md)\
示範如何實作與設定一般服務和用戶端使用 WCF。

- [使用標準端點](usage-of-standard-endpoints.md)\
示範如何在服務組態檔中使用標準端點。

- [延伸的保護原則](extended-protection-policy.md)\
示範延伸保護，這是防止中間人 (MITM) 攻擊的一項安全性方案。

- [組態通道處理站](configuration-channel-factory.md)\
示範 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> 的使用方式。

- [定址](addressing.md)\
示範端點位址的各方面與功能。

- [命令式](imperative.md)\
示範如何使用程式碼定義服務的 <xref:System.ServiceModel.WSHttpBinding>，而不是定義組態中的 `wsHttpBinding` 繫結。

- [多個合約](multiple-contracts.md)\
示範如何在服務實作一個以上的合約，以及如何設定要與每個已實作合約進行通訊的端點。

- [多個端點](multiple-endpoints.md)\
示範如何在服務上設定多個端點，以及如何從用戶端與每個端點進行通訊。

- [單一 listenuri 的多個端點](multiple-endpoints-at-a-single-listenuri.md)\
示範在單一 `ListenUri` 裝載多個端點的服務。

- [OperationContextScope](operationcontextscope.md)\
示範如何傳送上使用標頭的 WCF 呼叫的額外資訊。

- [服務描述](service-description.md)\
示範服務如何在執行階段擷取其服務描述資訊。

- [ConcurrencyMode.Reentrant](concurrencymode-reentrant.md)\
示範如何在服務實作上使用可重新進入的並行模式。