---
title: IBindingDisplay::InitializeForProcess 方法
ms.date: 03/30/2017
api_name:
- IBindingDisplay.InitializeForProcess
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- IBindingDisplay::InitializeForProcess
helpviewer_keywords:
- IBindingDisplay::InitializeForProcess method [.NET Framework debugging]
- InitializeForProcess method [.NET Framework debugging]
ms.assetid: 59417acb-4e59-46ad-acfe-d827e6ab6078
topic_type:
- apiref
ms.openlocfilehash: 8645878132359b6218cd62b1ff707208de53704b
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442146"
---
# <a name="ibindingdisplayinitializeforprocess-method"></a>IBindingDisplay::InitializeForProcess 方法
初始化[IBindingDisplay](ibindingdisplay-interface.md)物件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT InitializeForProcess (  
    [in] ULONG32   pid  
);  
```  
  
## <a name="parameters"></a>參數  
 `pid`  
 在處理序識別碼。  
  
## <a name="remarks"></a>備註  
 偵錯工具會 `InitializeForProcess` 在建立時呼叫方法，以初始化系結顯示。 `InitializeForProcess`在呼叫上的任何其他方法之前，必須在建立期間呼叫 `IBindingDisplay` 。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** BindingDisplay。h  
  
 連結**庫：** BindingDisplay .idl  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IBindingDisplay 介面](ibindingdisplay-interface.md)
