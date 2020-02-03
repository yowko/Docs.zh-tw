---
title: SaveToHistory 函式-WPF 非受控 API 參考
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- SaveToHistory
api_location:
- PresentationHost_v0400.dll
ms.assetid: 6dd101a3-44ad-4143-b228-772156f9b8ff
ms.openlocfilehash: 7337e5dc23a3dce5de8270902bce228c49bc6edb
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731758"
---
# <a name="savetohistory-function-wpf-unmanaged-api-reference"></a>SaveToHistory 函式（WPF 非受控 API 參考）
這個 API 支援 Windows Presentation Foundation （WPF）基礎結構，但不適合直接從程式碼使用。  
  
 由適用于 Windows 管理的 Windows Presentation Foundation （WPF）基礎結構使用。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SaveToHistory(  
   __in_ecount(1) IStream* pHistoryStream  
)  
```  
  
## <a name="parameters"></a>參數  
 pHistoryStream  
 歷程記錄資料流程的指標。  
  
## <a name="requirements"></a>需求  
  
## <a name="requirements"></a>需求  
 **平臺：** 請參閱[.NET Framework 系統需求](../../get-started/system-requirements.md)。  
  
 **URLMON.DLL**  
  
 在 .NET Framework 3.0 和3.5： PresentationHostDLL 中  
  
 在 .NET Framework 4 和更新版本中： PresentationHost_v0400 .dll  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [WPF Unmanaged API 參考](wpf-unmanaged-api-reference.md)
