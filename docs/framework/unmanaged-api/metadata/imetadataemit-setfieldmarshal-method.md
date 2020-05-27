---
title: IMetaDataEmit::SetFieldMarshal 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetFieldMarshal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetFieldMarshal
helpviewer_keywords:
- SetFieldMarshal method [.NET Framework metadata]
- IMetaDataEmit::SetFieldMarshal method [.NET Framework metadata]
ms.assetid: be232314-7f69-4855-bfab-63361bd22307
topic_type:
- apiref
ms.openlocfilehash: d0066c6590a9e0cf278e036111c2739f7cfaf679
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84003902"
---
# <a name="imetadataemitsetfieldmarshal-method"></a><span data-ttu-id="10af3-102">IMetaDataEmit::SetFieldMarshal 方法</span><span class="sxs-lookup"><span data-stu-id="10af3-102">IMetaDataEmit::SetFieldMarshal Method</span></span>
<span data-ttu-id="10af3-103">針對指定之標記所參考的欄位、方法傳回或方法參數，設定 PInvoke 封送處理資訊。</span><span class="sxs-lookup"><span data-stu-id="10af3-103">Sets the PInvoke marshaling information for the field, method return, or method parameter referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10af3-104">語法</span><span class="sxs-lookup"><span data-stu-id="10af3-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFieldMarshal (  
    [in]  mdToken          tk,
    [in]  PCCOR_SIGNATURE  pvNativeType,
    [in]  ULONG            cbNativeType
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="10af3-105">參數</span><span class="sxs-lookup"><span data-stu-id="10af3-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="10af3-106">在目標資料項目的 token。</span><span class="sxs-lookup"><span data-stu-id="10af3-106">[in] The token for target data item.</span></span> <span data-ttu-id="10af3-107">這可能是 `mdFieldDef` 或 `mdParamDef` 權杖。</span><span class="sxs-lookup"><span data-stu-id="10af3-107">This is either a `mdFieldDef` or a `mdParamDef` token.</span></span>  
  
 `pvNativeType`  
 <span data-ttu-id="10af3-108">在非受控類型的簽章。</span><span class="sxs-lookup"><span data-stu-id="10af3-108">[in] The signature for unmanaged type.</span></span>  
  
 `cbNativeType`  
 <span data-ttu-id="10af3-109">在中的位元組計數 `pvNativeType` 。</span><span class="sxs-lookup"><span data-stu-id="10af3-109">[in] The count of bytes in `pvNativeType`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10af3-110">需求</span><span class="sxs-lookup"><span data-stu-id="10af3-110">Requirements</span></span>  
 <span data-ttu-id="10af3-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="10af3-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10af3-112">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="10af3-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="10af3-113">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="10af3-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="10af3-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10af3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10af3-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="10af3-115">See also</span></span>

- [<span data-ttu-id="10af3-116">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="10af3-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="10af3-117">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="10af3-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
