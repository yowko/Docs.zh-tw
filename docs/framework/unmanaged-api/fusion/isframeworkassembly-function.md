---
title: IsFrameworkAssembly 函式
ms.date: 03/30/2017
api_name:
- IsFrameworkAssembly
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IsFrameworkAssembly
helpviewer_keywords:
- IsFrameworkAssembly function [.NET Framework fusion]
ms.assetid: b0c6f19b-d4fd-4971-88f0-12ffb5793da3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c3fd130759ab11b54b597d5c099c33dab93070ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="isframeworkassembly-function"></a>IsFrameworkAssembly 函式
取得值，指出指定的組件是否為 managed。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT IsFrameworkAssembly (  
    [in]  LPCWSTR pwzAssemblyReference,  
    [out] LPBOOL  pbIsFrameworkAssembly,  
    [in]  LPWSTR  pwzFrameworkAssemblyIdentity,  
    [in]  LPDWORD pccSize  
 );  
```  
  
#### <a name="parameters"></a>參數  
 `pwzAssemblyReference`  
 [in]若要檢查組件的名稱。  
  
 `pbIsFrameworkAssembly`  
 [out]布林值，指出是否為 managed 組件。  
  
 `pwzFrameworkAssemblyIdentity`  
 [in]Uncanonicalized 的字串，包含組件的唯一識別。  
  
 `pccSize`  
 [in] `pwzFrameworkAssemblyIdentity` 的大小。  
  
## <a name="remarks"></a>備註  
 `pwzAssemblyReference`參數是指向字元字串，包含組件的名稱。  
  
 如果這個組件是.NET framework 的一部分`pbIsFrameworkAssembly`參數會包含布林值`true`。  
  
 如果具名組件不是.NET framework 的一部分，或如果`pwzAssemblyReference`參數無法命名組件，`pbIsFrameworkAssembly`就會包含布林值`false`。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
## <a name="see-also"></a>另請參閱  
 [融合全域靜態函式](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
