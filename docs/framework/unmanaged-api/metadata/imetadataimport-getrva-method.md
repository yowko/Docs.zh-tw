---
title: IMetaDataImport::GetRVA 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetRVA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetRVA
helpviewer_keywords:
- GetRVA method [.NET Framework metadata]
- IMetaDataImport::GetRVA method [.NET Framework metadata]
ms.assetid: ea422217-988b-4acd-b2db-c55357938275
topic_type:
- apiref
ms.openlocfilehash: b4e7209c357f21a3f0de5770b483b673d5a5570b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729209"
---
# <a name="imetadataimportgetrva-method"></a><span data-ttu-id="e60c1-102">IMetaDataImport::GetRVA 方法</span><span class="sxs-lookup"><span data-stu-id="e60c1-102">IMetaDataImport::GetRVA Method</span></span>

<span data-ttu-id="e60c1-103">取得 (RVA) 的相對虛擬位址，以及指定標記所代表之方法或欄位的實旗標。</span><span class="sxs-lookup"><span data-stu-id="e60c1-103">Gets the relative virtual address (RVA) and the implementation flags of the method or field represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e60c1-104">語法</span><span class="sxs-lookup"><span data-stu-id="e60c1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRVA (  
   [in]  mdToken     tk,
   [out] ULONG       *pulCodeRVA,
   [out]  DWORD      *pdwImplFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e60c1-105">參數</span><span class="sxs-lookup"><span data-stu-id="e60c1-105">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="e60c1-106">在MethodDef 或 FieldDef 元資料標記，代表要傳回 RVA 的程式碼物件。</span><span class="sxs-lookup"><span data-stu-id="e60c1-106">[in] A MethodDef or FieldDef metadata token that represents the code object to return the RVA for.</span></span> <span data-ttu-id="e60c1-107">如果 token 是 FieldDef，則欄位必須是全域變數。</span><span class="sxs-lookup"><span data-stu-id="e60c1-107">If the token is a FieldDef, the field must be a global variable.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="e60c1-108">擴展標記所代表之程式碼物件的相對虛擬位址的指標。</span><span class="sxs-lookup"><span data-stu-id="e60c1-108">[out] A pointer to the relative virtual address of the code object represented by the token.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="e60c1-109">擴展方法之實旗標的指標。</span><span class="sxs-lookup"><span data-stu-id="e60c1-109">[out] A pointer to the implementation flags for the method.</span></span> <span data-ttu-id="e60c1-110">這個值是 [CorMethodImpl](cormethodimpl-enumeration.md) 列舉的位元遮罩。</span><span class="sxs-lookup"><span data-stu-id="e60c1-110">This value is a bitmask from the [CorMethodImpl](cormethodimpl-enumeration.md) enumeration.</span></span> <span data-ttu-id="e60c1-111">`pdwImplFlags`只有當是 MethodDef 標記時，的值才有效 `tk` 。</span><span class="sxs-lookup"><span data-stu-id="e60c1-111">The value of `pdwImplFlags` is valid only if `tk` is a MethodDef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e60c1-112">需求</span><span class="sxs-lookup"><span data-stu-id="e60c1-112">Requirements</span></span>  

 <span data-ttu-id="e60c1-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e60c1-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e60c1-114">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="e60c1-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e60c1-115">連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="e60c1-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e60c1-116">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e60c1-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e60c1-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e60c1-117">See also</span></span>

- [<span data-ttu-id="e60c1-118">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="e60c1-118">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="e60c1-119">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="e60c1-119">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
