---
title: s_isDebuggerCheckDisabledForTestPurposes 欄位
ms.date: 03/30/2017
ms.technology: dotnet-wpf
topic_type:
- apiref
api_name:
- System.Windows.Diagnostics.VisualDiagnostics.s_isDebuggerCheckDisabledForTestPurposes
api_location:
- PresentationCore.dll
api_type:
- Assembly
ms.assetid: 9033a513-c255-4f31-b6d7-09b8d8c50e2d
ms.openlocfilehash: ad9bc0ecf4b7a8e5f3ef13fdff5aa59ca8915922
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634663"
---
# <a name="sisdebuggercheckdisabledfortestpurposes-field"></a><span data-ttu-id="4b287-102">s_isDebuggerCheckDisabledForTestPurposes 欄位</span><span class="sxs-lookup"><span data-stu-id="4b287-102">s_isDebuggerCheckDisabledForTestPurposes Field</span></span>

<span data-ttu-id="4b287-103">在此私用欄位`System.Windows.Diagnostics.VisualDiagnostics`類別可由 Visual Studio 來判斷是否要執行的內部檢查作用中的偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="4b287-103">This private field in the `System.Windows.Diagnostics.VisualDiagnostics` class is used by Visual Studio to determine whether an internal check for an active debugger will be performed.</span></span>

## <a name="syntax"></a><span data-ttu-id="4b287-104">語法</span><span class="sxs-lookup"><span data-stu-id="4b287-104">Syntax</span></span>

```csharp
private static bool s_isDebuggerCheckDisabledForTestPurposes
```

> [!WARNING]
> <span data-ttu-id="4b287-105">中的 Api`System.Windows.Diagnostics.VisualDiagnostics`偵錯工具下執行應用程式時，才可用類別。</span><span class="sxs-lookup"><span data-stu-id="4b287-105">APIs in the `System.Windows.Diagnostics.VisualDiagnostics` class are only available when an application is running under a debugger.</span></span> <span data-ttu-id="4b287-106">設定`s_isDebuggerCheckDisabledForTestPurposes`至`true`來存取偵錯工具外部 Api。</span><span class="sxs-lookup"><span data-stu-id="4b287-106">Set `s_isDebuggerCheckDisabledForTestPurposes` to `true` to access the APIs outside of a debugger.</span></span>
>
> <span data-ttu-id="4b287-107">Microsoft 不支援在生產環境應用程式中任何情況下使用此欄位。</span><span class="sxs-lookup"><span data-stu-id="4b287-107">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="4b287-108">需求</span><span class="sxs-lookup"><span data-stu-id="4b287-108">Requirements</span></span>

<span data-ttu-id="4b287-109">**命名空間︰** <xref:System.Windows.Diagnostics></span><span class="sxs-lookup"><span data-stu-id="4b287-109">**Namespace:** <xref:System.Windows.Diagnostics></span></span>

<span data-ttu-id="4b287-110">**組件：** PresentationCore （在 PresentationCore.dll 中)</span><span class="sxs-lookup"><span data-stu-id="4b287-110">**Assembly:** PresentationCore (in PresentationCore.dll)</span></span>

<span data-ttu-id="4b287-111">**.NET framework 版本：** 自 4.6 起可用。</span><span class="sxs-lookup"><span data-stu-id="4b287-111">**.NET Framework versions:** Available since 4.6.</span></span>
