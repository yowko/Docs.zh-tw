---
title: 'ICorDebugSymbolProvider:: GetTypeProps 方法'
ms.date: 03/30/2017
ms.assetid: 35ac4140-91ea-4c77-b1c4-1daf41986ca5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8c8ea3a201cc94ef7bdf679371ef43ab2641b791
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955535"
---
# <a name="icordebugsymbolprovidergettypeprops-method"></a>ICorDebugSymbolProvider:: GetTypeProps 方法
根據 vtable 中指定的相對虛擬位址 (RVA)，傳回類型之屬性的相關資訊，例如其泛型參數的簽章數目。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetTypeProps(  
   [in]  ULONG32 vtableRva,  
   [in]  ULONG32 cbSignature,  
   [out] ULONG32 *pcbSignature,  
   [out, size_is(cbSignature), length_is(*pcbSignature)] BYTE signature[]  
);  
```  
  
## <a name="parameters"></a>參數  
 `tableRva`  
 [in] vtable 中的相對虛擬位址 (RVA)。  
  
 `cbSignature`  
 [in] `signature` 陣列的大小。 請參閱＜備註＞一節。  
  
 `pcbSignature`  
 [out] [out] 所傳回 `signature` 陣列的大小指標。  
  
 `signature`  
 [out] 保留所有泛型參數之 TypeSpec 簽章的緩衝區。  
  
## <a name="remarks"></a>備註  
 若要取得`signature`類型陣列所需的大小, 請`cbSignature`將引數設為 0 `signature` , 並將設定為**null**。 當這個方法傳回時，`pcbSignature` 會包含 `signature` 陣列所需的位元組數目。  
  
> [!NOTE]
> 這個方法僅適用於 .NET Native。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [GetMethodProps 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodprops-method.md)
- [ICorDebugSymbolProvider 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
