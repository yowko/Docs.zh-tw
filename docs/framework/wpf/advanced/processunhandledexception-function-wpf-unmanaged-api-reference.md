---
title: ProcessUnhandledException 函式-WPF 非受控 API 參考
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ProcessUnhandledException
api_location:
- PresentationHost_v0400.dll
ms.assetid: 495ce5f6-bb4d-4b30-807a-c3c35f1ca95c
ms.openlocfilehash: 757e5ac3aa2dc4c87b210b026998523bd82045c1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743916"
---
# <a name="processunhandledexception-function-wpf-unmanaged-api-reference"></a>ProcessUnhandledException 函式（WPF 非受控 API 參考）
這個 API 支援 Windows Presentation Foundation （WPF）基礎結構，但不適合直接從程式碼使用。  
  
 由 Windows Presentation Foundation （WPF）基礎結構用來處理例外狀況。  
  
## <a name="syntax"></a>語法  
  
```cpp  
void __stdcall ProcessUnhandledException(  
   __in_ecount(1) BSTR errorMsg  
)  
```  
  
## <a name="parameters"></a>參數  
 errorMsg  
 錯誤訊息。  
  
## <a name="requirements"></a>需求  
 **平臺：** 請參閱[.NET Framework 系統需求](../../get-started/system-requirements.md)。  
  
 **URLMON.DLL**  
  
 在 .NET Framework 3.0 和3.5： PresentationHostDLL 中  
  
 在 .NET Framework 4 和更新版本中： PresentationHost_v0400 .dll  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [WPF Unmanaged API 參考](wpf-unmanaged-api-reference.md)
