---
title: GetCustomUI
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom error messages [WPF]
ms.assetid: e55180fc-35bb-4f80-a136-772b5eb3e4e5
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 88c2873a5929e25335b0c6ef64f8121e31177ab4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="getcustomui"></a><span data-ttu-id="ed703-102">GetCustomUI</span><span class="sxs-lookup"><span data-stu-id="ed703-102">GetCustomUI</span></span>
<span data-ttu-id="ed703-103">如果實作，呼叫 PresentationHost.exe 從主機上，取得自訂的進度和錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="ed703-103">Called by PresentationHost.exe to get custom progress and error messages from the host, if implemented.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed703-104">語法</span><span class="sxs-lookup"><span data-stu-id="ed703-104">Syntax</span></span>  
  
```  
HRESULT GetCustomUI( [out] BSTR* pwzProgressAssemblyName, [out] BSTR* pwzProgressClassName, [out] BSTR* pwzErrorAssemblyName, [out] BSTR* pwzErrorClassName );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ed703-105">參數</span><span class="sxs-lookup"><span data-stu-id="ed703-105">Parameters</span></span>  
 `pwzProgressAssemblyName`  
  
 <span data-ttu-id="ed703-106">[out]指標，包含主機提供進度使用者介面的組件。</span><span class="sxs-lookup"><span data-stu-id="ed703-106">[out] A pointer to the assembly that contains the host-supplied progress user interface.</span></span>  
  
 `pwzProgressClassName`  
  
 <span data-ttu-id="ed703-107">[out]最好是主機提供進度使用者介面、 類別名稱[!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]檔案搭配<xref:System.Windows.Controls.Page>是其最上層元素。</span><span class="sxs-lookup"><span data-stu-id="ed703-107">[out] The name of the class that is the host-supplied progress user interface, preferably a [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] file with <xref:System.Windows.Controls.Page> is its top-level element.</span></span> <span data-ttu-id="ed703-108">這個類別位於所指定的組件`pwzProgressAssemblyName`。</span><span class="sxs-lookup"><span data-stu-id="ed703-108">This class resides in the assembly that is specified by `pwzProgressAssemblyName`.</span></span>  
  
 `pwzErrorAssemblyName`  
  
 <span data-ttu-id="ed703-109">[out]指標，包含主機提供的錯誤使用者介面的組件。</span><span class="sxs-lookup"><span data-stu-id="ed703-109">[out] A pointer to the assembly that contains the host-supplied error user interface.</span></span>  
  
 `pwzErrorClassName`  
  
 <span data-ttu-id="ed703-110">[out]為主機提供的錯誤使用者類別的名稱介面，最好是使用 XAML 檔案<xref:System.Windows.Controls.Page>是其最上層元素。</span><span class="sxs-lookup"><span data-stu-id="ed703-110">[out] The name of the class that is the host-supplied error user interface, preferably a XAML file with <xref:System.Windows.Controls.Page> is its top-level element.</span></span> <span data-ttu-id="ed703-111">這個類別位於所指定的組件`pwzErrorAssemblyName`。</span><span class="sxs-lookup"><span data-stu-id="ed703-111">This class resides in the assembly that is specified by `pwzErrorAssemblyName`.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="ed703-112">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="ed703-112">Property Value/Return Value</span></span>  
 <span data-ttu-id="ed703-113">HRESULT： 忽略。</span><span class="sxs-lookup"><span data-stu-id="ed703-113">HRESULT: Ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ed703-114">備註</span><span class="sxs-lookup"><span data-stu-id="ed703-114">Remarks</span></span>  
 <span data-ttu-id="ed703-115">主應用程式可能 PresentationHost.exe 的預設使用者介面可能不符合特定主題。</span><span class="sxs-lookup"><span data-stu-id="ed703-115">A host application may have a specific theme that PresentationHost.exe’s default user interfaces may not conform to.</span></span> <span data-ttu-id="ed703-116">如果這種情況，主應用程式可以實作[GetCustomUI](../../../../docs/framework/wpf/app-development/getcustomui.md)回到進度和錯誤的使用者介面 PresentationHost.exe。</span><span class="sxs-lookup"><span data-stu-id="ed703-116">If this is the case, the host application can implement [GetCustomUI](../../../../docs/framework/wpf/app-development/getcustomui.md) to return progress and error user interfaces to PresentationHost.exe.</span></span> <span data-ttu-id="ed703-117">一定會呼叫 PresentationHost.exe [GetCustomUI](../../../../docs/framework/wpf/app-development/getcustomui.md)才能使用其預設使用者介面。</span><span class="sxs-lookup"><span data-stu-id="ed703-117">PresentationHost.exe will always call [GetCustomUI](../../../../docs/framework/wpf/app-development/getcustomui.md) before using its default user interfaces.</span></span>  
  
 <span data-ttu-id="ed703-118">一次 PresentationHost 的初始化期間，會呼叫此函式。</span><span class="sxs-lookup"><span data-stu-id="ed703-118">This function is called once during PresentationHost’s initialization.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed703-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="ed703-119">See Also</span></span>  
 [<span data-ttu-id="ed703-120">IWpfHostSupport</span><span class="sxs-lookup"><span data-stu-id="ed703-120">IWpfHostSupport</span></span>](../../../../docs/framework/wpf/app-development/iwpfhostsupport.md)
