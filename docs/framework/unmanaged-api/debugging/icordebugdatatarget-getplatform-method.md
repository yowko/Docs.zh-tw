---
title: ICorDebugDataTarget::GetPlatform 方法
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget.GetPlatform Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget::GetPlatform
helpviewer_keywords:
- GetPlatform method [.NET Framework debugging]
- ICorDebugDataTarget::GetPlatform method [.NET Framework debugging]
ms.assetid: 9ee96c9d-7a3d-4129-a6cc-7675c7f2dda4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ab4cdaf87b6fd65eecbe62f2e3b927eee6094e72
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57496166"
---
# <a name="icordebugdatatargetgetplatform-method"></a>ICorDebugDataTarget::GetPlatform 方法
提供的平台，包括處理器架構與目標處理序執行所在的作業系統的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetPlatform([out] CorDebugPlatform * pTargetPlatform);  
```  
  
## <a name="parameters"></a>參數  
 `pTargetPlatform`  
 [out]指標[CorDebugPlatformEnum](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md)列舉型別描述的目標平台。  
  
## <a name="remarks"></a>備註  
 `CorDebugPlatformEnum`列舉型別傳回值由[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)介面，以判斷目標處理序，例如其指標大小、 位址空間配置、 暫存器組合、 指示格式、 內容配置的詳細資料和呼叫慣例。  
  
 `pTargetPlatform`值可能會參考正在模擬的目標，而不是使用中指定實際的硬體平台。 例如，使用 64 位元版本的 Windows 作業系統執行 Windows (WOW) 環境上的 Windows 中的程序應該`CORDB_PLATFORM_WINDOWS_X86`的值[CorDebugPlatformEnum](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md)列舉型別。  
  
 這個方法必須成功。 如果失敗，目標平台是無法使用。 此方法可能會失敗，原因如下：  
  
-   正在模擬的目標平台是無法使用。  
  
-   目標平台上實際的硬體就無法使用。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [ICorDebugDataTarget 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
