---
title: ICorConfiguration::SetGCThreadControl 方法
ms.date: 03/30/2017
api_name:
- ICorConfiguration.SetGCThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetGCThreadControl
helpviewer_keywords:
- ICorConfiguration::SetGCThreadControl method [.NET Framework hosting]
- SetGCThreadControl method [.NET Framework hosting]
ms.assetid: 72e38e61-3d56-4ae3-b8f6-0ab7922aaf11
topic_type:
- apiref
ms.openlocfilehash: 7874424150e0f4e1818ad9c72e31fd584e016829
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762392"
---
# <a name="icorconfigurationsetgcthreadcontrol-method"></a>ICorConfiguration::SetGCThreadControl 方法
設定回呼介面，用於針對非執行時間工作排程執行緒，否則會封鎖垃圾收集。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetGCThreadControl (  
    [in] IGCThreadControl* pGCThreadControl  
);  
```  
  
## <a name="parameters"></a>參數  
 `pGCThreadControl`  
 在[IGCThreadControl](igcthreadcontrol-interface.md)物件的指標，會通知主機有關非執行時間工作的執行緒暫停。  
  
## <a name="remarks"></a>備註  
 主機可以在[IGCThreadControl：： ThreadIsBlockingForSuspension](igcthreadcontrol-threadisblockingforsuspension-method.md)回呼中選擇是否要重新排定執行緒。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorConfiguration 介面](icorconfiguration-interface.md)
