---
title: ForwardTranslateAccelerator 函式 (WPF Unmanaged API 參考)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ForwardTranslateAccelerator
api_location:
- PresentationHost_v0400.dll
ms.assetid: fff47a86-9d9f-4176-9530-10e1876e393f
ms.openlocfilehash: 4bb7e665bb836dc5f95b14f39179f1d4b9f8173d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59080250"
---
# <a name="forwardtranslateaccelerator-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="363ef-102">ForwardTranslateAccelerator 函式 (WPF Unmanaged API 參考)</span><span class="sxs-lookup"><span data-stu-id="363ef-102">ForwardTranslateAccelerator Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="363ef-103">此 API 支援 Windows Presentation Foundation (WPF) 基礎結構，並不是直接從您的程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="363ef-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="363ef-104">使用 windows 管理的 Windows Presentation Foundation (WPF) 基礎結構。</span><span class="sxs-lookup"><span data-stu-id="363ef-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="363ef-105">語法</span><span class="sxs-lookup"><span data-stu-id="363ef-105">Syntax</span></span>  
  
```cpp  
HRESULT ForwardTranslateAccelerator(  
   MSG* pMsg,   
   VARIANT_BOOL appUnhandled  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="363ef-106">參數</span><span class="sxs-lookup"><span data-stu-id="363ef-106">Parameters</span></span>  
 <span data-ttu-id="363ef-107">pMsg</span><span class="sxs-lookup"><span data-stu-id="363ef-107">pMsg</span></span>  
 <span data-ttu-id="363ef-108">訊息指標。</span><span class="sxs-lookup"><span data-stu-id="363ef-108">A pointer to a message.</span></span>  
  
 <span data-ttu-id="363ef-109">appUnhandled</span><span class="sxs-lookup"><span data-stu-id="363ef-109">appUnhandled</span></span>  
 <span data-ttu-id="363ef-110">`true` 此應用程式時已指定有機會處理輸入的訊息，但未處理，否則， `false`。</span><span class="sxs-lookup"><span data-stu-id="363ef-110">`true` when the app has already been given a chance to handle the input message, but has not handled it; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="363ef-111">需求</span><span class="sxs-lookup"><span data-stu-id="363ef-111">Requirements</span></span>  
 <span data-ttu-id="363ef-112">**平台：** 請參閱[.NET Framework 系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="363ef-112">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="363ef-113">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="363ef-113">**DLL:**</span></span>  
  
 <span data-ttu-id="363ef-114">在.NET Framework 3.0 和 3.5:PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="363ef-114">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="363ef-115">在.NET Framework 4 及更新版本：PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="363ef-115">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="363ef-116">**.NET framework 版本：** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="363ef-116">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="363ef-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="363ef-117">See also</span></span>

- [<span data-ttu-id="363ef-118">WPF Unmanaged API 參考</span><span class="sxs-lookup"><span data-stu-id="363ef-118">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
