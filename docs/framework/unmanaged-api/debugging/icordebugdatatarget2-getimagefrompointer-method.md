---
title: ICorDebugDataTarget2::GetImageFromPointer 方法
ms.date: 03/30/2017
ms.assetid: 939cabe1-b647-4090-b662-eeec23c6c58d
ms.openlocfilehash: 3ac1f8ab98583357a3aa622b5032d9ae121ebdf2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178925"
---
# <a name="icordebugdatatarget2getimagefrompointer-method"></a>ICorDebugDataTarget2::GetImageFromPointer 方法
從模組中的位址傳回模組基底位址和大小。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetImageFromPointer(  
   [in] CORDB_ADDRESS addr,
   [out] CORDB_ADDRESS *pImageBase,
   [out] ULONG32 *pSize  
);  
```  
  
## <a name="parameters"></a>參數  
 `addr`  
 表示模組中位址[CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)值。  
  
 `pImageBase`  
 [出]表示模組基本位址[的CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)值。  
  
 `pSize`  
 模組大小的指標。  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
> 這個方法僅適用於 .NET Native。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET 框架版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugDataTarget2 介面](icordebugdatatarget2-interface.md)
- [偵錯介面](debugging-interfaces.md)
