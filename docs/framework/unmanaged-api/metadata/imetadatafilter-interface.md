---
title: IMetaDataFilter 介面
ms.date: 03/30/2017
api_name:
- IMetaDataFilter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataFilter
helpviewer_keywords:
- IMetaDataFilter interface [.NET Framework metadata]
ms.assetid: ec0856ef-8c56-40ba-bf60-86e0ce8b337f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ad77aba02c819749794534ca2ecd478661bc363f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444977"
---
# <a name="imetadatafilter-interface"></a><span data-ttu-id="4d414-102">IMetaDataFilter 介面</span><span class="sxs-lookup"><span data-stu-id="4d414-102">IMetaDataFilter Interface</span></span>
<span data-ttu-id="4d414-103">提供標記和篩選中繼資料語彙基元的方法，以避免重複已採取的動作。</span><span class="sxs-lookup"><span data-stu-id="4d414-103">Provides methods for marking and filtering metadata tokens to avoid repeating actions that have already been taken.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4d414-104">方法</span><span class="sxs-lookup"><span data-stu-id="4d414-104">Methods</span></span>  
  
|<span data-ttu-id="4d414-105">方法</span><span class="sxs-lookup"><span data-stu-id="4d414-105">Method</span></span>|<span data-ttu-id="4d414-106">描述</span><span class="sxs-lookup"><span data-stu-id="4d414-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4d414-107">IsTokenMarked 方法</span><span class="sxs-lookup"><span data-stu-id="4d414-107">IsTokenMarked Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-istokenmarked-method.md)|<span data-ttu-id="4d414-108">取得值，指出是否已經處理指定的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="4d414-108">Gets a value indicating whether the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="4d414-109">MarkToken 方法</span><span class="sxs-lookup"><span data-stu-id="4d414-109">MarkToken Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-marktoken-method.md)|<span data-ttu-id="4d414-110">設定值，指出指定的中繼資料語彙基元已經處理。</span><span class="sxs-lookup"><span data-stu-id="4d414-110">Sets a value indicating that the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="4d414-111">UnmarkAll 方法</span><span class="sxs-lookup"><span data-stu-id="4d414-111">UnmarkAll Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-unmarkall-method.md)|<span data-ttu-id="4d414-112">移除目前的中繼資料範圍內的所有權杖處理標記。</span><span class="sxs-lookup"><span data-stu-id="4d414-112">Removes the processing marks from all the tokens in the current metadata scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4d414-113">需求</span><span class="sxs-lookup"><span data-stu-id="4d414-113">Requirements</span></span>  
 <span data-ttu-id="4d414-114">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4d414-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d414-115">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4d414-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4d414-116">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="4d414-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4d414-117">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d414-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d414-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d414-118">See Also</span></span>  
 [<span data-ttu-id="4d414-119">中繼資料介面</span><span class="sxs-lookup"><span data-stu-id="4d414-119">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
