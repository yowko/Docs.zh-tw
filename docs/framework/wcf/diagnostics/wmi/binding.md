---
title: Binding2
ms.date: 03/30/2017
ms.assetid: 09511c6c-5749-4bb0-874e-0f0be36bfe04
ms.openlocfilehash: a040cc6e12833d2c737eb14c591300e5873ddce7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "59979156"
---
# <a name="binding"></a>繫結
wmi 繫結  
  
## <a name="syntax"></a>語法  
  
```csharp
class Binding  
{  
  BindingElement BindingElements[];  
  datetime CloseTimeout;  
  string Name;  
  string Namespace;  
  datetime OpenTimeout;  
  datetime ReceiveTimeout;  
  string Scheme;  
  datetime SendTimeout;  
};  
```  
  
## <a name="methods"></a>方法  
 Binding 類別並未定義任何方法。  
  
## <a name="properties"></a>屬性  
 Binding 類別具有下列屬性。  
  
### <a name="bindingelements"></a>BindingElements  
 資料類型：BindingElement 陣列  
  
 存取類型：唯讀  
  
 此繫結類別所實作之繫結項目的集合。  
  
### <a name="closetimeout"></a>CloseTimeout  
 資料型別：日期時間  
  
 存取類型：唯讀  
  
 供關閉作業完成其作業的時間間隔。  
  
### <a name="name"></a>名稱  
 資料型別：字串  
  
 存取類型：唯讀  
  
 繫結的名稱。  
  
### <a name="namespace"></a>命名空間  
 資料型別：字串  
  
 存取類型：唯讀  
  
 繫結的 XML 命名空間。  
  
### <a name="opentimeout"></a>OpenTimeout  
 資料型別：日期時間  
  
 存取類型：唯讀  
  
 供開啟作業完成其作業的時間間隔。  
  
### <a name="receivetimeout"></a>ReceiveTimeout  
 資料型別：日期時間  
  
 存取類型：唯讀  
  
 供接收作業完成其作業的時間間隔。  
  
### <a name="scheme"></a>配置  
 資料型別：字串  
  
 存取類型：唯讀  
  
 繫結建立之通道與接聽項處理站所使用的 URI 傳輸配置。  
  
### <a name="sendtimeout"></a>SendTimeout  
 資料型別：日期時間  
  
 存取類型：唯讀  
  
 針對完成傳送作業所提供的時間間隔。  
  
## <a name="requirements"></a>需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------------|  
|命名空間|於 root\ServiceModel 中定義|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Channels.Binding>
