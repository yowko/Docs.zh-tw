---
title: IBindingDisplay::GetCurrentDisplay 方法
ms.date: 03/30/2017
api_name:
- IBindingDisplay.GetCurrentDisplay
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- IBindingDisplay::GetCurrentDisplay
helpviewer_keywords:
- IBindingDisplay::GetCurrentDisplay method [.NET Framework debugging]
- GetCurrentDisplay method [.NET Framework debugging]
ms.assetid: d28eeea4-c4e0-40d4-91de-198d98cfa13c
topic_type:
- apiref
ms.openlocfilehash: 6fe8c3266a8c9a52cd1022589cd68485c4326fd1
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442185"
---
# <a name="ibindingdisplaygetcurrentdisplay-method"></a>IBindingDisplay::GetCurrentDisplay 方法
傳回目前的系結顯示資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetCurrentDisplay (  
    [out, retval] SAFEARRAY(struct BindingDisplayTabControl) *display  
);  
```  
  
## <a name="parameters"></a>參數  
 `display`  
 [out，retval]包含系結顯示資訊之 safearray 的指標。  
  
## <a name="remarks"></a>備註  
 [IBindingDisplay：： InitializeForProcess](ibindingdisplay-initializeforprocess-method.md)方法先前必須已成功，而且偵錯工具必須停止此程式。  
  
 呼叫端必須 `SAFEARRAY` 使用[SafeArrayDestroy](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy)來解除配置傳回的記憶體。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** BindingDisplay。h  
  
 連結**庫：** BindingDisplay .idl  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IBindingDisplay 介面](ibindingdisplay-interface.md)
- [InitializeForProcess 方法](ibindingdisplay-initializeforprocess-method.md)
