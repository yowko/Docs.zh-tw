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
ms.openlocfilehash: e28659f3c6912489775dd09951610f19e4400942
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672743"
---
# <a name="imetadataassemblyemitsetassemblyrefprops-method"></a><span data-ttu-id="4f5c2-102">IMetaDataAssemblyEmit::SetAssemblyRefProps 方法</span><span class="sxs-lookup"><span data-stu-id="4f5c2-102">IMetaDataAssemblyEmit::SetAssemblyRefProps Method</span></span>

<span data-ttu-id="4f5c2-103">修改指定的 `AssemblyRef` 中繼資料結構。</span><span class="sxs-lookup"><span data-stu-id="4f5c2-103">Modifies the specified `AssemblyRef` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f5c2-104">語法</span><span class="sxs-lookup"><span data-stu-id="4f5c2-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="4f5c2-105">參數</span><span class="sxs-lookup"><span data-stu-id="4f5c2-105">Parameters</span></span>  

 `ar`  
 <span data-ttu-id="4f5c2-106">在元資料標記，指定 `AssemblyRef` 要修改的元資料結構。</span><span class="sxs-lookup"><span data-stu-id="4f5c2-106">[in] The metadata token that specifies the `AssemblyRef` metadata structure to be modified.</span></span>  
  
 `pbPublicKeyOrToken`  
 <span data-ttu-id="4f5c2-107">在參考之元件發行者的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="4f5c2-107">[in] The public key of the publisher of the referenced assembly.</span></span>  
  
 `cbPublicKeyOrToken`  
 <span data-ttu-id="4f5c2-108">在的大小（以位元組為單位） `pbPublicKeyOrToken` 。</span><span class="sxs-lookup"><span data-stu-id="4f5c2-108">[in] The size in bytes of `pbPublicKeyOrToken`.</span></span>  
  
 `szName`  
 <span data-ttu-id="4f5c2-109">在元件的人們可讀取文字名稱。</span><span class="sxs-lookup"><span data-stu-id="4f5c2-109">[in] The human-readable text name of the assembly.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="4f5c2-110">在ASSEMBLYMETADATA 實例的指標，其中包含元件的版本、平臺和地區設定資訊。</span><span class="sxs-lookup"><span data-stu-id="4f5c2-110">[in] A pointer to an ASSEMBLYMETADATA instance that contains the version, platform, and locale information for the assembly.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="4f5c2-111">在與元件相關聯之雜湊資料的指標。</span><span class="sxs-lookup"><span data-stu-id="4f5c2-111">[in] A pointer to the hash data associated with the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="4f5c2-112">在的大小（以位元組為單位） `pbHashValue` 。</span><span class="sxs-lookup"><span data-stu-id="4f5c2-112">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwAssemblyRefFlags`  
 <span data-ttu-id="4f5c2-113">在 [AssemblyRefFlags](assemblyrefflags-enumeration.md) 值的位元組合，指定參考元件的屬性。</span><span class="sxs-lookup"><span data-stu-id="4f5c2-113">[in] A bitwise combination of [AssemblyRefFlags](assemblyrefflags-enumeration.md) values that specify attributes of the referenced assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4f5c2-114">備註</span><span class="sxs-lookup"><span data-stu-id="4f5c2-114">Remarks</span></span>  

 <span data-ttu-id="4f5c2-115">若要建立 `AssemblyRef` 元資料結構，請使用 [IMetaDataAssemblyEmit：:D efineassemblyref](imetadataassemblyemit-defineassemblyref-method.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="4f5c2-115">To create an `AssemblyRef` metadata structure, use the [IMetaDataAssemblyEmit::DefineAssemblyRef](imetadataassemblyemit-defineassemblyref-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f5c2-116">需求</span><span class="sxs-lookup"><span data-stu-id="4f5c2-116">Requirements</span></span>  

 <span data-ttu-id="4f5c2-117">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4f5c2-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f5c2-118">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="4f5c2-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4f5c2-119">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="4f5c2-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4f5c2-120">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f5c2-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f5c2-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4f5c2-121">See also</span></span>

- [<span data-ttu-id="4f5c2-122">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="4f5c2-122">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
