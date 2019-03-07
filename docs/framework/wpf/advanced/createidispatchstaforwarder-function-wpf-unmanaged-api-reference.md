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
ms.openlocfilehash: 1a19b7699c7a9e2b663149ea31bccb67189e68c4
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57487820"
---
# <a name="createidispatchstaforwarder-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="b5ec2-102">CreateIDispatchSTAForwarder 函式 (WPF Unmanaged API 參考)</span><span class="sxs-lookup"><span data-stu-id="b5ec2-102">CreateIDispatchSTAForwarder Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="b5ec2-103">此 API 支援 Windows Presentation Foundation (WPF) 基礎結構，並不是直接從您的程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="b5ec2-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="b5ec2-104">Windows Presentation Foundation (WPF) 基礎結構用於執行緒和 windows 的管理。</span><span class="sxs-lookup"><span data-stu-id="b5ec2-104">Used by the Windows Presentation Foundation (WPF) infrastructure for thread and windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5ec2-105">語法</span><span class="sxs-lookup"><span data-stu-id="b5ec2-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateIDispatchSTAForwarder(  
   __in IDispatch *pDispatchDelegate,   
   __deref_out IDispatch **ppForwarder  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="b5ec2-106">參數</span><span class="sxs-lookup"><span data-stu-id="b5ec2-106">Parameters</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="b5ec2-107">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="b5ec2-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="b5ec2-108">pDispatchDelegate</span><span class="sxs-lookup"><span data-stu-id="b5ec2-108">pDispatchDelegate</span></span>  
 <span data-ttu-id="b5ec2-109">指標`IDispatch`介面。</span><span class="sxs-lookup"><span data-stu-id="b5ec2-109">A pointer to an `IDispatch` interface.</span></span>  
  
 <span data-ttu-id="b5ec2-110">ppForwarder</span><span class="sxs-lookup"><span data-stu-id="b5ec2-110">ppForwarder</span></span>  
 <span data-ttu-id="b5ec2-111">位址指標`IDispatch`介面。</span><span class="sxs-lookup"><span data-stu-id="b5ec2-111">A pointer to the address of an `IDispatch` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5ec2-112">需求</span><span class="sxs-lookup"><span data-stu-id="b5ec2-112">Requirements</span></span>  
 <span data-ttu-id="b5ec2-113">**平台：** 請參閱[.NET Framework 系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b5ec2-113">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5ec2-114">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="b5ec2-114">**DLL:**</span></span>  
  
 <span data-ttu-id="b5ec2-115">在.NET Framework 3.0 和 3.5:PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="b5ec2-115">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="b5ec2-116">在.NET Framework 4 及更新版本：PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="b5ec2-116">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="b5ec2-117">**.NET framework 版本：** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5ec2-117">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5ec2-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b5ec2-118">See also</span></span>
- [<span data-ttu-id="b5ec2-119">WPF Unmanaged API 參考</span><span class="sxs-lookup"><span data-stu-id="b5ec2-119">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
