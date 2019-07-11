---
title: IMapToken::Map 方法
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8ac12d5b6bc2911e3bd879285a9a12f65c426f0d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745851"
---
# <a name="imaptokenmap-method"></a>IMapToken::Map 方法
對應使用中繼資料簽章的組件之間的關聯性。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Map (  
    [in]  mdToken tkImp,   
    [in]  mdToken tkEmit  
);  
```  
  
## <a name="parameters"></a>參數  
 `tkImp`  
 [in]表示匯入的程式碼物件的中繼資料語彙基元。  
  
 `tkEmit`  
 [in]表示發出的程式碼物件的中繼資料語彙基元。  
  
## <a name="remarks"></a>備註  
 當語彙基元重新對應，就會發生在合併期間時，原始的語彙基元的範圍匯入 （來源） 中繼資料範圍內，新的語彙基元的範圍中發出 （目標） 中繼資料範圍。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **LIBRARY:** 做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMapToken 介面](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)
