---
title: ICorConfiguration::AddDebuggerSpecialThread 方法
ms.date: 03/30/2017
api_name:
- ICorConfiguration.AddDebuggerSpecialThread
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AddDebuggerSpecialThread
helpviewer_keywords:
- AddDebuggerSpecialThread method [.NET Framework hosting]
- ICorConfiguration::AddDebuggerSpecialThread method [.NET Framework hosting]
ms.assetid: 1f1e3239-438e-4be9-a3bb-7d0722d3a76d
topic_type:
- apiref
ms.openlocfilehash: 8b6593ad995872f0e0014b1e8bcd8a4b576bbeaf
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762420"
---
# <a name="icorconfigurationadddebuggerspecialthread-method"></a>ICorConfiguration::AddDebuggerSpecialThread 方法
向偵錯工具表示，當偵錯工具在 managed 或非受控的偵測案例中停止時，應該允許特定執行緒繼續執行。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT AddDebuggerSpecialThread (  
    [in] DWORD dwSpecialThreadId  
);  
```  
  
## <a name="parameters"></a>參數  
 `dwSpecialThreadId`  
 在應允許繼續執行之執行緒的識別碼。  
  
## <a name="remarks"></a>備註  
 指定的執行緒將不允許執行 managed 程式碼，或以任何方式進入執行時間。 這類執行緒的範例就是支援舊版腳本偵錯工具的同進程執行緒。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorConfiguration 介面](icorconfiguration-interface.md)
