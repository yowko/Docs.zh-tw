---
title: CreateHistoryReader 函式
ms.date: 03/30/2017
api_name:
- CreateHistoryReader
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- CreateHistoryReader
helpviewer_keywords:
- CreateHistoryReader function [.NET Framework fusion]
ms.assetid: 66a89acf-8c32-44c0-8787-960c99c7b3ec
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ee30d4f32e05fab27ae70052b28d3d152594cf90
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778423"
---
# <a name="createhistoryreader-function"></a>CreateHistoryReader 函式
建立記錄讀取器指定的檔案。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CreateHistoryReader (  
    [in]  LPCWSTR        wzFilePath,  
    [out] IHistoryReader **ppHistoryReader  
 );  
```  
  
## <a name="parameters"></a>參數  
 `wzFilePath`  
 [in]檔案路徑。  
  
 `ppHistoryReader`  
 [out]成功完成時，包含歷程記錄讀取器的指標。  
  
## <a name="return-value"></a>傳回值  
 中所定義 WinError.h，除了下表中所述的值，這個方法會傳回標準 COM 錯誤碼。  
  
|傳回碼|說明|  
|-----------------|-----------------|  
|S_OK|表示已成功完成的方法。|  
|E_INVALIDARG|指出`wzFilePath`或`ppHistoryReader`設為 null 參考。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **LIBRARY:** Fusion.dll  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [融合全域靜態函式](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
