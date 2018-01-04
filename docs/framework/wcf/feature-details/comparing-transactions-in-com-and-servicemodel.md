---
title: "比較 COM+ 與 ServiceModel 的異動"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e493bcdd-b91a-4486-853f-83dbcd1931b7
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 87e3df31060a9c71e0b2868aa34373bca221fa79
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="comparing-transactions-in-com-and-servicemodel"></a>比較 COM+ 與 ServiceModel 的異動
這個主題會討論如何使用 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 命名空間提供的 <xref:System.ServiceModel> 屬性，來模擬交易 COM+ 服務的行為。  
  
## <a name="emulating-com-using-servicemodel-attributes"></a>使用 ServiceModel 屬性模擬 COM+  
 下列表格會比較用來建立 <xref:System.EnterpriseServices.TransactionOption> 交易的 `EnterpriseServices` 列舉，以及如何與 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 命名空間提供的 <xref:System.ServiceModel> 屬性產生關聯。  
  
|COM+ 屬性|[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 屬性|  
|---------------------|------------------------------------------------------------------------|  
|RequiresNew|<xref:System.ServiceModel.TransactionFlowAttribute> 設定為 <xref:System.ServiceModel.TransactionFlowOption.NotAllowed>。<br /><br /> <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> 為 `true`。<br /><br /> 繫結項目中的 `TransactionFlow` 屬性為 `false`。|  
|必要項|<xref:System.ServiceModel.TransactionFlowAttribute> 設定為 <xref:System.ServiceModel.TransactionFlowOption.Allowed>。<br /><br /> <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> 為 `true`。<br /><br /> 繫結項目中的 `TransactionFlow` 屬性為 `true`。|  
|支援|沒有直接的對等項目。 一般來說，您應該採用對 `Required` 所指定的行為。|  
|NotSupported|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> 為 `false`。<br /><br /> 繫結項目中的 `TransactionFlow` 屬性為 `false`。|  
|已停用|沒有直接的對等項目。 一般來說，您應該採用對 `NotSupported` 所指定的行為。|
