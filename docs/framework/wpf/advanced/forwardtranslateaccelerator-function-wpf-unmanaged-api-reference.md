---
title: ForwardTranslateAccelerator 函式 (WPF Unmanaged API 參考)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ForwardTranslateAccelerator
api_location:
- PresentationHost_v0400.dll
ms.assetid: fff47a86-9d9f-4176-9530-10e1876e393f
ms.openlocfilehash: 78031ed80fe83b736a351886457f9200534f470b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54591509"
---
# <a name="forwardtranslateaccelerator-function-wpf-unmanaged-api-reference"></a>ForwardTranslateAccelerator 函式 (WPF Unmanaged API 參考)
此 API 支援 Windows Presentation Foundation (WPF) 基礎結構，並不是直接從您的程式碼使用。  
  
 使用 windows 管理的 Windows Presentation Foundation (WPF) 基礎結構。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ForwardTranslateAccelerator(  
   MSG* pMsg,   
   VARIANT_BOOL appUnhandled  
)  
```  
  
#### <a name="parameters"></a>參數  
 pMsg  
 訊息指標。  
  
 appUnhandled  
 `true` 此應用程式時已指定有機會處理輸入的訊息，但未處理，否則， `false`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[.NET Framework 系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **DLL:**  
  
 在.NET Framework 3.0 和 3.5:PresentationHostDLL.dll  
  
 在.NET Framework 4 及更新版本：PresentationHost_v0400.dll  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [WPF Unmanaged API 參考](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
