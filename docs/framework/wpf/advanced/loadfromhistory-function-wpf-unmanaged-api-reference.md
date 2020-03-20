---
title: 負載從歷史函數 - WPF 非託管 API 引用
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- LoadFromHistory
api_location:
- PresentationHost_v0400.dll
ms.assetid: d037c062-a911-4949-b251-ccd3e48b1d17
ms.openlocfilehash: be9b8658614e678b4370044a753554859d230fed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141571"
---
# <a name="loadfromhistory-function-wpf-unmanaged-api-reference"></a>從歷史載入函數（WPF 非託管 API 引用）
此 API 支援 Windows 演示基礎 （WPF） 基礎結構，不用於直接從代碼中使用。  
  
 由 Windows 演示基礎 （WPF） 基礎結構用於視窗管理。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT LoadFromHistory_export(  
        IStream* pHistoryStream,
        IBindCtx* pBindCtx  
)  
```  
  
## <a name="parameters"></a>參數  
 p歷史流  
 指向歷史記錄資訊流的指標。  
  
 pBindCtx  
 指向綁定上下文的指標。  
  
## <a name="requirements"></a>需求  
 **平臺：** 請參閱[.NET 框架系統要求](../../get-started/system-requirements.md)。  
  
 **Dll：**  
  
 在 .NET 框架 3.0 和 3.5 中：演示HostDLL.dll  
  
 在 .NET 框架 4 及更高版本：PresentationHost_v0400.dll  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [WPF 非受控 API 參考](wpf-unmanaged-api-reference.md)
