---
title: ProcessUnhandledException 函式 (WPF Unmanaged API 參考)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ProcessUnhandledException
api_location:
- PresentationHost_v0400.dll
ms.assetid: 495ce5f6-bb4d-4b30-807a-c3c35f1ca95c
ms.openlocfilehash: bcde3fe6d3fdc1749f29a5c9f7625f802dd49535
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544520"
---
# <a name="processunhandledexception-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="76677-102">ProcessUnhandledException 函式 (WPF Unmanaged API 參考)</span><span class="sxs-lookup"><span data-stu-id="76677-102">ProcessUnhandledException Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="76677-103">這個 API 支援的 Windows Presentation Foundation (WPF) 基礎結構，並不是直接從您的程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="76677-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="76677-104">Windows Presentation Foundation (WPF) 基礎結構用於例外狀況處理。</span><span class="sxs-lookup"><span data-stu-id="76677-104">Used by the Windows Presentation Foundation (WPF) infrastructure for exception handling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76677-105">語法</span><span class="sxs-lookup"><span data-stu-id="76677-105">Syntax</span></span>  
  
```cpp  
void __stdcall ProcessUnhandledException(  
   __in_ecount(1) BSTR errorMsg  
)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="76677-106">參數</span><span class="sxs-lookup"><span data-stu-id="76677-106">Parameters</span></span>  
 <span data-ttu-id="76677-107">errorMsg</span><span class="sxs-lookup"><span data-stu-id="76677-107">errorMsg</span></span>  
 <span data-ttu-id="76677-108">錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="76677-108">The error message.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76677-109">需求</span><span class="sxs-lookup"><span data-stu-id="76677-109">Requirements</span></span>  
 <span data-ttu-id="76677-110">**平台：** 看到[.NET Framework 系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="76677-110">**Platforms:** See [.NET Framework System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76677-111">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="76677-111">**DLL:**</span></span>  
  
 <span data-ttu-id="76677-112">在.NET Framework 3.0 和 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="76677-112">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="76677-113">在.NET Framework 4 和更新版本： PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="76677-113">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="76677-114">**.NET framework 版本：** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76677-114">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76677-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="76677-115">See Also</span></span>  
 [<span data-ttu-id="76677-116">WPF Unmanaged API 參考</span><span class="sxs-lookup"><span data-stu-id="76677-116">WPF Unmanaged API Reference</span></span>](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
