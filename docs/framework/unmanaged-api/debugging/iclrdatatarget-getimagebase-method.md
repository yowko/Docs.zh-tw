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
ms.openlocfilehash: 71b07e11cd3fec1a0dbebe986d98067c2e6f18e1
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860627"
---
# <a name="iclrdatatargetgetimagebase-method"></a><span data-ttu-id="6857f-102">ICLRDataTarget::GetImageBase 方法</span><span class="sxs-lookup"><span data-stu-id="6857f-102">ICLRDataTarget::GetImageBase Method</span></span>
<span data-ttu-id="6857f-103">取得指定之映射的基底記憶體位址。</span><span class="sxs-lookup"><span data-stu-id="6857f-103">Gets the base memory address of the specified image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6857f-104">語法</span><span class="sxs-lookup"><span data-stu-id="6857f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetImageBase (  
    [in, string] LPCWSTR    imagePath,  
    [out] CLRDATA_ADDRESS   *baseAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6857f-105">參數</span><span class="sxs-lookup"><span data-stu-id="6857f-105">Parameters</span></span>  
 `imagePath`  
 <span data-ttu-id="6857f-106">在映射的檔案名，包括其路徑。</span><span class="sxs-lookup"><span data-stu-id="6857f-106">[in] The file name of the image, including its path.</span></span>  
  
 `baseAddress`  
 <span data-ttu-id="6857f-107">脫銷儲存映射基底位址之 CLRDATA_ADDRESS 的指標。</span><span class="sxs-lookup"><span data-stu-id="6857f-107">[out] A pointer to a CLRDATA_ADDRESS that stores the base address of the image.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6857f-108">備註</span><span class="sxs-lookup"><span data-stu-id="6857f-108">Remarks</span></span>  
 <span data-ttu-id="6857f-109">影像檔案名稱不一定有路徑。</span><span class="sxs-lookup"><span data-stu-id="6857f-109">The image file name may or may not have a path.</span></span> <span data-ttu-id="6857f-110">如果指定了路徑，則會對整個路徑進行比對;否則，只會對檔案名進行比對。</span><span class="sxs-lookup"><span data-stu-id="6857f-110">If a path is specified, matching is done on the whole path; otherwise, matching is done only on the file name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6857f-111">需求</span><span class="sxs-lookup"><span data-stu-id="6857f-111">Requirements</span></span>  
 <span data-ttu-id="6857f-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6857f-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6857f-113">**標頭：** ClrData .idl，ClrData。h</span><span class="sxs-lookup"><span data-stu-id="6857f-113">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="6857f-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6857f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6857f-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6857f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6857f-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="6857f-116">See also</span></span>

- [<span data-ttu-id="6857f-117">ICLRDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="6857f-117">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
