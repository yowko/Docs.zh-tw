---
title: ISymUnmanagedAsyncMethod::GetKickoffMethod 方法
ms.date: 03/30/2017
ms.assetid: ba084444-9e68-4cde-9388-54b950670987
ms.openlocfilehash: 879b9eac7cb6df06ffe4f994b505ea9cb2396d7f
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441834"
---
# <a name="isymunmanagedasyncmethodgetkickoffmethod-method"></a><span data-ttu-id="79e14-102">ISymUnmanagedAsyncMethod::GetKickoffMethod 方法</span><span class="sxs-lookup"><span data-stu-id="79e14-102">ISymUnmanagedAsyncMethod::GetKickoffMethod Method</span></span>
<span data-ttu-id="79e14-103">請參閱[DefineKickoffMethod 方法](isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md)。</span><span class="sxs-lookup"><span data-stu-id="79e14-103">See [DefineKickoffMethod Method](isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79e14-104">語法</span><span class="sxs-lookup"><span data-stu-id="79e14-104">Syntax</span></span>  
  
```idl  
HRESULT GetKickoffMethod(    [out, retval] mdToken* kickoffMethod);  
```  
  
## <a name="parameters"></a><span data-ttu-id="79e14-105">參數</span><span class="sxs-lookup"><span data-stu-id="79e14-105">Parameters</span></span>  
  
|<span data-ttu-id="79e14-106">參數</span><span class="sxs-lookup"><span data-stu-id="79e14-106">Parameter</span></span>|<span data-ttu-id="79e14-107">說明</span><span class="sxs-lookup"><span data-stu-id="79e14-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="79e14-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="79e14-108">Return Value</span></span>  
 <span data-ttu-id="79e14-109">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="79e14-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79e14-110">需求</span><span class="sxs-lookup"><span data-stu-id="79e14-110">Requirements</span></span>  
 <span data-ttu-id="79e14-111">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="79e14-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79e14-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="79e14-112">See also</span></span>

- [<span data-ttu-id="79e14-113">ISymUnmanagedAsyncMethod 介面</span><span class="sxs-lookup"><span data-stu-id="79e14-113">ISymUnmanagedAsyncMethod Interface</span></span>](isymunmanagedasyncmethod-interface.md)
