---
title: ForwardTranslateAccelerator 函式-WPF 非受控 API 參考
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ForwardTranslateAccelerator
api_location:
- PresentationHost_v0400.dll
ms.assetid: fff47a86-9d9f-4176-9530-10e1876e393f
ms.openlocfilehash: f6e8208ffe2c186234f30f31e346ca6b1d0be4c0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747045"
---
# <a name="forwardtranslateaccelerator-function-wpf-unmanaged-api-reference"></a>ForwardTranslateAccelerator 函式（WPF 非受控 API 參考）
這個 API 支援 Windows Presentation Foundation （WPF）基礎結構，但不適合直接從程式碼使用。  
  
 由適用于 Windows 管理的 Windows Presentation Foundation （WPF）基礎結構使用。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ForwardTranslateAccelerator(  
   MSG* pMsg,   
   VARIANT_BOOL appUnhandled  
)  
```  
  
## <a name="parameters"></a>參數  
 pMsg  
 訊息的指標。  
  
 appUnhandled  
 當應用程式已獲得處理輸入訊息的機會，但尚未處理時，`true`。否則，`false`。  
  
## <a name="requirements"></a>需求  
 **平臺：** 請參閱[.NET Framework 系統需求](../../get-started/system-requirements.md)。  
  
 **URLMON.DLL**  
  
 在 .NET Framework 3.0 和3.5： PresentationHostDLL 中  
  
 在 .NET Framework 4 和更新版本中： PresentationHost_v0400 .dll  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [WPF Unmanaged API 參考](wpf-unmanaged-api-reference.md)
