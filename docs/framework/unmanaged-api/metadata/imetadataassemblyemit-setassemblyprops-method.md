---
title: IMetaDataAssemblyEmit::SetAssemblyProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetAssemblyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetAssemblyProps
helpviewer_keywords:
- SetAssemblyProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetAssemblyProps method [.NET Framework metadata]
ms.assetid: 91b633d7-9e75-43c3-a8d2-2144984e5f9e
topic_type:
- apiref
ms.openlocfilehash: f79320d5b7d2ad4ad44a79fae063ce6718490a70
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431957"
---
# <a name="imetadataassemblyemitsetassemblyprops-method"></a><span data-ttu-id="05c91-102">IMetaDataAssemblyEmit::SetAssemblyProps 方法</span><span class="sxs-lookup"><span data-stu-id="05c91-102">IMetaDataAssemblyEmit::SetAssemblyProps Method</span></span>
<span data-ttu-id="05c91-103">修改指定的 `Assembly` 中繼資料結構。</span><span class="sxs-lookup"><span data-stu-id="05c91-103">Modifies the specified `Assembly` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05c91-104">語法</span><span class="sxs-lookup"><span data-stu-id="05c91-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyProps (  
    [in] mdAssembly               pma,  
    [in] const void               *pbPublicKey,  
    [in] ULONG                    cbPublicKey,  
    [in] ULONG                    ulHashAlgId,  
    [in] LPCWSTR                  szName,  
    [in] const ASSEMBLYMETADATA   *pMetaData,  
    [in] DWORD                    dwAssemblyFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="05c91-105">參數</span><span class="sxs-lookup"><span data-stu-id="05c91-105">Parameters</span></span>  
 `pma`  
 <span data-ttu-id="05c91-106">在元資料標記，指定要修改的 `Assembly` 元資料結構。</span><span class="sxs-lookup"><span data-stu-id="05c91-106">[in] The metadata token that specifies the `Assembly` metadata structure to be modified.</span></span>  
  
 `pbPublicKey`  
 <span data-ttu-id="05c91-107">在元件發行者公用金鑰的指標。</span><span class="sxs-lookup"><span data-stu-id="05c91-107">[in] A pointer to the public key of the publisher of the assembly.</span></span>  
  
 `cbPublicKey`  
 <span data-ttu-id="05c91-108">在`pbPublicKey`的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="05c91-108">[in] The size in bytes of `pbPublicKey`.</span></span>  
  
 `ulHashAlgId`  
 <span data-ttu-id="05c91-109">在用來雜湊元件檔的雜湊演算法識別碼。</span><span class="sxs-lookup"><span data-stu-id="05c91-109">[in] The identifier for the hash algorithm used to hash the assembly files.</span></span>  
  
 `szName`  
 <span data-ttu-id="05c91-110">在元件的人類看得懂的文字名稱。</span><span class="sxs-lookup"><span data-stu-id="05c91-110">[in] The human-readable text name of the assembly.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="05c91-111">在ASSEMBLYMETADATA 的指標，其中包含元件的版本、平臺和地區設定資訊。</span><span class="sxs-lookup"><span data-stu-id="05c91-111">[in] A pointer to the ASSEMBLYMETADATA that contains version, platform, and locale information for the assembly.</span></span>  
  
 `dwAssemblyFlags`  
 <span data-ttu-id="05c91-112">在[AssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md)值的位元組合，這個組合會指定元件的各種屬性。</span><span class="sxs-lookup"><span data-stu-id="05c91-112">[in] A bitwise combination of [AssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md) values that specify various attributes of the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="05c91-113">備註</span><span class="sxs-lookup"><span data-stu-id="05c91-113">Remarks</span></span>  
 <span data-ttu-id="05c91-114">若要建立 `Assembly` 元資料結構，請使用[IMetaDataAssemblyEmit：:D efineassembly](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="05c91-114">To create an `Assembly` metadata structure, use the [IMetaDataAssemblyEmit::DefineAssembly](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05c91-115">需求</span><span class="sxs-lookup"><span data-stu-id="05c91-115">Requirements</span></span>  
 <span data-ttu-id="05c91-116">**平臺：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="05c91-116">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05c91-117">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="05c91-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="05c91-118">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="05c91-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="05c91-119">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05c91-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05c91-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="05c91-120">See also</span></span>

- [<span data-ttu-id="05c91-121">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="05c91-121">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
