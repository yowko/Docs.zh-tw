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
ms.openlocfilehash: a6b1a7c9be821890a3f15d8c3297273607f5bedd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709696"
---
# <a name="icordebugmodule2applychanges-method"></a>ICorDebugModule2::ApplyChanges 方法

將中繼資料中的變更，以及 Microsoft 中繼語言 (MSIL) 程式碼中的變更套用至執行中的進程。  
  
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
 在差異中繼資料的大小（以位元組為單位）。  
  
 `pbMetadata`  
 在包含差異中繼資料的緩衝區。 緩衝區的位址會從 [IMetaDataEmit2：： SaveDeltaToMemory](../metadata/imetadataemit2-savedeltatomemory-method.md) 方法傳回。  
  
 中繼資料中 (Rva) 的相對虛擬位址應該相對於 MSIL 程式碼的開頭。  
  
 `cbIL`  
 在Delta MSIL 程式碼的大小（以位元組為單位）。  
  
 `pbIL`  
 在包含已更新之 MSIL 程式碼的緩衝區。  
  
## <a name="remarks"></a>備註  

 此 `pbMetadata` 參數為特殊的差異元資料格式， (為 [IMetaDataEmit2：： SaveDeltaToMemory](../metadata/imetadataemit2-savedeltatomemory-method.md)) 的輸出。 `pbMetadata` 採用先前的中繼資料作為基底，並描述要套用至該基底的個別變更。  
  
 相反地，此 `pbIL[` 參數包含已更新方法的新 msil，目的是要完全取代該方法的先前 msil。  
  
 當您在偵錯工具的記憶體中建立 delta MSIL 和中繼資料時，偵錯工具會呼叫，將 `ApplyChanges` 變更傳送至 common language runtime (CLR) 。 執行時間會更新其中繼資料資料表、將新的 MSIL 放入處理常式中，並設定及時 (JIT) 新 MSIL 的編譯。 套用變更之後，偵錯工具應該呼叫 [IMetaDataEmit2：： ResetENCLog](../metadata/imetadataemit2-resetenclog-method.md) ，以準備下一個編輯會話。 偵錯工具可能會繼續執行此程式。  
  
 每當偵錯工具 `ApplyChanges` 在具有 delta 中繼資料的模組上呼叫時，它也應該在該模組的中繼資料的所有複本上，使用相同的差異中繼資料來呼叫 [IMetaDataEmit：： ApplyEditAndContinue](../metadata/imetadataemit-applyeditandcontinue-method.md) ，但用來發出變更的複製除外。 如果中繼資料的複本以某種方式與實際的中繼資料不同步，則偵錯工具一律會擲回該複本並取得新的複本。  
  
 如果 `ApplyChanges` 方法失敗，則偵錯工具會處於無效狀態，而且必須重新開機。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
