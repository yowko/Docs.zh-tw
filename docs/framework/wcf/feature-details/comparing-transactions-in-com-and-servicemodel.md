---
title: 比較 COM+ 與 ServiceModel 的異動
ms.date: 03/30/2017
ms.assetid: e493bcdd-b91a-4486-853f-83dbcd1931b7
ms.openlocfilehash: 30ecbd374e909141dbc944740f90c1b41ac44ed2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96264904"
---
# <a name="comparing-transactions-in-com-and-servicemodel"></a>比較 COM+ 與 ServiceModel 的異動

本主題討論如何使用命名空間所提供的 Windows Communication Foundation (WCF) 屬性來模擬交易式 COM + 服務的行為 <xref:System.ServiceModel> 。  
  
## <a name="emulating-com-using-servicemodel-attributes"></a>使用 ServiceModel 屬性模擬 COM+  

 下表比較 <xref:System.EnterpriseServices.TransactionOption> 用來建立交易的列舉 `EnterpriseServices` ，以及它們如何與命名空間所提供的 WCF 屬性相互關聯 <xref:System.ServiceModel> 。  
  
|COM+ 屬性|WCF 屬性|  
|---------------------|------------------------------------------------------------------------|  
|RequiresNew|<xref:System.ServiceModel.TransactionFlowAttribute> 設定為 <xref:System.ServiceModel.TransactionFlowOption.NotAllowed>。<br /><br /> <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> 為 `true`。<br /><br /> 繫結項目中的 `TransactionFlow` 屬性為 `false`。|  
|必要|<xref:System.ServiceModel.TransactionFlowAttribute> 設定為 <xref:System.ServiceModel.TransactionFlowOption.Allowed>。<br /><br /> <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> 為 `true`。<br /><br /> 繫結項目中的 `TransactionFlow` 屬性為 `true`。|  
|支援|沒有直接的對等項目。 一般來說，您應該採用對 `Required` 所指定的行為。|  
|NotSupported|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> 為 `false`。<br /><br /> 繫結項目中的 `TransactionFlow` 屬性為 `false`。|  
|已停用|沒有直接的對等項目。 一般來說，您應該採用對 `NotSupported` 所指定的行為。|
