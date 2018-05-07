---
title: LPTHREAD_START_ROUTINE 函式指標
ms.date: 03/30/2017
api_name:
- LPTHREAD_START_ROUTINE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- LPTHREAD_START_ROUTINE
helpviewer_keywords:
- LPTHREAD_START_ROUTINE function pointer [.NET Framework hosting]
ms.assetid: 7b9b93b0-fe92-42ba-8693-701168a29dde
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5025b75106b2cb0853047a09ca263f795d99633f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="lpthreadstartroutine-function-pointer"></a>LPTHREAD_START_ROUTINE 函式指標
指向以通知主機在執行緒已開始執行的函式。  
  
 此函式指標中已被取代[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。  
  
## <a name="syntax"></a>語法  
  
```  
typedef DWORD (__stdcall *LPTHREAD_START_ROUTINE) (  
    [in] LPVOID lpThreadParameter  
);  
```  
  
#### <a name="parameters"></a>參數  
 `lpThreadParameter`  
 [in]已開始執行的程式碼之指標。  
  
## <a name="remarks"></a>備註  
 函式`LPTHREAD_START_ROUTINE`點是回呼函式，而且必須在裝載應用程式寫入器實作。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：** MSCorWks.dll  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [已被取代的 CLR 裝載函式](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
