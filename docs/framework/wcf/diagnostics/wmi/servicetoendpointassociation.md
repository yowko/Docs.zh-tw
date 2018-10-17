---
title: ServiceToEndpointAssociation
ms.date: 03/30/2017
ms.assetid: 03c3cd15-e1b2-4dc2-bdc2-59fdccdae110
ms.openlocfilehash: 3d23a3ee10c47e04ea7bdba202ea5063c0d84fac
ms.sourcegitcommit: e42d09e5966dd9fd02847d3e7eeb4ec0877069f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2018
ms.locfileid: "49372170"
---
# <a name="servicetoendpointassociation"></a>ServiceToEndpointAssociation
將服務對應至端點。  
  
## <a name="syntax"></a>語法  
  
```csharp
class ServiceToEndpointAssociation  
{  
  Service ref;  
  Endpoint ref;  
};  
```  
  
## <a name="methods"></a>方法  
 ServiceToEndpointAssociation 類別並未定義任何方法。  
  
## <a name="properties"></a>屬性  
 ServiceToEndpointAssociation 類別有下列屬性：  
  
### <a name="ref"></a>ref  
 資料型別：服務  
  
 存取類型：唯讀  
限定詞：索引鍵  
  
 與端點關聯的服務。  
  
### <a name="ref"></a>ref  
 資料型別：端點  
  
 存取類型：唯讀  
限定詞：索引鍵  
  
 與服務關聯的端點。  
  
## <a name="requirements"></a>需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------------|  
|命名空間|於 root\ServiceModel 中定義|
