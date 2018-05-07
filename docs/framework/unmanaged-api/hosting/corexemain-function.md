---
title: _CorExeMain 函式
ms.date: 03/30/2017
api_name:
- _CorExeMain
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- _CorExeMain
helpviewer_keywords:
- _CorExeMain function [.NET Framework hosting]
ms.assetid: 898f76e2-16f4-4a63-b7d9-dad2d3824d8a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 63af5979b113f81c01c9c68d6cccdfa10811265a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="corexemain-function"></a>_CorExeMain 函式
初始化 common language runtime (CLR)、 找出 managed 的進入點中可執行組件的 CLR 標頭，並開始執行。  
  
## <a name="syntax"></a>語法  
  
```  
__int32 STDMETHODCALLTYPE _CorExeMain ();  
```  
  
## <a name="remarks"></a>備註  
 在處理序所建立的 managed 可執行組件載入器會呼叫此函式。 DLL 的組件載入器會呼叫[_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md)函式。  
  
 作業系統載入器會呼叫這個方法，不論映像檔中指定的進入點。  
  
 在 Windows 98、 Windows ME、 Windows NT 和 Windows 2000`_CorExeMain`間接透過一個修復作業系統載入器在呼叫函式。 在所有其他 Windows 版本，它會呼叫直接由作業系統載入器。  
  
 如需詳細資訊，請參閱中的 < 備註 > 一節[_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md)主題。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：**包含做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [中繼資料全域靜態函式](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
