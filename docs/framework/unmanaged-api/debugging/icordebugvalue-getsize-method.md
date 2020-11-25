---
title: ICorDebugValue::GetSize 方法
ms.date: 03/30/2017
api_name:
- ICorDebugValue.GetSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue::GetSize
helpviewer_keywords:
- GetSize method, ICorDebugValue interface [.NET Framework debugging]
- ICorDebugValue::GetSize method [.NET Framework debugging]
ms.assetid: 445a9ee3-e050-4f3a-931a-96b0efb00110
topic_type:
- apiref
ms.openlocfilehash: 9f5688ae4f76f9ddfde231aa6252d666c9152eec
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731075"
---
# <a name="icordebugvaluegetsize-method"></a>ICorDebugValue::GetSize 方法

取得這個 "ICorDebugValue" 物件的大小（以位元組為單位）。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetSize (  
    [out] ULONG32   *pSize  
);  
```  
  
## <a name="parameters"></a>參數  

 `pSize`  
 擴展此值物件的大小（以位元組為單位）。  
  
## <a name="remarks"></a>備註  

 如果值的型別是參考型別，這個方法會傳回指標的大小，而不是物件的大小。  
  
 `ICorDebugValue::GetSize`方法 `COR_E_OVERFLOW` 會針對64位平臺上大於 4 GB 的物件傳回。 針對大於 4 GB 的物件，請改用 [ICorDebugValue3：： GetSize64](icordebugvalue3-getsize64-method.md) 方法。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [GetSize64 方法](icordebugvalue3-getsize64-method.md)
