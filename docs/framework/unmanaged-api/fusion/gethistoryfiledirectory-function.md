---
title: GetHistoryFileDirectory 函式
ms.date: 03/30/2017
api_name:
- GetHistoryFileDirectory
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- GetHistoryFileDirectory
helpviewer_keywords:
- GetHistoryFileDirectory function [.NET Framework fusion]
ms.assetid: 93232222-926e-42ac-b85d-8a6d33977672
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: adbbf94dc36c6d82360ed532b283cd666a1a52ed
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796857"
---
# <a name="gethistoryfiledirectory-function"></a>GetHistoryFileDirectory 函式
抓取應用程式歷程記錄目錄的路徑。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetHistoryFileDirectory (  
    [in]      LPWSTR      wzDir,  
    [in,out]  LPCWSTR  *pdwsize,  
);  
```  
  
## <a name="parameters"></a>參數  
 `wzDir`  
 脫銷保存應用程式歷程記錄目錄路徑的緩衝區。  
  
 `pdwSize`  
 [in、out]緩衝區的長度。  
  
## <a name="return-value"></a>傳回值  
 除了下列值之外，這個方法會傳回 Winerror.h 檔案中定義的標準 COM 錯誤碼。  
  
|傳回碼|描述|  
|-----------------|-----------------|  
|S_OK|已成功完成命令。|  
|E_INVALIDARG|`wzDir`或`pdwSize`為 null，或版本字串不正確。|  
  
## <a name="remarks"></a>備註  
 成功完成時， `pdwSize`引數會設定為路徑字串的長度。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** 融合。h  
  
 **LIBRARY:** 融合 .dll 和 Mscorwks.dll。 請使用 [Mscorwks.dll]，而不是 []，以確保您以正確的 .NET Framework 版本為目標。  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [CreateHistoryReader 函式](createhistoryreader-function.md)
- [NukeDownloadedCache 函式](nukedownloadedcache-function.md)
- [融合全域靜態函式](fusion-global-static-functions.md)
