---
title: ICorDebugSymbolProvider::GetInstanceFieldSymbols 方法
ms.date: 03/30/2017
ms.assetid: a29b9233-ee67-4b53-b8bc-c00b281e7edb
ms.openlocfilehash: 9c55ce4d36681e173047cfb51515a74899c5a9fe
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791640"
---
# <a name="icordebugsymbolprovidergetinstancefieldsymbols-method"></a>ICorDebugSymbolProvider::GetInstanceFieldSymbols 方法
取得對應 TypeSpec 簽章的執行個體欄位符號。  
  
## <a name="syntax"></a>語法  
  
```cpp  
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
 脫銷[ICorDebugStaticFieldSymbol](icordebugstaticfieldsymbol-interface.md)陣列的指標，其中包含所要求的實例欄位符號。  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
> 這個方法僅適用於 .NET Native。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>請參閱

- [GetStaticFieldSymbols 方法](icordebugsymbolprovider-getstaticfieldsymbols-method.md)
- [ICorDebugSymbolProvider 介面](icordebugsymbolprovider-interface.md)
- [偵錯介面](debugging-interfaces.md)
