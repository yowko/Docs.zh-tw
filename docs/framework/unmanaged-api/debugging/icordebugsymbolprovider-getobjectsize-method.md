---
title: ICorDebugSymbolProvider::GetObjectSize 方法
ms.date: 03/30/2017
ms.assetid: 3c564396-ac64-4ef3-b4f6-df96f1d46fc7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1da526ac133604fa43081f86988459c4238517c9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugsymbolprovidergetobjectsize-method"></a>ICorDebugSymbolProvider::GetObjectSize 方法
傳回根據某物件之 typespec 簽章的該物件大小。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetObjectSize(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [out] ULONG32 *pObjectSize  
);  
```  
  
#### <a name="parameters"></a>參數  
 `cbSignature`  
 [in] Typespec 簽章中的位元組數目。  
  
 typeSig  
 [in] Typespec 簽章。  
  
 `pObjectSize`  
 [out] 物件大小的指標。  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
>  本方法只適用於 .NET 原生。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorDebugSymbolProvider 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
