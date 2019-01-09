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
ms.openlocfilehash: f490ccb4675a434e3f3336723e321f256b10093d
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149172"
---
# <a name="sisdebuggercheckdisabledfortestpurposes-field"></a>s_isDebuggerCheckDisabledForTestPurposes 欄位

在此私用欄位`System.Windows.Diagnostics.VisualDiagnostics`類別可由 Visual Studio 來判斷是否要執行的內部檢查作用中的偵錯工具。

## <a name="syntax"></a>語法
  
```csharp  
private static bool s_isDebuggerCheckDisabledForTestPurposes
```
  
> [!WARNING]
>  API 在`System.Windows.Diagnostics.VisualDiagnostics`偵錯工具下執行應用程式時，才可用類別。 設定`s_isDebuggerCheckDisabledForTestPurposes`至`true`來存取偵錯工具外部 Api。  
>   
>  Microsoft 不支援在生產環境應用程式中任何情況下使用此欄位。  

## <a name="requirements"></a>需求

**命名空間︰** <xref:System.Windows.Diagnostics>

**組件：** PresentationCore （在 PresentationCore.dll 中)

**.NET framework 版本：** 自 4.6 起可用。