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
ms.openlocfilehash: fd362beb9f8fd7a1f2076eb6490a96c0358520e4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432145"
---
# <a name="imaptokenmap-method"></a>IMapToken::Map 方法
使用中繼資料簽章來對應元件之間的關聯性。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Map (  
    [in]  mdToken tkImp,   
    [in]  mdToken tkEmit  
);  
```  
  
## <a name="parameters"></a>參數  
 `tkImp`  
 在表示已匯入之程式碼物件的元資料標記。  
  
 `tkEmit`  
 在表示發出的程式碼物件的元資料標記。  
  
## <a name="remarks"></a>備註  
 在合併期間發生權杖重新對應時，會將原始權杖的範圍限定在匯入的（來源）中繼資料範圍內，而新的 token 會限定在發出的（目標）中繼資料範圍中。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMapToken 介面](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)
