---
title: 啟動函式-WPF 非受控 API 參考
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- Activate
api_location:
- PresentationHost_v0400.dll
ms.assetid: 1400329c-b598-465f-80f2-e3dabf044811
ms.openlocfilehash: 9c0a235e8b94294ab82da88e43f7446c29739c12
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734507"
---
# <a name="activate-function-wpf-unmanaged-api-reference"></a>Activate 函式（WPF 非受控 API 參考）

這個 API 支援 Windows Presentation Foundation （WPF）基礎結構，但不適合直接從程式碼使用。

由適用于 Windows 管理的 Windows Presentation Foundation （WPF）基礎結構使用。

## <a name="syntax"></a>語法

```cpp
void Activate(
    const ActivateParameters* pParameters,
    __deref_out_ecount(1) LPUNKNOWN* ppInner,
    );
```

## <a name="parameters"></a>參數

`pParameters`\
視窗啟用參數的指標。

`ppInner`\
單一元素緩衝區的位址指標，其中包含指向 <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> 物件的指標。

## <a name="requirements"></a>需求

**平臺：** 請參閱[.NET Framework 系統需求](../../get-started/system-requirements.md)。

**URLMON.DLL**

在 .NET Framework 3.0 和3.5： PresentationHostDLL 中

在 .NET Framework 4 和更新版本中： PresentationHost_v0400 .dll

**.NET Framework 版本：** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]

## <a name="see-also"></a>請參閱

- [WPF Unmanaged API 參考](wpf-unmanaged-api-reference.md)
