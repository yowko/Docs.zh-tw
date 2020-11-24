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
ms.openlocfilehash: 8823f3cc016072d3f20100c29532459da5e97492
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95682385"
---
# <a name="imetadatainfogetfilemapping-method"></a><span data-ttu-id="e5828-102">IMetaDataInfo::GetFileMapping 方法</span><span class="sxs-lookup"><span data-stu-id="e5828-102">IMetaDataInfo::GetFileMapping Method</span></span>

<span data-ttu-id="e5828-103">取得對應檔案的記憶體區域，以及對應的類型。</span><span class="sxs-lookup"><span data-stu-id="e5828-103">Gets the memory region of the mapped file, and the type of mapping.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5828-104">語法</span><span class="sxs-lookup"><span data-stu-id="e5828-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFileMapping (  
    [out] const void           **ppvData,
    [out] ULONGLONG            *pcbData,
    [out] DWORD                *pdwMappingType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e5828-105">參數</span><span class="sxs-lookup"><span data-stu-id="e5828-105">Parameters</span></span>  

 `ppvData`  
 <span data-ttu-id="e5828-106">擴展對應檔案開頭的指標。</span><span class="sxs-lookup"><span data-stu-id="e5828-106">[out] A pointer to the start of the mapped file.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="e5828-107">擴展對應區域的大小。</span><span class="sxs-lookup"><span data-stu-id="e5828-107">[out] The size of the mapped region.</span></span> <span data-ttu-id="e5828-108">如果 `pdwMappingType` 為 `fmFlat` ，則這是檔案的大小。</span><span class="sxs-lookup"><span data-stu-id="e5828-108">If `pdwMappingType` is `fmFlat`, this is the size of the file.</span></span>  
  
 `pdwMappingType`  
 <span data-ttu-id="e5828-109">擴展表示對應類型的 [CorFileMapping](corfilemapping-enumeration.md) 值。</span><span class="sxs-lookup"><span data-stu-id="e5828-109">[out] A [CorFileMapping](corfilemapping-enumeration.md) value that indicates the type of mapping.</span></span> <span data-ttu-id="e5828-110">Common language runtime (CLR) 的目前實作為一律會傳回 `fmFlat` 。</span><span class="sxs-lookup"><span data-stu-id="e5828-110">The current implementation of the common language runtime (CLR) always returns `fmFlat`.</span></span> <span data-ttu-id="e5828-111">保留其他值供以後使用。</span><span class="sxs-lookup"><span data-stu-id="e5828-111">Other values are reserved for future use.</span></span> <span data-ttu-id="e5828-112">不過，您應該一律驗證傳回的值，因為其他值可能會在未來的版本或服務版本中啟用。</span><span class="sxs-lookup"><span data-stu-id="e5828-112">However, you should always verify the returned value, because other values may be enabled in future versions or service releases.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e5828-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="e5828-113">Return Value</span></span>  
  
|<span data-ttu-id="e5828-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e5828-114">HRESULT</span></span>|<span data-ttu-id="e5828-115">描述</span><span class="sxs-lookup"><span data-stu-id="e5828-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="e5828-116">所有輸出都會填滿。</span><span class="sxs-lookup"><span data-stu-id="e5828-116">All outputs are filled.</span></span>|  
|`E_INVALIDARG`|<span data-ttu-id="e5828-117">傳遞 Null 做為引數值。</span><span class="sxs-lookup"><span data-stu-id="e5828-117">NULL was passed as an argument value.</span></span>|  
|`COR_E_NOTSUPPORTED`|<span data-ttu-id="e5828-118">CLR 執行無法提供記憶體區域的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="e5828-118">The CLR implementation cannot provide information about the memory region.</span></span> <span data-ttu-id="e5828-119">這可能因為以下原因而發生：</span><span class="sxs-lookup"><span data-stu-id="e5828-119">This can happen for the following reasons:</span></span><br /><br /> <span data-ttu-id="e5828-120">-中繼資料範圍是以 `ofWrite` 或旗標開啟 `ofCopyMemory` 。</span><span class="sxs-lookup"><span data-stu-id="e5828-120">-   The metadata scope was opened with the `ofWrite` or `ofCopyMemory` flag.</span></span><br /><span data-ttu-id="e5828-121">-中繼資料範圍已在沒有旗標的情況下開啟 `ofReadOnly` 。</span><span class="sxs-lookup"><span data-stu-id="e5828-121">-   The metadata scope was opened without the `ofReadOnly` flag.</span></span><br /><span data-ttu-id="e5828-122">- [IMetaDataDispenser：： OpenScopeOnMemory](imetadatadispenser-openscopeonmemory-method.md) 方法是用來只開啟檔案的中繼資料部分。</span><span class="sxs-lookup"><span data-stu-id="e5828-122">-   The [IMetaDataDispenser::OpenScopeOnMemory](imetadatadispenser-openscopeonmemory-method.md) method was used to open only the metadata portion of the file.</span></span><br /><span data-ttu-id="e5828-123">-檔案不是可移植的可執行檔 (PE) 檔。</span><span class="sxs-lookup"><span data-stu-id="e5828-123">-   The file is not a portable executable (PE) file.</span></span> <span data-ttu-id="e5828-124">**注意：**  這些條件取決於 CLR 的執行，而且可能會在未來的 CLR 版本中減弱。</span><span class="sxs-lookup"><span data-stu-id="e5828-124">**Note:**  These conditions depend on the CLR implementation, and are likely to be weakened in future versions of the CLR.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e5828-125">備註</span><span class="sxs-lookup"><span data-stu-id="e5828-125">Remarks</span></span>  

 <span data-ttu-id="e5828-126">`ppvData`只有在基礎中繼資料範圍已開啟時，指向的記憶體才有效。</span><span class="sxs-lookup"><span data-stu-id="e5828-126">The memory that `ppvData` points to is valid only as long as the underlying metadata scope is open.</span></span>  
  
 <span data-ttu-id="e5828-127">為了讓這個方法能夠運作，當您藉由呼叫 [IMetaDataDispenser：： OpenScope](imetadatadispenser-openscope-method.md) 方法將磁片上檔案的中繼資料對應至記憶體時，必須指定旗標， `ofReadOnly` 而且您不能指定 `ofWrite` 或旗標 `ofCopyMemory` 。</span><span class="sxs-lookup"><span data-stu-id="e5828-127">In order for this method to work, when you map the metadata of an on-disk file into memory by calling the [IMetaDataDispenser::OpenScope](imetadatadispenser-openscope-method.md) method, you must specify the `ofReadOnly` flag and you must not specify the `ofWrite` or `ofCopyMemory` flag.</span></span>  
  
 <span data-ttu-id="e5828-128">針對每個範圍所選擇的檔案對應類型，是指定的 CLR 執行所特有的。</span><span class="sxs-lookup"><span data-stu-id="e5828-128">The choice of file mapping type for each scope is specific to a given implementation of the CLR.</span></span> <span data-ttu-id="e5828-129">無法由使用者設定。</span><span class="sxs-lookup"><span data-stu-id="e5828-129">It cannot be set by the user.</span></span> <span data-ttu-id="e5828-130">目前的 CLR 執行一律 `fmFlat` 會在中 `pdwMappingType` 傳回，但是在未來的 clr 版本或特定版本的未來服務版本中，這可能會變更。</span><span class="sxs-lookup"><span data-stu-id="e5828-130">The current implementation of the CLR always returns `fmFlat` in `pdwMappingType`, but this can change in future versions of the CLR or in future service releases of a given version.</span></span> <span data-ttu-id="e5828-131">`pdwMappingType`因為不同的類型會有不同的版面配置和位移，所以您應該一律在中檢查傳回的值。</span><span class="sxs-lookup"><span data-stu-id="e5828-131">You should always check the returned value in `pdwMappingType`, because different types will have different layouts and offsets.</span></span>  
  
 <span data-ttu-id="e5828-132">不支援針對三個參數傳遞 Null。</span><span class="sxs-lookup"><span data-stu-id="e5828-132">Passing NULL for any of the three parameters is not supported.</span></span> <span data-ttu-id="e5828-133">方法會傳回 `E_INVALIDARG` ，而且不會填入任何輸出。</span><span class="sxs-lookup"><span data-stu-id="e5828-133">The method returns `E_INVALIDARG`, and none of the outputs are filled.</span></span> <span data-ttu-id="e5828-134">忽略對應類型或區域的大小可能會導致異常程式終止。</span><span class="sxs-lookup"><span data-stu-id="e5828-134">Ignoring the mapping type or the size of the region can result in abnormal program termination.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5828-135">需求</span><span class="sxs-lookup"><span data-stu-id="e5828-135">Requirements</span></span>  

 <span data-ttu-id="e5828-136">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e5828-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5828-137">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="e5828-137">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e5828-138">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="e5828-138">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e5828-139">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5828-139">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5828-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5828-140">See also</span></span>

- [<span data-ttu-id="e5828-141">IMetaDataInfo 介面</span><span class="sxs-lookup"><span data-stu-id="e5828-141">IMetaDataInfo Interface</span></span>](imetadatainfo-interface.md)
- [<span data-ttu-id="e5828-142">CorFileMapping 列舉</span><span class="sxs-lookup"><span data-stu-id="e5828-142">CorFileMapping Enumeration</span></span>](corfilemapping-enumeration.md)
