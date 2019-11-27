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
ms.openlocfilehash: 3a628aec0823c5db07d31d33813a020606906163
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438133"
---
# <a name="isymunmanagedwriter3openmethod2-method"></a><span data-ttu-id="fe691-102">ISymUnmanagedWriter3::OpenMethod2 方法</span><span class="sxs-lookup"><span data-stu-id="fe691-102">ISymUnmanagedWriter3::OpenMethod2 Method</span></span>
<span data-ttu-id="fe691-103">開啟方法，並在影像中提供其實數區段位移。</span><span class="sxs-lookup"><span data-stu-id="fe691-103">Opens a method and provides its real section offset in the image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe691-104">語法</span><span class="sxs-lookup"><span data-stu-id="fe691-104">Syntax</span></span>  
  
```cpp  
HRESULT OpenMethod2(   
    [in] mdMethodDef method,  
    [in] ULONG32 isect,  
    [in] ULONG32 offset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fe691-105">參數</span><span class="sxs-lookup"><span data-stu-id="fe691-105">Parameters</span></span>  
 `method`  
 <span data-ttu-id="fe691-106">在要開啟之方法的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="fe691-106">[in] The metadata token for the method to be opened.</span></span>  
  
 `isect`  
 <span data-ttu-id="fe691-107">在影像中的區段位移。</span><span class="sxs-lookup"><span data-stu-id="fe691-107">[in] The section offset in the image.</span></span>  
  
 `offset`  
 <span data-ttu-id="fe691-108">在影像中的位移。</span><span class="sxs-lookup"><span data-stu-id="fe691-108">[in] The offset in the image.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fe691-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="fe691-109">Return Value</span></span>  
 <span data-ttu-id="fe691-110">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="fe691-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe691-111">需求</span><span class="sxs-lookup"><span data-stu-id="fe691-111">Requirements</span></span>  
 <span data-ttu-id="fe691-112">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="fe691-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe691-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="fe691-113">See also</span></span>

- [<span data-ttu-id="fe691-114">ISymUnmanagedWriter3 介面</span><span class="sxs-lookup"><span data-stu-id="fe691-114">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
- [<span data-ttu-id="fe691-115">OpenMethod 方法</span><span class="sxs-lookup"><span data-stu-id="fe691-115">OpenMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)
