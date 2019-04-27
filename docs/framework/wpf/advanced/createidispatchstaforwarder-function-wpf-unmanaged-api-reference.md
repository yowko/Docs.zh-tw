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
ms.openlocfilehash: a89b29cd459060c93d5ca77bb2154e1a10b02d03
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61926447"
---
# <a name="createidispatchstaforwarder-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="f5196-102">CreateIDispatchSTAForwarder 函式 (WPF Unmanaged API 參考)</span><span class="sxs-lookup"><span data-stu-id="f5196-102">CreateIDispatchSTAForwarder Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="f5196-103">此 API 支援 Windows Presentation Foundation (WPF) 基礎結構，並不是直接從您的程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="f5196-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="f5196-104">Windows Presentation Foundation (WPF) 基礎結構用於執行緒和 windows 的管理。</span><span class="sxs-lookup"><span data-stu-id="f5196-104">Used by the Windows Presentation Foundation (WPF) infrastructure for thread and windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5196-105">語法</span><span class="sxs-lookup"><span data-stu-id="f5196-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateIDispatchSTAForwarder(  
   __in IDispatch *pDispatchDelegate,   
   __deref_out IDispatch **ppForwarder  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5196-106">參數</span><span class="sxs-lookup"><span data-stu-id="f5196-106">Parameters</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="f5196-107">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="f5196-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="f5196-108">pDispatchDelegate</span><span class="sxs-lookup"><span data-stu-id="f5196-108">pDispatchDelegate</span></span>  
 <span data-ttu-id="f5196-109">指標`IDispatch`介面。</span><span class="sxs-lookup"><span data-stu-id="f5196-109">A pointer to an `IDispatch` interface.</span></span>  
  
 <span data-ttu-id="f5196-110">ppForwarder</span><span class="sxs-lookup"><span data-stu-id="f5196-110">ppForwarder</span></span>  
 <span data-ttu-id="f5196-111">位址指標`IDispatch`介面。</span><span class="sxs-lookup"><span data-stu-id="f5196-111">A pointer to the address of an `IDispatch` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5196-112">需求</span><span class="sxs-lookup"><span data-stu-id="f5196-112">Requirements</span></span>  
 <span data-ttu-id="f5196-113">**平台：** 請參閱[.NET Framework 系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f5196-113">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5196-114">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="f5196-114">**DLL:**</span></span>  
  
 <span data-ttu-id="f5196-115">在.NET Framework 3.0 和 3.5:PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="f5196-115">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="f5196-116">在.NET Framework 4 及更新版本：PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="f5196-116">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="f5196-117">**.NET framework 版本：** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5196-117">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5196-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5196-118">See also</span></span>

- [<span data-ttu-id="f5196-119">WPF Unmanaged API 參考</span><span class="sxs-lookup"><span data-stu-id="f5196-119">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
