---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod 方法
ms.date: 03/30/2017
ms.assetid: 4662f70d-817b-4374-8da8-e0545585939f
ms.openlocfilehash: c35455fc679d79d56814a9c2f026ec395e944f24
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441717"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinekickoffmethod-method"></a><span data-ttu-id="06155-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod 方法</span><span class="sxs-lookup"><span data-stu-id="06155-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod Method</span></span>
<span data-ttu-id="06155-103">設定啟動非同步作業的起始方法。</span><span class="sxs-lookup"><span data-stu-id="06155-103">Sets the starting method that initiates the async operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06155-104">語法</span><span class="sxs-lookup"><span data-stu-id="06155-104">Syntax</span></span>  
  
```idl  
HRESULT DefineKickoffMethod(    [in] mdToken kickoffMethod);  
```  
  
## <a name="parameters"></a><span data-ttu-id="06155-105">參數</span><span class="sxs-lookup"><span data-stu-id="06155-105">Parameters</span></span>  
  
|<span data-ttu-id="06155-106">參數</span><span class="sxs-lookup"><span data-stu-id="06155-106">Parameter</span></span>|<span data-ttu-id="06155-107">說明</span><span class="sxs-lookup"><span data-stu-id="06155-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="06155-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="06155-108">Return Value</span></span>  
 <span data-ttu-id="06155-109">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="06155-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06155-110">需求</span><span class="sxs-lookup"><span data-stu-id="06155-110">Requirements</span></span>  
 <span data-ttu-id="06155-111">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="06155-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06155-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="06155-112">See also</span></span>

- [<span data-ttu-id="06155-113">ISymUnmanagedAsyncMethodPropertiesWriter 介面</span><span class="sxs-lookup"><span data-stu-id="06155-113">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](isymunmanagedasyncmethodpropertieswriter-interface.md)
