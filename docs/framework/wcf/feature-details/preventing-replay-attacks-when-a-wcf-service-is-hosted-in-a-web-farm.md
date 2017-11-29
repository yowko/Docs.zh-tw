---
title: "防止 WCF 服務裝載於 Web 伺服陣列時的重新執行攻擊"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c2ed695-7a31-4257-92bd-9e9731b886a5
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4ecf37ffb87ddfdd483cebcac3f5892bab43dcd6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="preventing-replay-attacks-when-a-wcf-service-is-hosted-in-a-web-farm"></a>防止 WCF 服務裝載於 Web 伺服陣列時的重新執行攻擊
使用訊息安全性時，WCF 會從傳入訊息中建立 NONCE 並檢查內部 `InMemoryNonceCache` 確認產生的 NONCE 是否存在，以防止重新執行攻擊。 如果是，則將該訊息視為重新執行來捨棄。 在 Web 伺服陣列中裝載 WCF 服務時，由於不是跨 Web 伺服陣列中的節點來共用 `InMemoryNonceCache`，這個服務很容易遭受重新執行攻擊的威脅。  為減輕這種情況，WCF 4.5 提供了擴充點，可讓您從 <xref:System.ServiceModel.Security.NonceCache> 抽象類別衍生類別，以實作自己的共用 NONCE 快取。  
  
## <a name="noncecache-implementation"></a>NonceCache 實作  
 若要實作您自己的共用 NONCE 快取，請從 <xref:System.ServiceModel.Security.NonceCache> 衍生類別，並覆寫 <xref:System.ServiceModel.Security.NonceCache.CheckNonce%2A> 和 <xref:System.ServiceModel.Security.NonceCache.TryAddNonce%2A> 方法。 <xref:System.ServiceModel.Security.NonceCache.CheckNonce%2A> 將會檢查快取中是否存在指定的 NONCE。 <xref:System.ServiceModel.Security.NonceCache.TryAddNonce%2A> 會嘗試將 NONCE 加入至快取。 實作這個類別之後，請具現化執行個體，將其指派給 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings.NonceCache%2A> 以進行用戶端重新執行偵測，並指派給 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NonceCache%2A> 以進行伺服器端重新執行偵測。 這項功能沒有立即可用的組態支援。  
  
## <a name="see-also"></a>另請參閱  
 [訊息安全性](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)  
 [SymmetricSecurityBindingElement](../../../../docs/framework/wcf/diagnostics/wmi/symmetricsecuritybindingelement.md)
