---
title: ICorDebugILFrame4::GetCodeEx 方法
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILFrame4.GetLocalVariableEx
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: aeda0e42-29ee-4ca8-9f21-ac4641677a62
topic_type:
- apiref
ms.openlocfilehash: 582e28c18f36b253425b1e0a2034cdd262fddd57
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213734"
---
# <a name="icordebugilframe4getcodeex-method"></a>ICorDebugILFrame4::GetCodeEx 方法
[.NET Framework 4.5.2 與更新版本提供支援]  
  
 取得此堆疊框架執行之程式碼的指標。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetCodeEx(  
   [in] ILCodeKind flags,
   [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a>參數  
 `flags`  
 在[ILCodeKind](ilcodekind-enumeration.md)列舉成員，指定由 Profiler 的 ReJIT 要求所定義的中繼語言（IL）是否包含在框架中。  
  
 `ppCode`  
 脫銷代表此堆疊框架正在執行之程式碼的 "ICorDebugCode" 物件位址的指標。  
  
## <a name="remarks"></a>備註  
 這個方法類似于[ICorDebugFrame：： GetCode](icordebugframe-getcode-method.md)方法，不同之處在于它會選擇性地存取分析工具的 ReJIT 要求所定義的程式碼。 使用的值呼叫此方法 `flags` `ILCODE_ORIGINAL_IL` 相當於呼叫[GetCode](icordebugframe-getcode-method.md); 如果已檢測方法，則無法存取其 IL。 `ILCODE_REJIT_IL` 可讓偵錯工具存取分析工具的 ReJIT 要求所定義的 IL。 如果未檢測 IL， `ppCode` 則為**null**，且方法會傳回 `S_OK` 。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugILFrame4 介面](icordebugilframe4-interface.md)
- [偵錯介面](debugging-interfaces.md)
- [ReJIT：使用說明指南](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
