---
title: IMetaDataInfo::GetFileMapping 方法
ms.date: 03/30/2017
api_name:
- IMetaDataInfo.GetFileMapping
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataInfo::GetFileMapping
helpviewer_keywords:
- IMetaDataInfo::GetFileMapping method [.NET Framework metadata]
- GetFileMapping method [.NET Framework metadata]
ms.assetid: 2868dfec-c992-4606-88bb-a8e0b6b18271
topic_type:
- apiref
ms.openlocfilehash: 0cd2071d4410615a08e774ba30e0e8fe8d1fa7c7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436183"
---
# <a name="imetadatainfogetfilemapping-method"></a><span data-ttu-id="d092a-102">IMetaDataInfo::GetFileMapping 方法</span><span class="sxs-lookup"><span data-stu-id="d092a-102">IMetaDataInfo::GetFileMapping Method</span></span>
<span data-ttu-id="d092a-103">取得對應檔案的記憶體區域，以及對應的類型。</span><span class="sxs-lookup"><span data-stu-id="d092a-103">Gets the memory region of the mapped file, and the type of mapping.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d092a-104">語法</span><span class="sxs-lookup"><span data-stu-id="d092a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFileMapping (  
    [out] const void           **ppvData,   
    [out] ULONGLONG            *pcbData,   
    [out] DWORD                *pdwMappingType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d092a-105">參數</span><span class="sxs-lookup"><span data-stu-id="d092a-105">Parameters</span></span>  
 `ppvData`  
 <span data-ttu-id="d092a-106">脫銷對應檔案開頭的指標。</span><span class="sxs-lookup"><span data-stu-id="d092a-106">[out] A pointer to the start of the mapped file.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="d092a-107">脫銷對應區域的大小。</span><span class="sxs-lookup"><span data-stu-id="d092a-107">[out] The size of the mapped region.</span></span> <span data-ttu-id="d092a-108">如果 `pdwMappingType` 是 `fmFlat`，這就是檔案的大小。</span><span class="sxs-lookup"><span data-stu-id="d092a-108">If `pdwMappingType` is `fmFlat`, this is the size of the file.</span></span>  
  
 `pdwMappingType`  
 <span data-ttu-id="d092a-109">脫銷表示對應類型的[CorFileMapping](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md)值。</span><span class="sxs-lookup"><span data-stu-id="d092a-109">[out] A [CorFileMapping](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md) value that indicates the type of mapping.</span></span> <span data-ttu-id="d092a-110">Common language runtime （CLR）的目前執行一律會傳回 `fmFlat`。</span><span class="sxs-lookup"><span data-stu-id="d092a-110">The current implementation of the common language runtime (CLR) always returns `fmFlat`.</span></span> <span data-ttu-id="d092a-111">保留其他值供以後使用。</span><span class="sxs-lookup"><span data-stu-id="d092a-111">Other values are reserved for future use.</span></span> <span data-ttu-id="d092a-112">不過，您應該一律驗證傳回的值，因為未來版本或服務版本可能會啟用其他值。</span><span class="sxs-lookup"><span data-stu-id="d092a-112">However, you should always verify the returned value, because other values may be enabled in future versions or service releases.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d092a-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="d092a-113">Return Value</span></span>  
  
|<span data-ttu-id="d092a-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d092a-114">HRESULT</span></span>|<span data-ttu-id="d092a-115">描述</span><span class="sxs-lookup"><span data-stu-id="d092a-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="d092a-116">所有輸出都會填滿。</span><span class="sxs-lookup"><span data-stu-id="d092a-116">All outputs are filled.</span></span>|  
|`E_INVALIDARG`|<span data-ttu-id="d092a-117">傳遞 Null 做為引數值。</span><span class="sxs-lookup"><span data-stu-id="d092a-117">NULL was passed as an argument value.</span></span>|  
|`COR_E_NOTSUPPORTED`|<span data-ttu-id="d092a-118">CLR 執行無法提供記憶體區域的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="d092a-118">The CLR implementation cannot provide information about the memory region.</span></span> <span data-ttu-id="d092a-119">這可能因為以下原因而發生：</span><span class="sxs-lookup"><span data-stu-id="d092a-119">This can happen for the following reasons:</span></span><br /><br /> <span data-ttu-id="d092a-120">-中繼資料範圍已以 `ofWrite` 或 `ofCopyMemory` 旗標開啟。</span><span class="sxs-lookup"><span data-stu-id="d092a-120">-   The metadata scope was opened with the `ofWrite` or `ofCopyMemory` flag.</span></span><br /><span data-ttu-id="d092a-121">-中繼資料範圍在沒有 `ofReadOnly` 旗標的情況下開啟。</span><span class="sxs-lookup"><span data-stu-id="d092a-121">-   The metadata scope was opened without the `ofReadOnly` flag.</span></span><br /><span data-ttu-id="d092a-122">- [IMetaDataDispenser：： OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md)方法只會用來開啟檔案的中繼資料部分。</span><span class="sxs-lookup"><span data-stu-id="d092a-122">-   The [IMetaDataDispenser::OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) method was used to open only the metadata portion of the file.</span></span><br /><span data-ttu-id="d092a-123">-檔案不是可移植的可執行檔（PE）。</span><span class="sxs-lookup"><span data-stu-id="d092a-123">-   The file is not a portable executable (PE) file.</span></span> <span data-ttu-id="d092a-124">**注意：** 這些條件取決於 CLR 的執行，而且可能會在未來的 CLR 版本中減弱。</span><span class="sxs-lookup"><span data-stu-id="d092a-124">**Note:**  These conditions depend on the CLR implementation, and are likely to be weakened in future versions of the CLR.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d092a-125">備註</span><span class="sxs-lookup"><span data-stu-id="d092a-125">Remarks</span></span>  
 <span data-ttu-id="d092a-126">只有在基礎中繼資料範圍已開啟時，`ppvData` 指向的記憶體才有效。</span><span class="sxs-lookup"><span data-stu-id="d092a-126">The memory that `ppvData` points to is valid only as long as the underlying metadata scope is open.</span></span>  
  
 <span data-ttu-id="d092a-127">為了讓這個方法能夠正常執行，當您藉由呼叫[IMetaDataDispenser：： OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)方法，將磁片上檔案的中繼資料對應至記憶體時，您必須指定 `ofReadOnly` 旗標，而且不能指定 `ofWrite` 或 `ofCopyMemory` 旗標。</span><span class="sxs-lookup"><span data-stu-id="d092a-127">In order for this method to work, when you map the metadata of an on-disk file into memory by calling the [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) method, you must specify the `ofReadOnly` flag and you must not specify the `ofWrite` or `ofCopyMemory` flag.</span></span>  
  
 <span data-ttu-id="d092a-128">針對每個範圍所選擇的檔案對應類型，是特定的 CLR 執行。</span><span class="sxs-lookup"><span data-stu-id="d092a-128">The choice of file mapping type for each scope is specific to a given implementation of the CLR.</span></span> <span data-ttu-id="d092a-129">不能由使用者設定。</span><span class="sxs-lookup"><span data-stu-id="d092a-129">It cannot be set by the user.</span></span> <span data-ttu-id="d092a-130">CLR 目前的執行一律會在 `pdwMappingType`中傳回 `fmFlat`，但在未來的 CLR 版本或特定版本的未來服務版本中可能會變更。</span><span class="sxs-lookup"><span data-stu-id="d092a-130">The current implementation of the CLR always returns `fmFlat` in `pdwMappingType`, but this can change in future versions of the CLR or in future service releases of a given version.</span></span> <span data-ttu-id="d092a-131">您應該一律檢查 `pdwMappingType`中傳回的值，因為不同的類型會有不同的版面配置和位移。</span><span class="sxs-lookup"><span data-stu-id="d092a-131">You should always check the returned value in `pdwMappingType`, because different types will have different layouts and offsets.</span></span>  
  
 <span data-ttu-id="d092a-132">不支援為三個參數傳遞 Null。</span><span class="sxs-lookup"><span data-stu-id="d092a-132">Passing NULL for any of the three parameters is not supported.</span></span> <span data-ttu-id="d092a-133">方法會傳回 `E_INVALIDARG`，而且不會填入任何輸出。</span><span class="sxs-lookup"><span data-stu-id="d092a-133">The method returns `E_INVALIDARG`, and none of the outputs are filled.</span></span> <span data-ttu-id="d092a-134">忽略對應類型或區域大小可能會導致異常程式終止。</span><span class="sxs-lookup"><span data-stu-id="d092a-134">Ignoring the mapping type or the size of the region can result in abnormal program termination.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d092a-135">需求</span><span class="sxs-lookup"><span data-stu-id="d092a-135">Requirements</span></span>  
 <span data-ttu-id="d092a-136">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d092a-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d092a-137">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="d092a-137">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d092a-138">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="d092a-138">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d092a-139">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d092a-139">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d092a-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d092a-140">See also</span></span>

- [<span data-ttu-id="d092a-141">IMetaDataInfo 介面</span><span class="sxs-lookup"><span data-stu-id="d092a-141">IMetaDataInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-interface.md)
- [<span data-ttu-id="d092a-142">CorFileMapping 列舉</span><span class="sxs-lookup"><span data-stu-id="d092a-142">CorFileMapping Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md)
