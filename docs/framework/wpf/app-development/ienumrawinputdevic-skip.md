---
title: IEnumRAWINPUTDEVIC:Skip
ms.date: 03/30/2017
helpviewer_keywords:
- Skip method [WPF]
ms.assetid: c967b0f8-1c6a-459c-8c16-d4f08918ab65
ms.openlocfilehash: f7d7df77c54d4551025aa5a344c96083c263f455
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61949756"
---
# <a name="ienumrawinputdevicskip"></a><span data-ttu-id="43300-102">IEnumRAWINPUTDEVIC:Skip</span><span class="sxs-lookup"><span data-stu-id="43300-102">IEnumRAWINPUTDEVIC:Skip</span></span>
<span data-ttu-id="43300-103">指示列舉程式略過下一個`celt`列舉中的項目，因此下次呼叫[IEnumRAWINPUTDEVIC:Next](ienumrawinputdevic-next.md)將不會傳回這些項目。</span><span class="sxs-lookup"><span data-stu-id="43300-103">Instructs the enumerator to skip the next `celt` elements in the enumeration so that the next call to [IEnumRAWINPUTDEVIC:Next](ienumrawinputdevic-next.md) will not return those elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43300-104">語法</span><span class="sxs-lookup"><span data-stu-id="43300-104">Syntax</span></span>  
  
```  
HRESULT Skip( [in] ULONG celt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="43300-105">參數</span><span class="sxs-lookup"><span data-stu-id="43300-105">Parameters</span></span>  
 `celt`  
  
 <span data-ttu-id="43300-106">[in]略過的項目數目。</span><span class="sxs-lookup"><span data-stu-id="43300-106">[in] Number of elements to be skipped.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="43300-107">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="43300-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="43300-108">HRESULT:如果提供的項目數目，為 S_OK `celt`;否則為 S_FALSE。</span><span class="sxs-lookup"><span data-stu-id="43300-108">HRESULT: S_OK if the number of elements supplied is `celt`; S_FALSE otherwise.</span></span>
