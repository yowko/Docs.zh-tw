---
title: "CreateIDispatchSTAForwarder 函式 (WPF Unmanaged API 參考)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
api_name: CreateIDispatchSTAForwarder
api_location: PresentationHost_v0400.dll
ms.assetid: 57a02dfa-f091-4ace-9c06-1f4ab52b3527
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5139784fdc067c09d032c0bf37114e0eb1caac33
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="createidispatchstaforwarder-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="e9066-102">CreateIDispatchSTAForwarder 函式 (WPF Unmanaged API 參考)</span><span class="sxs-lookup"><span data-stu-id="e9066-102">CreateIDispatchSTAForwarder Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="e9066-103">這個 API 支援的 Windows Presentation Foundation (WPF) 基礎結構，並不是直接從您的程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="e9066-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="e9066-104">Windows Presentation Foundation (WPF) 基礎結構用於執行緒和 windows 的管理。</span><span class="sxs-lookup"><span data-stu-id="e9066-104">Used by the Windows Presentation Foundation (WPF) infrastructure for thread and windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9066-105">語法</span><span class="sxs-lookup"><span data-stu-id="e9066-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateIDispatchSTAForwarder(  
   __in IDispatch *pDispatchDelegate,   
   __deref_out IDispatch **ppForwarder  
)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e9066-106">參數</span><span class="sxs-lookup"><span data-stu-id="e9066-106">Parameters</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="e9066-107">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="e9066-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="e9066-108">pDispatchDelegate</span><span class="sxs-lookup"><span data-stu-id="e9066-108">pDispatchDelegate</span></span>  
 <span data-ttu-id="e9066-109">指標`IDispatch`介面。</span><span class="sxs-lookup"><span data-stu-id="e9066-109">A pointer to an `IDispatch` interface.</span></span>  
  
 <span data-ttu-id="e9066-110">ppForwarder</span><span class="sxs-lookup"><span data-stu-id="e9066-110">ppForwarder</span></span>  
 <span data-ttu-id="e9066-111">位址指標`IDispatch`介面。</span><span class="sxs-lookup"><span data-stu-id="e9066-111">A pointer to the address of an `IDispatch` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9066-112">需求</span><span class="sxs-lookup"><span data-stu-id="e9066-112">Requirements</span></span>  
 <span data-ttu-id="e9066-113">**平台：**看到[.NET Framework 系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e9066-113">**Platforms:** See [.NET Framework System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9066-114">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="e9066-114">**DLL:**</span></span>  
  
 <span data-ttu-id="e9066-115">在.NET Framework 3.0 和 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="e9066-115">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="e9066-116">在.NET Framework 4 和更新版本： PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="e9066-116">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="e9066-117">**.NET framework 版本：**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9066-117">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9066-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="e9066-118">See Also</span></span>  
 [<span data-ttu-id="e9066-119">WPF Unmanaged API 參考</span><span class="sxs-lookup"><span data-stu-id="e9066-119">WPF Unmanaged API Reference</span></span>](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
