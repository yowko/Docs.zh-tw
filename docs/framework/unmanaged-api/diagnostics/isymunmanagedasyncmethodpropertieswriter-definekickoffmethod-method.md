---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod 方法
ms.date: 03/30/2017
ms.assetid: 4662f70d-817b-4374-8da8-e0545585939f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 24560ed4b0bb7ca04d5859280baa594fbb2e4097
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57473459"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinekickoffmethod-method"></a><span data-ttu-id="269b9-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod 方法</span><span class="sxs-lookup"><span data-stu-id="269b9-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod Method</span></span>
<span data-ttu-id="269b9-103">設定啟始非同步作業的開始方法。</span><span class="sxs-lookup"><span data-stu-id="269b9-103">Sets the starting method that initiates the async operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="269b9-104">語法</span><span class="sxs-lookup"><span data-stu-id="269b9-104">Syntax</span></span>  
  
```idl  
HRESULT DefineKickoffMethod(    [in] mdToken kickoffMethod);  
```  
  
## <a name="parameters"></a><span data-ttu-id="269b9-105">參數</span><span class="sxs-lookup"><span data-stu-id="269b9-105">Parameters</span></span>  
  
|<span data-ttu-id="269b9-106">參數</span><span class="sxs-lookup"><span data-stu-id="269b9-106">Parameter</span></span>|<span data-ttu-id="269b9-107">描述</span><span class="sxs-lookup"><span data-stu-id="269b9-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="269b9-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="269b9-108">Return Value</span></span>  
 <span data-ttu-id="269b9-109">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="269b9-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="269b9-110">需求</span><span class="sxs-lookup"><span data-stu-id="269b9-110">Requirements</span></span>  
 <span data-ttu-id="269b9-111">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="269b9-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="269b9-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="269b9-112">See also</span></span>
- [<span data-ttu-id="269b9-113">ISymUnmanagedAsyncMethodPropertiesWriter 介面</span><span class="sxs-lookup"><span data-stu-id="269b9-113">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
