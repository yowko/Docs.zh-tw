---
title: "IMapToken::Map 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMapToken.Map
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMapToken::Map
helpviewer_keywords:
- IMapToken::Map method [.NET Framework metadata]
- Map method [.NET Framework metadata]
ms.assetid: b9b4bf2f-1098-43d6-9619-a99b4bda1940
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fe034d2bc6d70e820fa3ad5de8140afa9a19a6bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imaptokenmap-method"></a>IMapToken::Map 方法
將對應使用中繼資料簽章的組件之間的關聯性。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT Map (  
    [in]  mdToken tkImp,   
    [in]  mdToken tkEmit  
);  
```  
  
#### <a name="parameters"></a>參數  
 `tkImp`  
 [in]代表已匯入程式碼物件中繼資料語彙基元。  
  
 `tkEmit`  
 [in]表示發出程式碼物件中繼資料語彙基元。  
  
## <a name="remarks"></a>備註  
 發生語彙基元重新對應合併期間，原始語彙基元的範圍匯入 （來源） 中繼資料範圍並將新的語彙基元的範圍發出 （目標） 中繼資料範圍內。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：**做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [IMapToken 介面](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)
