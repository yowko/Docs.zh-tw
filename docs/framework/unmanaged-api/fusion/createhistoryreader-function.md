---
title: "CreateHistoryReader 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CreateHistoryReader
api_location: fusion.dll
api_type: DLLExport
f1_keywords: CreateHistoryReader
helpviewer_keywords: CreateHistoryReader function [.NET Framework fusion]
ms.assetid: 66a89acf-8c32-44c0-8787-960c99c7b3ec
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4f4b09f592a27b7d3d25b2dbe13be7e261023bf5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="createhistoryreader-function"></a>CreateHistoryReader 函式
建立指定的檔案歷程記錄讀取器。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT CreateHistoryReader (  
    [in]  LPCWSTR        wzFilePath,  
    [out] IHistoryReader **ppHistoryReader  
 );  
```  
  
#### <a name="parameters"></a>參數  
 `wzFilePath`  
 [in]檔案路徑。  
  
 `ppHistoryReader`  
 [out]在成功完成時，包含歷程記錄讀取器的指標。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回除了下表中描述的值定義了 WinError.h，在標準的 COM 錯誤碼。  
  
|傳回碼|描述|  
|-----------------|-----------------|  
|S_OK|表示已成功完成的方法。|  
|E_INVALIDARG|表示`wzFilePath`或`ppHistoryReader`會設為 null 參考。|  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **程式庫：** Fusion.dll  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [融合全域靜態函式](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
