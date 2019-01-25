---
title: CreateIDispatchSTAForwarder 函式 (WPF Unmanaged API 參考)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CreateIDispatchSTAForwarder
api_location:
- PresentationHost_v0400.dll
ms.assetid: 57a02dfa-f091-4ace-9c06-1f4ab52b3527
ms.openlocfilehash: 215f6ff727b814e7e7d7c708c29a8c5221f5797f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54575972"
---
# <a name="createidispatchstaforwarder-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="f237d-102">CreateIDispatchSTAForwarder 函式 (WPF Unmanaged API 參考)</span><span class="sxs-lookup"><span data-stu-id="f237d-102">CreateIDispatchSTAForwarder Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="f237d-103">此 API 支援 Windows Presentation Foundation (WPF) 基礎結構，並不是直接從您的程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="f237d-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="f237d-104">Windows Presentation Foundation (WPF) 基礎結構用於執行緒和 windows 的管理。</span><span class="sxs-lookup"><span data-stu-id="f237d-104">Used by the Windows Presentation Foundation (WPF) infrastructure for thread and windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f237d-105">語法</span><span class="sxs-lookup"><span data-stu-id="f237d-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateIDispatchSTAForwarder(  
   __in IDispatch *pDispatchDelegate,   
   __deref_out IDispatch **ppForwarder  
)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f237d-106">參數</span><span class="sxs-lookup"><span data-stu-id="f237d-106">Parameters</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="f237d-107">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="f237d-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="f237d-108">pDispatchDelegate</span><span class="sxs-lookup"><span data-stu-id="f237d-108">pDispatchDelegate</span></span>  
 <span data-ttu-id="f237d-109">指標`IDispatch`介面。</span><span class="sxs-lookup"><span data-stu-id="f237d-109">A pointer to an `IDispatch` interface.</span></span>  
  
 <span data-ttu-id="f237d-110">ppForwarder</span><span class="sxs-lookup"><span data-stu-id="f237d-110">ppForwarder</span></span>  
 <span data-ttu-id="f237d-111">位址指標`IDispatch`介面。</span><span class="sxs-lookup"><span data-stu-id="f237d-111">A pointer to the address of an `IDispatch` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f237d-112">需求</span><span class="sxs-lookup"><span data-stu-id="f237d-112">Requirements</span></span>  
 <span data-ttu-id="f237d-113">**平台：** 請參閱[.NET Framework 系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f237d-113">**Platforms:** See [.NET Framework System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f237d-114">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="f237d-114">**DLL:**</span></span>  
  
 <span data-ttu-id="f237d-115">在.NET Framework 3.0 和 3.5:PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="f237d-115">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="f237d-116">在.NET Framework 4 及更新版本：PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="f237d-116">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="f237d-117">**.NET framework 版本：** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f237d-117">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f237d-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f237d-118">See also</span></span>
- [<span data-ttu-id="f237d-119">WPF Unmanaged API 參考</span><span class="sxs-lookup"><span data-stu-id="f237d-119">WPF Unmanaged API Reference</span></span>](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
