---
title: "IMetaDataAssemblyEmit::SetAssemblyRefProps 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataAssemblyEmit.SetAssemblyRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetAssemblyRefProps
helpviewer_keywords:
- SetAssemblyRefProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetAssemblyRefProps method [.NET Framework metadata]
ms.assetid: 70a32bf3-9051-4f96-ae87-11356d06a073
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 446137d28fdd64d7f9e5c84cc57e9ec967982430
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyemitsetassemblyrefprops-method"></a><span data-ttu-id="b5e4e-102">IMetaDataAssemblyEmit::SetAssemblyRefProps 方法</span><span class="sxs-lookup"><span data-stu-id="b5e4e-102">IMetaDataAssemblyEmit::SetAssemblyRefProps Method</span></span>
<span data-ttu-id="b5e4e-103">修改指定的 `AssemblyRef` 中繼資料結構。</span><span class="sxs-lookup"><span data-stu-id="b5e4e-103">Modifies the specified `AssemblyRef` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5e4e-104">語法</span><span class="sxs-lookup"><span data-stu-id="b5e4e-104">Syntax</span></span>  
  
```  
HRESULT SetAssemblyRefProps (  
    [in] mdAssemblyRef              ar,  
    [in] const void                 *pbPublicKeyOrToken,  
    [in] ULONG                      cbPublicKeyOrToken,  
    [in] LPCWSTR                    szName,   
    [in] const ASSEMBLYMETADATA     *pMetaData,   
    [in] const void                 *pbHashValue,  
    [in] ULONG                      cbHashValue,  
    [in] DWORD                      dwAssemblyRefFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b5e4e-105">參數</span><span class="sxs-lookup"><span data-stu-id="b5e4e-105">Parameters</span></span>  
 `ar`  
 <span data-ttu-id="b5e4e-106">[in]指定的中繼資料語彙基元`AssemblyRef`要修改的中繼資料結構。</span><span class="sxs-lookup"><span data-stu-id="b5e4e-106">[in] The metadata token that specifies the `AssemblyRef` metadata structure to be modified.</span></span>  
  
 `pbPublicKeyOrToken`  
 <span data-ttu-id="b5e4e-107">[in]參考的組件的 「 發行者 」 的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="b5e4e-107">[in] The public key of the publisher of the referenced assembly.</span></span>  
  
 `cbPublicKeyOrToken`  
 <span data-ttu-id="b5e4e-108">[in]以位元組為單位的大小`pbPublicKeyOrToken`。</span><span class="sxs-lookup"><span data-stu-id="b5e4e-108">[in] The size in bytes of `pbPublicKeyOrToken`.</span></span>  
  
 `szName`  
 <span data-ttu-id="b5e4e-109">[in]人類看得懂的文字之組件的名稱。</span><span class="sxs-lookup"><span data-stu-id="b5e4e-109">[in] The human-readable text name of the assembly.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="b5e4e-110">[in]ASSEMBLYMETADATA 執行個體，其中包含組件的版本、 平台，以及地區設定資訊指標。</span><span class="sxs-lookup"><span data-stu-id="b5e4e-110">[in] A pointer to an ASSEMBLYMETADATA instance that contains the version, platform, and locale information for the assembly.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="b5e4e-111">[in]與組件相關聯的雜湊資料指標。</span><span class="sxs-lookup"><span data-stu-id="b5e4e-111">[in] A pointer to the hash data associated with the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="b5e4e-112">[in]以位元組為單位的大小`pbHashValue`。</span><span class="sxs-lookup"><span data-stu-id="b5e4e-112">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwAssemblyRefFlags`  
 <span data-ttu-id="b5e4e-113">[in]位元組合[AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md)指定參考組件屬性的值。</span><span class="sxs-lookup"><span data-stu-id="b5e4e-113">[in] A bitwise combination of [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) values that specify attributes of the referenced assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b5e4e-114">備註</span><span class="sxs-lookup"><span data-stu-id="b5e4e-114">Remarks</span></span>  
 <span data-ttu-id="b5e4e-115">若要建立`AssemblyRef`中繼資料結構，使用[imetadataassemblyemit:: Defineassemblyref](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="b5e4e-115">To create an `AssemblyRef` metadata structure, use the [IMetaDataAssemblyEmit::DefineAssemblyRef](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5e4e-116">需求</span><span class="sxs-lookup"><span data-stu-id="b5e4e-116">Requirements</span></span>  
 <span data-ttu-id="b5e4e-117">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b5e4e-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5e4e-118">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b5e4e-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b5e4e-119">**程式庫：**做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b5e4e-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b5e4e-120">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5e4e-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5e4e-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="b5e4e-121">See Also</span></span>  
 [<span data-ttu-id="b5e4e-122">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="b5e4e-122">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
