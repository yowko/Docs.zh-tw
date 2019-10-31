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
ms.openlocfilehash: 103ac75e7c3eaf9739c3a448ff1c052c158621db
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73090899"
---
# <a name="lpoverlapped_completion_routine-function-pointer"></a>LPOVERLAPPED_COMPLETION_ROUTINE 函式指標
指向函式，當裝置的重迭（也就是非同步） i/o 完成時，會通知主機。  
  
 這個函式指標在 .NET Framework 4 中已被取代。  
  
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
 在如果裝置已關閉，則為錯誤碼的值;否則，這個值會是零。  
  
 關閉裝置會導致裝置的所有擱置中 i/o 立即完成。  
  
 `dwNumberOfBytesTransfered`  
 在I/o 作業所傳輸的位元組數目。  
  
 `lpOverlapped`  
 在結構的指標，其中包含用來完成 i/o 要求的資訊。  
  
## <a name="remarks"></a>備註  
 `LPOVERLAPPED_COMPLETION_ROUTINE` 點的函式是回呼函式，必須由主控應用程式的寫入器來執行。 回呼函式可讓主機處理已完成的 i/o 要求。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** Mscorwks.dll .dll  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [已被取代的 CLR 裝載函式](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
