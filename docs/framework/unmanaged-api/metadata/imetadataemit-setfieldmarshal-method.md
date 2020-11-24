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
ms.openlocfilehash: d479416f5f1cb4042f9b3fc112e22b67e37d3f78
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672704"
---
# <a name="imetadataemitsetfieldmarshal-method"></a><span data-ttu-id="5213e-102">IMetaDataEmit::SetFieldMarshal 方法</span><span class="sxs-lookup"><span data-stu-id="5213e-102">IMetaDataEmit::SetFieldMarshal Method</span></span>

<span data-ttu-id="5213e-103">針對指定之標記所參考的欄位、方法傳回或方法參數，設定 PInvoke 封送處理資訊。</span><span class="sxs-lookup"><span data-stu-id="5213e-103">Sets the PInvoke marshaling information for the field, method return, or method parameter referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5213e-104">語法</span><span class="sxs-lookup"><span data-stu-id="5213e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFieldMarshal (  
    [in]  mdToken          tk,
    [in]  PCCOR_SIGNATURE  pvNativeType,
    [in]  ULONG            cbNativeType
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5213e-105">參數</span><span class="sxs-lookup"><span data-stu-id="5213e-105">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="5213e-106">在目標資料項目目的標記。</span><span class="sxs-lookup"><span data-stu-id="5213e-106">[in] The token for target data item.</span></span> <span data-ttu-id="5213e-107">這可能是 `mdFieldDef` 或 `mdParamDef` 標記。</span><span class="sxs-lookup"><span data-stu-id="5213e-107">This is either a `mdFieldDef` or a `mdParamDef` token.</span></span>  
  
 `pvNativeType`  
 <span data-ttu-id="5213e-108">在非受控型別的簽章。</span><span class="sxs-lookup"><span data-stu-id="5213e-108">[in] The signature for unmanaged type.</span></span>  
  
 `cbNativeType`  
 <span data-ttu-id="5213e-109">在中的位元組計數 `pvNativeType` 。</span><span class="sxs-lookup"><span data-stu-id="5213e-109">[in] The count of bytes in `pvNativeType`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5213e-110">需求</span><span class="sxs-lookup"><span data-stu-id="5213e-110">Requirements</span></span>  

 <span data-ttu-id="5213e-111">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5213e-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5213e-112">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="5213e-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5213e-113">連結 **庫：** 當做 MSCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="5213e-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5213e-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5213e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5213e-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5213e-115">See also</span></span>

- [<span data-ttu-id="5213e-116">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="5213e-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="5213e-117">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="5213e-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
