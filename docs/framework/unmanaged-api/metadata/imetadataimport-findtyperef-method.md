---
title: IMetaDataImport::FindTypeRef 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindTypeRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindTypeRef
helpviewer_keywords:
- IMetaDataImport::FindTypeRef method [.NET Framework metadata]
- FindTypeRef method [.NET Framework metadata]
ms.assetid: 1b2bbf3f-943e-412e-b66c-e802431b055c
topic_type:
- apiref
ms.openlocfilehash: 3c96a9b601824cc4001568c4656f968fad70cf39
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711282"
---
# <a name="imetadataimportfindtyperef-method"></a><span data-ttu-id="17282-102">IMetaDataImport::FindTypeRef 方法</span><span class="sxs-lookup"><span data-stu-id="17282-102">IMetaDataImport::FindTypeRef Method</span></span>

<span data-ttu-id="17282-103">取得位於 <xref:System.Type> 指定範圍且具有指定名稱之參考的 TypeRef token 指標。</span><span class="sxs-lookup"><span data-stu-id="17282-103">Gets a pointer to the TypeRef token for the <xref:System.Type> reference that is in the specified scope and that has the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17282-104">語法</span><span class="sxs-lookup"><span data-stu-id="17282-104">Syntax</span></span>  
  
```cpp  
HRESULT FindTypeRef (  
   [in] mdToken        tkResolutionScope,  
   [in]  LPCWSTR       szName,  
   [out] mdTypeRef     *ptr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="17282-105">參數</span><span class="sxs-lookup"><span data-stu-id="17282-105">Parameters</span></span>  

 `tkResolutionScope`  
 <span data-ttu-id="17282-106">在ModuleRef、AssemblyRef 或 TypeRef 權杖，可分別指定定義型別參考所在的模組、元件或類型。</span><span class="sxs-lookup"><span data-stu-id="17282-106">[in] A ModuleRef, AssemblyRef, or TypeRef token that specifies the module, assembly, or type, respectively, in which the type reference is defined.</span></span>  
  
 `szName`  
 <span data-ttu-id="17282-107">在要搜尋之類型參考的名稱。</span><span class="sxs-lookup"><span data-stu-id="17282-107">[in] The name of the type reference to search for.</span></span>  
  
 `ptr`  
 <span data-ttu-id="17282-108">擴展對應的 TypeRef token 指標。</span><span class="sxs-lookup"><span data-stu-id="17282-108">[out] A pointer to the matching TypeRef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17282-109">需求</span><span class="sxs-lookup"><span data-stu-id="17282-109">Requirements</span></span>  

 <span data-ttu-id="17282-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="17282-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17282-111">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="17282-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="17282-112">連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="17282-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="17282-113">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17282-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17282-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="17282-114">See also</span></span>

- [<span data-ttu-id="17282-115">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="17282-115">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="17282-116">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="17282-116">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
