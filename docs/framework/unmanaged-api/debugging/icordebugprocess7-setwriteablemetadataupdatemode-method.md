---
title: ICorDebugProcess7::SetWriteableMetadataUpdateMode 方法
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugProcess7.SetWriteableMetadataUpdateMode
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 8589bba7-7304-45ba-9e31-7bf43dfd5c19
topic_type:
- apiref
ms.openlocfilehash: 6de75e1e27660ac91bd6320a501db47f3b055fb0
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212252"
---
# <a name="icordebugprocess7setwriteablemetadataupdatemode-method"></a>ICorDebugProcess7::SetWriteableMetadataUpdateMode 方法
[.NET Framework 4.5.2 與更新版本提供支援]  
  
 設定偵錯工具如何處理對目標處理序中之中繼資料的記憶體中更新。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT SetWriteableMetadataUpdateMode(  
   WriteableMetadataUpdateMode flags  
);  
```  
  
## <a name="parameters"></a>參數  
 `flags`  
 [WriteableMetadataUpdateMode](writeablemetadataupdatemode-enumeration.md)列舉值，指定目標進程中的中繼資料的記憶體中更新是否可見（）， `WriteableMetadataUpdateMode::AlwaysShowUpdates` 或不會 `WriteableMetadataUpdateMode::LegacyCompatPolicy` 對偵錯工具顯示（）。  
  
## <a name="remarks"></a>備註  
 對目標處理序之中繼資料的更新可能是透過 [編輯後繼續]、分析工具或 <xref:System.Reflection.Emit?displayProperty=nameWithType>。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugProcess7 介面](icordebugprocess7-interface.md)
- [偵錯介面](debugging-interfaces.md)
