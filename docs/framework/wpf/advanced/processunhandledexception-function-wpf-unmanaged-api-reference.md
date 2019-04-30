---
title: ProcessUnhandledException 函式 (WPF Unmanaged API 參考)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ProcessUnhandledException
api_location:
- PresentationHost_v0400.dll
ms.assetid: 495ce5f6-bb4d-4b30-807a-c3c35f1ca95c
ms.openlocfilehash: 0c8751454be6e0eed547c38e9d0bc7931abaec3d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62030346"
---
# <a name="processunhandledexception-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="a6e1a-102">ProcessUnhandledException 函式 (WPF Unmanaged API 參考)</span><span class="sxs-lookup"><span data-stu-id="a6e1a-102">ProcessUnhandledException Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="a6e1a-103">此 API 支援 Windows Presentation Foundation (WPF) 基礎結構，並不是直接從您的程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="a6e1a-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="a6e1a-104">Windows Presentation Foundation (WPF) 基礎結構用於例外狀況處理。</span><span class="sxs-lookup"><span data-stu-id="a6e1a-104">Used by the Windows Presentation Foundation (WPF) infrastructure for exception handling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6e1a-105">語法</span><span class="sxs-lookup"><span data-stu-id="a6e1a-105">Syntax</span></span>  
  
```cpp  
void __stdcall ProcessUnhandledException(  
   __in_ecount(1) BSTR errorMsg  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="a6e1a-106">參數</span><span class="sxs-lookup"><span data-stu-id="a6e1a-106">Parameters</span></span>  
 <span data-ttu-id="a6e1a-107">errorMsg</span><span class="sxs-lookup"><span data-stu-id="a6e1a-107">errorMsg</span></span>  
 <span data-ttu-id="a6e1a-108">錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="a6e1a-108">The error message.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6e1a-109">需求</span><span class="sxs-lookup"><span data-stu-id="a6e1a-109">Requirements</span></span>  
 <span data-ttu-id="a6e1a-110">**平台：** 請參閱[.NET Framework 系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a6e1a-110">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6e1a-111">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="a6e1a-111">**DLL:**</span></span>  
  
 <span data-ttu-id="a6e1a-112">在.NET Framework 3.0 和 3.5:PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="a6e1a-112">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="a6e1a-113">在.NET Framework 4 及更新版本：PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="a6e1a-113">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="a6e1a-114">**.NET framework 版本：** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6e1a-114">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6e1a-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6e1a-115">See also</span></span>

- [<span data-ttu-id="a6e1a-116">WPF Unmanaged API 參考</span><span class="sxs-lookup"><span data-stu-id="a6e1a-116">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
