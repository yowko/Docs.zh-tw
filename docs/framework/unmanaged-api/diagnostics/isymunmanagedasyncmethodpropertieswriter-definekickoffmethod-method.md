---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod 方法
ms.date: 03/30/2017
ms.assetid: 4662f70d-817b-4374-8da8-e0545585939f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce3c135e031d0c8425e990811fedc40f4ec45243
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59226608"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinekickoffmethod-method"></a><span data-ttu-id="a04ee-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod 方法</span><span class="sxs-lookup"><span data-stu-id="a04ee-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod Method</span></span>
<span data-ttu-id="a04ee-103">設定啟始非同步作業的開始方法。</span><span class="sxs-lookup"><span data-stu-id="a04ee-103">Sets the starting method that initiates the async operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a04ee-104">語法</span><span class="sxs-lookup"><span data-stu-id="a04ee-104">Syntax</span></span>  
  
```idl  
HRESULT DefineKickoffMethod(    [in] mdToken kickoffMethod);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a04ee-105">參數</span><span class="sxs-lookup"><span data-stu-id="a04ee-105">Parameters</span></span>  
  
|<span data-ttu-id="a04ee-106">參數</span><span class="sxs-lookup"><span data-stu-id="a04ee-106">Parameter</span></span>|<span data-ttu-id="a04ee-107">描述</span><span class="sxs-lookup"><span data-stu-id="a04ee-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="a04ee-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="a04ee-108">Return Value</span></span>  
 <span data-ttu-id="a04ee-109">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="a04ee-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a04ee-110">需求</span><span class="sxs-lookup"><span data-stu-id="a04ee-110">Requirements</span></span>  
 <span data-ttu-id="a04ee-111">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a04ee-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a04ee-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a04ee-112">See also</span></span>

- [<span data-ttu-id="a04ee-113">ISymUnmanagedAsyncMethodPropertiesWriter 介面</span><span class="sxs-lookup"><span data-stu-id="a04ee-113">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
