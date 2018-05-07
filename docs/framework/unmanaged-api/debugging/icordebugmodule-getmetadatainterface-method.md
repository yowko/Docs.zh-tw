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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fef23f2b128b1e5393c5104b6e33758882b34882
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugmodulegetmetadatainterface-method"></a>ICorDebugModule::GetMetaDataInterface 方法
取得可以用來檢查模組的中繼資料的中繼資料介面物件。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetMetaDataInterface (  
    [in] REFIID      riid,  
    [out] IUnknown **ppObj  
);  
```  
  
#### <a name="parameters"></a>參數  
 `riid`  
 [in]指定的中繼資料介面的參考識別碼。  
  
 `ppObj`  
 [out]位址指標`T:IUnknown`物件的其中一個[中繼資料介面](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)。  
  
## <a name="remarks"></a>備註  
 偵錯工具可以使用`GetMetaDataInterface`方法來建立模組，則必須執行才能編輯該模組的原始中繼資料的副本。 偵錯工具呼叫`GetMetaDataInterface`取得[IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)介面物件模組，然後呼叫[imetadataemit:: Savetomemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetomemory-method.md)模組的中繼資料的副本儲存至記憶體。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [中繼資料](../../../../docs/framework/unmanaged-api/metadata/index.md)
