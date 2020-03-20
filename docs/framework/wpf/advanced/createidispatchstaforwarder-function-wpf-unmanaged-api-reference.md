---
title: 創建IDispatchSTA轉寄站功能 - WPF非託管 API 引用
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CreateIDispatchSTAForwarder
api_location:
- PresentationHost_v0400.dll
ms.assetid: 57a02dfa-f091-4ace-9c06-1f4ab52b3527
ms.openlocfilehash: e151ffa6eb5f1dc7479c699e0d7f9f3f57833ebd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174715"
---
# <a name="createidispatchstaforwarder-function-wpf-unmanaged-api-reference"></a>創建IDispatchSTA轉寄站功能（WPF非託管 API 參考）
此 API 支援 Windows 演示基礎 （WPF） 基礎結構，不用於直接從代碼中使用。  
  
 由 Windows 演示基礎 （WPF） 基礎結構用於執行緒和視窗管理。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CreateIDispatchSTAForwarder(  
   __in IDispatch *pDispatchDelegate,
   __deref_out IDispatch **ppForwarder  
)  
```  
  
## <a name="parameters"></a>參數  
  
## <a name="property-valuereturn-value"></a>屬性值/傳回值  
 p調度委託  
 指向介面的`IDispatch`指標。  
  
 pp 轉寄站  
 指向介面位址的`IDispatch`指標。  
  
## <a name="requirements"></a>需求  
 **平臺：** 請參閱[.NET 框架系統要求](../../get-started/system-requirements.md)。  
  
 **Dll：**  
  
 在 .NET 框架 3.0 和 3.5 中：演示HostDLL.dll  
  
 在 .NET 框架 4 及更高版本：PresentationHost_v0400.dll  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [WPF 非受控 API 參考](wpf-unmanaged-api-reference.md)
