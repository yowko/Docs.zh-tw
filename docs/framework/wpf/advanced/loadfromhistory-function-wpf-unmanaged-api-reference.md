---
title: LoadFromHistory 函式 (WPF Unmanaged API 參考)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- LoadFromHistory
api_location:
- PresentationHost_v0400.dll
ms.assetid: d037c062-a911-4949-b251-ccd3e48b1d17
ms.openlocfilehash: 4fc083313c99b1b93db380bfbf6ddeacbc784dcb
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57487404"
---
# <a name="loadfromhistory-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="01802-102">LoadFromHistory 函式 (WPF Unmanaged API 參考)</span><span class="sxs-lookup"><span data-stu-id="01802-102">LoadFromHistory Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="01802-103">此 API 支援 Windows Presentation Foundation (WPF) 基礎結構，並不是直接從您的程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="01802-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="01802-104">使用 windows 管理的 Windows Presentation Foundation (WPF) 基礎結構。</span><span class="sxs-lookup"><span data-stu-id="01802-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01802-105">語法</span><span class="sxs-lookup"><span data-stu-id="01802-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadFromHistory_export(  
        IStream* pHistoryStream,   
        IBindCtx* pBindCtx  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="01802-106">參數</span><span class="sxs-lookup"><span data-stu-id="01802-106">Parameters</span></span>  
 <span data-ttu-id="01802-107">pHistoryStream</span><span class="sxs-lookup"><span data-stu-id="01802-107">pHistoryStream</span></span>  
 <span data-ttu-id="01802-108">歷程記錄資訊的資料流的指標。</span><span class="sxs-lookup"><span data-stu-id="01802-108">A pointer to a stream of history information.</span></span>  
  
 <span data-ttu-id="01802-109">pBindCtx</span><span class="sxs-lookup"><span data-stu-id="01802-109">pBindCtx</span></span>  
 <span data-ttu-id="01802-110">繫結內容的指標。</span><span class="sxs-lookup"><span data-stu-id="01802-110">A pointer to a bind context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01802-111">需求</span><span class="sxs-lookup"><span data-stu-id="01802-111">Requirements</span></span>  
 <span data-ttu-id="01802-112">**平台：** 請參閱[.NET Framework 系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="01802-112">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01802-113">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="01802-113">**DLL:**</span></span>  
  
 <span data-ttu-id="01802-114">在.NET Framework 3.0 和 3.5:PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="01802-114">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="01802-115">在.NET Framework 4 及更新版本：PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="01802-115">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="01802-116">**.NET framework 版本：** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01802-116">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01802-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01802-117">See also</span></span>
- [<span data-ttu-id="01802-118">WPF Unmanaged API 參考</span><span class="sxs-lookup"><span data-stu-id="01802-118">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
