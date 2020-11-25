---
title: IMetaDataImport::GetModuleFromScope 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetModuleFromScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetModuleFromScope
helpviewer_keywords:
- GetModuleFromScope method [.NET Framework metadata]
- IMetaDataImport::GetModuleFromScope method [.NET Framework metadata]
ms.assetid: add68d3f-45fd-4bef-af94-eb5273f26b11
topic_type:
- apiref
ms.openlocfilehash: 2eddd7a80c2b9c1b71f3e7fc5b1e4686ba11bccd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733161"
---
# <a name="imetadataimportgetmodulefromscope-method"></a><span data-ttu-id="756b6-102">IMetaDataImport::GetModuleFromScope 方法</span><span class="sxs-lookup"><span data-stu-id="756b6-102">IMetaDataImport::GetModuleFromScope Method</span></span>

<span data-ttu-id="756b6-103">取得目前中繼資料範圍中所參考之模組的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="756b6-103">Gets a metadata token for the module referenced in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="756b6-104">語法</span><span class="sxs-lookup"><span data-stu-id="756b6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleFromScope (  
   [out] mdModule    *pmd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="756b6-105">參數</span><span class="sxs-lookup"><span data-stu-id="756b6-105">Parameters</span></span>  

 `pmd`  
 <span data-ttu-id="756b6-106">擴展Token 的指標，代表目前中繼資料範圍中所參考的模組。</span><span class="sxs-lookup"><span data-stu-id="756b6-106">[out] A pointer to the token representing the module referenced in the current metadata scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="756b6-107">需求</span><span class="sxs-lookup"><span data-stu-id="756b6-107">Requirements</span></span>  

 <span data-ttu-id="756b6-108">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="756b6-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="756b6-109">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="756b6-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="756b6-110">連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="756b6-110">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="756b6-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="756b6-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="756b6-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="756b6-112">See also</span></span>

- [<span data-ttu-id="756b6-113">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="756b6-113">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="756b6-114">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="756b6-114">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
