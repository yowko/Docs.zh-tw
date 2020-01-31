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
ms.openlocfilehash: 3654c94975d16e35d5c3d8e762730d17509a2c6d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788883"
---
# <a name="icordebugdatatargetgetplatform-method"></a>ICorDebugDataTarget::GetPlatform 方法
提供目標進程執行所在平臺的相關資訊，包括處理器架構和作業系統。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetPlatform([out] CorDebugPlatform * pTargetPlatform);  
```  
  
## <a name="parameters"></a>參數  
 `pTargetPlatform`  
 脫銷描述目標平臺之[CorDebugPlatformEnum](cordebugplatform-enumeration.md)列舉的指標。  
  
## <a name="remarks"></a>備註  
 [ICorDebug](icordebug-interface.md)介面會使用 `CorDebugPlatformEnum` 列舉傳回值來判斷目標進程的詳細資料，例如其指標大小、位址空間配置、暫存器組、指令格式、內容配置和呼叫慣例。  
  
 `pTargetPlatform` 值可能會參考針對目標模擬的平臺，而不是指定實際使用的硬體。 例如，在 windows 作業系統64位版本的 windows on windows （WOW）環境中執行的進程，應使用[CorDebugPlatformEnum](cordebugplatform-enumeration.md)列舉的 `CORDB_PLATFORM_WINDOWS_X86` 值。  
  
 這個方法必須成功。 如果失敗，則目標平臺無法使用。 方法可能會因為下列原因而失敗：  
  
- 針對目標模擬的平臺無法使用。  
  
- 目標平臺上的實際硬體無法使用。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugDataTarget 介面](icordebugdatatarget-interface.md)
- [偵錯介面](debugging-interfaces.md)
- [偵錯](index.md)
