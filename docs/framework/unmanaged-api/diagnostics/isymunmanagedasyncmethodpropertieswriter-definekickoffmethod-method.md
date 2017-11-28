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
ms.openlocfilehash: 68c5d6662d8cbecca06268bd5010878c4e476f47
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinekickoffmethod-method"></a><span data-ttu-id="b55d7-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod 方法</span><span class="sxs-lookup"><span data-stu-id="b55d7-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod Method</span></span>
<span data-ttu-id="b55d7-103">設定啟始非同步作業的開始方法。</span><span class="sxs-lookup"><span data-stu-id="b55d7-103">Sets the starting method that initiates the async operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b55d7-104">語法</span><span class="sxs-lookup"><span data-stu-id="b55d7-104">Syntax</span></span>  
  
```idl  
HRESULT DefineKickoffMethod(    [in] mdToken kickoffMethod);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b55d7-105">參數</span><span class="sxs-lookup"><span data-stu-id="b55d7-105">Parameters</span></span>  
  
|<span data-ttu-id="b55d7-106">參數</span><span class="sxs-lookup"><span data-stu-id="b55d7-106">Parameter</span></span>|<span data-ttu-id="b55d7-107">說明</span><span class="sxs-lookup"><span data-stu-id="b55d7-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="b55d7-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="b55d7-108">Return Value</span></span>  
 <span data-ttu-id="b55d7-109">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="b55d7-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b55d7-110">需求</span><span class="sxs-lookup"><span data-stu-id="b55d7-110">Requirements</span></span>  
 <span data-ttu-id="b55d7-111">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b55d7-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b55d7-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b55d7-112">See Also</span></span>  
 [<span data-ttu-id="b55d7-113">ISymUnmanagedAsyncMethodPropertiesWriter 介面</span><span class="sxs-lookup"><span data-stu-id="b55d7-113">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
