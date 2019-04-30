---
title: 'Icordebugsymbolprovider:: Getinstancefieldsymbols 方法'
ms.date: 03/30/2017
ms.assetid: a29b9233-ee67-4b53-b8bc-c00b281e7edb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9ea9afdd2c032e99d7feee6b2935161c70c56787
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994223"
---
# <a name="icordebugsymbolprovidergetinstancefieldsymbols-method"></a>Icordebugsymbolprovider:: Getinstancefieldsymbols 方法
取得對應 TypeSpec 簽章的執行個體欄位符號。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetInstanceFieldSymbols(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugInstanceFieldSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a>參數  
 `cbSignature`  
 [in] `typeSig` 陣列中的位元組數。  
  
 `typeSig`  
 [in] 包含 `typespec` 簽章的位元組陣列。  
  
 `cRequestedSymbols`  
 [in] 要求的符號數目。  
  
 `pcFetchedSymbols`  
 [out] 方法所擷取之符號數的指標。  
  
 `pSymbols`  
 [out]指標[ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)陣列，其中包含所要求的執行個體欄位符號。  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
>  這個方法僅適用於 .NET Native。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [GetStaticFieldSymbols 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getstaticfieldsymbols-method.md)
- [ICorDebugSymbolProvider 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
