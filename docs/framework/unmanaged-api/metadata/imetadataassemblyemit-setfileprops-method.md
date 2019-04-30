---
title: IMetaDataAssemblyEmit::SetFileProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetFileProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetFileProps
helpviewer_keywords:
- IMetaDataAssemblyEmit::SetFileProps method [.NET Framework metadata]
- SetFileProps method [.NET Framework metadata]
ms.assetid: 85667d38-611c-45a9-938d-930ac7a7b681
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fd0c2da234fa89bbf92c2117d6428d64502da0c5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62044742"
---
# <a name="imetadataassemblyemitsetfileprops-method"></a><span data-ttu-id="985bf-102">IMetaDataAssemblyEmit::SetFileProps 方法</span><span class="sxs-lookup"><span data-stu-id="985bf-102">IMetaDataAssemblyEmit::SetFileProps Method</span></span>
<span data-ttu-id="985bf-103">修改指定的 `File` 中繼資料結構。</span><span class="sxs-lookup"><span data-stu-id="985bf-103">Modifies the specified `File` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="985bf-104">語法</span><span class="sxs-lookup"><span data-stu-id="985bf-104">Syntax</span></span>  
  
```  
HRESULT SetFileProps (  
    [in] mdFile        file,  
    [in] const void    *pbHashValue,   
    [in] ULONG         cbHashValue,  
    [in] DWORD         dwFileFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="985bf-105">參數</span><span class="sxs-lookup"><span data-stu-id="985bf-105">Parameters</span></span>  
 `file`  
 <span data-ttu-id="985bf-106">[in]指定中繼資料語彙基元`File`要修改的中繼資料結構。</span><span class="sxs-lookup"><span data-stu-id="985bf-106">[in] The metadata token that specifies the `File` metadata structure to be modified.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="985bf-107">[in]與檔案相關聯的雜湊資料指標。</span><span class="sxs-lookup"><span data-stu-id="985bf-107">[in] A pointer to the hash data associated with the file.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="985bf-108">[in]以位元組為單位的大小`pbHashValue`。</span><span class="sxs-lookup"><span data-stu-id="985bf-108">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="985bf-109">[in]位元組合[CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md)指定檔案的各種屬性的值。</span><span class="sxs-lookup"><span data-stu-id="985bf-109">[in] A bitwise combination of [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) values that specify various attributes of the file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="985bf-110">備註</span><span class="sxs-lookup"><span data-stu-id="985bf-110">Remarks</span></span>  
 <span data-ttu-id="985bf-111">若要建立`File`中繼資料結構，使用[imetadataassemblyemit:: Definefile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="985bf-111">To create a `File` metadata structure, use the [IMetaDataAssemblyEmit::DefineFile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="985bf-112">需求</span><span class="sxs-lookup"><span data-stu-id="985bf-112">Requirements</span></span>  
 <span data-ttu-id="985bf-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="985bf-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="985bf-114">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="985bf-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="985bf-115">**LIBRARY:** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="985bf-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="985bf-116">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="985bf-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="985bf-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="985bf-117">See also</span></span>

- [<span data-ttu-id="985bf-118">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="985bf-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
