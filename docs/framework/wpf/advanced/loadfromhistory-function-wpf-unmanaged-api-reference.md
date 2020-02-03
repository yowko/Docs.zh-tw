---
title: LoadFromHistory 函式-WPF 非受控 API 參考
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- LoadFromHistory
api_location:
- PresentationHost_v0400.dll
ms.assetid: d037c062-a911-4949-b251-ccd3e48b1d17
ms.openlocfilehash: 7807e073d1f09ac6a6213aee6d86d53cc75a3c56
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76727937"
---
# <a name="loadfromhistory-function-wpf-unmanaged-api-reference"></a>LoadFromHistory 函式（WPF 非受控 API 參考）
這個 API 支援 Windows Presentation Foundation （WPF）基礎結構，但不適合直接從程式碼使用。  
  
 由適用于 Windows 管理的 Windows Presentation Foundation （WPF）基礎結構使用。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT LoadFromHistory_export(  
        IStream* pHistoryStream,   
        IBindCtx* pBindCtx  
)  
```  
  
## <a name="parameters"></a>參數  
 pHistoryStream  
 歷程記錄資訊資料流程的指標。  
  
 pBindCtx  
 系結內容的指標。  
  
## <a name="requirements"></a>需求  
 **平臺：** 請參閱[.NET Framework 系統需求](../../get-started/system-requirements.md)。  
  
 **URLMON.DLL**  
  
 在 .NET Framework 3.0 和3.5： PresentationHostDLL 中  
  
 在 .NET Framework 4 和更新版本中： PresentationHost_v0400 .dll  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [WPF Unmanaged API 參考](wpf-unmanaged-api-reference.md)
