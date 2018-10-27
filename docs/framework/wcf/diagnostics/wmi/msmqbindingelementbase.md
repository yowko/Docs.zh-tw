---
title: MsmqBindingElementBase
ms.date: 03/30/2017
ms.assetid: 210d41ab-a2a4-4d7a-afd2-0916c08a4015
ms.openlocfilehash: e7f4cf41168bd1e5483524195e20541d896a6569
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50183187"
---
# <a name="msmqbindingelementbase"></a>MsmqBindingElementBase
MsmqBindingElementBase  
  
## <a name="syntax"></a>語法  
  
```csharp  
class MsmqBindingElementBase : TransportBindingElement  
{  
  string CustomDeadLetterQueue;  
  string DeadLetterQueue;  
  boolean Durable;  
  boolean ExactlyOnce;  
  sint32 MaxRetryCycles;  
  string ReceiveErrorHandling;  
  sint32 ReceiveRetryCount;  
  datetime RetryCycleDelay;  
  datetime TimeToLive;  
  boolean UseMsmqTracing;  
  boolean UseSourceJournal;  
};  
```  
  
## <a name="methods"></a>方法  
 MsmqBindingElementBase 類別不會定義任何方法。  
  
## <a name="properties"></a>屬性  
 MsmqBindingElementBase 類別具有下列屬性：  
  
### <a name="customdeadletterqueue"></a>CustomDeadLetterQueue  
 資料型別：字串  
  
 存取類型：唯讀  
  
 包含每個應用程式寄不出的信件佇列位置的 URI，該佇列含有已過期、無法傳輸或延遲傳遞的訊息。  
  
### <a name="deadletterqueue"></a>DeadLetterQueue  
 資料型別：字串  
  
 存取類型：唯讀  
  
 代表要使用之寄不出的信件佇列類型的列舉值。  
  
### <a name="durable"></a>Durable  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 代表此繫結處理之訊息為永久性或變動性的值。  
  
### <a name="exactlyonce"></a>ExactlyOnce  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 代表由此繫結處理的訊息是否只接收一次的布林值。  
  
### <a name="maxretrycycles"></a>MaxRetryCycles  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 嘗試傳遞訊息至接收應用程式的重試循環次數上限。  
  
### <a name="receiveerrorhandling"></a>ReceiveErrorHandling  
 資料型別：字串  
  
 存取類型：唯讀  
  
 有害訊息處理設定。  
  
### <a name="receiveretrycount"></a>ReceiveRetryCount  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 從應用程式佇列讀取之訊息的立即重試次數上限。  
  
### <a name="retrycycledelay"></a>RetryCycleDelay  
 資料型別：日期時間  
  
 存取類型：唯讀  
  
 代表嘗試傳遞無法立即傳遞之訊息時，重試循環之間的時間延遲值。  
  
### <a name="timetolive"></a>TimeToLive  
 資料型別：日期時間  
  
 存取類型：唯讀  
  
 代表由此繫結所處理之訊息在到期前可保留在佇列中的時間間隔值。  
  
### <a name="usemsmqtracing"></a>UseMsmqTracing  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 代表是否應該追蹤由此繫結所處理之訊息的布林值。  
  
### <a name="usesourcejournal"></a>UseSourceJournal  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 代表由此繫結所處理之訊息複本是否應該儲存在來源日誌佇列的布林值。  
  
## <a name="requirements"></a>需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------------|  
|命名空間|於 root\ServiceModel 中定義|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.NetMsmqBinding>  
 <xref:System.ServiceModel.MsmqBindingBase>
