---
title: 負載從歷史函數 - WPF 非託管 API 引用
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- LoadFromHistory
api_location:
- PresentationHost_v0400.dll
ms.assetid: d037c062-a911-4949-b251-ccd3e48b1d17
ms.openlocfilehash: be9b8658614e678b4370044a753554859d230fed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141571"
---
# <a name="loadfromhistory-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="13953-102">從歷史載入函數（WPF 非託管 API 引用）</span><span class="sxs-lookup"><span data-stu-id="13953-102">LoadFromHistory Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="13953-103">此 API 支援 Windows 演示基礎 （WPF） 基礎結構，不用於直接從代碼中使用。</span><span class="sxs-lookup"><span data-stu-id="13953-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="13953-104">由 Windows 演示基礎 （WPF） 基礎結構用於視窗管理。</span><span class="sxs-lookup"><span data-stu-id="13953-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13953-105">語法</span><span class="sxs-lookup"><span data-stu-id="13953-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadFromHistory_export(  
        IStream* pHistoryStream,
        IBindCtx* pBindCtx  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="13953-106">參數</span><span class="sxs-lookup"><span data-stu-id="13953-106">Parameters</span></span>  
 <span data-ttu-id="13953-107">p歷史流</span><span class="sxs-lookup"><span data-stu-id="13953-107">pHistoryStream</span></span>  
 <span data-ttu-id="13953-108">指向歷史記錄資訊流的指標。</span><span class="sxs-lookup"><span data-stu-id="13953-108">A pointer to a stream of history information.</span></span>  
  
 <span data-ttu-id="13953-109">pBindCtx</span><span class="sxs-lookup"><span data-stu-id="13953-109">pBindCtx</span></span>  
 <span data-ttu-id="13953-110">指向綁定上下文的指標。</span><span class="sxs-lookup"><span data-stu-id="13953-110">A pointer to a bind context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13953-111">需求</span><span class="sxs-lookup"><span data-stu-id="13953-111">Requirements</span></span>  
 <span data-ttu-id="13953-112">**平臺：** 請參閱[.NET 框架系統要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="13953-112">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13953-113">**Dll：**</span><span class="sxs-lookup"><span data-stu-id="13953-113">**DLL:**</span></span>  
  
 <span data-ttu-id="13953-114">在 .NET 框架 3.0 和 3.5 中：演示HostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="13953-114">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="13953-115">在 .NET 框架 4 及更高版本：PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="13953-115">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="13953-116">**.NET 框架版本：**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13953-116">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13953-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="13953-117">See also</span></span>

- [<span data-ttu-id="13953-118">WPF 非受控 API 參考</span><span class="sxs-lookup"><span data-stu-id="13953-118">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
