---
title: TransportBindingElement
ms.date: 03/30/2017
ms.assetid: 54ecfbee-53c0-410c-a7fa-a98f2e40c545
ms.openlocfilehash: bdb5ca7400a41dd724c2ad7fc76695a82874ded6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61641615"
---
# <a name="transportbindingelement"></a>TransportBindingElement
TransportBindingElement  
  
## <a name="syntax"></a>語法  
  
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
 資料型別：字串  
  
 存取類型：唯讀  
  
 傳輸的 URI 配置。  
  
## <a name="requirements"></a>需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------------|  
|命名空間|於 root\ServiceModel 中定義|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Channels.TransportBindingElement>
