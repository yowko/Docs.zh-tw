---
title: '&lt;synchronousReceive&gt; 項目'
ms.date: 03/30/2017
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
ms.openlocfilehash: af1ca2ee1fe3c03c33f05e0c30c7b843b3720a36
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32753257"
---
# <a name="ltsynchronousreceivegt-element"></a>&lt;synchronousReceive&gt; 項目
這個組態項目用於指定在服務或用戶端應用程式中接收訊息的執行階段行為。 它沒有任何屬性或子項目。  
  
 \<system.ServiceModel>  
\<行為 >  
\<endpointBehaviors>  
\<行為 >  
\<synchronousReceive >  
  
## <a name="syntax"></a>語法  
  
```xml  
<synchronousReceive />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子項目  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<行為 >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|指定端點行為。|  
  
## <a name="remarks"></a>備註  
 您可以使用此行為指示通道接聽程式使用同步接收，而非預設的非同步接收。 Windows Communication Foundation (WCF) 發出新的執行緒，以提取每個可接受的通道。 如果有許多個通道，執行緒可能會用完。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>  
 <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>
