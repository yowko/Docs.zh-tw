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
ms.openlocfilehash: 0f5bdf97132c05e765cd6fa423a19bb996105d28
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175261"
---
# <a name="imetadatainfogetfilemapping-method"></a><span data-ttu-id="44d58-102">IMetaDataInfo::GetFileMapping 方法</span><span class="sxs-lookup"><span data-stu-id="44d58-102">IMetaDataInfo::GetFileMapping Method</span></span>
<span data-ttu-id="44d58-103">獲取映射檔的記憶體區域和映射類型。</span><span class="sxs-lookup"><span data-stu-id="44d58-103">Gets the memory region of the mapped file, and the type of mapping.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44d58-104">語法</span><span class="sxs-lookup"><span data-stu-id="44d58-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFileMapping (  
    [out] const void           **ppvData,
    [out] ULONGLONG            *pcbData,
    [out] DWORD                *pdwMappingType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="44d58-105">參數</span><span class="sxs-lookup"><span data-stu-id="44d58-105">Parameters</span></span>  
 `ppvData`  
 <span data-ttu-id="44d58-106">[出]指向映射檔開頭的指標。</span><span class="sxs-lookup"><span data-stu-id="44d58-106">[out] A pointer to the start of the mapped file.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="44d58-107">[出]映射區域的大小。</span><span class="sxs-lookup"><span data-stu-id="44d58-107">[out] The size of the mapped region.</span></span> <span data-ttu-id="44d58-108">如果是`pdwMappingType``fmFlat`，則這是檔的大小。</span><span class="sxs-lookup"><span data-stu-id="44d58-108">If `pdwMappingType` is `fmFlat`, this is the size of the file.</span></span>  
  
 `pdwMappingType`  
 <span data-ttu-id="44d58-109">[出]指示映射類型的[CorFile 映射](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md)值。</span><span class="sxs-lookup"><span data-stu-id="44d58-109">[out] A [CorFileMapping](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md) value that indicates the type of mapping.</span></span> <span data-ttu-id="44d58-110">公共語言運行時 （CLR） 的當前實現始終返回`fmFlat`。</span><span class="sxs-lookup"><span data-stu-id="44d58-110">The current implementation of the common language runtime (CLR) always returns `fmFlat`.</span></span> <span data-ttu-id="44d58-111">保留其他值供以後使用。</span><span class="sxs-lookup"><span data-stu-id="44d58-111">Other values are reserved for future use.</span></span> <span data-ttu-id="44d58-112">但是，應始終驗證返回的值，因為將來的版本或服務版本中可能會啟用其他值。</span><span class="sxs-lookup"><span data-stu-id="44d58-112">However, you should always verify the returned value, because other values may be enabled in future versions or service releases.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="44d58-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="44d58-113">Return Value</span></span>  
  
|<span data-ttu-id="44d58-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="44d58-114">HRESULT</span></span>|<span data-ttu-id="44d58-115">描述</span><span class="sxs-lookup"><span data-stu-id="44d58-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="44d58-116">所有輸出都已填充。</span><span class="sxs-lookup"><span data-stu-id="44d58-116">All outputs are filled.</span></span>|  
|`E_INVALIDARG`|<span data-ttu-id="44d58-117">Null 作為參數值傳遞。</span><span class="sxs-lookup"><span data-stu-id="44d58-117">NULL was passed as an argument value.</span></span>|  
|`COR_E_NOTSUPPORTED`|<span data-ttu-id="44d58-118">CLR 實現不能提供有關記憶體區域的資訊。</span><span class="sxs-lookup"><span data-stu-id="44d58-118">The CLR implementation cannot provide information about the memory region.</span></span> <span data-ttu-id="44d58-119">這可能因為以下原因而發生：</span><span class="sxs-lookup"><span data-stu-id="44d58-119">This can happen for the following reasons:</span></span><br /><br /> <span data-ttu-id="44d58-120">- 中繼資料作用域已打開`ofWrite`，`ofCopyMemory`或 標誌。</span><span class="sxs-lookup"><span data-stu-id="44d58-120">-   The metadata scope was opened with the `ofWrite` or `ofCopyMemory` flag.</span></span><br /><span data-ttu-id="44d58-121">- 中繼資料作用域在沒有`ofReadOnly`標誌的情況下打開。</span><span class="sxs-lookup"><span data-stu-id="44d58-121">-   The metadata scope was opened without the `ofReadOnly` flag.</span></span><br /><span data-ttu-id="44d58-122">- [IMetaDataDispenser：：OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md)方法僅用於打開檔的中繼資料部分。</span><span class="sxs-lookup"><span data-stu-id="44d58-122">-   The [IMetaDataDispenser::OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) method was used to open only the metadata portion of the file.</span></span><br /><span data-ttu-id="44d58-123">- 該檔不是可攜式可執行檔 （PE）。</span><span class="sxs-lookup"><span data-stu-id="44d58-123">-   The file is not a portable executable (PE) file.</span></span> <span data-ttu-id="44d58-124">**注：** 這些條件取決於 CLR 實現，並且將來版本的 CLR 可能會減弱。</span><span class="sxs-lookup"><span data-stu-id="44d58-124">**Note:**  These conditions depend on the CLR implementation, and are likely to be weakened in future versions of the CLR.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44d58-125">備註</span><span class="sxs-lookup"><span data-stu-id="44d58-125">Remarks</span></span>  
 <span data-ttu-id="44d58-126">只要基礎中繼資料`ppvData`作用域處於打開狀態，指向的記憶體才有效。</span><span class="sxs-lookup"><span data-stu-id="44d58-126">The memory that `ppvData` points to is valid only as long as the underlying metadata scope is open.</span></span>  
  
 <span data-ttu-id="44d58-127">為了使此方法正常工作，當您通過調用[IMetaDataDispenser：：openScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)方法將磁片檔的元資料對應到記憶體時，必須指定`ofReadOnly`標誌，並且不能指定`ofWrite`或`ofCopyMemory`標誌。</span><span class="sxs-lookup"><span data-stu-id="44d58-127">In order for this method to work, when you map the metadata of an on-disk file into memory by calling the [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) method, you must specify the `ofReadOnly` flag and you must not specify the `ofWrite` or `ofCopyMemory` flag.</span></span>  
  
 <span data-ttu-id="44d58-128">每個作用域的檔案對應類型的選擇特定于 CLR 的給定實現。</span><span class="sxs-lookup"><span data-stu-id="44d58-128">The choice of file mapping type for each scope is specific to a given implementation of the CLR.</span></span> <span data-ttu-id="44d58-129">使用者無法設置它。</span><span class="sxs-lookup"><span data-stu-id="44d58-129">It cannot be set by the user.</span></span> <span data-ttu-id="44d58-130">CLR 的當前實現始終在`fmFlat`中`pdwMappingType`返回，但這可能在 CLR 的未來版本或給定版本的將來服務版本中更改。</span><span class="sxs-lookup"><span data-stu-id="44d58-130">The current implementation of the CLR always returns `fmFlat` in `pdwMappingType`, but this can change in future versions of the CLR or in future service releases of a given version.</span></span> <span data-ttu-id="44d58-131">應始終在 中`pdwMappingType`檢查返回的值，因為不同類型的佈局和偏移量將不同。</span><span class="sxs-lookup"><span data-stu-id="44d58-131">You should always check the returned value in `pdwMappingType`, because different types will have different layouts and offsets.</span></span>  
  
 <span data-ttu-id="44d58-132">不支援為三個參數中的任何一個傳遞 Null。</span><span class="sxs-lookup"><span data-stu-id="44d58-132">Passing NULL for any of the three parameters is not supported.</span></span> <span data-ttu-id="44d58-133">該方法返回`E_INVALIDARG`，並且不會填充任何輸出。</span><span class="sxs-lookup"><span data-stu-id="44d58-133">The method returns `E_INVALIDARG`, and none of the outputs are filled.</span></span> <span data-ttu-id="44d58-134">忽略映射類型或區域大小可能會導致異常程式終止。</span><span class="sxs-lookup"><span data-stu-id="44d58-134">Ignoring the mapping type or the size of the region can result in abnormal program termination.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44d58-135">需求</span><span class="sxs-lookup"><span data-stu-id="44d58-135">Requirements</span></span>  
 <span data-ttu-id="44d58-136">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="44d58-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44d58-137">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="44d58-137">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="44d58-138">**庫：** 用作 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="44d58-138">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="44d58-139">**.NET 框架版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44d58-139">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44d58-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="44d58-140">See also</span></span>

- [<span data-ttu-id="44d58-141">IMetaDataInfo 介面</span><span class="sxs-lookup"><span data-stu-id="44d58-141">IMetaDataInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-interface.md)
- [<span data-ttu-id="44d58-142">CorFileMapping 列舉</span><span class="sxs-lookup"><span data-stu-id="44d58-142">CorFileMapping Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md)
