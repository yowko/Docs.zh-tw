---
title: SaveToHistory 函式 (WPF Unmanaged API 參考)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- SaveToHistory
api_location:
- PresentationHost_v0400.dll
ms.assetid: 6dd101a3-44ad-4143-b228-772156f9b8ff
ms.openlocfilehash: 3f6413558ff1f259e497c6a1c31eb2664f70cc48
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59213712"
---
# <a name="savetohistory-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="9b166-102">SaveToHistory 函式 (WPF Unmanaged API 參考)</span><span class="sxs-lookup"><span data-stu-id="9b166-102">SaveToHistory Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="9b166-103">此 API 支援 Windows Presentation Foundation (WPF) 基礎結構，並不是直接從您的程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="9b166-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="9b166-104">使用 windows 管理的 Windows Presentation Foundation (WPF) 基礎結構。</span><span class="sxs-lookup"><span data-stu-id="9b166-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b166-105">語法</span><span class="sxs-lookup"><span data-stu-id="9b166-105">Syntax</span></span>  
  
```cpp  
HRESULT SaveToHistory(  
   __in_ecount(1) IStream* pHistoryStream  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b166-106">參數</span><span class="sxs-lookup"><span data-stu-id="9b166-106">Parameters</span></span>  
 <span data-ttu-id="9b166-107">pHistoryStream</span><span class="sxs-lookup"><span data-stu-id="9b166-107">pHistoryStream</span></span>  
 <span data-ttu-id="9b166-108">歷程記錄資料流的指標。</span><span class="sxs-lookup"><span data-stu-id="9b166-108">A pointer to the history stream.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b166-109">需求</span><span class="sxs-lookup"><span data-stu-id="9b166-109">Requirements</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b166-110">需求</span><span class="sxs-lookup"><span data-stu-id="9b166-110">Requirements</span></span>  
 <span data-ttu-id="9b166-111">**平台：** 請參閱[.NET Framework 系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9b166-111">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 **<span data-ttu-id="9b166-112">DLL:</span><span class="sxs-lookup"><span data-stu-id="9b166-112">DLL:</span></span>**  
  
 <span data-ttu-id="9b166-113">在.NET Framework 3.0 和 3.5:PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="9b166-113">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="9b166-114">在.NET Framework 4 及更新版本：PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="9b166-114">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 **<span data-ttu-id="9b166-115">.NET framework 版本：</span><span class="sxs-lookup"><span data-stu-id="9b166-115">.NET Framework Version:</span></span>** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9b166-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9b166-116">See also</span></span>

- [<span data-ttu-id="9b166-117">WPF 非受控 API 參考</span><span class="sxs-lookup"><span data-stu-id="9b166-117">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
