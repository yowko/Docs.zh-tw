---
title: 轉發加速器功能 - WPF 非託管 API 引用
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ForwardTranslateAccelerator
api_location:
- PresentationHost_v0400.dll
ms.assetid: fff47a86-9d9f-4176-9530-10e1876e393f
ms.openlocfilehash: a0a01be3000dc53df7855cb74015ba1164206838
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186624"
---
# <a name="forwardtranslateaccelerator-function-wpf-unmanaged-api-reference"></a>轉發加速器功能（WPF 非託管 API 引用）
此 API 支援 Windows 演示基礎 （WPF） 基礎結構，不用於直接從代碼中使用。  
  
 由 Windows 演示基礎 （WPF） 基礎結構用於視窗管理。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ForwardTranslateAccelerator(  
   MSG* pMsg,
   VARIANT_BOOL appUnhandled  
)  
```  
  
## <a name="parameters"></a>參數  
 pMsg  
 指向消息的指標。  
  
 應用程式未處理  
 `true`當應用程式已有機會處理輸入消息，但尚未處理它;否則， `false`.  
  
## <a name="requirements"></a>需求  
 **平臺：** 請參閱[.NET 框架系統要求](../../get-started/system-requirements.md)。  
  
 **Dll：**  
  
 在 .NET 框架 3.0 和 3.5 中：演示HostDLL.dll  
  
 在 .NET 框架 4 及更高版本：PresentationHost_v0400.dll  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [WPF 非受控 API 參考](wpf-unmanaged-api-reference.md)
