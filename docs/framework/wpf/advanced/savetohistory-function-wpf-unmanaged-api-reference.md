---
title: "SaveToHistory 函式 (WPF Unmanaged API 參考)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
api_name: SaveToHistory
api_location: PresentationHost_v0400.dll
ms.assetid: 6dd101a3-44ad-4143-b228-772156f9b8ff
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b30884433f81aa5e4bf1241ae4fe34494bef788e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="savetohistory-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="de6cc-102">SaveToHistory 函式 (WPF Unmanaged API 參考)</span><span class="sxs-lookup"><span data-stu-id="de6cc-102">SaveToHistory Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="de6cc-103">這個 API 支援的 Windows Presentation Foundation (WPF) 基礎結構，並不是直接從您的程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="de6cc-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="de6cc-104">Windows Presentation Foundation (WPF) 基礎結構用於 windows 的管理。</span><span class="sxs-lookup"><span data-stu-id="de6cc-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de6cc-105">語法</span><span class="sxs-lookup"><span data-stu-id="de6cc-105">Syntax</span></span>  
  
```cpp  
HRESULT SaveToHistory(  
   __in_ecount(1) IStream* pHistoryStream  
)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="de6cc-106">參數</span><span class="sxs-lookup"><span data-stu-id="de6cc-106">Parameters</span></span>  
 <span data-ttu-id="de6cc-107">pHistoryStream</span><span class="sxs-lookup"><span data-stu-id="de6cc-107">pHistoryStream</span></span>  
 <span data-ttu-id="de6cc-108">歷程記錄資料流的指標。</span><span class="sxs-lookup"><span data-stu-id="de6cc-108">A pointer to the history stream.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de6cc-109">需求</span><span class="sxs-lookup"><span data-stu-id="de6cc-109">Requirements</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de6cc-110">需求</span><span class="sxs-lookup"><span data-stu-id="de6cc-110">Requirements</span></span>  
 <span data-ttu-id="de6cc-111">**平台：**看到[.NET Framework 系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="de6cc-111">**Platforms:** See [.NET Framework System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de6cc-112">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="de6cc-112">**DLL:**</span></span>  
  
 <span data-ttu-id="de6cc-113">在.NET Framework 3.0 和 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="de6cc-113">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="de6cc-114">在.NET Framework 4 和更新版本： PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="de6cc-114">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="de6cc-115">**.NET framework 版本：**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de6cc-115">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de6cc-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="de6cc-116">See Also</span></span>  
 [<span data-ttu-id="de6cc-117">WPF Unmanaged API 參考</span><span class="sxs-lookup"><span data-stu-id="de6cc-117">WPF Unmanaged API Reference</span></span>](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
