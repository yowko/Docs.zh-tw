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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59080250"
---
# <a name="forwardtranslateaccelerator-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="9b19e-102">ForwardTranslateAccelerator 函式 (WPF Unmanaged API 參考)</span><span class="sxs-lookup"><span data-stu-id="9b19e-102">ForwardTranslateAccelerator Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="9b19e-103">此 API 支援 Windows Presentation Foundation (WPF) 基礎結構，並不是直接從您的程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="9b19e-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="9b19e-104">使用 windows 管理的 Windows Presentation Foundation (WPF) 基礎結構。</span><span class="sxs-lookup"><span data-stu-id="9b19e-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b19e-105">語法</span><span class="sxs-lookup"><span data-stu-id="9b19e-105">Syntax</span></span>  
  
```cpp  
HRESULT ForwardTranslateAccelerator(  
   MSG* pMsg,   
   VARIANT_BOOL appUnhandled  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b19e-106">參數</span><span class="sxs-lookup"><span data-stu-id="9b19e-106">Parameters</span></span>  
 <span data-ttu-id="9b19e-107">pMsg</span><span class="sxs-lookup"><span data-stu-id="9b19e-107">pMsg</span></span>  
 <span data-ttu-id="9b19e-108">訊息指標。</span><span class="sxs-lookup"><span data-stu-id="9b19e-108">A pointer to a message.</span></span>  
  
 <span data-ttu-id="9b19e-109">appUnhandled</span><span class="sxs-lookup"><span data-stu-id="9b19e-109">appUnhandled</span></span>  
 `true` <span data-ttu-id="9b19e-110">此應用程式時已指定有機會處理輸入的訊息，但未處理，否則， `false`。</span><span class="sxs-lookup"><span data-stu-id="9b19e-110">when the app has already been given a chance to handle the input message, but has not handled it; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b19e-111">需求</span><span class="sxs-lookup"><span data-stu-id="9b19e-111">Requirements</span></span>  
 <span data-ttu-id="9b19e-112">**平台：** 請參閱[.NET Framework 系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9b19e-112">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 **<span data-ttu-id="9b19e-113">DLL:</span><span class="sxs-lookup"><span data-stu-id="9b19e-113">DLL:</span></span>**  
  
 <span data-ttu-id="9b19e-114">在.NET Framework 3.0 和 3.5:PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="9b19e-114">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="9b19e-115">在.NET Framework 4 及更新版本：PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="9b19e-115">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 **<span data-ttu-id="9b19e-116">.NET framework 版本：</span><span class="sxs-lookup"><span data-stu-id="9b19e-116">.NET Framework Version:</span></span>** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9b19e-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9b19e-117">See also</span></span>

- [<span data-ttu-id="9b19e-118">WPF 非受控 API 參考</span><span class="sxs-lookup"><span data-stu-id="9b19e-118">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
