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
ms.openlocfilehash: 9cf5f3d926c1e742dd9134e7bf292df53e1a4909
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720174"
---
# <a name="imetadataassemblyemitsetfileprops-method"></a><span data-ttu-id="cb5fb-102">IMetaDataAssemblyEmit::SetFileProps 方法</span><span class="sxs-lookup"><span data-stu-id="cb5fb-102">IMetaDataAssemblyEmit::SetFileProps Method</span></span>

<span data-ttu-id="cb5fb-103">修改指定的 `File` 中繼資料結構。</span><span class="sxs-lookup"><span data-stu-id="cb5fb-103">Modifies the specified `File` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb5fb-104">語法</span><span class="sxs-lookup"><span data-stu-id="cb5fb-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFileProps (  
    [in] mdFile        file,  
    [in] const void    *pbHashValue,
    [in] ULONG         cbHashValue,  
    [in] DWORD         dwFileFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb5fb-105">參數</span><span class="sxs-lookup"><span data-stu-id="cb5fb-105">Parameters</span></span>  

 `file`  
 <span data-ttu-id="cb5fb-106">在元資料標記，指定 `File` 要修改的元資料結構。</span><span class="sxs-lookup"><span data-stu-id="cb5fb-106">[in] The metadata token that specifies the `File` metadata structure to be modified.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="cb5fb-107">在與檔案相關聯之雜湊資料的指標。</span><span class="sxs-lookup"><span data-stu-id="cb5fb-107">[in] A pointer to the hash data associated with the file.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="cb5fb-108">在的大小（以位元組為單位） `pbHashValue` 。</span><span class="sxs-lookup"><span data-stu-id="cb5fb-108">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="cb5fb-109">在 [CorFileFlags](corfileflags-enumeration.md) 值的位元組合，指定檔案的各種屬性。</span><span class="sxs-lookup"><span data-stu-id="cb5fb-109">[in] A bitwise combination of [CorFileFlags](corfileflags-enumeration.md) values that specify various attributes of the file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb5fb-110">備註</span><span class="sxs-lookup"><span data-stu-id="cb5fb-110">Remarks</span></span>  

 <span data-ttu-id="cb5fb-111">若要建立 `File` 元資料結構，請使用 [IMetaDataAssemblyEmit：:D efinefile](imetadataassemblyemit-definefile-method.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="cb5fb-111">To create a `File` metadata structure, use the [IMetaDataAssemblyEmit::DefineFile](imetadataassemblyemit-definefile-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb5fb-112">需求</span><span class="sxs-lookup"><span data-stu-id="cb5fb-112">Requirements</span></span>  

 <span data-ttu-id="cb5fb-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cb5fb-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb5fb-114">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="cb5fb-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cb5fb-115">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="cb5fb-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cb5fb-116">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb5fb-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb5fb-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb5fb-117">See also</span></span>

- [<span data-ttu-id="cb5fb-118">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="cb5fb-118">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
