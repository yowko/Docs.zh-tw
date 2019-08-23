---
title: ICorDebugFunction 介面
ms.date: 03/30/2017
api_name:
- ICorDebugFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction
helpviewer_keywords:
- ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: 783faea9-8083-41c1-b04a-51a81ac4c8f3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ae65c59efe1d925b5e058e8664d1e093fdfec875
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917197"
---
# <a name="icordebugfunction-interface"></a>ICorDebugFunction 介面

表示 Managed 函式或方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[CreateBreakpoint 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-createbreakpoint-method.md)|在此函式的開頭建立中斷點。|  
|[GetClass 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getclass-method.md)|取得 ICorDebugClass 物件, 代表此函式為其成員的類別。|  
|[GetCurrentVersionNumber 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md)|取得對此函式進行之最新編輯的版本號碼。|  
|[GetILCode 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getilcode-method.md)|取得此函式的 Microsoft 中繼語言 (MSIL) 程式碼。|  
|[GetLocalVarSigToken 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getlocalvarsigtoken-method.md)|取得這個`ICorDebugFunction`實例所表示之函式的區域變數簽章的元資料標記。|  
|[GetModule 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getmodule-method.md)|取得定義此函數的模組。|  
|[GetNativeCode 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getnativecode-method.md)|取得此函式的原生程式碼。|  
|[GetToken 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-gettoken-method.md)|取得此函式的元資料標記。|  
  
## <a name="remarks"></a>備註  
 `ICorDebugFunction`介面不代表具有泛型型別參數的函式。 例如, 實例會`ICorDebugFunction`代表`Func<T>` , 而不`Func<string>`是。 呼叫[ICorDebugILFrame2:: EnumerateTypeParameters](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md)以取得泛型型別參數。  
  
 方法的元資料標記`mdMethodDef`與方法的`ICorDebugFunction`物件之間的關聯性, 取決於函式上是否允許 [編輯後繼續]:  
  
- 如果函式不允許 [編輯後繼續], 則`ICorDebugFunction`物件`mdMethodDef`與標記之間會存在一對一關聯性。 也就是, 函式有`ICorDebugFunction`一個物件和`mdMethodDef`一個 token。  
  
- 如果允許在函式上進行 [編輯後繼續], 則`ICorDebugFunction`物件`mdMethodDef`與標記之間會存在多對一關聯性。 也就是說, 函式可能有多個實例`ICorDebugFunction`, 每個函式版本各一個, 但只會有一個`mdMethodDef` token。  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
