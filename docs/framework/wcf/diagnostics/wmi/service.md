---
title: Service
ms.date: 03/30/2017
ms.assetid: 999806e1-6376-409e-b998-b0af391adfe7
ms.openlocfilehash: aa4eecbcc8a2ef818cd99d777b0e3c2f1f222e46
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273278"
---
# <a name="service"></a>服務

服務  
  
## <a name="syntax"></a>Syntax  
  
```csharp
class Service  
{  
  string BaseAddresses[];  
  Behavior Behaviors[];  
  string ConfigurationName;  
  string CounterInstanceName;  
  string DistinguishedName;  
  string Extensions[];  
  string Metadata[];  
  string Name;  
  string Namespace;  
  datetime Opened;  
  Channel OutgoingChannels[];  
  sint32 ProcessId;  
};  
```  
  
## <a name="methods"></a>方法  

 此服務類別不會定義任何方法。  
  
## <a name="properties"></a>屬性  

 此服務類別具有下列屬性：  
  
### <a name="baseaddresses"></a>BaseAddresses  

 資料型別：字串陣列  
  
 存取類型：唯讀  
  
 由服務使用的基底位址。  
  
### <a name="behaviors"></a>行為  

 資料型別：行為陣列  
  
 存取類型：唯讀  
  
 與此服務關聯的行為。  
  
### <a name="configurationname"></a>ConfigurationName  

 資料類型：字串  
  
 存取類型：唯讀  
  
 ServiceElement_BehaviorConfiguration  
  
### <a name="counterinstancename"></a>CounterInstanceName  

 資料類型：字串  
  
 存取類型：唯讀  
  
 服務效能計數器之執行個體的名稱。  
  
### <a name="distinguishedname"></a>DistinguishedName  

 資料類型：字串  
  
 存取類型：唯讀  
  
 位址的服務名稱。  
  
### <a name="extensions"></a>延伸模組  

 資料型別：字串陣列  
  
 存取類型：唯讀  
  
 服務執行個體擴充的執行個體內容。  
  
### <a name="metadata"></a>中繼資料  

 資料型別：字串陣列  
  
 存取類型：唯讀  
  
 服務中繼資料設定。  
  
### <a name="name"></a>Name  

 資料類型：字串  
  
 存取類型：唯讀  
  
 這個服務的唯一名稱。  
  
### <a name="namespace"></a>命名空間  

 資料類型：字串  
  
 存取類型：唯讀  
  
 服務的命名空間。  
  
### <a name="opened"></a>已開啟  

 資料型別：日期時間  
  
 存取類型：唯讀  
  
 服務開啟的時間。  
  
### <a name="outgoingchannels"></a>OutgoingChannels  

 資料類型：通道陣列  
  
 存取類型：唯讀  
  
 從服務執行個體傳出的通道。  
  
### <a name="processid"></a>ProcessId  

 資料型別：sint32  
  
 存取類型：唯讀  
  
 裝載服務之處理序的處理序識別碼。  
  
## <a name="requirements"></a>規格需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------------|  
|命名空間|於 root\ServiceModel 中定義|
