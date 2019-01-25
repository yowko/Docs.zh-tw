---
title: IMetaDataAssemblyEmit::SetAssemblyRefProps 方法
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0a4f0fd100397fc52ca917c54f0276598d714640
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54642840"
---
# <a name="imetadataassemblyemitsetassemblyrefprops-method"></a><span data-ttu-id="4b374-102">IMetaDataAssemblyEmit::SetAssemblyRefProps 方法</span><span class="sxs-lookup"><span data-stu-id="4b374-102">IMetaDataAssemblyEmit::SetAssemblyRefProps Method</span></span>
<span data-ttu-id="4b374-103">修改指定的 `AssemblyRef` 中繼資料結構。</span><span class="sxs-lookup"><span data-stu-id="4b374-103">Modifies the specified `AssemblyRef` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b374-104">語法</span><span class="sxs-lookup"><span data-stu-id="4b374-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="4b374-105">參數</span><span class="sxs-lookup"><span data-stu-id="4b374-105">Parameters</span></span>  
 `ar`  
 <span data-ttu-id="4b374-106">[in]指定中繼資料語彙基元`AssemblyRef`要修改的中繼資料結構。</span><span class="sxs-lookup"><span data-stu-id="4b374-106">[in] The metadata token that specifies the `AssemblyRef` metadata structure to be modified.</span></span>  
  
 `pbPublicKeyOrToken`  
 <span data-ttu-id="4b374-107">[in]參考的組件的 「 發行者 」 的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="4b374-107">[in] The public key of the publisher of the referenced assembly.</span></span>  
  
 `cbPublicKeyOrToken`  
 <span data-ttu-id="4b374-108">[in]以位元組為單位的大小`pbPublicKeyOrToken`。</span><span class="sxs-lookup"><span data-stu-id="4b374-108">[in] The size in bytes of `pbPublicKeyOrToken`.</span></span>  
  
 `szName`  
 <span data-ttu-id="4b374-109">[in]組件的人類看得懂的文字名稱。</span><span class="sxs-lookup"><span data-stu-id="4b374-109">[in] The human-readable text name of the assembly.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="4b374-110">[in]ASSEMBLYMETADATA 執行個體，其中包含組件的版本、 平台，以及地區設定資訊的指標。</span><span class="sxs-lookup"><span data-stu-id="4b374-110">[in] A pointer to an ASSEMBLYMETADATA instance that contains the version, platform, and locale information for the assembly.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="4b374-111">[in]組件相關聯的雜湊資料指標。</span><span class="sxs-lookup"><span data-stu-id="4b374-111">[in] A pointer to the hash data associated with the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="4b374-112">[in]以位元組為單位的大小`pbHashValue`。</span><span class="sxs-lookup"><span data-stu-id="4b374-112">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwAssemblyRefFlags`  
 <span data-ttu-id="4b374-113">[in]位元組合[AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md)指定參考組件屬性的值。</span><span class="sxs-lookup"><span data-stu-id="4b374-113">[in] A bitwise combination of [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) values that specify attributes of the referenced assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4b374-114">備註</span><span class="sxs-lookup"><span data-stu-id="4b374-114">Remarks</span></span>  
 <span data-ttu-id="4b374-115">若要建立`AssemblyRef`中繼資料結構，使用[imetadataassemblyemit:: Defineassemblyref](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="4b374-115">To create an `AssemblyRef` metadata structure, use the [IMetaDataAssemblyEmit::DefineAssemblyRef](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b374-116">需求</span><span class="sxs-lookup"><span data-stu-id="4b374-116">Requirements</span></span>  
 <span data-ttu-id="4b374-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4b374-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b374-118">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4b374-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4b374-119">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="4b374-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4b374-120">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b374-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b374-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b374-121">See also</span></span>
- [<span data-ttu-id="4b374-122">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="4b374-122">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
