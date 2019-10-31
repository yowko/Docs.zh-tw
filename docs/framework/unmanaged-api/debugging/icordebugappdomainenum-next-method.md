---
title: ICorDebugAppDomainEnum::Next 方法
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomainEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomainEnum::Next method
helpviewer_keywords:
- ICorDebugAppDomainEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugAppDomainEnum interface [.NET Framework debugging]
ms.assetid: b8d1def7-0ebc-4314-a3a2-fd36a75973e7
topic_type:
- apiref
ms.openlocfilehash: 55e331ff4e6ada73dc92bb2e880f555887639714
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088784"
---
# <a name="icordebugappdomainenumnext-method"></a>ICorDebugAppDomainEnum::Next 方法
從目前的資料指標位置開始，取得集合中指定的應用程式域數目。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
                           ICorDebugAppDomain *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>參數  
 `celt`  
 在要抓取的應用程式域數目。  
  
 `values`  
 脫銷指標陣列，其中每一個都會指向代表應用程式域的 ICorDebugAppDomain 物件。  
  
 `pceltFetched`  
 脫銷實際傳回的應用程式網域數目的指標。 如果 `celt` 是一個，這個值可能會是 null。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
