---
title: ICorDebugMergedAssemblyRecord::GetPublicKey 方法
ms.date: 03/30/2017
ms.assetid: 72020b72-9611-4bc3-b1e7-5a16b023bfa3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1cc02c1f69235403e2f5df28168e17a70f183682
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762422"
---
# <a name="icordebugmergedassemblyrecordgetpublickeytoken-method"></a>ICorDebugMergedAssemblyRecord::GetPublicKey 方法
取得組件的公開金鑰語彙基元。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetPublicKeyToken(  
   [in] ULONG32 cbPublicKeyToken,   
   [out] ULONG32 *pcbPublicKeyToken,   
   [out, size_is(cbPublicKeyToken), length_is(*pcbPublicKeyToken)] BYTE pbPublicKeyToken[]  
);  
```  
  
## <a name="parameters"></a>參數  
 `cbPublicKeyToken`  
 [in] `pbPublicKeyToken` 陣列中的最大位元組數。  
  
 `pcbPublicKeyToken`  
 [out] 寫入 `pbPublicKeyToken` 陣列之實際位元組數的指標。  
  
 `pbPublicKeyToken`  
 [out] 包含組件公開金鑰語彙基元之位元組陣列的指標。  
  
## <a name="remarks"></a>備註  
 組件的公開金鑰語彙基元是其公開金鑰之 SHA1 雜湊的最後 8 個位元組。  
  
> [!NOTE]
>  這個方法僅適用於 .NET Native。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugMergedAssemblyRecord 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
