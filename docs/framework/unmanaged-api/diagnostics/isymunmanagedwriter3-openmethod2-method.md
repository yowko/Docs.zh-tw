---
title: ISymUnmanagedWriter3::OpenMethod2 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter3.OpenMethod2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter3::OpenMethod2
helpviewer_keywords:
- ISymUnmanagedWriter3::OpenMethod2 method [.NET Framework debugging]
- OpenMethod2 method [.NET Framework debugging]
ms.assetid: 025e358c-448f-4423-a2f2-57acf437c8a5
topic_type:
- apiref
ms.openlocfilehash: 0c112819ef3bc4f9a7146ee80f55202ff89d689a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178322"
---
# <a name="isymunmanagedwriter3openmethod2-method"></a><span data-ttu-id="ee4b6-102">ISymUnmanagedWriter3::OpenMethod2 方法</span><span class="sxs-lookup"><span data-stu-id="ee4b6-102">ISymUnmanagedWriter3::OpenMethod2 Method</span></span>
<span data-ttu-id="ee4b6-103">打開方法並在圖像中提供其實際截面偏移。</span><span class="sxs-lookup"><span data-stu-id="ee4b6-103">Opens a method and provides its real section offset in the image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee4b6-104">語法</span><span class="sxs-lookup"><span data-stu-id="ee4b6-104">Syntax</span></span>  
  
```cpp  
HRESULT OpenMethod2(
    [in] mdMethodDef method,  
    [in] ULONG32 isect,  
    [in] ULONG32 offset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ee4b6-105">參數</span><span class="sxs-lookup"><span data-stu-id="ee4b6-105">Parameters</span></span>  
 `method`  
 <span data-ttu-id="ee4b6-106">[在]要打開的方法的中繼資料權杖。</span><span class="sxs-lookup"><span data-stu-id="ee4b6-106">[in] The metadata token for the method to be opened.</span></span>  
  
 `isect`  
 <span data-ttu-id="ee4b6-107">[在]圖像中的截面偏移。</span><span class="sxs-lookup"><span data-stu-id="ee4b6-107">[in] The section offset in the image.</span></span>  
  
 `offset`  
 <span data-ttu-id="ee4b6-108">[在]圖像中的偏移量。</span><span class="sxs-lookup"><span data-stu-id="ee4b6-108">[in] The offset in the image.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ee4b6-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="ee4b6-109">Return Value</span></span>  
 <span data-ttu-id="ee4b6-110">如果方法成功，S_OK;否則，E_FAIL或其他錯誤代碼。</span><span class="sxs-lookup"><span data-stu-id="ee4b6-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee4b6-111">需求</span><span class="sxs-lookup"><span data-stu-id="ee4b6-111">Requirements</span></span>  
 <span data-ttu-id="ee4b6-112">**標題：** 科西姆.伊德爾，科西姆.h</span><span class="sxs-lookup"><span data-stu-id="ee4b6-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee4b6-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee4b6-113">See also</span></span>

- [<span data-ttu-id="ee4b6-114">ISymUnmanagedWriter3 介面</span><span class="sxs-lookup"><span data-stu-id="ee4b6-114">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
- [<span data-ttu-id="ee4b6-115">OpenMethod 方法</span><span class="sxs-lookup"><span data-stu-id="ee4b6-115">OpenMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)
