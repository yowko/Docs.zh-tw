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
ms.openlocfilehash: 39235c5c26cb168dfc995de97f72b80dccb6b818
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720291"
---
# <a name="isymunmanagedwriter3openmethod2-method"></a><span data-ttu-id="94948-102">ISymUnmanagedWriter3::OpenMethod2 方法</span><span class="sxs-lookup"><span data-stu-id="94948-102">ISymUnmanagedWriter3::OpenMethod2 Method</span></span>

<span data-ttu-id="94948-103">開啟方法，並在影像中提供其實際區段位移。</span><span class="sxs-lookup"><span data-stu-id="94948-103">Opens a method and provides its real section offset in the image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94948-104">語法</span><span class="sxs-lookup"><span data-stu-id="94948-104">Syntax</span></span>  
  
```cpp  
HRESULT OpenMethod2(
    [in] mdMethodDef method,  
    [in] ULONG32 isect,  
    [in] ULONG32 offset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="94948-105">參數</span><span class="sxs-lookup"><span data-stu-id="94948-105">Parameters</span></span>  

 `method`  
 <span data-ttu-id="94948-106">在要開啟之方法的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="94948-106">[in] The metadata token for the method to be opened.</span></span>  
  
 `isect`  
 <span data-ttu-id="94948-107">在影像中的區段位移。</span><span class="sxs-lookup"><span data-stu-id="94948-107">[in] The section offset in the image.</span></span>  
  
 `offset`  
 <span data-ttu-id="94948-108">在影像中的位移。</span><span class="sxs-lookup"><span data-stu-id="94948-108">[in] The offset in the image.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="94948-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="94948-109">Return Value</span></span>  

 <span data-ttu-id="94948-110">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="94948-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94948-111">需求</span><span class="sxs-lookup"><span data-stu-id="94948-111">Requirements</span></span>  

 <span data-ttu-id="94948-112">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="94948-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94948-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="94948-113">See also</span></span>

- [<span data-ttu-id="94948-114">ISymUnmanagedWriter3 介面</span><span class="sxs-lookup"><span data-stu-id="94948-114">ISymUnmanagedWriter3 Interface</span></span>](isymunmanagedwriter3-interface.md)
- [<span data-ttu-id="94948-115">OpenMethod 方法</span><span class="sxs-lookup"><span data-stu-id="94948-115">OpenMethod Method</span></span>](isymunmanagedwriter-openmethod-method.md)
