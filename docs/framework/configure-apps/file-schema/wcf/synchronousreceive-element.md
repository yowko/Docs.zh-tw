---
title: <synchronousReceive> 項目
ms.date: 03/30/2017
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
ms.openlocfilehash: 20390f747c8beaccba1cfea7a9ea0ed366037ecb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59166539"
---
# <a name="synchronousreceive-element"></a>\<synchronousReceive > 項目
這個組態項目用於指定在服務或用戶端應用程式中接收訊息的執行階段行為。 它沒有任何屬性或子項目。  
  
 \<system.ServiceModel>  
\<behaviors>  
\<endpointBehaviors>  
\<behavior>  
\<synchronousReceive>  
  
## <a name="syntax"></a>語法  
  
```xml  
<synchronousReceive />
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<behavior>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|指定端點行為。|  
  
## <a name="remarks"></a>備註  
 您可以使用此行為指示通道接聽程式使用同步接收，而非預設的非同步接收。 Windows Communication Foundation (WCF) 會發出新的執行緒，以提取每個接受的通道。 如果有許多個通道，執行緒可能會用完。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>
- <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>
