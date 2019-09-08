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
ms.openlocfilehash: 29f492173a7fd22ab497d6e0096798e164fccf26
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796301"
---
# <a name="nukedownloadedcache-function"></a>NukeDownloadedCache 函式
刪除 common language runtime （CLR）下載快取。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT NukeDownloadedCache();  
```  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回標準 COM 錯誤碼（如 Winerror.h 中所定義）。  
  
## <a name="remarks"></a>備註  
 CLR 下載快取是用來儲存從 URL 下載之強式名稱元件的區域，以供重複使用。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** 融合。h  
  
 **LIBRARY:** 融合 .dll 和 Mscorwks.dll。 請使用 [Mscorwks.dll]，而不是 []，以確保您以正確的 .NET Framework 版本為目標。  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [CreateHistoryReader 函式](createhistoryreader-function.md)
- [GetHistoryFileDirectory 函式](gethistoryfiledirectory-function.md)
- [融合全域靜態函式](fusion-global-static-functions.md)
