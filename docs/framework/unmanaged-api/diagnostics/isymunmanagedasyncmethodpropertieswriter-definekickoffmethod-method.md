---
title: "ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 4662f70d-817b-4374-8da8-e0545585939f
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 691a46e20339b659b5df3136d4dca6c03a69d3d8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinekickoffmethod-method"></a><span data-ttu-id="57ad8-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod 方法</span><span class="sxs-lookup"><span data-stu-id="57ad8-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod Method</span></span>
<span data-ttu-id="57ad8-103">設定啟始非同步作業的開始方法。</span><span class="sxs-lookup"><span data-stu-id="57ad8-103">Sets the starting method that initiates the async operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57ad8-104">語法</span><span class="sxs-lookup"><span data-stu-id="57ad8-104">Syntax</span></span>  
  
```idl  
HRESULT DefineKickoffMethod(    [in] mdToken kickoffMethod);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="57ad8-105">參數</span><span class="sxs-lookup"><span data-stu-id="57ad8-105">Parameters</span></span>  
  
|<span data-ttu-id="57ad8-106">參數</span><span class="sxs-lookup"><span data-stu-id="57ad8-106">Parameter</span></span>|<span data-ttu-id="57ad8-107">描述</span><span class="sxs-lookup"><span data-stu-id="57ad8-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="57ad8-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="57ad8-108">Return Value</span></span>  
 <span data-ttu-id="57ad8-109">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="57ad8-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57ad8-110">需求</span><span class="sxs-lookup"><span data-stu-id="57ad8-110">Requirements</span></span>  
 <span data-ttu-id="57ad8-111">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="57ad8-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57ad8-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="57ad8-112">See Also</span></span>  
 [<span data-ttu-id="57ad8-113">ISymUnmanagedAsyncMethodPropertiesWriter 介面</span><span class="sxs-lookup"><span data-stu-id="57ad8-113">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
