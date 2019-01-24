---
title: NukeDownloadedCache 函式
ms.date: 03/30/2017
api_name:
- NukeDownloadedCache
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- NukeDownloadedCache
helpviewer_keywords:
- NukeDownloadedCache function [.NET Framework fusion]
ms.assetid: fac2b1c6-6fa3-4818-805b-b63972024c86
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 80891da7d61aa5114d5cc4d8aff4c7ce82020237
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54720089"
---
# <a name="nukedownloadedcache-function"></a>NukeDownloadedCache 函式
刪除 common language runtime (CLR) 下載快取。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT NukeDownloadedCache();  
```  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回標準 COM 錯誤碼，WinError.h 中定義。  
  
## <a name="remarks"></a>備註  
 CLR 下載快取是從 URL 下載的強式名稱組件可能重複使用的儲存位置的區域。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Fusion.h  
  
 **程式庫：** Fusion.dll 和 Mscorwks.dll。 使用而不是 Mscorwks.dll 的 Fusion.dll，以確保您設為目標的.NET framework 的正確版本。  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [CreateHistoryReader 函式](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)
- [GetHistoryFileDirectory 函式](../../../../docs/framework/unmanaged-api/fusion/gethistoryfiledirectory-function.md)
- [融合全域靜態函式](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
