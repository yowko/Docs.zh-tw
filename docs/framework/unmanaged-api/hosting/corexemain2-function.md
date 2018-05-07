---
title: _CorExeMain2 函式
ms.date: 03/30/2017
api_name:
- _CorExeMain2
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorExeMain2
helpviewer_keywords:
- _CorExeMain2 function [.NET Framework hosting]
ms.assetid: 72ea68b4-689f-4733-9416-9664b75e8892
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 573336b32040f44ff1b59fcbb75b59aa00976b5c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="corexemain2-function"></a>_CorExeMain2 函式
指定記憶體對應程式碼中執行的進入點。 作業系統載入器會呼叫此函式。  
  
## <a name="syntax"></a>語法  
  
```  
__int32 STDMETHODCALLTYPE _CorExeMain2 (  
   [in] PBYTE           pUnmappedPE,  
   [in] DWORD           cUnmappedPE,  
   [in] __in LPWSTR     pImageNameIn,  
   [in] __in LPWSTR     pLoadersFileName,  
   [in] __in LPWSTR     pCmdLine  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pUnmappedPE`  
 [in]記憶體對應的程式碼之指標。  
  
 `cUnmappedPE`  
 [in]項目數`pUnmappedPE`可以保存。  
  
 `pImageNameIn`  
 [in]可執行檔映像的名稱指標。  
  
 `pLoadersFileName`  
 [in]載入器檔案的名稱。  
  
 `pCmdLine`  
 [in]命令列參數，如果有的話。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：**包含做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [中繼資料全域靜態函式](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
