---
title: 比較 COM+ 與 ServiceModel 的異動
ms.date: 03/30/2017
ms.assetid: e493bcdd-b91a-4486-853f-83dbcd1931b7
ms.openlocfilehash: 4a47fe1686dff2e705b06b001d7d5e4ea6e8c5f2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857866"
---
# <a name="comparing-transactions-in-com-and-servicemodel"></a>比較 COM+ 與 ServiceModel 的異動
本主題討論如何模擬異動式 COM + 服務使用 Windows Communication Foundation (WCF) 屬性的行為<xref:System.ServiceModel>命名空間提供。  
  
## <a name="emulating-com-using-servicemodel-attributes"></a>使用 ServiceModel 屬性模擬 COM+  
 下表會比較<xref:System.EnterpriseServices.TransactionOption>列舉，用來建立`EnterpriseServices`交易和 WCF 屬性如何相互關聯<xref:System.ServiceModel>命名空間提供。  
  
|COM+ 屬性|WCF 屬性|  
|---------------------|------------------------------------------------------------------------|  
|RequiresNew|<xref:System.ServiceModel.TransactionFlowAttribute> 設定為 <xref:System.ServiceModel.TransactionFlowOption.NotAllowed>。<br /><br /> <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> 為 `true`。<br /><br /> 繫結項目中的 `TransactionFlow` 屬性為 `false`。|  
|必要|<xref:System.ServiceModel.TransactionFlowAttribute> 設定為 <xref:System.ServiceModel.TransactionFlowOption.Allowed>。<br /><br /> <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> 為 `true`。<br /><br /> 繫結項目中的 `TransactionFlow` 屬性為 `true`。|  
|支援|沒有直接的對等項目。 一般來說，您應該採用對 `Required` 所指定的行為。|  
|NotSupported|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> 為 `false`。<br /><br /> 繫結項目中的 `TransactionFlow` 屬性為 `false`。|  
|已停用|沒有直接的對等項目。 一般來說，您應該採用對 `NotSupported` 所指定的行為。|
