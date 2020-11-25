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
ms.openlocfilehash: a729249f7b0681941a0b1a478dbe2c0d9d6cd01c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723957"
---
# <a name="prebindassemblyex-function"></a>PreBindAssemblyEx 函式

取得元件的原則後顯示名稱。  
  
 此函式支援 .NET Framework 基礎結構，而且不適合直接從程式碼使用。  
  
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
 在識別應用程式內容。  
  
 `pName`  
 在識別元件名稱。  
  
 `pAsmParent`  
 在識別父元件。 這個參數已忽略。  
  
 `pwzRuntimeVersion`  
 在識別執行階段版本。  
  
 `ppNamePostPolicy`  
 擴展包含原則後顯示名稱。  
  
 `pvReserved`  
 在保留供未來擴充性之用。 `pvReserved` 必須是 null 參考。  
  
## <a name="remarks"></a>備註  

 `ppNamePostPolicy`只有當函數傳回 HRESULT FUSION_E_REF_DEF_MISMATCH 時，才會設定 output 參數。 否則為 Null。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** 融合。h  
  
 連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [融合全域靜態函式](fusion-global-static-functions.md)
