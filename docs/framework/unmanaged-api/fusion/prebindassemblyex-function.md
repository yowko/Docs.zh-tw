---
title: PreBindAssemblyEx 函式
ms.date: 03/30/2017
api_name:
- PreBindAssemblyEx
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- PreBindAssemblyEx
helpviewer_keywords:
- PreBindAssemblyEx function [.NET Framework fusion]
ms.assetid: bd285233-a4a2-4b52-bbca-0025a60e4864
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a23d3c4fd8eef2e361abf1602157cb4fbb820b48
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67773855"
---
# <a name="prebindassemblyex-function"></a>PreBindAssemblyEx 函式
取得組件的原則後顯示名稱。  
  
 此函式支援.NET Framework 基礎結構，並不是直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT PreBindAssemblyEx (  
    [in]  IApplicationContext *pAppCtx,  
    [in]  IAssemblyName       *pName,  
    [in]  IAssembly           *pAsmParent,  
    [in]  LPCWSTR             pwzRuntimeVersion,  
    [out] IAssemblyName       **ppNamePostPolicy,  
    [in]  LPVOID              pvReserved  
 );  
```  
  
## <a name="parameters"></a>參數  
 `pAppCtx`  
 [in]識別應用程式內容。  
  
 `pName`  
 [in]識別組件名稱。  
  
 `pAsmParent`  
 [in]識別父組件。 這個參數已忽略。  
  
 `pwzRuntimeVersion`  
 [in]識別執行階段版本。  
  
 `ppNamePostPolicy`  
 [out]包含的原則後顯示名稱。  
  
 `pvReserved`  
 [in]保留供未來擴充。 `pvReserved` 必須是 null 參考。  
  
## <a name="remarks"></a>備註  
 `ppNamePostPolicy`函式會傳回 HRESULT FUSION_E_REF_DEF_MISMATCH 時，才設定輸出參數。 否則，它是 null。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Fusion.h  
  
 **LIBRARY:** 包含做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [融合全域靜態函式](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
