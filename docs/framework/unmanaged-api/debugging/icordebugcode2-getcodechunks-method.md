---
title: "ICorDebugCode2::GetCodeChunks 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugCode2.GetCodeChunks
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugCode2::GetCodeChunks
helpviewer_keywords:
- GetCodeChunks method [.NET Framework debugging]
- ICorDebugCode2::GetCodeChunks method [.NET Framework debugging]
ms.assetid: 210a2f02-2678-4555-bc4a-78a0408764c8
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4b90913f05cc2e0a3e98a5890f76a41eb2eafc6d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcode2getcodechunks-method"></a>ICorDebugCode2::GetCodeChunks 方法
取得這個程式碼物件組成的程式碼區塊。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetCodeChunks (  
    [in]  ULONG32     cbufSize,  
    [out] ULONG32     *pcnumChunks,  
    [out, size_is(cbufSize), length_is(*pcnumChunks)]   
        CodeChunkInfo chunks[]  
);  
```  
  
#### <a name="parameters"></a>參數  
 `cbufSize`  
 [in]大小`chunks`陣列。  
  
 `pcnumChunks`  
 [out]區塊中傳回的數目`chunks`陣列。  
  
 `chunks`  
 [out]結構的陣列 」 CodeChunkInfo"，其中每一個都代表單一的程式碼區塊。 如果值`cbufSize`是 0，這個參數可以是 null。  
  
## <a name="remarks"></a>備註  
 程式碼區塊將會永遠不會重疊，而且它們會將遵照的順序中串連這些區塊會有已由[Icordebugcode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md)。 在.NET Framework 2.0 版的 Microsoft intermediate language (MSIL) 程式碼物件將由一個單一程式碼區塊所組成。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 
