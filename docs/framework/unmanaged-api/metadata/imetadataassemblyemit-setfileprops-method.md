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
ms.openlocfilehash: 106ffeee521f69a73628b1fb6a611abc733583f9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431879"
---
# <a name="imetadataassemblyemitsetfileprops-method"></a><span data-ttu-id="3d881-102">IMetaDataAssemblyEmit::SetFileProps 方法</span><span class="sxs-lookup"><span data-stu-id="3d881-102">IMetaDataAssemblyEmit::SetFileProps Method</span></span>
<span data-ttu-id="3d881-103">修改指定的 `File` 中繼資料結構。</span><span class="sxs-lookup"><span data-stu-id="3d881-103">Modifies the specified `File` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d881-104">語法</span><span class="sxs-lookup"><span data-stu-id="3d881-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFileProps (  
    [in] mdFile        file,  
    [in] const void    *pbHashValue,   
    [in] ULONG         cbHashValue,  
    [in] DWORD         dwFileFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3d881-105">參數</span><span class="sxs-lookup"><span data-stu-id="3d881-105">Parameters</span></span>  
 `file`  
 <span data-ttu-id="3d881-106">在元資料標記，指定要修改的 `File` 元資料結構。</span><span class="sxs-lookup"><span data-stu-id="3d881-106">[in] The metadata token that specifies the `File` metadata structure to be modified.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="3d881-107">在與檔案相關聯之雜湊資料的指標。</span><span class="sxs-lookup"><span data-stu-id="3d881-107">[in] A pointer to the hash data associated with the file.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="3d881-108">在`pbHashValue`的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="3d881-108">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="3d881-109">在[CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md)值的位元組合，這個組合會指定檔案的各種屬性。</span><span class="sxs-lookup"><span data-stu-id="3d881-109">[in] A bitwise combination of [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) values that specify various attributes of the file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d881-110">備註</span><span class="sxs-lookup"><span data-stu-id="3d881-110">Remarks</span></span>  
 <span data-ttu-id="3d881-111">若要建立 `File` 元資料結構，請使用[IMetaDataAssemblyEmit：:D efinefile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="3d881-111">To create a `File` metadata structure, use the [IMetaDataAssemblyEmit::DefineFile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d881-112">需求</span><span class="sxs-lookup"><span data-stu-id="3d881-112">Requirements</span></span>  
 <span data-ttu-id="3d881-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3d881-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d881-114">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="3d881-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3d881-115">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="3d881-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3d881-116">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d881-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d881-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3d881-117">See also</span></span>

- [<span data-ttu-id="3d881-118">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="3d881-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
