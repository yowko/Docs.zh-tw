---
title: CoEEShutDownCOM 函式
ms.date: 03/30/2017
api_name:
- CoEEShutDownCOM
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoEEShutDownCOM
helpviewer_keywords:
- CoEEShutDownCOM function [.NET Framework hosting]
ms.assetid: b634cae2-632f-4737-9be4-92d0652844d7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 164384f043a1722ace6e5c4098cb31c4327cba1e
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044064"
---
# <a name="coeeshutdowncom-function"></a>CoEEShutDownCOM 函式
強制 common language runtime (CLR) 釋放它在執行時間可呼叫包裝函式 (RCW) 內所擁有的所有介面指標。 這有釋放所有 RCW 快取的效果。 此全域函數在 .NET Framework 4 中已被取代。 相反地, 請使用特定執行時間的進入點。  
  
## <a name="syntax"></a>語法  
  
```cpp  
void CoEEShutDownCOM ();  
```  
  
## <a name="remarks"></a>備註  
 `CoEEShutDownCOM`函式會先釋放所有內容和所有快取中的所有 rcw, 然後移除安裝程式中現有的任何中斷通知。 不會卸載任何 DLL。  
  
> [!CAUTION]
> 此函式會影響載入進程中的所有執行時間。  
  
 從 .NET Framework 4 開始, 請在您想要影響的特定執行時間上呼叫此函式的進入點。 若要取得進入點, 請呼叫[ICLRRuntimeInfo:: GetProcAddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md)方法並指定 "CoEEShutDownCOM"。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 **LIBRARY:** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料全域靜態函式](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
