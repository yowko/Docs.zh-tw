---
title: SaveToHistory 函式 (WPF Unmanaged API 參考)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- SaveToHistory
api_location:
- PresentationHost_v0400.dll
ms.assetid: 6dd101a3-44ad-4143-b228-772156f9b8ff
ms.openlocfilehash: 3f6413558ff1f259e497c6a1c31eb2664f70cc48
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053453"
---
# <a name="savetohistory-function-wpf-unmanaged-api-reference"></a>SaveToHistory 函式 (WPF Unmanaged API 參考)
此 API 支援 Windows Presentation Foundation (WPF) 基礎結構，並不是直接從您的程式碼使用。  
  
 使用 windows 管理的 Windows Presentation Foundation (WPF) 基礎結構。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SaveToHistory(  
   __in_ecount(1) IStream* pHistoryStream  
)  
```  
  
## <a name="parameters"></a>參數  
 pHistoryStream  
 歷程記錄資料流的指標。  
  
## <a name="requirements"></a>需求  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[.NET Framework 系統需求](../../get-started/system-requirements.md)。  
  
 **DLL:**  
  
 在.NET Framework 3.0 和 3.5:PresentationHostDLL.dll  
  
 在.NET Framework 4 及更新版本：PresentationHost_v0400.dll  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [WPF Unmanaged API 參考](wpf-unmanaged-api-reference.md)
