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
ms.openlocfilehash: 9b7624c2902d17e437cda9a0a84ddf288323b577
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676175"
---
# <a name="_efn_stacktrace-function"></a>\_EFN \_ StackTrace 函式

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
 擴展堆疊追蹤的文字標記法。  
  
 `puiTextLength`  
 擴展中字元數的指標 `wszTextOut` 。  
  
 `pTransitionContexts`  
 擴展轉換內容的陣列。  
  
 `puiTransitionContextCount`  
 擴展陣列中轉換內容數目的指標。  
  
 `uiSizeOfContext`  
 在內容結構的大小。  
  
 `Flags`  
 在設定為0或 SOS_STACKTRACE_SHOWADDRESSES (0x01) 以顯示 EBP 暫存器，以及每一行前面的 [輸入堆疊指標] (ESP) `module!functionname` 。  
  
## <a name="remarks"></a>備註  

 您 `_EFN_StackTrace` 可以從 WinDbg 程式設計介面呼叫此結構。 參數的使用方式如下：  
  
- 如果 `wszTextOut` 是 null，且不 `puiTextLength` 是 null，則函數會在中傳回字串長度 `puiTextLength` 。  
  
- 如果不 `wszTextOut` 是 null，則函式會將文字儲存 `wszTextOut` 到所指定的位置 `puiTextLength` 。 如果緩衝區有足夠的空間，則會成功傳回，如果緩衝區的長度不夠長，則會傳回 E_OUTOFMEMORY。  
  
- 如果 `pTransitionContexts` 和 `puiTransitionContextCount` 都是 null，則會忽略函數的轉換部分。 在此情況下，函式只會提供具有函式名稱之文字輸出的呼叫端。  
  
- 如果 `pTransitionContexts` 是 null，且不 `puiTransitionContextCount` 是 null，則函式會在中傳回所需的內容專案數目 `puiTransitionContextCount` 。  
  
- 如果不 `pTransitionContexts` 是 null，則函式會將它視為長度結構的陣列 `puiTransitionContextCount` 。 結構大小是由所提供 `uiSizeOfContext` ，且必須是 [SimpleCoNtext](stacktrace-simplecontext-structure.md) 或架構的大小 `CONTEXT` 。  
  
- `wszTextOut` 會以下列格式寫入：  
  
    ```output  
    "<ModuleName>!<Function Name>[+<offset in hex>]  
    ...  
    (TRANSITION)  
    ..."  
    ```  
  
- 如果十六進位的位移為0x0，則不會寫入位移。  
  
- 如果目前在內容中的執行緒上沒有 managed 程式碼，函數會傳回 SOS_E_NOMANAGEDCODE。  
  
- `Flags`參數可以是0或 SOS_STACKTRACE_SHOWADDRESSES，以查看每一行前面的 EBP 和 ESP `module!functionname` 。 依預設，它是0。  
  
    ```cpp  
    #define SOS_STACKTRACE_SHOWADDRESSES   0x00000001  
    ```  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** SOS_Stacktrace。h  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯全域靜態函式](debugging-global-static-functions.md)
