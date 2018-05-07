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
ms.openlocfilehash: 5a406e945a67352bc7f126b40bd56f4a11dd693b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugmodule2applychanges-method"></a>ICorDebugModule2::ApplyChanges 方法
適用於執行的處理序的中繼資料中的變更和 Microsoft intermediate language (MSIL) 程式碼中的變更。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT ApplyChanges (  
    [in] ULONG                       cbMetadata,  
    [in, size_is(cbMetadata)] BYTE   pbMetadata[],  
    [in] ULONG                       cbIL,  
    [in, size_is(cbIL)] BYTE         pbIL[]  
);  
```  
  
#### <a name="parameters"></a>參數  
 `cbMetadata`  
 [in]以位元組為單位的差異中繼資料的大小。  
  
 `pbMetadata`  
 [in]包含差異中繼資料的緩衝區。 從傳回的緩衝區位址[imetadataemit2:: Savedeltatomemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)方法。  
  
 中繼資料中的相對虛擬位址 (Rva) 應該是相對於 MSIL 程式碼的開頭。  
  
 `cbIL`  
 [in]以位元組為單位的差異 MSIL 程式碼的大小。  
  
 `pbIL`  
 [in]包含更新的 MSIL 程式碼的緩衝區。  
  
## <a name="remarks"></a>備註  
 `pbMetadata`參數的特殊差異中繼資料格式 (如輸出所[imetadataemit2:: Savedeltatomemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md))。 `pbMetadata` 接受做為基底的上一個中繼資料，並描述要套用至該基底的個別變更。  
  
 相反地， `pbIL[`] 參數包含更新的方法，新的 MSIL，而且完全取代先前的 MSIL 方法  
  
 當差異 MSIL 和中繼資料中已建立偵錯工具的記憶體時，偵錯工具呼叫`ApplyChanges`傳送到 common language runtime (CLR) 的變更。 執行階段會更新它的中繼資料資料表，將新的 MSIL 放入此程序，並且設定在 just-in-time (JIT) 編譯新的 MSIL。 偵錯工具時已套用所做的變更，應該呼叫[imetadataemit2:: Resetenclog](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md)準備的下一個編輯工作階段。 偵錯工具就可以繼續處理程序。  
  
 每當偵錯工具呼叫`ApplyChanges`上具有差異的中繼資料的模組，它也應該呼叫[imetadataemit:: Applyeditandcontinue](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-applyeditandcontinue-method.md)與該模組的中繼資料除了複製其複本的所有相同的差異中繼資料用來發出所做的變更。 如果中繼資料的副本由於某種原因而變成不同步的與實際的中繼資料，偵錯工具可以永遠丟棄該複本，並取得新的複本。  
  
 如果`ApplyChanges`方法失敗，偵錯工作階段處於無效狀態，必須重新啟動。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
