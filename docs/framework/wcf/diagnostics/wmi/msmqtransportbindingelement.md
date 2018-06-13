---
title: MsmqTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 1c89f073-9ed3-4025-a8c5-13535a0f526b
ms.openlocfilehash: 643ab0f30c771f79df8ef7dd885013d5186fba59
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485904"
---
# <a name="msmqtransportbindingelement"></a>MsmqTransportBindingElement
MsmqTransportBindingElement  
  
## <a name="syntax"></a>語法  
  
```  
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
 資料型別：字串  
  
 存取類型：唯讀  
  
 代表此繫結使用之已佇列通訊通道傳輸的列舉值。  
  
### <a name="useactivedirectory"></a>UseActiveDirectory  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 傳回布林值，這個值會指出是否應該使用 Active Directory 來轉換佇列位址。  
  
## <a name="requirements"></a>需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------------|  
|命名空間|於 root\ServiceModel 中定義|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>
