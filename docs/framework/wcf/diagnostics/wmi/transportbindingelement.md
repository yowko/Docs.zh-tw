---
title: TransportBindingElement
ms.date: 03/30/2017
ms.assetid: 54ecfbee-53c0-410c-a7fa-a98f2e40c545
ms.openlocfilehash: 45bfcd069391156bc85cc4c26f2b172770197a9e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96234839"
---
# <a name="transportbindingelement"></a>TransportBindingElement

TransportBindingElement  
  
## <a name="syntax"></a>Syntax  
  
```csharp
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

 資料類型：字串  
  
 存取類型：唯讀  
  
 傳輸的 URI 配置。  
  
## <a name="requirements"></a>規格需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------------|  
|命名空間|於 root\ServiceModel 中定義|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Channels.TransportBindingElement>
