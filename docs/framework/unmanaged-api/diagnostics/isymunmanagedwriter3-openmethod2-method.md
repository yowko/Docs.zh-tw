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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a3dcb1327ad50761a8268e8adc7b1e976cae0b3a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59200294"
---
# <a name="isymunmanagedwriter3openmethod2-method"></a><span data-ttu-id="7a1a2-102">ISymUnmanagedWriter3::OpenMethod2 方法</span><span class="sxs-lookup"><span data-stu-id="7a1a2-102">ISymUnmanagedWriter3::OpenMethod2 Method</span></span>
<span data-ttu-id="7a1a2-103">開啟的方法，並提供映像中的實際的區段位移。</span><span class="sxs-lookup"><span data-stu-id="7a1a2-103">Opens a method and provides its real section offset in the image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a1a2-104">語法</span><span class="sxs-lookup"><span data-stu-id="7a1a2-104">Syntax</span></span>  
  
```  
HRESULT OpenMethod2(   
    [in] mdMethodDef method,  
    [in] ULONG32 isect,  
    [in] ULONG32 offset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7a1a2-105">參數</span><span class="sxs-lookup"><span data-stu-id="7a1a2-105">Parameters</span></span>  
 `method`  
 <span data-ttu-id="7a1a2-106">[in]若要開啟方法的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="7a1a2-106">[in] The metadata token for the method to be opened.</span></span>  
  
 `isect`  
 <span data-ttu-id="7a1a2-107">[in]一節中的位移映像。</span><span class="sxs-lookup"><span data-stu-id="7a1a2-107">[in] The section offset in the image.</span></span>  
  
 `offset`  
 <span data-ttu-id="7a1a2-108">[in]映像中的位移。</span><span class="sxs-lookup"><span data-stu-id="7a1a2-108">[in] The offset in the image.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7a1a2-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="7a1a2-109">Return Value</span></span>  
 <span data-ttu-id="7a1a2-110">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="7a1a2-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a1a2-111">需求</span><span class="sxs-lookup"><span data-stu-id="7a1a2-111">Requirements</span></span>  
 <span data-ttu-id="7a1a2-112">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7a1a2-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a1a2-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7a1a2-113">See also</span></span>

- [<span data-ttu-id="7a1a2-114">ISymUnmanagedWriter3 介面</span><span class="sxs-lookup"><span data-stu-id="7a1a2-114">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
- [<span data-ttu-id="7a1a2-115">OpenMethod 方法</span><span class="sxs-lookup"><span data-stu-id="7a1a2-115">OpenMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)
