---
title: CreateCordbObject 函式
ms.date: 03/30/2017
api_name:
- CreateCoredbObject
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CreateCordbObject
helpviewer_keywords:
- remote debugging API [Silverlight]
- CreateCordbObject function
- Silverlight, remote debugging
ms.assetid: b259821d-4fa7-464d-85cf-304dfffc8089
topic_type:
- apiref
ms.openlocfilehash: eccdfcb60b2d2b5d652ccac948c01c16e7cb828d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725972"
---
# <a name="createcordbobject-function"></a>CreateCordbObject 函式

建立偵錯工具介面 ([ICorDebug](icordebug-interface.md)) ，以提供在遠端進程上具現化 managed 偵錯工具的功能。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CordbCreateObject (  
       [in]  int         iDebuggerVersion,
       [out] IUnknown**  ppCordb  
);  
```  
  
## <a name="parameters"></a>參數  

 `iDebuggerVersion`  
 [in] 目標處理序的偵錯工具版本。 這個參數必須是 CorDebugVersion_2_0，才能進行遠端偵錯。  
  
 `ppCordb`  
 擴展指向物件指標的指標，該物件將會轉換成 [ICorDebug](icordebug-interface.md) 介面並傳回。  
  
## <a name="return-value"></a>傳回值  

 S_OK  
 已成功確定處理序中的 CLR 數目，並且已正確填入對應的控制代碼和路徑陣列。  
  
 E_INVALIDARG  
 `ppCordb` 為 null，或 `iDebuggerVersion` 不是 CorDebugVersion_2_0。  
  
 E_OUTOFMEMORY  
 無法為 `ppCordb` 配置足夠的記憶體。  
  
 E_FAIL (或其他 E_ 傳回碼)  
 其他失敗。  
  
## <a name="remarks"></a>備註  

 中傳回的 [ICorDebug](icordebug-interface.md) 介面 `ppCordb` 是所有 managed 偵錯工具的最上層偵錯工具介面。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CoreClrRemoteDebuggingInterfaces。h  
  
 連結 **庫：** mscordbi_macx86.dll  
  
 **.NET Framework 版本：** 3.5 SP1
