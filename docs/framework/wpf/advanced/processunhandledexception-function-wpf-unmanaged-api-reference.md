---
title: ProcessUnhandledException 函式-WPF 非受控 API 參考
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ProcessUnhandledException
api_location:
- PresentationHost_v0400.dll
ms.assetid: 495ce5f6-bb4d-4b30-807a-c3c35f1ca95c
ms.openlocfilehash: 757e5ac3aa2dc4c87b210b026998523bd82045c1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743916"
---
# <a name="processunhandledexception-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="4140c-102">ProcessUnhandledException 函式（WPF 非受控 API 參考）</span><span class="sxs-lookup"><span data-stu-id="4140c-102">ProcessUnhandledException Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="4140c-103">這個 API 支援 Windows Presentation Foundation （WPF）基礎結構，但不適合直接從程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="4140c-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="4140c-104">由 Windows Presentation Foundation （WPF）基礎結構用來處理例外狀況。</span><span class="sxs-lookup"><span data-stu-id="4140c-104">Used by the Windows Presentation Foundation (WPF) infrastructure for exception handling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4140c-105">語法</span><span class="sxs-lookup"><span data-stu-id="4140c-105">Syntax</span></span>  
  
```cpp  
void __stdcall ProcessUnhandledException(  
   __in_ecount(1) BSTR errorMsg  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="4140c-106">參數</span><span class="sxs-lookup"><span data-stu-id="4140c-106">Parameters</span></span>  
 <span data-ttu-id="4140c-107">errorMsg</span><span class="sxs-lookup"><span data-stu-id="4140c-107">errorMsg</span></span>  
 <span data-ttu-id="4140c-108">錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="4140c-108">The error message.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4140c-109">需求</span><span class="sxs-lookup"><span data-stu-id="4140c-109">Requirements</span></span>  
 <span data-ttu-id="4140c-110">**平臺：** 請參閱[.NET Framework 系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4140c-110">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4140c-111">**URLMON.DLL**</span><span class="sxs-lookup"><span data-stu-id="4140c-111">**DLL:**</span></span>  
  
 <span data-ttu-id="4140c-112">在 .NET Framework 3.0 和3.5： PresentationHostDLL 中</span><span class="sxs-lookup"><span data-stu-id="4140c-112">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="4140c-113">在 .NET Framework 4 和更新版本中： PresentationHost_v0400 .dll</span><span class="sxs-lookup"><span data-stu-id="4140c-113">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="4140c-114">**.NET Framework 版本：** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4140c-114">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4140c-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4140c-115">See also</span></span>

- [<span data-ttu-id="4140c-116">WPF Unmanaged API 參考</span><span class="sxs-lookup"><span data-stu-id="4140c-116">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
