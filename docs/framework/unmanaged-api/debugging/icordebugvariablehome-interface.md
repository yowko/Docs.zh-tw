---
title: ICorDebugVariableHome 介面
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugVariableHome
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome
helpviewer_keywords:
- ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 76f2bf3b-759f-4eed-bce7-119415b25915
topic_type:
- apiref
ms.openlocfilehash: 306a07450b8ae6d29875ca0cc4679390472e4d1d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121034"
---
# <a name="icordebugvariablehome-interface"></a>ICorDebugVariableHome 介面
表示函數的區域變數或引數。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetArgumentIndex 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getargumentindex-method.md)|取得函數引數的索引。|  
|[GetCode 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getcode-method.md)|取得包含這個 `ICorDebugVariableHome` 物件的 "ICorDebugCode" 實例。|  
|[GetLiveRange 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getliverange-method.md)|取得此變數所在的原生範圍。|  
|[GetLocationType 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md)|取得變數原生位置的類型。|  
|[GetOffset 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getoffset-method.md)|取得變數基底暫存器的位移。|  
|[GetRegister 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getregister-method.md)|取得包含 `VLT_REGISTER`之位置類型之變數的暫存器，以及具有 `VLT_REGISTER_RELATIVE`位置類型之變數的基底暫存器。|  
|[GetSlotIndex 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getslotindex-method.md)|取得本機變數的 managed 位置索引。|  
  
## <a name="example"></a>範例  
 下列程式碼片段會使用名為 `pCode4`的[ICorDebugCode4](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md)物件。  
  
```cpp  
ICorDebugCode4 *pCode4 = NULL;  
pCode->QueryInterface(IID_ICorDebugCode4, &pCode4);  
  
ICorDebugVariableEnum *pVarLocEnum = NULL;  
pCode4->EnumerateVariableHomes(&pVarLocEnum);  
  
// retrieve local variables and arguments  
ULONG celt = 0;  
pVarLocEnum->GetCount(&celt);  
ICorDebugVariableHome **homes = new ICorDebugVariableHome *[celt];  
ULONG celtFetched = 0;  
pVarLocEnum->Next(celt, homes, &celtFetched);  
  
for (int i = 0; i < celtFetched; i++)  
{  
    VariableLocationType locType = VLT_INVALID;  
    homes[i].GetLocationType(&locType);  
    switch (locType)  
    {  
    case VLT_REGISTER:  
        CorDebugRegister register = 0;  
        locals[i].GetRegister(&register);  
        // now we know which register it is in  
        break;  
    case VLT_REGISTER_RELATIVE:  
        CorDebugRegister baseRegister = 0;  
        LONG offset = 0;  
        locals[i].GetRegister(&register);  
        locals[i].GetOffset(&offset);  
        // now we know the register-relative offset  
        break;  
    case VLT_INVALID:  
        // handle case where we can't access the location  
        break;  
    }  
}  
```  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [ICorDebugVariableHomeEnum 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)
