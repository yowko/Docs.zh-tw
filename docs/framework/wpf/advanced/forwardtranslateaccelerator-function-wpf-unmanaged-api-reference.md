---
title: "ForwardTranslateAccelerator 函式 (WPF Unmanaged API 參考)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- cpp
api_name:
- ForwardTranslateAccelerator
api_location:
- PresentationHost_v0400.dll
ms.assetid: fff47a86-9d9f-4176-9530-10e1876e393f
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: cca9c78eaf13e04d22fce9f61ce4a7ab9ee09769
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="forwardtranslateaccelerator-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="80412-102">ForwardTranslateAccelerator 函式 (WPF Unmanaged API 參考)</span><span class="sxs-lookup"><span data-stu-id="80412-102">ForwardTranslateAccelerator Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="80412-103">這個 API 支援的 Windows Presentation Foundation (WPF) 基礎結構，並不是直接從您的程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="80412-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="80412-104">Windows Presentation Foundation (WPF) 基礎結構用於 windows 的管理。</span><span class="sxs-lookup"><span data-stu-id="80412-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80412-105">語法</span><span class="sxs-lookup"><span data-stu-id="80412-105">Syntax</span></span>  
  
```cpp  
HRESULT ForwardTranslateAccelerator(  
   MSG* pMsg,   
   VARIANT_BOOL appUnhandled  
)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="80412-106">參數</span><span class="sxs-lookup"><span data-stu-id="80412-106">Parameters</span></span>  
 <span data-ttu-id="80412-107">pMsg</span><span class="sxs-lookup"><span data-stu-id="80412-107">pMsg</span></span>  
 <span data-ttu-id="80412-108">訊息指標。</span><span class="sxs-lookup"><span data-stu-id="80412-108">A pointer to a message.</span></span>  
  
 <span data-ttu-id="80412-109">appUnhandled</span><span class="sxs-lookup"><span data-stu-id="80412-109">appUnhandled</span></span>  
 <span data-ttu-id="80412-110">`true`當此應用程式已經指定有機會處理輸入的訊息，但未處理。否則， `false`。</span><span class="sxs-lookup"><span data-stu-id="80412-110">`true` when the app has already been given a chance to handle the input message, but has not handled it; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80412-111">需求</span><span class="sxs-lookup"><span data-stu-id="80412-111">Requirements</span></span>  
 <span data-ttu-id="80412-112">**平台：**看到[.NET Framework 系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="80412-112">**Platforms:** See [.NET Framework System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80412-113">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="80412-113">**DLL:**</span></span>  
  
 <span data-ttu-id="80412-114">在.NET Framework 3.0 和 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="80412-114">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="80412-115">在.NET Framework 4 和更新版本： PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="80412-115">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="80412-116">**.NET framework 版本：**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80412-116">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80412-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="80412-117">See Also</span></span>  
 [<span data-ttu-id="80412-118">WPF Unmanaged API 參考</span><span class="sxs-lookup"><span data-stu-id="80412-118">WPF Unmanaged API Reference</span></span>](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
