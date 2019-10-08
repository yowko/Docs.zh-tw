---
title: GetCustomUI
ms.date: 03/30/2017
helpviewer_keywords:
- custom error messages [WPF]
ms.assetid: e55180fc-35bb-4f80-a136-772b5eb3e4e5
ms.openlocfilehash: e9ef32912c2afb3c99e46e1e14bb3daa5a2e99af
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005705"
---
# <a name="getcustomui"></a><span data-ttu-id="cf3cd-102">GetCustomUI</span><span class="sxs-lookup"><span data-stu-id="cf3cd-102">GetCustomUI</span></span>
<span data-ttu-id="cf3cd-103">由 Presentationhost.exe 呼叫，以從主機取得自訂進度和錯誤訊息（如果已執行）。</span><span class="sxs-lookup"><span data-stu-id="cf3cd-103">Called by PresentationHost.exe to get custom progress and error messages from the host, if implemented.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf3cd-104">語法</span><span class="sxs-lookup"><span data-stu-id="cf3cd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCustomUI( [out] BSTR* pwzProgressAssemblyName, [out] BSTR* pwzProgressClassName, [out] BSTR* pwzErrorAssemblyName, [out] BSTR* pwzErrorClassName );  
```  
  
## <a name="parameters"></a><span data-ttu-id="cf3cd-105">參數</span><span class="sxs-lookup"><span data-stu-id="cf3cd-105">Parameters</span></span>  
 `pwzProgressAssemblyName`  
  
 <span data-ttu-id="cf3cd-106">脫銷元件的指標，其中包含主機提供的進度使用者介面。</span><span class="sxs-lookup"><span data-stu-id="cf3cd-106">[out] A pointer to the assembly that contains the host-supplied progress user interface.</span></span>  
  
 `pwzProgressClassName`  
  
 <span data-ttu-id="cf3cd-107">脫銷屬於主機提供的進度使用者介面的類別名稱，最好是具有 <xref:System.Windows.Controls.Page> 的 XAML 檔案是其最上層元素。</span><span class="sxs-lookup"><span data-stu-id="cf3cd-107">[out] The name of the class that is the host-supplied progress user interface, preferably a XAML file with <xref:System.Windows.Controls.Page> is its top-level element.</span></span> <span data-ttu-id="cf3cd-108">這個類別位於 `pwzProgressAssemblyName` 所指定的元件中。</span><span class="sxs-lookup"><span data-stu-id="cf3cd-108">This class resides in the assembly that is specified by `pwzProgressAssemblyName`.</span></span>  
  
 `pwzErrorAssemblyName`  
  
 <span data-ttu-id="cf3cd-109">脫銷包含主機提供的錯誤使用者介面之元件的指標。</span><span class="sxs-lookup"><span data-stu-id="cf3cd-109">[out] A pointer to the assembly that contains the host-supplied error user interface.</span></span>  
  
 `pwzErrorClassName`  
  
 <span data-ttu-id="cf3cd-110">脫銷屬於主機提供的錯誤使用者介面之類別的名稱，最好是具有 <xref:System.Windows.Controls.Page> 的 XAML 檔案是其最上層元素。</span><span class="sxs-lookup"><span data-stu-id="cf3cd-110">[out] The name of the class that is the host-supplied error user interface, preferably a XAML file with <xref:System.Windows.Controls.Page> is its top-level element.</span></span> <span data-ttu-id="cf3cd-111">這個類別位於 `pwzErrorAssemblyName` 所指定的元件中。</span><span class="sxs-lookup"><span data-stu-id="cf3cd-111">This class resides in the assembly that is specified by `pwzErrorAssemblyName`.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="cf3cd-112">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="cf3cd-112">Property Value/Return Value</span></span>  
 <span data-ttu-id="cf3cd-113">HRESULT:忽略。</span><span class="sxs-lookup"><span data-stu-id="cf3cd-113">HRESULT: Ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cf3cd-114">備註</span><span class="sxs-lookup"><span data-stu-id="cf3cd-114">Remarks</span></span>  
 <span data-ttu-id="cf3cd-115">主應用程式可能有特定主題，Presentationhost.exe .exe 的預設使用者介面可能不符合。</span><span class="sxs-lookup"><span data-stu-id="cf3cd-115">A host application may have a specific theme that PresentationHost.exe’s default user interfaces may not conform to.</span></span> <span data-ttu-id="cf3cd-116">如果是這種情況，主應用程式可以執行[GetCustomUI](getcustomui.md) ，將進度和錯誤使用者介面傳回 presentationhost.exe。</span><span class="sxs-lookup"><span data-stu-id="cf3cd-116">If this is the case, the host application can implement [GetCustomUI](getcustomui.md) to return progress and error user interfaces to PresentationHost.exe.</span></span> <span data-ttu-id="cf3cd-117">Presentationhost.exe 在使用其預設的使用者介面之前，一律會呼叫[GetCustomUI](getcustomui.md) 。</span><span class="sxs-lookup"><span data-stu-id="cf3cd-117">PresentationHost.exe will always call [GetCustomUI](getcustomui.md) before using its default user interfaces.</span></span>  
  
 <span data-ttu-id="cf3cd-118">在 Presentationhost.exe 的初始化期間，會呼叫這個函式一次。</span><span class="sxs-lookup"><span data-stu-id="cf3cd-118">This function is called once during PresentationHost’s initialization.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf3cd-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cf3cd-119">See also</span></span>

- [<span data-ttu-id="cf3cd-120">IWpfHostSupport</span><span class="sxs-lookup"><span data-stu-id="cf3cd-120">IWpfHostSupport</span></span>](iwpfhostsupport.md)
