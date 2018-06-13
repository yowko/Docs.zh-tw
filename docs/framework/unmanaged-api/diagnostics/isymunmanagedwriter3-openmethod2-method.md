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
ms.openlocfilehash: 643666df9f93d1aa5e09579359ae0db87908f10b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428329"
---
# <a name="isymunmanagedwriter3openmethod2-method"></a><span data-ttu-id="9bae4-102">ISymUnmanagedWriter3::OpenMethod2 方法</span><span class="sxs-lookup"><span data-stu-id="9bae4-102">ISymUnmanagedWriter3::OpenMethod2 Method</span></span>
<span data-ttu-id="9bae4-103">開啟的方法，並提供其實際的區段位移，映像中。</span><span class="sxs-lookup"><span data-stu-id="9bae4-103">Opens a method and provides its real section offset in the image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bae4-104">語法</span><span class="sxs-lookup"><span data-stu-id="9bae4-104">Syntax</span></span>  
  
```  
HRESULT OpenMethod2(   
    [in] mdMethodDef method,  
    [in] ULONG32 isect,  
    [in] ULONG32 offset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9bae4-105">參數</span><span class="sxs-lookup"><span data-stu-id="9bae4-105">Parameters</span></span>  
 `method`  
 <span data-ttu-id="9bae4-106">[in]若要開啟方法的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="9bae4-106">[in] The metadata token for the method to be opened.</span></span>  
  
 `isect`  
 <span data-ttu-id="9bae4-107">[in]中的映像的區段位移。</span><span class="sxs-lookup"><span data-stu-id="9bae4-107">[in] The section offset in the image.</span></span>  
  
 `offset`  
 <span data-ttu-id="9bae4-108">[in]映像中的位移。</span><span class="sxs-lookup"><span data-stu-id="9bae4-108">[in] The offset in the image.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9bae4-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="9bae4-109">Return Value</span></span>  
 <span data-ttu-id="9bae4-110">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="9bae4-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9bae4-111">需求</span><span class="sxs-lookup"><span data-stu-id="9bae4-111">Requirements</span></span>  
 <span data-ttu-id="9bae4-112">**標頭：** 於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="9bae4-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bae4-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9bae4-113">See Also</span></span>  
 [<span data-ttu-id="9bae4-114">ISymUnmanagedWriter3 介面</span><span class="sxs-lookup"><span data-stu-id="9bae4-114">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)  
 [<span data-ttu-id="9bae4-115">OpenMethod 方法</span><span class="sxs-lookup"><span data-stu-id="9bae4-115">OpenMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)
