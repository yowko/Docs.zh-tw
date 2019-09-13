---
title: _EFN_StackTrace 函式
ms.date: 03/30/2017
api_name:
- _EFN_StackTrace
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_StackTrace
helpviewer_keywords:
- _EFN_StackTrace function [.NET Framework debugging]
ms.assetid: caea7754-867c-4360-a65c-5ced4408fd9d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9035d9a53c4b0c8822b79e641aef092b4a48c418
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2019
ms.locfileid: "70895042"
---
# <a name="_efn_stacktrace-function"></a>\_EFN\_StackTrace 函式
提供 Managed 堆疊追蹤以及 `CONTEXT` 記錄之陣列的文字表示，再各提供一個文字表示給 Unmanaged 和 Managed 程式碼之間的每個轉換。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CALLBACK _EFN_StackTrace(  
    [in]  PDEBUG_CLIENT  Client,  
    [out] WCHAR          wszTextOut[],  
    [out] size_t         *puiTextLength,  
    [out] LPVOID         pTransitionContexts,  
    [out] size_t         *puiTransitionContextCount,  
    [in]  size_t         uiSizeOfContext,  
    [in]  DWORD          Flags  
);  
```  
  
## <a name="parameters"></a>參數  
 `Client`  
 在正在進行調試的用戶端。  
  
 `wszTextOut`  
 脫銷堆疊追蹤的文字表示。  
  
 `puiTextLength`  
 脫銷中`wszTextOut`的字元數指標。  
  
 `pTransitionContexts`  
 脫銷轉換內容的陣列。  
  
 `puiTransitionContextCount`  
 脫銷陣列中轉換內容數目的指標。  
  
 `uiSizeOfContext`  
 在內容結構的大小。  
  
 `Flags`  
 在設定為0或 SOS_STACKTRACE_SHOWADDRESSES （0x01）以顯示 EBP 暫存器，以及每`module!functionname`一行前面的輸入堆疊指標（ESP）。  
  
## <a name="remarks"></a>備註  
 您可以從 WinDbg 程式設計介面呼叫結構。`_EFN_StackTrace` 參數的使用方式如下：  
  
- 如果`wszTextOut`為 null 且`puiTextLength`不是 null，則函式會傳回中`puiTextLength`的字串長度。  
  
- 如果`wszTextOut`不是 null，函式會將文字`wszTextOut`儲存在所指定`puiTextLength`的位置。 如果緩衝區中有足夠的空間，它會傳回成功，如果緩衝區不夠長，則會傳回 E_OUTOFMEMORY。  
  
- 如果`pTransitionContexts` 和`puiTransitionContextCount`都是 null，則會忽略函數的轉換部分。 在此情況下，函式會為呼叫端提供只有函數名稱的文字輸出。  
  
- 如果`pTransitionContexts`為 null 且`puiTransitionContextCount`不是 null，則函式會傳回中`puiTransitionContextCount`所需的內容專案數目。  
  
- 如果`pTransitionContexts`不是 null，函式會將它視為長度`puiTransitionContextCount`的結構陣列。 結構大小是由`uiSizeOfContext`所提供，而且必須是[SimpleCoNtext](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md)或`CONTEXT`架構的大小。  
  
- `wszTextOut`會以下列格式寫入：  
  
    ```output  
    "<ModuleName>!<Function Name>[+<offset in hex>]  
    ...  
    (TRANSITION)  
    ..."  
    ```  
  
- 如果 hex 中的位移是0x0，則不會寫入位移。  
  
- 如果目前在內容中的執行緒上沒有 managed 程式碼，則函式會傳回 SOS_E_NOMANAGEDCODE。  
  
- 參數可以是0或 SOS_STACKTRACE_SHOWADDRESSES，以查看每`module!functionname`一行前面的 EBP 和 ESP。 `Flags` 根據預設，它是0。  
  
    ```cpp  
    #define SOS_STACKTRACE_SHOWADDRESSES   0x00000001  
    ```  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** SOS_Stacktrace.h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯全域靜態函式](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
