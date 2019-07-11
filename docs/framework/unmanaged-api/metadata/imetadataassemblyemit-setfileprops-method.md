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
ms.openlocfilehash: 6505995b128e31ed2a18881d31afa0bb1bfe150e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779419"
---
# <a name="imetadataassemblyemitsetfileprops-method"></a><span data-ttu-id="3e3b9-102">IMetaDataAssemblyEmit::SetFileProps 方法</span><span class="sxs-lookup"><span data-stu-id="3e3b9-102">IMetaDataAssemblyEmit::SetFileProps Method</span></span>
<span data-ttu-id="3e3b9-103">修改指定的 `File` 中繼資料結構。</span><span class="sxs-lookup"><span data-stu-id="3e3b9-103">Modifies the specified `File` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e3b9-104">語法</span><span class="sxs-lookup"><span data-stu-id="3e3b9-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFileProps (  
    [in] mdFile        file,  
    [in] const void    *pbHashValue,   
    [in] ULONG         cbHashValue,  
    [in] DWORD         dwFileFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3e3b9-105">參數</span><span class="sxs-lookup"><span data-stu-id="3e3b9-105">Parameters</span></span>  
 `file`  
 <span data-ttu-id="3e3b9-106">[in]指定中繼資料語彙基元`File`要修改的中繼資料結構。</span><span class="sxs-lookup"><span data-stu-id="3e3b9-106">[in] The metadata token that specifies the `File` metadata structure to be modified.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="3e3b9-107">[in]與檔案相關聯的雜湊資料指標。</span><span class="sxs-lookup"><span data-stu-id="3e3b9-107">[in] A pointer to the hash data associated with the file.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="3e3b9-108">[in]以位元組為單位的大小`pbHashValue`。</span><span class="sxs-lookup"><span data-stu-id="3e3b9-108">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="3e3b9-109">[in]位元組合[CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md)指定檔案的各種屬性的值。</span><span class="sxs-lookup"><span data-stu-id="3e3b9-109">[in] A bitwise combination of [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) values that specify various attributes of the file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3e3b9-110">備註</span><span class="sxs-lookup"><span data-stu-id="3e3b9-110">Remarks</span></span>  
 <span data-ttu-id="3e3b9-111">若要建立`File`中繼資料結構，使用[imetadataassemblyemit:: Definefile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="3e3b9-111">To create a `File` metadata structure, use the [IMetaDataAssemblyEmit::DefineFile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e3b9-112">需求</span><span class="sxs-lookup"><span data-stu-id="3e3b9-112">Requirements</span></span>  
 <span data-ttu-id="3e3b9-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3e3b9-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e3b9-114">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3e3b9-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3e3b9-115">**LIBRARY:** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="3e3b9-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3e3b9-116">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e3b9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e3b9-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3e3b9-117">See also</span></span>

- [<span data-ttu-id="3e3b9-118">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="3e3b9-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
