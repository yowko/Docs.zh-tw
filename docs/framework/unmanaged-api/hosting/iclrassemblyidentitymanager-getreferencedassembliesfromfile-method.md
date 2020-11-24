---
title: ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile 方法
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetReferencedAssembliesFromFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile
helpviewer_keywords:
- ICLRAssemblyIdentityManager::GetReferenceAssembliesFromFile method [.NET Framework hosting]
- GetReferenceAssembliesFromFile method [.NET Framework hosting]
ms.assetid: eed63d31-d977-4c7d-9443-f9d37a2a7d81
topic_type:
- apiref
ms.openlocfilehash: 6b67ba9d022d94f51d7cc6a4645855f6b6ac3e19
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679310"
---
# <a name="iclrassemblyidentitymanagergetreferencedassembliesfromfile-method"></a><span data-ttu-id="8149b-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile 方法</span><span class="sxs-lookup"><span data-stu-id="8149b-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile Method</span></span>

<span data-ttu-id="8149b-103">取得 [ICLRReferenceAssemblyEnum](iclrreferenceassemblyenum-interface.md) 實例，其中包含元件在指定檔案路徑所參考的元件清單。</span><span class="sxs-lookup"><span data-stu-id="8149b-103">Gets an [ICLRReferenceAssemblyEnum](iclrreferenceassemblyenum-interface.md) instance that contains a list of assemblies referenced by the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8149b-104">語法</span><span class="sxs-lookup"><span data-stu-id="8149b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReferencedAssembliesFromFile (  
    [in]  LPCWSTR pwzFilePath,  
    [in]  DWORD   dwFlags,  
    [in]  ICLRAssemblyReferenceList   *pExcludeAssembliesList,  
    [out] ICLRReferenceAssemblyEnum  **ppReferenceEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8149b-105">參數</span><span class="sxs-lookup"><span data-stu-id="8149b-105">Parameters</span></span>  

 `pwzFilePath`  
 <span data-ttu-id="8149b-106">在要評估之元件的路徑。</span><span class="sxs-lookup"><span data-stu-id="8149b-106">[in] The path to the assembly to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="8149b-107">在提供給未來的擴充性。</span><span class="sxs-lookup"><span data-stu-id="8149b-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="8149b-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT 是目前版本的 common language runtime (CLR) 支援的唯一值。</span><span class="sxs-lookup"><span data-stu-id="8149b-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pExcludeAssembliesList`  
 <span data-ttu-id="8149b-109">在 [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) 物件的指標，該物件代表應排除的元件 `ppReferenceEnum` 。</span><span class="sxs-lookup"><span data-stu-id="8149b-109">[in] A pointer to an [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) object that represents assemblies that should be excluded from `ppReferenceEnum`.</span></span>  
  
 `ppReferenceEnum`  
 <span data-ttu-id="8149b-110">擴展物件位址的指標 `ICLRReferenceAssemblyEnum` ，該物件包含元件的元件識別資料（由元件所參考的元件 `pwzFilePath` ），但不包括由所表示的元件 `pExcludeAssembliesList` 。</span><span class="sxs-lookup"><span data-stu-id="8149b-110">[out] A pointer to the address of an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly at `pwzFilePath`, excluding the assemblies represented by `pExcludeAssembliesList`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8149b-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="8149b-111">Return Value</span></span>  
  
|<span data-ttu-id="8149b-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8149b-112">HRESULT</span></span>|<span data-ttu-id="8149b-113">描述</span><span class="sxs-lookup"><span data-stu-id="8149b-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8149b-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="8149b-114">S_OK</span></span>|<span data-ttu-id="8149b-115">此方法已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="8149b-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="8149b-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8149b-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8149b-117">CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="8149b-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8149b-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8149b-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8149b-119">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="8149b-119">The call timed out.</span></span>|  
|<span data-ttu-id="8149b-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8149b-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8149b-121">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="8149b-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8149b-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8149b-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8149b-123">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="8149b-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8149b-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8149b-124">E_FAIL</span></span>|<span data-ttu-id="8149b-125">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="8149b-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8149b-126">如果方法傳回 E_FAIL，則 CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="8149b-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8149b-127">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="8149b-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8149b-128">備註</span><span class="sxs-lookup"><span data-stu-id="8149b-128">Remarks</span></span>  

 <span data-ttu-id="8149b-129">呼叫端可以選擇從傳回的清單中排除一組已知的元件參考。</span><span class="sxs-lookup"><span data-stu-id="8149b-129">The caller can choose to exclude a set of known assembly references from the returned list.</span></span> <span data-ttu-id="8149b-130">這個集合是由參數所定義 `pExcludeAssembliesList` 。</span><span class="sxs-lookup"><span data-stu-id="8149b-130">This set is defined by the `pExcludeAssembliesList` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8149b-131">需求</span><span class="sxs-lookup"><span data-stu-id="8149b-131">Requirements</span></span>  

 <span data-ttu-id="8149b-132">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8149b-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8149b-133">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="8149b-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8149b-134">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="8149b-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8149b-135">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8149b-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8149b-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8149b-136">See also</span></span>

- [<span data-ttu-id="8149b-137">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="8149b-137">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="8149b-138">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="8149b-138">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="8149b-139">ICLRReferenceAssemblyEnum 介面</span><span class="sxs-lookup"><span data-stu-id="8149b-139">ICLRReferenceAssemblyEnum Interface</span></span>](iclrreferenceassemblyenum-interface.md)
