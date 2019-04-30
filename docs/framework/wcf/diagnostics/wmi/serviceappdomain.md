---
title: ServiceAppDomain
ms.date: 03/30/2017
ms.assetid: f28e5186-a66d-46c1-abe9-b50e07f8cb4f
ms.openlocfilehash: 05be495dbfe87e7dd14b0cfbb38b30c6f8278e6d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61957069"
---
# <a name="serviceappdomain"></a>ServiceAppDomain
將服務對應至應用程式定義域。  
  
## <a name="syntax"></a>語法  
  
```csharp
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
 資料類型：服務  
限定詞：Key  
  
 存取類型：唯讀  
  
 這個應用程式定義域的服務。  
  
### <a name="ref"></a>ref  
 資料類型：AppDomainInfo  
限定詞：Key  
  
 存取類型：唯讀  
  
 包含應用程式定義域的屬性。  
  
## <a name="requirements"></a>需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------------|  
|命名空間|於 root\ServiceModel 中定義|
