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
ms.openlocfilehash: 2710d14d6e73879fd17a6b58659463ea205f2384
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795373"
---
# <a name="createhistoryreader-function"></a>CreateHistoryReader 函式
為指定的檔案建立記錄讀取器。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CreateHistoryReader (  
    [in]  LPCWSTR        wzFilePath,  
    [out] IHistoryReader **ppHistoryReader  
 );  
```  
  
## <a name="parameters"></a>參數  
 `wzFilePath`  
 在檔案路徑。  
  
 `ppHistoryReader`  
 脫銷成功完成時，會包含記錄讀取器的指標。  
  
## <a name="return-value"></a>傳回值  
 除了下表所述的值之外，這個方法會傳回 Winerror.h 中定義的標準 COM 錯誤碼。  
  
|傳回碼|描述|  
|-----------------|-----------------|  
|S_OK|表示方法已順利完成。|  
|E_INVALIDARG|`wzFilePath`指出或`ppHistoryReader`設定為 null 參考。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **LIBRARY:** 融合 .dll  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [融合全域靜態函式](fusion-global-static-functions.md)
