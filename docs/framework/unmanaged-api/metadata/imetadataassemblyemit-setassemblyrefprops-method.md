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
ms.openlocfilehash: 6ad6bbb8a4c69f575bbeba3a297c46e049a97325
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176041"
---
# <a name="imetadataassemblyemitsetassemblyrefprops-method"></a><span data-ttu-id="31e20-102">IMetaDataAssemblyEmit::SetAssemblyRefProps 方法</span><span class="sxs-lookup"><span data-stu-id="31e20-102">IMetaDataAssemblyEmit::SetAssemblyRefProps Method</span></span>
<span data-ttu-id="31e20-103">修改指定的 `AssemblyRef` 中繼資料結構。</span><span class="sxs-lookup"><span data-stu-id="31e20-103">Modifies the specified `AssemblyRef` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31e20-104">語法</span><span class="sxs-lookup"><span data-stu-id="31e20-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="31e20-105">參數</span><span class="sxs-lookup"><span data-stu-id="31e20-105">Parameters</span></span>  
 `ar`  
 <span data-ttu-id="31e20-106">[在]指定要修改的`AssemblyRef`元資料結構的中繼資料權杖。</span><span class="sxs-lookup"><span data-stu-id="31e20-106">[in] The metadata token that specifies the `AssemblyRef` metadata structure to be modified.</span></span>  
  
 `pbPublicKeyOrToken`  
 <span data-ttu-id="31e20-107">[在]引用程式集的發行者的公共金鑰。</span><span class="sxs-lookup"><span data-stu-id="31e20-107">[in] The public key of the publisher of the referenced assembly.</span></span>  
  
 `cbPublicKeyOrToken`  
 <span data-ttu-id="31e20-108">[在]的大小（以位元組為單位）。 `pbPublicKeyOrToken`</span><span class="sxs-lookup"><span data-stu-id="31e20-108">[in] The size in bytes of `pbPublicKeyOrToken`.</span></span>  
  
 `szName`  
 <span data-ttu-id="31e20-109">[在]程式集的人類可讀文本名稱。</span><span class="sxs-lookup"><span data-stu-id="31e20-109">[in] The human-readable text name of the assembly.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="31e20-110">[在]指向 ASSEMBLYMETADATA 實例的指標，其中包含程式集的版本、平臺和地區設定資訊。</span><span class="sxs-lookup"><span data-stu-id="31e20-110">[in] A pointer to an ASSEMBLYMETADATA instance that contains the version, platform, and locale information for the assembly.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="31e20-111">[在]指向與程式集關聯的雜湊資料的指標。</span><span class="sxs-lookup"><span data-stu-id="31e20-111">[in] A pointer to the hash data associated with the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="31e20-112">[在]的大小（以位元組為單位）。 `pbHashValue`</span><span class="sxs-lookup"><span data-stu-id="31e20-112">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwAssemblyRefFlags`  
 <span data-ttu-id="31e20-113">[在]指定引用程式集屬性的[程式集 RefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md)值的位組合。</span><span class="sxs-lookup"><span data-stu-id="31e20-113">[in] A bitwise combination of [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) values that specify attributes of the referenced assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31e20-114">備註</span><span class="sxs-lookup"><span data-stu-id="31e20-114">Remarks</span></span>  
 <span data-ttu-id="31e20-115">要創建`AssemblyRef`元資料結構，請使用[IMetaDataAssemblyEmit：:DefineAssemblyRef](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="31e20-115">To create an `AssemblyRef` metadata structure, use the [IMetaDataAssemblyEmit::DefineAssemblyRef](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31e20-116">需求</span><span class="sxs-lookup"><span data-stu-id="31e20-116">Requirements</span></span>  
 <span data-ttu-id="31e20-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="31e20-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31e20-118">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="31e20-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="31e20-119">**庫：** 用作 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="31e20-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="31e20-120">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31e20-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31e20-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="31e20-121">See also</span></span>

- [<span data-ttu-id="31e20-122">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="31e20-122">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
