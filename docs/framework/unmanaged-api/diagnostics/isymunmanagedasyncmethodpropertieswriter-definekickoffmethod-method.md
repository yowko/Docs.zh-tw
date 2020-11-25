---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod 方法
ms.date: 03/30/2017
ms.assetid: 4662f70d-817b-4374-8da8-e0545585939f
ms.openlocfilehash: 418a77855d1cb34a07f5957059b5a6f5a106c321
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707083"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinekickoffmethod-method"></a><span data-ttu-id="708bd-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod 方法</span><span class="sxs-lookup"><span data-stu-id="708bd-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod Method</span></span>

<span data-ttu-id="708bd-103">設定啟動非同步作業的起始方法。</span><span class="sxs-lookup"><span data-stu-id="708bd-103">Sets the starting method that initiates the async operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="708bd-104">語法</span><span class="sxs-lookup"><span data-stu-id="708bd-104">Syntax</span></span>  
  
```idl  
HRESULT DefineKickoffMethod(    [in] mdToken kickoffMethod);  
```  
  
## <a name="parameters"></a><span data-ttu-id="708bd-105">參數</span><span class="sxs-lookup"><span data-stu-id="708bd-105">Parameters</span></span>  
  
|<span data-ttu-id="708bd-106">參數</span><span class="sxs-lookup"><span data-stu-id="708bd-106">Parameter</span></span>|<span data-ttu-id="708bd-107">描述</span><span class="sxs-lookup"><span data-stu-id="708bd-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="708bd-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="708bd-108">Return Value</span></span>  

 <span data-ttu-id="708bd-109">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="708bd-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="708bd-110">需求</span><span class="sxs-lookup"><span data-stu-id="708bd-110">Requirements</span></span>  

 <span data-ttu-id="708bd-111">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="708bd-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="708bd-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="708bd-112">See also</span></span>

- [<span data-ttu-id="708bd-113">ISymUnmanagedAsyncMethodPropertiesWriter 介面</span><span class="sxs-lookup"><span data-stu-id="708bd-113">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](isymunmanagedasyncmethodpropertieswriter-interface.md)
