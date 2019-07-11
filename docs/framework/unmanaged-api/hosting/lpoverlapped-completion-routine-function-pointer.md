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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dcf63000de549b42d92ba157a7e550ac605bbfcd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768386"
---
# <a name="lpoverlappedcompletionroutine-function-pointer"></a>LPOVERLAPPED_COMPLETION_ROUTINE 函式指標
指向主應用程式時之重疊的函式 (也就是非同步) 至裝置的 I/O 已完成。  
  
 在.NET Framework 4 中，已被取代此函式指標。  
  
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
 [in]如果裝置已關閉; 為錯誤碼的值否則，此值為零。  
  
 關閉裝置，讓所有擱置 I/O 裝置中的立即完成。  
  
 `dwNumberOfBytesTransfered`  
 [in]I/O 作業所傳送的位元組數目。  
  
 `lpOverlapped`  
 [in]包含用來完成的 I/O 要求的資訊結構的指標。  
  
## <a name="remarks"></a>備註  
 函式，其中`LPOVERLAPPED_COMPLETION_ROUTINE`點是回呼函式，而且必須在裝載應用程式寫入器實作。 回呼函式可讓主應用程式處理已完成的 I/O 要求。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **LIBRARY:** MSCorWks.dll  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [已被取代的 CLR 裝載函式](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
