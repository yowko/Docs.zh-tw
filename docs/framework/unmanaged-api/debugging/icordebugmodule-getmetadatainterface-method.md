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
ms.openlocfilehash: f5d0dd7a99087b21a5f827e4dce0f6342ae7b25a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501764"
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
 脫銷物件位址的指標， `T:IUnknown` 這是其中一個[中繼資料介面](../metadata/metadata-interfaces.md)。  
  
## <a name="remarks"></a>備註  
 偵錯工具可以使用 `GetMetaDataInterface` 方法，針對模組建立原始中繼資料的複本，它必須執行才能編輯該模組。 偵錯工具會呼叫 `GetMetaDataInterface` 來取得模組的[IMetaDataEmit](../metadata/imetadataemit-interface.md)介面物件，然後呼叫[IMetaDataEmit：： SaveToMemory](../metadata/imetadataemit-savetomemory-method.md) ，將模組的中繼資料複本儲存至記憶體。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料](../metadata/index.md)
