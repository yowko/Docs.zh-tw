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
ms.openlocfilehash: a3fb9d87b6433d46dad081619e0692a42219408d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673615"
---
# <a name="_corexemain2-function"></a>_CorExeMain2 函式

執行指定之記憶體對應程式碼中的進入點。 作業系統載入器會呼叫這個函式。  
  
## <a name="syntax"></a>語法  
  
```cpp  
__int32 STDMETHODCALLTYPE _CorExeMain2 (  
   [in] PBYTE           pUnmappedPE,  
   [in] DWORD           cUnmappedPE,  
   [in] __in LPWSTR     pImageNameIn,  
   [in] __in LPWSTR     pLoadersFileName,  
   [in] __in LPWSTR     pCmdLine  
);  
```  
  
## <a name="parameters"></a>參數  

 `pUnmappedPE`  
 在記憶體對應程式碼的指標。  
  
 `cUnmappedPE`  
 在元素數目 `pUnmappedPE` 可以保留。  
  
 `pImageNameIn`  
 在可執行檔映射名稱的指標。  
  
 `pLoadersFileName`  
 在載入器檔案的名稱。  
  
 `pCmdLine`  
 在命令列參數（如果有的話）。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料全域靜態函式](../metadata/metadata-global-static-functions.md)
