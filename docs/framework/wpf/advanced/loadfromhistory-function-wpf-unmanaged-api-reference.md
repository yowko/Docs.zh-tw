---
title: LoadFromHistory 函式-WPF 非受控 API 參考
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- LoadFromHistory
api_location:
- PresentationHost_v0400.dll
ms.assetid: d037c062-a911-4949-b251-ccd3e48b1d17
ms.openlocfilehash: 7807e073d1f09ac6a6213aee6d86d53cc75a3c56
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76727937"
---
# <a name="loadfromhistory-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="5bd5e-102">LoadFromHistory 函式（WPF 非受控 API 參考）</span><span class="sxs-lookup"><span data-stu-id="5bd5e-102">LoadFromHistory Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="5bd5e-103">這個 API 支援 Windows Presentation Foundation （WPF）基礎結構，但不適合直接從程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="5bd5e-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="5bd5e-104">由適用于 Windows 管理的 Windows Presentation Foundation （WPF）基礎結構使用。</span><span class="sxs-lookup"><span data-stu-id="5bd5e-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bd5e-105">語法</span><span class="sxs-lookup"><span data-stu-id="5bd5e-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadFromHistory_export(  
        IStream* pHistoryStream,   
        IBindCtx* pBindCtx  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="5bd5e-106">參數</span><span class="sxs-lookup"><span data-stu-id="5bd5e-106">Parameters</span></span>  
 <span data-ttu-id="5bd5e-107">pHistoryStream</span><span class="sxs-lookup"><span data-stu-id="5bd5e-107">pHistoryStream</span></span>  
 <span data-ttu-id="5bd5e-108">歷程記錄資訊資料流程的指標。</span><span class="sxs-lookup"><span data-stu-id="5bd5e-108">A pointer to a stream of history information.</span></span>  
  
 <span data-ttu-id="5bd5e-109">pBindCtx</span><span class="sxs-lookup"><span data-stu-id="5bd5e-109">pBindCtx</span></span>  
 <span data-ttu-id="5bd5e-110">系結內容的指標。</span><span class="sxs-lookup"><span data-stu-id="5bd5e-110">A pointer to a bind context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5bd5e-111">需求</span><span class="sxs-lookup"><span data-stu-id="5bd5e-111">Requirements</span></span>  
 <span data-ttu-id="5bd5e-112">**平臺：** 請參閱[.NET Framework 系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5bd5e-112">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5bd5e-113">**URLMON.DLL**</span><span class="sxs-lookup"><span data-stu-id="5bd5e-113">**DLL:**</span></span>  
  
 <span data-ttu-id="5bd5e-114">在 .NET Framework 3.0 和3.5： PresentationHostDLL 中</span><span class="sxs-lookup"><span data-stu-id="5bd5e-114">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="5bd5e-115">在 .NET Framework 4 和更新版本中： PresentationHost_v0400 .dll</span><span class="sxs-lookup"><span data-stu-id="5bd5e-115">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="5bd5e-116">**.NET Framework 版本：** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5bd5e-116">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bd5e-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5bd5e-117">See also</span></span>

- [<span data-ttu-id="5bd5e-118">WPF Unmanaged API 參考</span><span class="sxs-lookup"><span data-stu-id="5bd5e-118">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
