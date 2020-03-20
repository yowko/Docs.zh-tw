---
title: 轉發加速器功能 - WPF 非託管 API 引用
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ForwardTranslateAccelerator
api_location:
- PresentationHost_v0400.dll
ms.assetid: fff47a86-9d9f-4176-9530-10e1876e393f
ms.openlocfilehash: a0a01be3000dc53df7855cb74015ba1164206838
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186624"
---
# <a name="forwardtranslateaccelerator-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="eb13a-102">轉發加速器功能（WPF 非託管 API 引用）</span><span class="sxs-lookup"><span data-stu-id="eb13a-102">ForwardTranslateAccelerator Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="eb13a-103">此 API 支援 Windows 演示基礎 （WPF） 基礎結構，不用於直接從代碼中使用。</span><span class="sxs-lookup"><span data-stu-id="eb13a-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="eb13a-104">由 Windows 演示基礎 （WPF） 基礎結構用於視窗管理。</span><span class="sxs-lookup"><span data-stu-id="eb13a-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb13a-105">語法</span><span class="sxs-lookup"><span data-stu-id="eb13a-105">Syntax</span></span>  
  
```cpp  
HRESULT ForwardTranslateAccelerator(  
   MSG* pMsg,
   VARIANT_BOOL appUnhandled  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="eb13a-106">參數</span><span class="sxs-lookup"><span data-stu-id="eb13a-106">Parameters</span></span>  
 <span data-ttu-id="eb13a-107">pMsg</span><span class="sxs-lookup"><span data-stu-id="eb13a-107">pMsg</span></span>  
 <span data-ttu-id="eb13a-108">指向消息的指標。</span><span class="sxs-lookup"><span data-stu-id="eb13a-108">A pointer to a message.</span></span>  
  
 <span data-ttu-id="eb13a-109">應用程式未處理</span><span class="sxs-lookup"><span data-stu-id="eb13a-109">appUnhandled</span></span>  
 <span data-ttu-id="eb13a-110">`true`當應用程式已有機會處理輸入消息，但尚未處理它;否則， `false`.</span><span class="sxs-lookup"><span data-stu-id="eb13a-110">`true` when the app has already been given a chance to handle the input message, but has not handled it; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb13a-111">需求</span><span class="sxs-lookup"><span data-stu-id="eb13a-111">Requirements</span></span>  
 <span data-ttu-id="eb13a-112">**平臺：** 請參閱[.NET 框架系統要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="eb13a-112">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb13a-113">**Dll：**</span><span class="sxs-lookup"><span data-stu-id="eb13a-113">**DLL:**</span></span>  
  
 <span data-ttu-id="eb13a-114">在 .NET 框架 3.0 和 3.5 中：演示HostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="eb13a-114">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="eb13a-115">在 .NET 框架 4 及更高版本：PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="eb13a-115">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="eb13a-116">**.NET 框架版本：**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb13a-116">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb13a-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eb13a-117">See also</span></span>

- [<span data-ttu-id="eb13a-118">WPF 非受控 API 參考</span><span class="sxs-lookup"><span data-stu-id="eb13a-118">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
