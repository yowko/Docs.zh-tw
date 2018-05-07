---
title: ServiceAppDomain
ms.date: 03/30/2017
ms.assetid: f28e5186-a66d-46c1-abe9-b50e07f8cb4f
ms.openlocfilehash: aef0a0da9d107b92d9d3017968d5554205a6fd71
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="serviceappdomain"></a>ServiceAppDomain
將服務對應至應用程式定義域。  
  
## <a name="syntax"></a>語法  
  
```  
class ServiceAppDomain  
{  
  Service ref;  
  AppDomainInfo ref;  
};  
```  
  
## <a name="methods"></a>方法  
 ServiceAppDomain 類別不會定義任何方法。  
  
## <a name="properties"></a>屬性  
 ServiceAppDomain 類別具有下列屬性：  
  
### <a name="ref"></a>ref  
 資料型別：服務  
限定詞：索引鍵  
  
 存取類型：唯讀  
  
 這個應用程式定義域的服務。  
  
### <a name="ref"></a>ref  
 資料型別：AppDomainInfo  
限定詞：索引鍵  
  
 存取類型：唯讀  
  
 包含應用程式定義域的屬性。  
  
## <a name="requirements"></a>需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------------|  
|命名空間|於 root\ServiceModel 中定義|
