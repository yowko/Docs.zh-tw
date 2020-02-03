---
title: CreateIDispatchSTAForwarder 函式-WPF 非受控 API 參考
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CreateIDispatchSTAForwarder
api_location:
- PresentationHost_v0400.dll
ms.assetid: 57a02dfa-f091-4ace-9c06-1f4ab52b3527
ms.openlocfilehash: 67f2542733fb9c6af197c99ede2bd097ce876b5d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738038"
---
# <a name="createidispatchstaforwarder-function-wpf-unmanaged-api-reference"></a>CreateIDispatchSTAForwarder 函式（WPF 非受控 API 參考）
這個 API 支援 Windows Presentation Foundation （WPF）基礎結構，但不適合直接從程式碼使用。  
  
 供執行緒和 Windows 管理的 Windows Presentation Foundation （WPF）基礎結構使用。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CreateIDispatchSTAForwarder(  
   __in IDispatch *pDispatchDelegate,   
   __deref_out IDispatch **ppForwarder  
)  
```  
  
## <a name="parameters"></a>參數  
  
## <a name="property-valuereturn-value"></a>屬性值/傳回值  
 pDispatchDelegate  
 `IDispatch` 介面的指標。  
  
 ppForwarder  
 `IDispatch` 介面之位址的指標。  
  
## <a name="requirements"></a>需求  
 **平臺：** 請參閱[.NET Framework 系統需求](../../get-started/system-requirements.md)。  
  
 **URLMON.DLL**  
  
 在 .NET Framework 3.0 和3.5： PresentationHostDLL 中  
  
 在 .NET Framework 4 和更新版本中： PresentationHost_v0400 .dll  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [WPF Unmanaged API 參考](wpf-unmanaged-api-reference.md)
