---
title: ICorDebugModule2::ApplyChanges 方法
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.ApplyChanges
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::ApplyChanges
helpviewer_keywords:
- ApplyChanges method [.NET Framework debugging]
- ICorDebugModule2::ApplyChanges method [.NET Framework debugging]
ms.assetid: 96fa3406-6a6f-41a1-88c6-d9bc5d1a16d1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 860b87b09ee487f893a1bba2aaa34292c50ffcb7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764335"
---
# <a name="icordebugmodule2applychanges-method"></a>ICorDebugModule2::ApplyChanges 方法
適用於執行中處理序在中繼資料中的變更和 Microsoft intermediate language (MSIL) 程式碼中的變更。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ApplyChanges (  
    [in] ULONG                       cbMetadata,  
    [in, size_is(cbMetadata)] BYTE   pbMetadata[],  
    [in] ULONG                       cbIL,  
    [in, size_is(cbIL)] BYTE         pbIL[]  
);  
```  
  
## <a name="parameters"></a>參數  
 `cbMetadata`  
 [in]以位元組為單位的差異中繼資料的大小。  
  
 `pbMetadata`  
 [in]包含差異中繼資料的緩衝區。 從傳回的緩衝區位址[IMetaDataEmit2::SaveDeltaToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)方法。  
  
 中繼資料中的相對虛擬位址 (Rva) 應該是相對於 MSIL 程式碼的開頭。  
  
 `cbIL`  
 [in]大小，以位元組為單位的 MSIL 程式碼的差異。  
  
 `pbIL`  
 [in]包含更新的 MSIL 程式碼的緩衝區。  
  
## <a name="remarks"></a>備註  
 `pbMetadata`參數的特殊差異中繼資料格式 (如輸出所[IMetaDataEmit2::SaveDeltaToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md))。 `pbMetadata` 接受做為基底的上一個中繼資料，並描述要套用至該基底的個別變更。  
  
 相反地， `pbIL[`] 參數包含更新的方法，新的 MSIL，而且完全取代該方法的先前 MSIL  
  
 當差異 MSIL 和中繼資料中已建立偵錯工具的記憶體時，偵錯工具就會呼叫`ApplyChanges`傳送到 common language runtime (CLR) 的變更。 執行階段更新及其中繼資料資料表、 將新的 MSIL 放到程序，並設定新的 MSIL-just-in-time (JIT) 編譯。 偵錯工具時已套用所做的變更，應該呼叫[IMetaDataEmit2::ResetENCLog](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md)準備的下一個編輯工作階段。 偵錯工具就可以繼續處理程序。  
  
 每當偵錯工具會呼叫`ApplyChanges`上有差異的中繼資料的模組，它也應該呼叫[imetadataemit:: Applyeditandcontinue](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-applyeditandcontinue-method.md)與該模組的中繼資料，但複本的其複本的所有相同的差異中繼資料用來發出所做的變更。 如果中繼資料的複本以某種方式變得同步處理與實際的中繼資料，偵錯工具可以一律擲出該複本，並取得新的複本。  
  
 如果`ApplyChanges`方法失敗，偵錯工作階段處於無效的狀態，必須重新啟動。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
