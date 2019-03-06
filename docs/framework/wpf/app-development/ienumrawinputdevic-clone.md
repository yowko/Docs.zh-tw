---
title: IEnumRAWINPUTDEVIC:Clone
ms.date: 03/30/2017
helpviewer_keywords:
- Clone method [WPF]
ms.assetid: 2a6a1900-aa55-45fa-9382-241d569a2dc4
ms.openlocfilehash: a4c5e7db813089d1dd138416ac54dd4be467b87b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57355013"
---
# <a name="ienumrawinputdevicclone"></a><span data-ttu-id="d1dc3-102">IEnumRAWINPUTDEVIC:Clone</span><span class="sxs-lookup"><span data-stu-id="d1dc3-102">IEnumRAWINPUTDEVIC:Clone</span></span>
<span data-ttu-id="d1dc3-103">使用與目前列舉程式相同的狀態，來建立另一個未經處理的輸入裝置列舉程式，以反覆查看相同的清單。</span><span class="sxs-lookup"><span data-stu-id="d1dc3-103">Creates another raw input device enumerator with the same state as the current enumerator to iterate over the same list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1dc3-104">語法</span><span class="sxs-lookup"><span data-stu-id="d1dc3-104">Syntax</span></span>  
  
```  
HRESULT Clone( [out] IEnumRAWINPUTDEVICE **ppenum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d1dc3-105">參數</span><span class="sxs-lookup"><span data-stu-id="d1dc3-105">Parameters</span></span>  
 `ppenum`  
  
 <span data-ttu-id="d1dc3-106">[out]收到的輸出變數位址[IEnumRAWINPUTDEVICE](ienumrawinputdevice.md)介面指標。</span><span class="sxs-lookup"><span data-stu-id="d1dc3-106">[out] Address of output variable that receives the [IEnumRAWINPUTDEVICE](ienumrawinputdevice.md) interface pointer.</span></span> <span data-ttu-id="d1dc3-107">如果方法不成功，這個輸出變數的值會是未定義。</span><span class="sxs-lookup"><span data-stu-id="d1dc3-107">If the method is unsuccessful, the value of this output variable is undefined.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="d1dc3-108">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="d1dc3-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="d1dc3-109">HRESULT:這個方法支援標準傳回值 E_INVALIDARG、 E_OUTOFMEMORY，以及 E_UNEXPECTED。</span><span class="sxs-lookup"><span data-stu-id="d1dc3-109">HRESULT: This method supports the standard return values E_INVALIDARG, E_OUTOFMEMORY, and E_UNEXPECTED.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d1dc3-110">備註</span><span class="sxs-lookup"><span data-stu-id="d1dc3-110">Remarks</span></span>  
 <span data-ttu-id="d1dc3-111">這個方法可讓您能夠記錄列舉序列中的點，才能在稍後返回該時間點。</span><span class="sxs-lookup"><span data-stu-id="d1dc3-111">This method makes it possible to record a point in the enumeration sequence in order to return to that point at a later time.</span></span> <span data-ttu-id="d1dc3-112">呼叫端必須釋放這個新的列舉值，分別從第一個列舉值。</span><span class="sxs-lookup"><span data-stu-id="d1dc3-112">The caller must release this new enumerator separately from the first enumerator.</span></span>
