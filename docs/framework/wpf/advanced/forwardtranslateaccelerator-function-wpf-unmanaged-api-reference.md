---
title: ForwardTranslateAccelerator 函式-WPF 非受控 API 參考
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ForwardTranslateAccelerator
api_location:
- PresentationHost_v0400.dll
ms.assetid: fff47a86-9d9f-4176-9530-10e1876e393f
ms.openlocfilehash: f6e8208ffe2c186234f30f31e346ca6b1d0be4c0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747045"
---
# <a name="forwardtranslateaccelerator-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="cfd4c-102">ForwardTranslateAccelerator 函式（WPF 非受控 API 參考）</span><span class="sxs-lookup"><span data-stu-id="cfd4c-102">ForwardTranslateAccelerator Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="cfd4c-103">這個 API 支援 Windows Presentation Foundation （WPF）基礎結構，但不適合直接從程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="cfd4c-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="cfd4c-104">由適用于 Windows 管理的 Windows Presentation Foundation （WPF）基礎結構使用。</span><span class="sxs-lookup"><span data-stu-id="cfd4c-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfd4c-105">語法</span><span class="sxs-lookup"><span data-stu-id="cfd4c-105">Syntax</span></span>  
  
```cpp  
HRESULT ForwardTranslateAccelerator(  
   MSG* pMsg,   
   VARIANT_BOOL appUnhandled  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="cfd4c-106">參數</span><span class="sxs-lookup"><span data-stu-id="cfd4c-106">Parameters</span></span>  
 <span data-ttu-id="cfd4c-107">pMsg</span><span class="sxs-lookup"><span data-stu-id="cfd4c-107">pMsg</span></span>  
 <span data-ttu-id="cfd4c-108">訊息的指標。</span><span class="sxs-lookup"><span data-stu-id="cfd4c-108">A pointer to a message.</span></span>  
  
 <span data-ttu-id="cfd4c-109">appUnhandled</span><span class="sxs-lookup"><span data-stu-id="cfd4c-109">appUnhandled</span></span>  
 <span data-ttu-id="cfd4c-110">當應用程式已獲得處理輸入訊息的機會，但尚未處理時，`true`。否則，`false`。</span><span class="sxs-lookup"><span data-stu-id="cfd4c-110">`true` when the app has already been given a chance to handle the input message, but has not handled it; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cfd4c-111">需求</span><span class="sxs-lookup"><span data-stu-id="cfd4c-111">Requirements</span></span>  
 <span data-ttu-id="cfd4c-112">**平臺：** 請參閱[.NET Framework 系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cfd4c-112">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cfd4c-113">**URLMON.DLL**</span><span class="sxs-lookup"><span data-stu-id="cfd4c-113">**DLL:**</span></span>  
  
 <span data-ttu-id="cfd4c-114">在 .NET Framework 3.0 和3.5： PresentationHostDLL 中</span><span class="sxs-lookup"><span data-stu-id="cfd4c-114">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="cfd4c-115">在 .NET Framework 4 和更新版本中： PresentationHost_v0400 .dll</span><span class="sxs-lookup"><span data-stu-id="cfd4c-115">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="cfd4c-116">**.NET Framework 版本：** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cfd4c-116">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfd4c-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="cfd4c-117">See also</span></span>

- [<span data-ttu-id="cfd4c-118">WPF Unmanaged API 參考</span><span class="sxs-lookup"><span data-stu-id="cfd4c-118">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
