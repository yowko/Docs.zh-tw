---
title: IMetaDataValidate 介面
ms.date: 03/30/2017
api_name:
- IMetaDataValidate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataValidate
helpviewer_keywords:
- IMetaDataValidate interface [.NET Framework metadata]
ms.assetid: db98608a-e85c-4f50-9d7b-5f57a426ddb6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c067ee16c8e64a1996b7267069dada4052b39db2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452032"
---
# <a name="imetadatavalidate-interface"></a><span data-ttu-id="74215-102">IMetaDataValidate 介面</span><span class="sxs-lookup"><span data-stu-id="74215-102">IMetaDataValidate Interface</span></span>
<span data-ttu-id="74215-103">提供方法來驗證中繼資料的簽章。</span><span class="sxs-lookup"><span data-stu-id="74215-103">Provides methods to validate metadata signatures.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="74215-104">方法</span><span class="sxs-lookup"><span data-stu-id="74215-104">Methods</span></span>  
  
|<span data-ttu-id="74215-105">方法</span><span class="sxs-lookup"><span data-stu-id="74215-105">Method</span></span>|<span data-ttu-id="74215-106">描述</span><span class="sxs-lookup"><span data-stu-id="74215-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="74215-107">ValidateMetaData 方法</span><span class="sxs-lookup"><span data-stu-id="74215-107">ValidateMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatavalidate-validatemetadata-method.md)|<span data-ttu-id="74215-108">驗證目前中繼資料範圍內物件的中繼資料簽章。</span><span class="sxs-lookup"><span data-stu-id="74215-108">Validates the metadata signatures of the objects in the current metadata scope.</span></span>|  
|[<span data-ttu-id="74215-109">ValidatorInit 方法</span><span class="sxs-lookup"><span data-stu-id="74215-109">ValidatorInit Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatavalidate-validatorinit-method.md)|<span data-ttu-id="74215-110">設定會指定目前中繼資料範圍內模組類型的旗標，並註冊對於驗證錯誤的指定回呼方法。</span><span class="sxs-lookup"><span data-stu-id="74215-110">Sets a flag that specifies the type of the module in the current metadata scope, and registers the specified callback method for validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="74215-111">需求</span><span class="sxs-lookup"><span data-stu-id="74215-111">Requirements</span></span>  
 <span data-ttu-id="74215-112">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="74215-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74215-113">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="74215-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="74215-114">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="74215-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="74215-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74215-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74215-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="74215-116">See Also</span></span>  
 [<span data-ttu-id="74215-117">中繼資料介面</span><span class="sxs-lookup"><span data-stu-id="74215-117">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
