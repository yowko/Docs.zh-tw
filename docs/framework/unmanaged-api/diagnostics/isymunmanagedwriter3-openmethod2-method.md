---
title: "ISymUnmanagedWriter3::OpenMethod2 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter3.OpenMethod2
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter3::OpenMethod2
helpviewer_keywords:
- ISymUnmanagedWriter3::OpenMethod2 method [.NET Framework debugging]
- OpenMethod2 method [.NET Framework debugging]
ms.assetid: 025e358c-448f-4423-a2f2-57acf437c8a5
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8da6de0271ddce5b956e667420a206c09cc291d8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriter3openmethod2-method"></a><span data-ttu-id="7be3e-102">ISymUnmanagedWriter3::OpenMethod2 方法</span><span class="sxs-lookup"><span data-stu-id="7be3e-102">ISymUnmanagedWriter3::OpenMethod2 Method</span></span>
<span data-ttu-id="7be3e-103">開啟的方法，並提供其實際的區段位移，映像中。</span><span class="sxs-lookup"><span data-stu-id="7be3e-103">Opens a method and provides its real section offset in the image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7be3e-104">語法</span><span class="sxs-lookup"><span data-stu-id="7be3e-104">Syntax</span></span>  
  
```  
HRESULT OpenMethod2(   
    [in] mdMethodDef method,  
    [in] ULONG32 isect,  
    [in] ULONG32 offset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7be3e-105">參數</span><span class="sxs-lookup"><span data-stu-id="7be3e-105">Parameters</span></span>  
 `method`  
 <span data-ttu-id="7be3e-106">[in]若要開啟方法的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="7be3e-106">[in] The metadata token for the method to be opened.</span></span>  
  
 `isect`  
 <span data-ttu-id="7be3e-107">[in]中的映像的區段位移。</span><span class="sxs-lookup"><span data-stu-id="7be3e-107">[in] The section offset in the image.</span></span>  
  
 `offset`  
 <span data-ttu-id="7be3e-108">[in]映像中的位移。</span><span class="sxs-lookup"><span data-stu-id="7be3e-108">[in] The offset in the image.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7be3e-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="7be3e-109">Return Value</span></span>  
 <span data-ttu-id="7be3e-110">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="7be3e-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7be3e-111">需求</span><span class="sxs-lookup"><span data-stu-id="7be3e-111">Requirements</span></span>  
 <span data-ttu-id="7be3e-112">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7be3e-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7be3e-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="7be3e-113">See Also</span></span>  
 [<span data-ttu-id="7be3e-114">ISymUnmanagedWriter3 介面</span><span class="sxs-lookup"><span data-stu-id="7be3e-114">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)  
 [<span data-ttu-id="7be3e-115">OpenMethod 方法</span><span class="sxs-lookup"><span data-stu-id="7be3e-115">OpenMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)
