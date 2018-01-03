---
title: ICorDebugFunction Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunction
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFunction
helpviewer_keywords: ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: 783faea9-8083-41c1-b04a-51a81ac4c8f3
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bd0dbe1304d85c856880c989312afb11d3b554c3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugfunction-interface1"></a>ICorDebugFunction Interface1
表示 Managed 函式或方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[CreateBreakpoint 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-createbreakpoint-method.md)|此函式的開頭建立中斷點。|  
|[GetClass 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getclass-method.md)|取得 ICorDebugClass 物件，表示此函式所屬的類別。|  
|[GetCurrentVersionNumber 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md)|取得最新的編輯，此函式的版本號碼。|  
|[GetILCode 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getilcode-method.md)|此函式取得的 Microsoft intermediate language (MSIL) 程式碼。|  
|[GetLocalVarSigToken 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getlocalvarsigtoken-method.md)|取得中繼資料語彙基元所表示的函式的本機變數簽章`ICorDebugFunction`執行個體。|  
|[GetModule 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getmodule-method.md)|取得定義此函式的模組。|  
|[GetNativeCode 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getnativecode-method.md)|取得此函式中的原生程式碼。|  
|[GetToken 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-gettoken-method.md)|取得此函式的中繼資料語彙基元。|  
  
## <a name="remarks"></a>備註  
 `ICorDebugFunction`介面不代表泛型型別參數的函式。 例如，`ICorDebugFunction`代表執行個體`Func<T>`但不是`Func<string>`。 呼叫[icordebugilframe2:: Enumeratetypeparameters](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md)取得泛型型別參數。  
  
 方法的中繼資料語彙基元之間的關聯性`mdMethodDef`，和該方法的`ICorDebugFunction`物件所相依的函式上是否允許編輯後繼續：  
  
-   如果函式上不允許編輯後繼續，之間有一對一的關聯性`ICorDebugFunction`物件和`mdMethodDef`語彙基元。 也就是說，函式有一個`ICorDebugFunction`物件和一個`mdMethodDef`語彙基元。  
  
-   如果函式允許編輯後繼續，多對一關聯性之間有`ICorDebugFunction`物件和`mdMethodDef`語彙基元。 也就是說，函式可能會有許多執行個體`ICorDebugFunction`，一個用於每個版本的函式，但是只有一個`mdMethodDef`語彙基元。  
  
> [!NOTE]
>  這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
