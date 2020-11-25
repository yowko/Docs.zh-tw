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
ms.openlocfilehash: 58b8b83ce1db9338612cbaa01a0db0862cf1054e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727896"
---
# <a name="iassemblynamegetname-method"></a>IAssemblyName::GetName 方法

取得這個 [IAssemblyName](iassemblyname-interface.md) 物件所參考之元件的簡單、未加密的名稱。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetName (  
    [in, out] LPDWORD lpcwBuffer,  
    [out]     WCHAR *pwzName  
);  
```  
  
## <a name="parameters"></a>參數  

 `lpcwBuffer`  
 [in，out] `pwzName` 以寬字元為單位的大小，包括 null 結束字元字元。  
  
 `pwzName`  
 擴展保存參考元件名稱的緩衝區。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** 融合。h  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IAssemblyName 介面](iassemblyname-interface.md)
