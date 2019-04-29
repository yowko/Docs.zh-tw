---
title: 啟用函式 (WPF Unmanaged API 參考)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- Activate
api_location:
- PresentationHost_v0400.dll
ms.assetid: 1400329c-b598-465f-80f2-e3dabf044811
ms.openlocfilehash: ee231653815bd5ef75d58979034e3b3be9f5ba54
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777165"
---
# <a name="activate-function-wpf-unmanaged-api-reference"></a>啟用函式 (WPF Unmanaged API 參考)

此 API 支援 Windows Presentation Foundation (WPF) 基礎結構，並不是直接從您的程式碼使用。

使用 windows 管理的 Windows Presentation Foundation (WPF) 基礎結構。

## <a name="syntax"></a>語法

```cpp
void Activate(
    const ActivateParameters* pParameters,
    __deref_out_ecount(1) LPUNKNOWN* ppInner,
    );
```

## <a name="parameters"></a>參數

`pParameters`\
指向視窗的啟動參數的指標。

`ppInner`\
包含一個指向單一項目緩衝區的位址指標<xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument>物件。

## <a name="requirements"></a>需求

**平台：** 請參閱[.NET Framework 系統需求](../../get-started/system-requirements.md)。

**DLL:**

在.NET Framework 3.0 和 3.5:PresentationHostDLL.dll

在.NET Framework 4 及更新版本：PresentationHost_v0400.dll

**.NET framework 版本：** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]

## <a name="see-also"></a>另請參閱

- [WPF Unmanaged API 參考](wpf-unmanaged-api-reference.md)
