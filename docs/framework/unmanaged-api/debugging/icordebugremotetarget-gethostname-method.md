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
ms.openlocfilehash: 3e946d8a27ec6b568b2f3c3633695c9f6795c938
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712049"
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
 在緩衝區的大小（以字元為單位） `szHostName` 。 如果這個參數是 0 (零)，則 `szHostName` 必須是 null。  
  
 `pcchHostName`  
 [out] 在主機名稱或 IP 位址中的字元數，包括 null 結束字元。 此參數可以是 null。  
  
 `szHostName`  
 [out] 包含主機名稱或 IP 位址的緩衝區。  
  
## <a name="return-value"></a>傳回值  

 S_OK  
 成功傳回主機名稱或 IP 位址。  
  
 E_FAIL (或其他 E_ 傳回碼)  
 無法傳回主機名稱或 IP 位址。  
  
## <a name="remarks"></a>備註  

 這個方法是由偵錯工具寫入器實作。 它必須遵循多個呼叫範例：在第一次呼叫時，呼叫端會將 null 傳遞給 `cchHostName` 和 `szHostName` ，並傳回 `pcchHostName` 所需緩衝區的大小。 第二次呼叫時，先前傳回的大小會在 `cchHostName` 中傳遞，而大小適當的緩衝區會在 `szHostName` 中傳遞。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cordebug.h .idl  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：** 3.5 SP1  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugRemoteTarget 介面](icordebugremotetarget-interface.md)
- [ICorDebug 介面](icordebug-interface.md)
