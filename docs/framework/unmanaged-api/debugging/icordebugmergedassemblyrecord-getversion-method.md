---
title: ICorDebugMergedAssemblyRecord：： GetVersion 方法
ms.date: 03/30/2017
ms.assetid: c6858b06-ae26-4312-b325-ea6025016675
ms.openlocfilehash: 0c89d0749281da412bbf71400d51bee1ed651fbe
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129775"
---
# <a name="icordebugmergedassemblyrecordgetversion-method"></a>ICorDebugMergedAssemblyRecord：： GetVersion 方法
取得組件的版本資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetVersion(  
   [out] USHORT *pMajor,   
   [out] USHORT *pMinor,   
   [out] USHORT *pBuild,   
   [out] USHORT *pRevision  
);  
```  
  
## <a name="parameters"></a>參數  
 `pMajor`  
 [out] 主要版本號碼的指標。  
  
 `pMinor`  
 [out] 次要版本號碼的指標。  
  
 `pBuild`  
 [out] 組建編號的指標。  
  
 `pRevision`  
 [out] 修訂編號的指標。  
  
## <a name="remarks"></a>備註  
 如需組件版本號碼的相關資訊，請參閱 <xref:System.Version> 類別主題。  
  
> [!NOTE]
> 這個方法僅適用於 .NET Native。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugMergedAssemblyRecord 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
