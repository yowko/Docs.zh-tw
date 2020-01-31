---
title: ICorDebugSymbolProvider::GetMethodProps 方法
ms.date: 03/30/2017
ms.assetid: 8f836b80-b7a5-460b-bf76-5f0e45652aea
ms.openlocfilehash: 58642d0a9b1cfe1fd969f39fa7e5ab22a8dbfa05
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791588"
---
# <a name="icordebugsymbolprovidergetmethodprops-method"></a>ICorDebugSymbolProvider::GetMethodProps 方法
傳回方法屬性的相關資訊，例如方法的中繼資料語彙基元，以及其泛型參數的相關資訊 (假設該方法中有相對虛擬位址 (RVA))。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetMethodProps(  
   [in]  ULONG32 codeRva,  
   [out] mdToken *pMethodToken,  
   [out] ULONG32 *pcGenericParams,  
   [in]  ULONG32 cbSignature,  
   [out] ULONG32 *pcbSignature,  
   [out, size_is(cbSignature), length_is(*pcbSignature)] BYTE signature[]  
);  
```  
  
## <a name="parameters"></a>參數  
 `codeRVA`  
 [in] 方法中的相對虛擬位址，將會擷取其相關資訊。  
  
 `pMethodToken`  
 [out] 方法的中繼資料語彙基元指標。  
  
 `pcGenericParams`  
 [out] 與這個方法相關聯之泛型參數的數目指標。  
  
 `cbSignature`  
 [in] `signature` 陣列的大小。 請參閱＜備註＞一節。  
  
 `pcbSignature`  
 [out] 所傳回之 `signature` 陣列的大小指標。  
  
 `signature`  
 [out] 保留所有泛型參數之 TypeSpec 簽章的緩衝區。  
  
## <a name="remarks"></a>備註  
 若要取得方法的 `signature` 陣列所需的大小，請將 `cbSignature` 引數設定為0，並將 `signature` 為**null**。 當這個方法傳回時，`pcbSignature` 會包含 `signature` 陣列所需的位元組數目。  
  
> [!NOTE]
> 這個方法僅適用於 .NET Native。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>請參閱

- [GetTypeProps 方法](icordebugsymbolprovider-gettypeprops-method.md)
- [ICorDebugSymbolProvider 介面](icordebugsymbolprovider-interface.md)
- [偵錯介面](debugging-interfaces.md)
