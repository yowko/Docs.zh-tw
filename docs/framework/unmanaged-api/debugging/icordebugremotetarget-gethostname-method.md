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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fda739a71a133a8c6177d0c7b8e0402d1dc97c4f
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/01/2019
ms.locfileid: "57202206"
---
# <a name="icordebugremotetargetgethostname-method"></a>ICorDebugRemoteTarget::GetHostName 方法
傳回遠端偵錯目標電腦的完整網域名稱或 IPv4 位址。 目前不支援 IPV6。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetHostName (  
    [in] ULONG32      cchHostName,  
    [out] ULONG32*    pcchHostName,  
    [out, size_is(cchHostName), length_is(*pcchHostName)]  
            WCHAR szHostName[]  
```  
  
#### <a name="parameters"></a>參數  
 `cchHostName`  
 [in]大小，以字元為單位的`szHostName`緩衝區。 如果這個參數是 0 (零)，則 `szHostName` 必須是 null。  
  
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
 這個方法是由偵錯工具寫入器實作。 它必須遵循的多個呼叫架構：第一次呼叫中，呼叫端傳遞 null 兩者`cchHostName`並`szHostName`，和`pcchHostName`傳回的所需的緩衝區大小。 第二次呼叫時，先前傳回的大小會在 `cchHostName` 中傳遞，而大小適當的緩衝區會在 `szHostName` 中傳遞。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** 3.5 SP1  
  
## <a name="see-also"></a>另請參閱
- [ICorDebugRemoteTarget 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)
- [ICorDebug 介面](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
