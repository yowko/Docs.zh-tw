---
title: s_isDebuggerCheckDisabledForTestPurposes 欄位
ms.date: 03/30/2017
ms.technology:
- dotnet-wpf
api_name:
- System.Windows.Diagnostics.VisualDiagnostics.s_isDebuggerCheckDisabledForTestPurposes
api_location:
- PresentationCore.dll
api_type:
- Assembly
ms.assetid: 9033a513-c255-4f31-b6d7-09b8d8c50e2d
robots: noindex,nofollow
ms.openlocfilehash: fbbd8d33ea163efaad1417ab4a1435df729e4897
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="sisdebuggercheckdisabledfortestpurposes-field"></a>s_isDebuggerCheckDisabledForTestPurposes 欄位

此私用欄位在`System.Windows.Diagnostics.VisualDiagnostics`類別可由 Visual Studio 來判斷是否要執行的內部檢查作用中的偵錯工具。

## <a name="syntax"></a>語法
  
```csharp  
private static bool s_isDebuggerCheckDisabledForTestPurposes
```
  
> [!WARNING]
>  API 中的`System.Windows.Diagnostics.VisualDiagnostics`偵錯工具下執行應用程式時，才可以使用類別。 設定`s_isDebuggerCheckDisabledForTestPurposes`至`true`存取偵錯工具外部的 Api。  
>   
>  Microsoft 不支援在實際執行應用程式在任何情況下使用此欄位。  

## <a name="requirements"></a>需求

**命名空間：** <xref:System.Windows.Diagnostics>

**組件：** PresentationCore （在 PresentationCore.dll)

**.NET framework 版本：**自 4.6 起可用。
