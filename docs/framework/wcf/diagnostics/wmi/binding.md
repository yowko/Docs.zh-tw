---
title: Binding2
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 09511c6c-5749-4bb0-874e-0f0be36bfe04
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6505fa08ca43e64df224b75500aacbc903783398
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="binding"></a>繫結
wmi 繫結  
  
## <a name="syntax"></a>語法  
  
```  
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
 資料型別：BindingElement 陣列  
  
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
 <xref:System.ServiceModel.Channels.Binding>
