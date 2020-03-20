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
ms.openlocfilehash: 428b022ed560648f59798154d5987d382938c280
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176067"
---
# <a name="imaptokenmap-method"></a>IMapToken::Map 方法
使用中繼資料簽名對應程式集之間的關係。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Map (  
    [in]  mdToken tkImp,
    [in]  mdToken tkEmit  
);  
```  
  
## <a name="parameters"></a>參數  
 `tkImp`  
 [在]表示導入的代碼物件的中繼資料權杖。  
  
 `tkEmit`  
 [在]表示已發出的代碼物件的中繼資料權杖。  
  
## <a name="remarks"></a>備註  
 當令牌重新映射在合併期間發生時，原始權杖在導入的（源）中繼資料作用域中作用域，新權杖在已發出（目標）中繼資料作用域中作用域。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾赫  
  
 **庫：** 用作 MsCorEE.dll 中的資源  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMapToken 介面](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)
