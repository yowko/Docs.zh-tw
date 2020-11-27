---
title: MsmqTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 1c89f073-9ed3-4025-a8c5-13535a0f526b
ms.openlocfilehash: 6590c5188e4e1758987a75fbd007099703ea6bc5
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96250420"
---
# <a name="msmqtransportbindingelement"></a>MsmqTransportBindingElement

MsmqTransportBindingElement  
  
## <a name="syntax"></a>Syntax  
  
```csharp
class MsmqTransportBindingElement : MsmqBindingElementBase  
{  
  sint32 MaxPoolSize;  
  string QueueTransferProtocol;  
  boolean UseActiveDirectory;  
};  
```  
  
## <a name="methods"></a>方法  

 MsmqTransportBindingElement 類別並未定義任何方法。  
  
## <a name="properties"></a>屬性  

 MsmqTransportBindingElement 類別具有下列屬性：  
  
### <a name="maxpoolsize"></a>MaxPoolSize  

 資料型別：sint32  
  
 存取類型：唯讀  
  
 包含內部 MSMQ 訊息物件之集區的大小上限。  
  
### <a name="queuetransferprotocol"></a>QueueTransferProtocol  

 資料類型：字串  
  
 存取類型：唯讀  
  
 代表此繫結使用之已佇列通訊通道傳輸的列舉值。  
  
### <a name="useactivedirectory"></a>UseActiveDirectory  

 資料型別：布林值  
  
 存取類型：唯讀  
  
 傳回布林值，這個值會指出是否應該使用 Active Directory 來轉換佇列位址。  
  
## <a name="requirements"></a>規格需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------------|  
|命名空間|於 root\ServiceModel 中定義|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>
