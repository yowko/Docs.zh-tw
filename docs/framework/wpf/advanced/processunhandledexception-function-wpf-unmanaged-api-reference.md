---
title: ProcessUnhandledException 函式 (WPF Unmanaged API 參考)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ProcessUnhandledException
api_location:
- PresentationHost_v0400.dll
ms.assetid: 495ce5f6-bb4d-4b30-807a-c3c35f1ca95c
ms.openlocfilehash: 73480f7cd8be7bcb5296782a8503eb689442a14c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54578636"
---
# <a name="processunhandledexception-function-wpf-unmanaged-api-reference"></a>ProcessUnhandledException 函式 (WPF Unmanaged API 參考)
此 API 支援 Windows Presentation Foundation (WPF) 基礎結構，並不是直接從您的程式碼使用。  
  
 Windows Presentation Foundation (WPF) 基礎結構用於例外狀況處理。  
  
## <a name="syntax"></a>語法  
  
```cpp  
void __stdcall ProcessUnhandledException(  
   __in_ecount(1) BSTR errorMsg  
)  
```  
  
#### <a name="parameters"></a>參數  
 errorMsg  
 錯誤訊息。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[.NET Framework 系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **DLL:**  
  
 在.NET Framework 3.0 和 3.5:PresentationHostDLL.dll  
  
 在.NET Framework 4 及更新版本：PresentationHost_v0400.dll  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [WPF Unmanaged API 參考](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
