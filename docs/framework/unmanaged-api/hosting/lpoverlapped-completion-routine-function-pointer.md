---
title: LPOVERLAPPED_COMPLETION_ROUTINE 函式指標
ms.date: 03/30/2017
api_name:
- LPOVERLAPPED_COMPLETION_ROUTINE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- LPOVERLAPPED_COMPLETION_ROUTINE
helpviewer_keywords:
- LPOVERLAPPED_COMPLETION_ROUTINE function pointer [.NET Framework hosting]
ms.assetid: 5fb645d9-b818-401c-8c2c-c30d86de58ba
topic_type:
- apiref
ms.openlocfilehash: a3a45a13073cf422064d28554a274e068db6f517
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727506"
---
# <a name="lpoverlapped_completion_routine-function-pointer"></a>LPOVERLAPPED_COMPLETION_ROUTINE 函式指標

指向函式，此函式會在重迭 (（也就是對裝置的非同步) i/o 完成）時通知主機。  
  
 在 .NET Framework 4 中，此函式指標已被取代。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef VOID (*LPOVERLAPPED_COMPLETION_ROUTINE) (  
    [in] DWORD  dwErrorCode,  
    [in] DWORD  dwNumberOfBytesTransfered,  
    [in] LPVOID lpOverlapped  
);  
```  
  
## <a name="parameters"></a>參數  

 `dwErrorCode`  
 在如果裝置已關閉，則為錯誤碼的值;否則，此值為零。  
  
 關閉裝置會立即完成裝置的所有暫止 i/o。  
  
 `dwNumberOfBytesTransfered`  
 在I/o 作業傳送的位元組數目。  
  
 `lpOverlapped`  
 在結構的指標，其中包含要用來完成 i/o 要求的資訊。  
  
## <a name="remarks"></a>備註  

 指向函式的函式 `LPOVERLAPPED_COMPLETION_ROUTINE` 是回呼函式，而且必須由主控應用程式的寫入器實作為。 回呼函數可讓主機處理已完成的 i/o 要求。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** MSCorWks.dll  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [已被取代的 CLR 裝載函式](deprecated-clr-hosting-functions.md)
