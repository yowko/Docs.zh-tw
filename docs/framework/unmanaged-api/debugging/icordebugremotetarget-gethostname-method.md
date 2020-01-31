---
title: ICorDebugRemoteTarget::GetHostName 方法
ms.date: 03/30/2017
api_name:
- ICorDebugRemoteTarget.GetHostName
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget::GetHostName
helpviewer_keywords:
- ICorDebugRemoteTarget::GetHostName method [.NET Framework debugging]
- GetHostName method, ICorDebugRemoteTarget interface [.NET Framework debugging]
ms.assetid: 1c7276f7-7e54-470c-808c-e13745ac07a1
topic_type:
- apiref
ms.openlocfilehash: f177d441da3bd967750781e487d9fed42bc132f5
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791952"
---
# <a name="icordebugremotetargetgethostname-method"></a>ICorDebugRemoteTarget::GetHostName 方法
傳回遠端偵錯目標電腦的完整網域名稱或 IPv4 位址。 目前不支援 IPV6。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetHostName (  
    [in] ULONG32      cchHostName,  
    [out] ULONG32*    pcchHostName,  
    [out, size_is(cchHostName), length_is(*pcchHostName)]  
            WCHAR szHostName[]  
```  
  
## <a name="parameters"></a>參數  
 `cchHostName`  
 在`szHostName` 緩衝區的大小（以字元為單位）。 如果這個參數是 0 (零)，則 `szHostName` 必須是 null。  
  
 `pcchHostName`  
 [out] 在主機名稱或 IP 位址中的字元數，包括 null 結束字元。 這個參數可以是 null。  
  
 `szHostName`  
 [out] 包含主機名稱或 IP 位址的緩衝區。  
  
## <a name="return-value"></a>傳回值  
 S_OK  
 成功傳回主機名稱或 IP 位址。  
  
 E_FAIL (或其他 E_ 傳回碼)  
 無法傳回主機名稱或 IP 位址。  
  
## <a name="remarks"></a>備註  
 這個方法是由偵錯工具寫入器實作。 它必須遵循多個呼叫範例：第一次呼叫時，呼叫端會將 null 傳遞給 `cchHostName` 和 `szHostName`，而 `pcchHostName` 會傳回所需的緩衝區大小。 第二次呼叫時，先前傳回的大小會在 `cchHostName` 中傳遞，而大小適當的緩衝區會在 `szHostName` 中傳遞。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cordebug.h .idl  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：** 3.5 SP1  
  
## <a name="see-also"></a>請參閱

- [ICorDebugRemoteTarget 介面](icordebugremotetarget-interface.md)
- [ICorDebug 介面](icordebug-interface.md)
