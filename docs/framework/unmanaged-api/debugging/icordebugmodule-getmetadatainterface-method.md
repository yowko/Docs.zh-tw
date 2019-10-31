---
title: ICorDebugModule::GetMetaDataInterface 方法
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetMetaDataInterface
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetMetaDataInterface
helpviewer_keywords:
- ICorDebugModule::GetMetaDatainterface method [.NET Framework debugging]
- GetMetaDatainterface method [.NET Framework debugging]
ms.assetid: 30d906f2-cf35-4fa9-9d4c-0c31b58c9f3a
topic_type:
- apiref
ms.openlocfilehash: fb96949e22b4edfc0e64780a54bb38da44eb8369
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129554"
---
# <a name="icordebugmodulegetmetadatainterface-method"></a>ICorDebugModule::GetMetaDataInterface 方法
取得可用於檢查模組中繼資料的中繼資料介面物件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetMetaDataInterface (  
    [in] REFIID      riid,  
    [out] IUnknown **ppObj  
);  
```  
  
## <a name="parameters"></a>參數  
 `riid`  
 在指定中繼資料介面的參考識別碼。  
  
 `ppObj`  
 脫銷屬於其中一個[中繼資料介面](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)之 `T:IUnknown` 物件的位址指標。  
  
## <a name="remarks"></a>備註  
 偵錯工具可以使用 `GetMetaDataInterface` 方法，針對模組建立原始中繼資料的複本，它必須執行此操作才能編輯該模組。 偵錯工具會呼叫 `GetMetaDataInterface` 來取得模組的[IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)介面物件，然後呼叫[IMetaDataEmit：： SaveToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetomemory-method.md) ，將模組的中繼資料複本儲存至記憶體。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [中繼資料](../../../../docs/framework/unmanaged-api/metadata/index.md)
