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
ms.openlocfilehash: 027694cee1b3e4d990796ba31300918f6d859679
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008192"
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
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMapToken 介面](imaptoken-interface.md)
