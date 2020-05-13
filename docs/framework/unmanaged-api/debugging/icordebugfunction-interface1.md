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
ms.openlocfilehash: 6b7b6969c1f207decbf47217e98b7fee3aa9ce54
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213233"
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
|[GetLocalVarSigToken 方法](icordebugfunction-getlocalvarsigtoken-method.md)|取得這個實例所表示之函式的區域變數簽章的元資料標記 `ICorDebugFunction` 。|  
|[GetModule 方法](icordebugfunction-getmodule-method.md)|取得定義此函數的模組。|  
|[GetNativeCode 方法](icordebugfunction-getnativecode-method.md)|取得此函式的原生程式碼。|  
|[GetToken 方法](icordebugfunction-gettoken-method.md)|取得此函式的元資料標記。|  
  
## <a name="remarks"></a>備註  
 `ICorDebugFunction`介面不代表具有泛型型別參數的函式。 例如， `ICorDebugFunction` 實例會代表， `Func<T>` 而不是 `Func<string>` 。 呼叫[ICorDebugILFrame2：： EnumerateTypeParameters](icordebugilframe2-enumeratetypeparameters-method.md)以取得泛型型別參數。  
  
 方法的元資料標記與方法的物件之間的關聯性， `mdMethodDef` `ICorDebugFunction` 取決於函式上是否允許 [編輯後繼續]：  
  
- 如果函式不允許 [編輯後繼續]，則物件與標記之間會存在一對一關聯性 `ICorDebugFunction` `mdMethodDef` 。 也就是，函式有一個 `ICorDebugFunction` 物件和一個 `mdMethodDef` token。  
  
- 如果允許在函式上進行 [編輯後繼續]，則物件與標記之間會存在多對一關聯性 `ICorDebugFunction` `mdMethodDef` 。 也就是說，函式可能有多個實例 `ICorDebugFunction` ，每個函式版本各一個，但只會有一個 `mdMethodDef` token。  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 連結**庫：** Corguids.lib .lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯介面](debugging-interfaces.md)
