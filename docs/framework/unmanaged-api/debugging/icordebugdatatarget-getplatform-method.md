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
ms.openlocfilehash: e8612b23cbfa506fddb2fad712848b285b9ac28e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679789"
---
# <a name="icordebugdatatargetgetplatform-method"></a>ICorDebugDataTarget::GetPlatform 方法

提供目標進程執行所在平臺的相關資訊，包括處理器架構和作業系統。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetPlatform([out] CorDebugPlatform * pTargetPlatform);  
```  
  
## <a name="parameters"></a>參數  

 `pTargetPlatform`  
 擴展描述目標平臺之 [CorDebugPlatformEnum](cordebugplatform-enumeration.md) 列舉的指標。  
  
## <a name="remarks"></a>備註  

 `CorDebugPlatformEnum` [ICorDebug](icordebug-interface.md)介面會使用列舉傳回值來判斷目標進程的詳細資料，例如它的指標大小、位址空間配置、暫存器集、指令格式、內容配置和呼叫慣例。  
  
 此 `pTargetPlatform` 值可能會參考針對目標模擬的平臺，而不是指定實際使用的硬體。 例如，在 windows on windows 上執行的處理常式，在64位版本的 Windows 作業系統上 (WOW) 環境應該使用 `CORDB_PLATFORM_WINDOWS_X86` [CorDebugPlatformEnum](cordebugplatform-enumeration.md) 列舉的值。  
  
 此方法必須成功。 如果失敗，則無法使用目標平臺。 方法可能會因為下列原因而失敗：  
  
- 針對目標模擬的平臺無法使用。  
  
- 目標平臺上的實際硬體無法使用。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugDataTarget 介面](icordebugdatatarget-interface.md)
- [偵錯介面](debugging-interfaces.md)
- [偵錯](index.md)
