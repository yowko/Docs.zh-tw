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
ms.openlocfilehash: ca21911f3d16b79887b9d6d8185f8fab17651321
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59093211"
---
# <a name="icordebugfunction-interface"></a>ICorDebugFunction 介面

表示 Managed 函式或方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[CreateBreakpoint 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-createbreakpoint-method.md)|此函式的開頭建立的中斷點。|  
|[GetClass 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getclass-method.md)|取得 ICorDebugClass 物件，表示此函式所屬的類別。|  
|[GetCurrentVersionNumber 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md)|取得最新的編輯，此函式的版本號碼。|  
|[GetILCode 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getilcode-method.md)|取得此函式中的 Microsoft intermediate language (MSIL) 程式碼。|  
|[GetLocalVarSigToken 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getlocalvarsigtoken-method.md)|取得中繼資料語彙基元區域變數簽章的函式，這由`ICorDebugFunction`執行個體。|  
|[GetModule 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getmodule-method.md)|取得在其中定義這個函式的模組。|  
|[GetNativeCode 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getnativecode-method.md)|取得此函式中的原生程式碼。|  
|[GetToken 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-gettoken-method.md)|取得此函式的中繼資料語彙基元。|  
  
## <a name="remarks"></a>備註  
 `ICorDebugFunction`介面並不代表泛型類型參數的函式。 例如，`ICorDebugFunction`執行個體代表`Func<T>`而非`Func<string>`。 呼叫[ICorDebugILFrame2::EnumerateTypeParameters](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md)取得泛型型別參數。  
  
 方法的中繼資料語彙基元，之間的關聯性`mdMethodDef`，以及方法的`ICorDebugFunction`物件所相依的函數上是否允許編輯後繼續：  
  
-   如果函式上不允許編輯後繼續，之間有一對一的關係`ICorDebugFunction`物件和`mdMethodDef`語彙基元。 也就是說，函式有一個`ICorDebugFunction`物件和一個`mdMethodDef`語彙基元。  
  
-   如果函式允許編輯後繼續，之間存在多對一關聯性`ICorDebugFunction`物件和`mdMethodDef`語彙基元。 也就是說，函式可能有許多執行個體`ICorDebugFunction`，一個用於每個版本的函式，不過只有一個`mdMethodDef`語彙基元。  
  
> [!NOTE]
>  這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
