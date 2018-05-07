---
title: IAssemblyName::GetName 方法
ms.date: 03/30/2017
api_name:
- IAssemblyName.GetName
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::GetName
helpviewer_keywords:
- GetName method, IAssemblyName interface [.NET Framework debugging]
- IAssemblyName::GetName method [.NET Framework fusion]
ms.assetid: 1dee9781-1cf3-48a9-a376-d18ea1f73280
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 06c918de10f86442b10b0d85e6554bb1af0a8928
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="iassemblynamegetname-method"></a>IAssemblyName::GetName 方法
取得所參考的組件的簡單、 未加密名稱[IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)物件。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetName (  
    [in, out] LPDWORD lpcwBuffer,  
    [out]     WCHAR *pwzName  
);  
```  
  
#### <a name="parameters"></a>參數  
 `lpcwBuffer`  
 [in、 out]大小`pwzName`寬字元，包括 null 結束字元。  
  
 `pwzName`  
 [out]緩衝區來保存參考的組件的名稱。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Fusion.h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [IAssemblyName 介面](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
