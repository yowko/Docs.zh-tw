---
title: ICLRDataTarget::GetImageBase 方法
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetImageBase
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetImageBase
helpviewer_keywords:
- ICLRDataTarget::GetImageBase method [.NET Framework debugging]
- GetImageBase method [.NET Framework debugging]
ms.assetid: 091c5f32-c160-49e3-a75f-4692e084c8e4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9a79133b117f3a718dd84af6c2144a6098bc79f2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33407223"
---
# <a name="iclrdatatargetgetimagebase-method"></a><span data-ttu-id="7ca0d-102">ICLRDataTarget::GetImageBase 方法</span><span class="sxs-lookup"><span data-stu-id="7ca0d-102">ICLRDataTarget::GetImageBase Method</span></span>
<span data-ttu-id="7ca0d-103">取得指定的映像的基底的記憶體位址。</span><span class="sxs-lookup"><span data-stu-id="7ca0d-103">Gets the base memory address of the specified image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ca0d-104">語法</span><span class="sxs-lookup"><span data-stu-id="7ca0d-104">Syntax</span></span>  
  
```  
HRESULT GetImageBase (  
    [in, string] LPCWSTR    imagePath,  
    [out] CLRDATA_ADDRESS   *baseAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7ca0d-105">參數</span><span class="sxs-lookup"><span data-stu-id="7ca0d-105">Parameters</span></span>  
 `imagePath`  
 <span data-ttu-id="7ca0d-106">[in]映像，包括其路徑的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="7ca0d-106">[in] The file name of the image, including its path.</span></span>  
  
 `baseAddress`  
 <span data-ttu-id="7ca0d-107">[out]CLRDATA_ADDRESS 儲存映像的基底位址指標。</span><span class="sxs-lookup"><span data-stu-id="7ca0d-107">[out] A pointer to a CLRDATA_ADDRESS that stores the base address of the image.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7ca0d-108">備註</span><span class="sxs-lookup"><span data-stu-id="7ca0d-108">Remarks</span></span>  
 <span data-ttu-id="7ca0d-109">映像檔案名稱可能會或可能不含路徑。</span><span class="sxs-lookup"><span data-stu-id="7ca0d-109">The image file name may or may not have a path.</span></span> <span data-ttu-id="7ca0d-110">如果指定的路徑，則比對會對整個路徑中;否則，比對是由只能在檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="7ca0d-110">If a path is specified, matching is done on the whole path; otherwise, matching is done only on the file name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ca0d-111">需求</span><span class="sxs-lookup"><span data-stu-id="7ca0d-111">Requirements</span></span>  
 <span data-ttu-id="7ca0d-112">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7ca0d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ca0d-113">**標頭：** ClrData.idl、 ClrData.h</span><span class="sxs-lookup"><span data-stu-id="7ca0d-113">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="7ca0d-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7ca0d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7ca0d-115">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ca0d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ca0d-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7ca0d-116">See Also</span></span>  
 [<span data-ttu-id="7ca0d-117">ICLRDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="7ca0d-117">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
