---
title: IEnumRAWINPUTDEVIC:Clone
ms.date: 03/30/2017
helpviewer_keywords:
- Clone method [WPF]
ms.assetid: 2a6a1900-aa55-45fa-9382-241d569a2dc4
ms.openlocfilehash: da089e5342e641ffebe22ca6a4a593f97faeb89c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545335"
---
# <a name="ienumrawinputdevicclone"></a><span data-ttu-id="ae5b7-102">IEnumRAWINPUTDEVIC:Clone</span><span class="sxs-lookup"><span data-stu-id="ae5b7-102">IEnumRAWINPUTDEVIC:Clone</span></span>
<span data-ttu-id="ae5b7-103">使用與目前列舉程式相同的狀態，來建立另一個未經處理的輸入裝置列舉程式，以反覆查看相同的清單。</span><span class="sxs-lookup"><span data-stu-id="ae5b7-103">Creates another raw input device enumerator with the same state as the current enumerator to iterate over the same list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae5b7-104">語法</span><span class="sxs-lookup"><span data-stu-id="ae5b7-104">Syntax</span></span>  
  
```  
HRESULT Clone( [out] IEnumRAWINPUTDEVICE **ppenum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ae5b7-105">參數</span><span class="sxs-lookup"><span data-stu-id="ae5b7-105">Parameters</span></span>  
 `ppenum`  
  
 <span data-ttu-id="ae5b7-106">[out]收到的輸出變數的位址[IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md)介面指標。</span><span class="sxs-lookup"><span data-stu-id="ae5b7-106">[out] Address of output variable that receives the [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) interface pointer.</span></span> <span data-ttu-id="ae5b7-107">如果此方法不成功，這個輸出變數的值未定義。</span><span class="sxs-lookup"><span data-stu-id="ae5b7-107">If the method is unsuccessful, the value of this output variable is undefined.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="ae5b7-108">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="ae5b7-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="ae5b7-109">HRESULT： 這個方法支援標準傳回值 E_INVALIDARG、 E_OUTOFMEMORY，以及 E_UNEXPECTED。</span><span class="sxs-lookup"><span data-stu-id="ae5b7-109">HRESULT: This method supports the standard return values E_INVALIDARG, E_OUTOFMEMORY, and E_UNEXPECTED.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae5b7-110">備註</span><span class="sxs-lookup"><span data-stu-id="ae5b7-110">Remarks</span></span>  
 <span data-ttu-id="ae5b7-111">這個方法可將列舉序列中記錄點，以便在稍後返回該點。</span><span class="sxs-lookup"><span data-stu-id="ae5b7-111">This method makes it possible to record a point in the enumeration sequence in order to return to that point at a later time.</span></span> <span data-ttu-id="ae5b7-112">呼叫端必須釋放這個新的列舉值，分別從第一個列舉值。</span><span class="sxs-lookup"><span data-stu-id="ae5b7-112">The caller must release this new enumerator separately from the first enumerator.</span></span>
