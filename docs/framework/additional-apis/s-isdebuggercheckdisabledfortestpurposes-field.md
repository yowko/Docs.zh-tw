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
# <a name="sisdebuggercheckdisabledfortestpurposes-field"></a><span data-ttu-id="8634e-102">s_isDebuggerCheckDisabledForTestPurposes 欄位</span><span class="sxs-lookup"><span data-stu-id="8634e-102">s_isDebuggerCheckDisabledForTestPurposes Field</span></span>

<span data-ttu-id="8634e-103">在此私用欄位`System.Windows.Diagnostics.VisualDiagnostics`類別可由 Visual Studio 來判斷是否要執行的內部檢查作用中的偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="8634e-103">This private field in the `System.Windows.Diagnostics.VisualDiagnostics` class is used by Visual Studio to determine whether an internal check for an active debugger will be performed.</span></span>

## <a name="syntax"></a><span data-ttu-id="8634e-104">語法</span><span class="sxs-lookup"><span data-stu-id="8634e-104">Syntax</span></span>
  
```csharp  
private static bool s_isDebuggerCheckDisabledForTestPurposes
```
  
> [!WARNING]
>  <span data-ttu-id="8634e-105">API 在`System.Windows.Diagnostics.VisualDiagnostics`偵錯工具下執行應用程式時，才可用類別。</span><span class="sxs-lookup"><span data-stu-id="8634e-105">API's in the `System.Windows.Diagnostics.VisualDiagnostics` class are only available when an application is running under a debugger.</span></span> <span data-ttu-id="8634e-106">設定`s_isDebuggerCheckDisabledForTestPurposes`至`true`來存取偵錯工具外部 Api。</span><span class="sxs-lookup"><span data-stu-id="8634e-106">Set `s_isDebuggerCheckDisabledForTestPurposes` to `true` to access the APIs outside of a debugger.</span></span>  
>   
>  <span data-ttu-id="8634e-107">Microsoft 不支援在生產環境應用程式中任何情況下使用此欄位。</span><span class="sxs-lookup"><span data-stu-id="8634e-107">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>  

## <a name="requirements"></a><span data-ttu-id="8634e-108">需求</span><span class="sxs-lookup"><span data-stu-id="8634e-108">Requirements</span></span>

<span data-ttu-id="8634e-109">**命名空間︰** <xref:System.Windows.Diagnostics></span><span class="sxs-lookup"><span data-stu-id="8634e-109">**Namespace:** <xref:System.Windows.Diagnostics></span></span>

<span data-ttu-id="8634e-110">**組件：** PresentationCore （在 PresentationCore.dll 中)</span><span class="sxs-lookup"><span data-stu-id="8634e-110">**Assembly:** PresentationCore (in PresentationCore.dll)</span></span>

<span data-ttu-id="8634e-111">**.NET framework 版本：** 自 4.6 起可用。</span><span class="sxs-lookup"><span data-stu-id="8634e-111">**.NET Framework versions:** Available since 4.6.</span></span>