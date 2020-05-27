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
ms.openlocfilehash: 9990daea1b097532de53684921d3f10c520a3b1a
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008062"
---
# <a name="imetadataassemblyemitsetfileprops-method"></a><span data-ttu-id="47000-102">IMetaDataAssemblyEmit::SetFileProps 方法</span><span class="sxs-lookup"><span data-stu-id="47000-102">IMetaDataAssemblyEmit::SetFileProps Method</span></span>
<span data-ttu-id="47000-103">修改指定的 `File` 中繼資料結構。</span><span class="sxs-lookup"><span data-stu-id="47000-103">Modifies the specified `File` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47000-104">語法</span><span class="sxs-lookup"><span data-stu-id="47000-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFileProps (  
    [in] mdFile        file,  
    [in] const void    *pbHashValue,
    [in] ULONG         cbHashValue,  
    [in] DWORD         dwFileFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="47000-105">參數</span><span class="sxs-lookup"><span data-stu-id="47000-105">Parameters</span></span>  
 `file`  
 <span data-ttu-id="47000-106">在元資料標記，指定 `File` 要修改的元資料結構。</span><span class="sxs-lookup"><span data-stu-id="47000-106">[in] The metadata token that specifies the `File` metadata structure to be modified.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="47000-107">在與檔案相關聯之雜湊資料的指標。</span><span class="sxs-lookup"><span data-stu-id="47000-107">[in] A pointer to the hash data associated with the file.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="47000-108">在的大小（以位元組為單位） `pbHashValue` 。</span><span class="sxs-lookup"><span data-stu-id="47000-108">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="47000-109">在[CorFileFlags](corfileflags-enumeration.md)值的位元組合，這個組合會指定檔案的各種屬性。</span><span class="sxs-lookup"><span data-stu-id="47000-109">[in] A bitwise combination of [CorFileFlags](corfileflags-enumeration.md) values that specify various attributes of the file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="47000-110">備註</span><span class="sxs-lookup"><span data-stu-id="47000-110">Remarks</span></span>  
 <span data-ttu-id="47000-111">若要建立 `File` 元資料結構，請使用[IMetaDataAssemblyEmit：:D efinefile](imetadataassemblyemit-definefile-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="47000-111">To create a `File` metadata structure, use the [IMetaDataAssemblyEmit::DefineFile](imetadataassemblyemit-definefile-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47000-112">需求</span><span class="sxs-lookup"><span data-stu-id="47000-112">Requirements</span></span>  
 <span data-ttu-id="47000-113">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="47000-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47000-114">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="47000-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="47000-115">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="47000-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="47000-116">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47000-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47000-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="47000-117">See also</span></span>

- [<span data-ttu-id="47000-118">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="47000-118">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
