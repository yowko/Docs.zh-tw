---
title: ServiceDebugBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a5ec9061-1e95-43fb-b0d9-dbd0a7bc3c44
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2d6b866c90e3e6c6e72dc75f230bcf7b4e03a6bb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="servicedebugbehavior"></a>ServiceDebugBehavior
ServiceDebugBehavior  
  
## <a name="syntax"></a>語法  
  
```  
class ServiceDebugBehavior : Behavior  
{  
  boolean HttpHelpPageEnabled;  
  string HttpHelpPageUrl;  
  boolean HttpsHelpPageEnabled;  
  string HttpsHelpPageUrl;  
  boolean IncludeExceptionDetailInFaults;  
};  
```  
  
## <a name="methods"></a>方法  
 ServiceDebugBehavior 類別並未定義任何方法。  
  
## <a name="properties"></a>屬性  
 ServiceDebugBehavior 類別具有下列屬性：  
  
### <a name="httphelppageenabled"></a>HttpHelpPageEnabled  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 控制服務是否會在由 `HttpGetUrl` 屬性控制的位址發行其 WSDL。  
  
### <a name="httphelppageurl"></a>HttpHelpPageUrl  
 資料型別：字串  
  
 存取類型：唯讀  
  
 設定服務 WSDL 的發行位置，以供使用 HTTP 擷取。  
  
### <a name="httpshelppageenabled"></a>HttpsHelpPageEnabled  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 控制服務是否會透過 HTTPS，在由 `HttpsGetUrl` 屬性控制的位址發行其 WSDL。  
  
### <a name="httpshelppageurl"></a>HttpsHelpPageUrl  
 資料型別：字串  
  
 存取類型：唯讀  
  
 設定服務 WSDL 的發行位置，以供使用 HTTPS 擷取。  
  
### <a name="includeexceptiondetailinfaults"></a>IncludeExceptionDetailInFaults  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 指定是否要針對偵錯用途，在傳回給用戶端的 SOAP 錯誤詳細資料中包含 Managed 例外狀況資訊。  
  
## <a name="requirements"></a>需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------------|  
|命名空間|於 root\ServiceModel 中定義|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Description.ServiceDebugBehavior>
