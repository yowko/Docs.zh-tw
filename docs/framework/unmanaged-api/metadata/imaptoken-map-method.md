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
ms.openlocfilehash: 51cca1ab61027090b0d22781dfd740038bc9372d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718198"
---
# <a name="imaptokenmap-method"></a>IMapToken::Map 方法

使用中繼資料簽章對應元件之間的關聯性。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Map (  
    [in]  mdToken tkImp,
    [in]  mdToken tkEmit  
);  
```  
  
## <a name="parameters"></a>參數  

 `tkImp`  
 在代表匯入之程式碼物件的元資料標記。  
  
 `tkEmit`  
 在代表發出的程式碼物件的元資料標記。  
  
## <a name="remarks"></a>備註  

 在合併期間發生權杖重新對應時，原始的權杖範圍會限定在匯入的 (源) 中繼資料範圍內，而新的權杖會限定在發出的 (目標) 中繼資料範圍內。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 當做 MsCorEE.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMapToken 介面](imaptoken-interface.md)
