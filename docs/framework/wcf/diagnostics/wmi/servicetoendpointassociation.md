---
title: ServiceToEndpointAssociation
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03c3cd15-e1b2-4dc2-bdc2-59fdccdae110
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2d2755294ba02b4d67bd7f62cf020a44525874d4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
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
