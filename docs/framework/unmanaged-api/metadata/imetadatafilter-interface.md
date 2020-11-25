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
ms.openlocfilehash: 2c22e45ca3d33b0a81ff0ecd90bf7574c45676bd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701844"
---
# <a name="imetadatafilter-interface"></a><span data-ttu-id="446f2-102">IMetaDataFilter 介面</span><span class="sxs-lookup"><span data-stu-id="446f2-102">IMetaDataFilter Interface</span></span>

<span data-ttu-id="446f2-103">提供標記和篩選中繼資料語彙基元的方法，以避免重複已採取的動作。</span><span class="sxs-lookup"><span data-stu-id="446f2-103">Provides methods for marking and filtering metadata tokens to avoid repeating actions that have already been taken.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="446f2-104">方法</span><span class="sxs-lookup"><span data-stu-id="446f2-104">Methods</span></span>  
  
|<span data-ttu-id="446f2-105">方法</span><span class="sxs-lookup"><span data-stu-id="446f2-105">Method</span></span>|<span data-ttu-id="446f2-106">描述</span><span class="sxs-lookup"><span data-stu-id="446f2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="446f2-107">IsTokenMarked 方法</span><span class="sxs-lookup"><span data-stu-id="446f2-107">IsTokenMarked Method</span></span>](imetadatafilter-istokenmarked-method.md)|<span data-ttu-id="446f2-108">取得值，指出是否已處理指定的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="446f2-108">Gets a value indicating whether the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="446f2-109">MarkToken 方法</span><span class="sxs-lookup"><span data-stu-id="446f2-109">MarkToken Method</span></span>](imetadatafilter-marktoken-method.md)|<span data-ttu-id="446f2-110">設定值，指出已處理指定的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="446f2-110">Sets a value indicating that the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="446f2-111">UnmarkAll 方法</span><span class="sxs-lookup"><span data-stu-id="446f2-111">UnmarkAll Method</span></span>](imetadatafilter-unmarkall-method.md)|<span data-ttu-id="446f2-112">從目前中繼資料範圍中的所有標記移除處理標記。</span><span class="sxs-lookup"><span data-stu-id="446f2-112">Removes the processing marks from all the tokens in the current metadata scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="446f2-113">需求</span><span class="sxs-lookup"><span data-stu-id="446f2-113">Requirements</span></span>  

 <span data-ttu-id="446f2-114">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="446f2-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="446f2-115">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="446f2-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="446f2-116">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="446f2-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="446f2-117">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="446f2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="446f2-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="446f2-118">See also</span></span>

- [<span data-ttu-id="446f2-119">中繼資料介面</span><span class="sxs-lookup"><span data-stu-id="446f2-119">Metadata Interfaces</span></span>](metadata-interfaces.md)
