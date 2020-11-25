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
ms.openlocfilehash: 5671f8cb51210c27dffdedba28b4b145b3fedc55
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732550"
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
 [WriteableMetadataUpdateMode](writeablemetadataupdatemode-enumeration.md)列舉值，這個值會指定在目標進程中中繼資料的記憶體中更新是否為可見的 (`WriteableMetadataUpdateMode::AlwaysShowUpdates`) ，或在 `WriteableMetadataUpdateMode::LegacyCompatPolicy` 偵錯工具) 看不到 (。  
  
## <a name="remarks"></a>備註  

 對目標處理序之中繼資料的更新可能是透過 [編輯後繼續]、分析工具或 <xref:System.Reflection.Emit?displayProperty=nameWithType>。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugProcess7 介面](icordebugprocess7-interface.md)
- [偵錯介面](debugging-interfaces.md)
