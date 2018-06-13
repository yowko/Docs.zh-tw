---
title: LoadFromHistory 函式 (WPF Unmanaged API 參考)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- LoadFromHistory
api_location:
- PresentationHost_v0400.dll
ms.assetid: d037c062-a911-4949-b251-ccd3e48b1d17
ms.openlocfilehash: 19674b45af84e1e6a6ca169f7b6654c6e3847416
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544660"
---
# <a name="loadfromhistory-function-wpf-unmanaged-api-reference"></a>LoadFromHistory 函式 (WPF Unmanaged API 參考)
這個 API 支援的 Windows Presentation Foundation (WPF) 基礎結構，並不是直接從您的程式碼使用。  
  
 Windows Presentation Foundation (WPF) 基礎結構用於 windows 的管理。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT LoadFromHistory_export(  
        IStream* pHistoryStream,   
        IBindCtx* pBindCtx  
)  
```  
  
#### <a name="parameters"></a>參數  
 pHistoryStream  
 歷程記錄資訊的資料流的指標。  
  
 pBindCtx  
 繫結內容的指標。  
  
## <a name="requirements"></a>需求  
 **平台：** 看到[.NET Framework 系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **DLL:**  
  
 在.NET Framework 3.0 和 3.5: PresentationHostDLL.dll  
  
 在.NET Framework 4 和更新版本： PresentationHost_v0400.dll  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [WPF Unmanaged API 參考](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
