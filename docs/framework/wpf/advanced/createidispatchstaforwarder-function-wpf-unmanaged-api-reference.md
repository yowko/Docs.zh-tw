---
title: CreateIDispatchSTAForwarder 函式-WPF 非受控 API 參考
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CreateIDispatchSTAForwarder
api_location:
- PresentationHost_v0400.dll
ms.assetid: 57a02dfa-f091-4ace-9c06-1f4ab52b3527
ms.openlocfilehash: 67f2542733fb9c6af197c99ede2bd097ce876b5d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738038"
---
# <a name="createidispatchstaforwarder-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="b853b-102">CreateIDispatchSTAForwarder 函式（WPF 非受控 API 參考）</span><span class="sxs-lookup"><span data-stu-id="b853b-102">CreateIDispatchSTAForwarder Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="b853b-103">這個 API 支援 Windows Presentation Foundation （WPF）基礎結構，但不適合直接從程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="b853b-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="b853b-104">供執行緒和 Windows 管理的 Windows Presentation Foundation （WPF）基礎結構使用。</span><span class="sxs-lookup"><span data-stu-id="b853b-104">Used by the Windows Presentation Foundation (WPF) infrastructure for thread and windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b853b-105">語法</span><span class="sxs-lookup"><span data-stu-id="b853b-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateIDispatchSTAForwarder(  
   __in IDispatch *pDispatchDelegate,   
   __deref_out IDispatch **ppForwarder  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="b853b-106">參數</span><span class="sxs-lookup"><span data-stu-id="b853b-106">Parameters</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="b853b-107">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="b853b-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="b853b-108">pDispatchDelegate</span><span class="sxs-lookup"><span data-stu-id="b853b-108">pDispatchDelegate</span></span>  
 <span data-ttu-id="b853b-109">`IDispatch` 介面的指標。</span><span class="sxs-lookup"><span data-stu-id="b853b-109">A pointer to an `IDispatch` interface.</span></span>  
  
 <span data-ttu-id="b853b-110">ppForwarder</span><span class="sxs-lookup"><span data-stu-id="b853b-110">ppForwarder</span></span>  
 <span data-ttu-id="b853b-111">`IDispatch` 介面之位址的指標。</span><span class="sxs-lookup"><span data-stu-id="b853b-111">A pointer to the address of an `IDispatch` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b853b-112">需求</span><span class="sxs-lookup"><span data-stu-id="b853b-112">Requirements</span></span>  
 <span data-ttu-id="b853b-113">**平臺：** 請參閱[.NET Framework 系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b853b-113">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b853b-114">**URLMON.DLL**</span><span class="sxs-lookup"><span data-stu-id="b853b-114">**DLL:**</span></span>  
  
 <span data-ttu-id="b853b-115">在 .NET Framework 3.0 和3.5： PresentationHostDLL 中</span><span class="sxs-lookup"><span data-stu-id="b853b-115">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="b853b-116">在 .NET Framework 4 和更新版本中： PresentationHost_v0400 .dll</span><span class="sxs-lookup"><span data-stu-id="b853b-116">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="b853b-117">**.NET Framework 版本：** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b853b-117">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b853b-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b853b-118">See also</span></span>

- [<span data-ttu-id="b853b-119">WPF Unmanaged API 參考</span><span class="sxs-lookup"><span data-stu-id="b853b-119">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
