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
ms.openlocfilehash: ba0e0b1b2bac785e28f41e09dda74841121a748d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794508"
---
# <a name="icordebugfunction-interface"></a>ICorDebugFunction 介面

表示 Managed 函式或方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[CreateBreakpoint 方法](icordebugfunction-createbreakpoint-method.md)|在此函式的開頭建立中斷點。|  
|[GetClass 方法](icordebugfunction-getclass-method.md)|取得 ICorDebugClass 物件，代表此函式為其成員的類別。|  
|[GetCurrentVersionNumber 方法](icordebugfunction-getcurrentversionnumber-method.md)|取得對此函式進行之最新編輯的版本號碼。|  
|[GetILCode 方法](icordebugfunction-getilcode-method.md)|取得此函式的 Microsoft 中繼語言（MSIL）程式碼。|  
|[GetLocalVarSigToken 方法](icordebugfunction-getlocalvarsigtoken-method.md)|取得此 `ICorDebugFunction` 實例所表示之函式的區域變數簽章的元資料標記。|  
|[GetModule 方法](icordebugfunction-getmodule-method.md)|取得定義此函數的模組。|  
|[GetNativeCode 方法](icordebugfunction-getnativecode-method.md)|取得此函式的原生程式碼。|  
|[GetToken 方法](icordebugfunction-gettoken-method.md)|取得此函式的元資料標記。|  
  
## <a name="remarks"></a>備註  
 `ICorDebugFunction` 介面不代表具有泛型型別參數的函式。 例如，`ICorDebugFunction` 實例會代表 `Func<T>`，但不會 `Func<string>`。 呼叫[ICorDebugILFrame2：： EnumerateTypeParameters](icordebugilframe2-enumeratetypeparameters-method.md)以取得泛型型別參數。  
  
 方法的元資料標記、`mdMethodDef`和方法的 `ICorDebugFunction` 物件之間的關聯性，取決於函式是否允許 [編輯後繼續]：  
  
- 如果函式不允許 [編輯後繼續]，則 `ICorDebugFunction` 物件和 `mdMethodDef` token 之間存在一對一關聯性。 也就是說，函式有一個 `ICorDebugFunction` 物件和一個 `mdMethodDef` token。  
  
- 如果函式允許 [編輯後繼續]，則 `ICorDebugFunction` 物件和 `mdMethodDef` token 之間存在多對一關聯性。 也就是說，函式可能有許多 `ICorDebugFunction`的實例，每個版本的函式各有一個，但只有一個 `mdMethodDef` token。  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 連結**庫：** Corguids.lib .lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯介面](debugging-interfaces.md)
