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
# <a name="sisdebuggercheckdisabledfortestpurposes-field"></a><span data-ttu-id="ad344-102">s_isDebuggerCheckDisabledForTestPurposes 欄位</span><span class="sxs-lookup"><span data-stu-id="ad344-102">s_isDebuggerCheckDisabledForTestPurposes Field</span></span>

<span data-ttu-id="ad344-103">此私用欄位在`System.Windows.Diagnostics.VisualDiagnostics`類別可由 Visual Studio 來判斷是否要執行的內部檢查作用中的偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="ad344-103">This private field in the `System.Windows.Diagnostics.VisualDiagnostics` class is used by Visual Studio to determine whether an internal check for an active debugger will be performed.</span></span>

## <a name="syntax"></a><span data-ttu-id="ad344-104">語法</span><span class="sxs-lookup"><span data-stu-id="ad344-104">Syntax</span></span>
  
```csharp  
private static bool s_isDebuggerCheckDisabledForTestPurposes
```
  
> [!WARNING]
>  <span data-ttu-id="ad344-105">API 中的`System.Windows.Diagnostics.VisualDiagnostics`偵錯工具下執行應用程式時，才可以使用類別。</span><span class="sxs-lookup"><span data-stu-id="ad344-105">API's in the `System.Windows.Diagnostics.VisualDiagnostics` class are only available when an application is running under a debugger.</span></span> <span data-ttu-id="ad344-106">設定`s_isDebuggerCheckDisabledForTestPurposes`至`true`存取偵錯工具外部的 Api。</span><span class="sxs-lookup"><span data-stu-id="ad344-106">Set `s_isDebuggerCheckDisabledForTestPurposes` to `true` to access the APIs outside of a debugger.</span></span>  
>   
>  <span data-ttu-id="ad344-107">Microsoft 不支援在實際執行應用程式在任何情況下使用此欄位。</span><span class="sxs-lookup"><span data-stu-id="ad344-107">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>  

## <a name="requirements"></a><span data-ttu-id="ad344-108">需求</span><span class="sxs-lookup"><span data-stu-id="ad344-108">Requirements</span></span>

<span data-ttu-id="ad344-109">**命名空間：** <xref:System.Windows.Diagnostics></span><span class="sxs-lookup"><span data-stu-id="ad344-109">**Namespace:** <xref:System.Windows.Diagnostics></span></span>

<span data-ttu-id="ad344-110">**組件：** PresentationCore （在 PresentationCore.dll)</span><span class="sxs-lookup"><span data-stu-id="ad344-110">**Assembly:** PresentationCore (in PresentationCore.dll)</span></span>

<span data-ttu-id="ad344-111">**.NET framework 版本：** 自 4.6 起可用。</span><span class="sxs-lookup"><span data-stu-id="ad344-111">**.NET Framework versions:** Available since 4.6.</span></span>
