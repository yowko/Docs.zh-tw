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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4c6a9473a698e4635c8b5cc9fb58963334dfd65e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992273"
---
# <a name="imetadatainfogetfilemapping-method"></a><span data-ttu-id="25965-102">IMetaDataInfo::GetFileMapping 方法</span><span class="sxs-lookup"><span data-stu-id="25965-102">IMetaDataInfo::GetFileMapping Method</span></span>
<span data-ttu-id="25965-103">取得記憶體區域的對應的檔，以及對應的類型。</span><span class="sxs-lookup"><span data-stu-id="25965-103">Gets the memory region of the mapped file, and the type of mapping.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25965-104">語法</span><span class="sxs-lookup"><span data-stu-id="25965-104">Syntax</span></span>  
  
```  
HRESULT GetFileMapping (  
    [out] const void           **ppvData,   
    [out] ULONGLONG            *pcbData,   
    [out] DWORD                *pdwMappingType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25965-105">參數</span><span class="sxs-lookup"><span data-stu-id="25965-105">Parameters</span></span>  
 `ppvData`  
 <span data-ttu-id="25965-106">[out]對應檔的開頭指標。</span><span class="sxs-lookup"><span data-stu-id="25965-106">[out] A pointer to the start of the mapped file.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="25965-107">[out]對應區域的大小。</span><span class="sxs-lookup"><span data-stu-id="25965-107">[out] The size of the mapped region.</span></span> <span data-ttu-id="25965-108">如果`pdwMappingType`是`fmFlat`，這是檔案的大小。</span><span class="sxs-lookup"><span data-stu-id="25965-108">If `pdwMappingType` is `fmFlat`, this is the size of the file.</span></span>  
  
 `pdwMappingType`  
 <span data-ttu-id="25965-109">[out]A [CorFileMapping](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md)值，指出對應的類型。</span><span class="sxs-lookup"><span data-stu-id="25965-109">[out] A [CorFileMapping](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md) value that indicates the type of mapping.</span></span> <span data-ttu-id="25965-110">目前的實作的 common language runtime (CLR) 永遠傳回`fmFlat`。</span><span class="sxs-lookup"><span data-stu-id="25965-110">The current implementation of the common language runtime (CLR) always returns `fmFlat`.</span></span> <span data-ttu-id="25965-111">其他值保留供日後使用。</span><span class="sxs-lookup"><span data-stu-id="25965-111">Other values are reserved for future use.</span></span> <span data-ttu-id="25965-112">不過，您一律應該確認傳回的值，因為其他值可能會在未來版本中啟用，或服務版本。</span><span class="sxs-lookup"><span data-stu-id="25965-112">However, you should always verify the returned value, because other values may be enabled in future versions or service releases.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="25965-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="25965-113">Return Value</span></span>  
  
|<span data-ttu-id="25965-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="25965-114">HRESULT</span></span>|<span data-ttu-id="25965-115">描述</span><span class="sxs-lookup"><span data-stu-id="25965-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="25965-116">所有的輸出會填滿。</span><span class="sxs-lookup"><span data-stu-id="25965-116">All outputs are filled.</span></span>|  
|`E_INVALIDARG`|<span data-ttu-id="25965-117">傳遞 NULL 做為引數的值。</span><span class="sxs-lookup"><span data-stu-id="25965-117">NULL was passed as an argument value.</span></span>|  
|`COR_E_NOTSUPPORTED`|<span data-ttu-id="25965-118">CLR 實作無法提供記憶體區域的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="25965-118">The CLR implementation cannot provide information about the memory region.</span></span> <span data-ttu-id="25965-119">這種情形，原因如下：</span><span class="sxs-lookup"><span data-stu-id="25965-119">This can happen for the following reasons:</span></span><br /><br /> <span data-ttu-id="25965-120">-在中繼資料範圍以開啟`ofWrite`或`ofCopyMemory`旗標。</span><span class="sxs-lookup"><span data-stu-id="25965-120">-   The metadata scope was opened with the `ofWrite` or `ofCopyMemory` flag.</span></span><br /><span data-ttu-id="25965-121">-在中繼資料範圍已開啟但`ofReadOnly`旗標。</span><span class="sxs-lookup"><span data-stu-id="25965-121">-   The metadata scope was opened without the `ofReadOnly` flag.</span></span><br /><span data-ttu-id="25965-122">- [Imetadatadispenser:: Openscopeonmemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md)方法用來開啟 僅中繼資料檔案的一部分。</span><span class="sxs-lookup"><span data-stu-id="25965-122">-   The [IMetaDataDispenser::OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) method was used to open only the metadata portion of the file.</span></span><br /><span data-ttu-id="25965-123">-檔案不是可攜式執行檔 (PE) 檔案。</span><span class="sxs-lookup"><span data-stu-id="25965-123">-   The file is not a portable executable (PE) file.</span></span> <span data-ttu-id="25965-124">**注意：** 這些條件取決於 CLR 實作中，而且可能會減弱在未來的 CLR 版本。</span><span class="sxs-lookup"><span data-stu-id="25965-124">**Note:**  These conditions depend on the CLR implementation, and are likely to be weakened in future versions of the CLR.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="25965-125">備註</span><span class="sxs-lookup"><span data-stu-id="25965-125">Remarks</span></span>  
 <span data-ttu-id="25965-126">記憶體的`ppvData`指向無效，只要基礎的中繼資料範圍已開啟。</span><span class="sxs-lookup"><span data-stu-id="25965-126">The memory that `ppvData` points to is valid only as long as the underlying metadata scope is open.</span></span>  
  
 <span data-ttu-id="25965-127">為了讓此方法才能運作，當您將磁碟上檔案的中繼資料對應到記憶體上呼叫[imetadatadispenser:: Openscope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)方法，您必須指定`ofReadOnly`旗標，您必須指定`ofWrite`或`ofCopyMemory`旗標。</span><span class="sxs-lookup"><span data-stu-id="25965-127">In order for this method to work, when you map the metadata of an on-disk file into memory by calling the [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) method, you must specify the `ofReadOnly` flag and you must not specify the `ofWrite` or `ofCopyMemory` flag.</span></span>  
  
 <span data-ttu-id="25965-128">選擇每個範圍的檔案對應類型是 CLR 的指定實作的特定項目。</span><span class="sxs-lookup"><span data-stu-id="25965-128">The choice of file mapping type for each scope is specific to a given implementation of the CLR.</span></span> <span data-ttu-id="25965-129">它不能由使用者設定。</span><span class="sxs-lookup"><span data-stu-id="25965-129">It cannot be set by the user.</span></span> <span data-ttu-id="25965-130">目前實作的 clr 一律會傳回`fmFlat`在`pdwMappingType`，但這在 CLR 的版本，或未來的特定版本的服務版本可以在未來變更。</span><span class="sxs-lookup"><span data-stu-id="25965-130">The current implementation of the CLR always returns `fmFlat` in `pdwMappingType`, but this can change in future versions of the CLR or in future service releases of a given version.</span></span> <span data-ttu-id="25965-131">您一律應該檢查傳回的值`pdwMappingType`，因為不同的版面配置和位移，會有不同的型別。</span><span class="sxs-lookup"><span data-stu-id="25965-131">You should always check the returned value in `pdwMappingType`, because different types will have different layouts and offsets.</span></span>  
  
 <span data-ttu-id="25965-132">不支援將傳遞的任何三個參數都是 NULL。</span><span class="sxs-lookup"><span data-stu-id="25965-132">Passing NULL for any of the three parameters is not supported.</span></span> <span data-ttu-id="25965-133">此方法會傳回`E_INVALIDARG`，且沒有任何輸出會填入。</span><span class="sxs-lookup"><span data-stu-id="25965-133">The method returns `E_INVALIDARG`, and none of the outputs are filled.</span></span> <span data-ttu-id="25965-134">忽略對應型別或區域的大小，可能會導致程式異常終止。</span><span class="sxs-lookup"><span data-stu-id="25965-134">Ignoring the mapping type or the size of the region can result in abnormal program termination.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25965-135">需求</span><span class="sxs-lookup"><span data-stu-id="25965-135">Requirements</span></span>  
 <span data-ttu-id="25965-136">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="25965-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25965-137">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="25965-137">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="25965-138">**LIBRARY:** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="25965-138">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="25965-139">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25965-139">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25965-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="25965-140">See also</span></span>

- [<span data-ttu-id="25965-141">IMetaDataInfo 介面</span><span class="sxs-lookup"><span data-stu-id="25965-141">IMetaDataInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-interface.md)
- [<span data-ttu-id="25965-142">CorFileMapping 列舉</span><span class="sxs-lookup"><span data-stu-id="25965-142">CorFileMapping Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md)
