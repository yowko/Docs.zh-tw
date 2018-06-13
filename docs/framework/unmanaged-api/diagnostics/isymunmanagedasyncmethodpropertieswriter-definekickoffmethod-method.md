---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod 方法
ms.date: 03/30/2017
ms.assetid: 4662f70d-817b-4374-8da8-e0545585939f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a476d92486d7f2523dfbcc8b25e9c11e26c55f2d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33425611"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinekickoffmethod-method"></a><span data-ttu-id="5ee78-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod 方法</span><span class="sxs-lookup"><span data-stu-id="5ee78-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod Method</span></span>
<span data-ttu-id="5ee78-103">設定啟始非同步作業的開始方法。</span><span class="sxs-lookup"><span data-stu-id="5ee78-103">Sets the starting method that initiates the async operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ee78-104">語法</span><span class="sxs-lookup"><span data-stu-id="5ee78-104">Syntax</span></span>  
  
```idl  
HRESULT DefineKickoffMethod(    [in] mdToken kickoffMethod);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5ee78-105">參數</span><span class="sxs-lookup"><span data-stu-id="5ee78-105">Parameters</span></span>  
  
|<span data-ttu-id="5ee78-106">參數</span><span class="sxs-lookup"><span data-stu-id="5ee78-106">Parameter</span></span>|<span data-ttu-id="5ee78-107">描述</span><span class="sxs-lookup"><span data-stu-id="5ee78-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="5ee78-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="5ee78-108">Return Value</span></span>  
 <span data-ttu-id="5ee78-109">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="5ee78-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ee78-110">需求</span><span class="sxs-lookup"><span data-stu-id="5ee78-110">Requirements</span></span>  
 <span data-ttu-id="5ee78-111">**標頭：** 於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5ee78-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ee78-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5ee78-112">See Also</span></span>  
 [<span data-ttu-id="5ee78-113">ISymUnmanagedAsyncMethodPropertiesWriter 介面</span><span class="sxs-lookup"><span data-stu-id="5ee78-113">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
