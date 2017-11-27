---
title: TransportBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 54ecfbee-53c0-410c-a7fa-a98f2e40c545
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c130093b9600c324e7179febce6857341b8a7d3c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="transportbindingelement"></a>TransportBindingElement
TransportBindingElement  
  
## <a name="syntax"></a>語法  
  
```  
class TransportBindingElement : BindingElement  
{  
  boolean ManualAddressing;  
  sint64 MaxBufferPoolSize;  
  sint64 MaxReceivedMessageSize;  
  string Scheme;  
};  
```  
  
## <a name="methods"></a>方法  
 TransportBindingElement 類別並未定義任何方法。  
  
## <a name="properties"></a>屬性  
 TransportBindingElement 類別具有下列屬性：  
  
### <a name="manualaddressing"></a>ManualAddressing  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 指定使用者是否要取得訊息定址控制權的布林值。  
  
### <a name="maxbufferpoolsize"></a>MaxBufferPoolSize  
 資料型別：sint64  
  
 存取類型：唯讀  
  
 繫結的緩衝集區大小上限。  
  
### <a name="maxreceivedmessagesize"></a>MaxReceivedMessageSize  
 資料型別：sint64  
  
 存取類型：唯讀  
  
 此繫結所處理之訊息的大小上限。  
  
### <a name="scheme"></a>配置  
 資料型別：字串  
  
 存取類型：唯讀  
  
 傳輸的 URI 配置。  
  
## <a name="requirements"></a>需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------------|  
|命名空間|於 root\ServiceModel 中定義|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Channels.TransportBindingElement>
