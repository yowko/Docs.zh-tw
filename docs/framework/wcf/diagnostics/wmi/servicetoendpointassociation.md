---
title: ServiceToEndpointAssociation
ms.date: 03/30/2017
ms.assetid: 03c3cd15-e1b2-4dc2-bdc2-59fdccdae110
ms.openlocfilehash: b1e5b87b053e947432cba9f6e716f7d1ea8f013f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="servicetoendpointassociation"></a>ServiceToEndpointAssociation
將服務對應至端點。  
  
## <a name="syntax"></a>語法  
  
```  
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
