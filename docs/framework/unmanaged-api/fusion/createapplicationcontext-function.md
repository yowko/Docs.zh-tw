---
title: CreateApplicationContext 函式
ms.date: 03/30/2017
api_name:
- CreateApplicationContext
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- CreateApplicationContext
helpviewer_keywords:
- CreateApplicationContext function [.NET Framework fusion]
ms.assetid: 7bf8a141-b2c0-4058-9885-1cef7dcaa811
topic_type:
- apiref
ms.openlocfilehash: e188fe80e770481aac02244a2c105639e4da19e2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108898"
---
# <a name="createapplicationcontext-function"></a>CreateApplicationContext 函式
此函式支援 .NET Framework 的基礎結構，但不適合直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CreateApplicationContext (  
    [in]  IAssemblyName  *pName,  
    [out] LPPAPPLICATIONCONTEXT  *ppCtx  
 );  
```  
  
## <a name="parameters"></a>參數  
 `pName`  
 在易記名稱的指標。  
  
 `ppCtx`  
 脫銷應用程式內容的指標。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** 融合。h  
  
 連結**庫：** 納入為融合 .dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [IAssemblyCache 介面](iassemblycache-interface.md)
- [融合全域靜態函式](fusion-global-static-functions.md)
- [全域組件快取](../../app-domains/gac.md)
