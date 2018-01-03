---
title: "IInstallReferenceEnum 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IInstallReferenceEnum
api_location: fusion.dll
api_type: COM
f1_keywords: IInstallReferenceEnum
helpviewer_keywords: IInstallReferenceEnum interface [.NET Framework fusion]
ms.assetid: 2863b33b-a541-462c-bbe8-702a2832898e
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2f1a80d1d79fce952a7071abd5e435604824d00e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iinstallreferenceenum-interface"></a><span data-ttu-id="8e69a-102">IInstallReferenceEnum 介面</span><span class="sxs-lookup"><span data-stu-id="8e69a-102">IInstallReferenceEnum Interface</span></span>
<span data-ttu-id="8e69a-103">代表安裝在全域組件快取的參考組件的列舉值。</span><span class="sxs-lookup"><span data-stu-id="8e69a-103">Represents an enumerator for the referenced assemblies installed in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e69a-104">語法</span><span class="sxs-lookup"><span data-stu-id="8e69a-104">Syntax</span></span>  
  
```  
interface IInstallReferenceEnum : IUnknown {  
    HRESULT GetNextInstallReferenceItem (  
        [out] IInstallReferenceItem **ppRefItem,  
        [in]  DWORD dwFlags,  
        [in]  LPVOID pvReserved  
    );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="8e69a-105">方法</span><span class="sxs-lookup"><span data-stu-id="8e69a-105">Methods</span></span>  
  
|<span data-ttu-id="8e69a-106">方法</span><span class="sxs-lookup"><span data-stu-id="8e69a-106">Method</span></span>|<span data-ttu-id="8e69a-107">描述</span><span class="sxs-lookup"><span data-stu-id="8e69a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8e69a-108">GetNextInstallReferenceItem 方法</span><span class="sxs-lookup"><span data-stu-id="8e69a-108">GetNextInstallReferenceItem Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-getnextinstallreferenceitem-method.md)|<span data-ttu-id="8e69a-109">取得下一個指標`IInstallReferenceItem`包含在這個`IInstallReferenceEnum`。</span><span class="sxs-lookup"><span data-stu-id="8e69a-109">Gets a pointer to the next `IInstallReferenceItem` contained in this `IInstallReferenceEnum`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8e69a-110">需求</span><span class="sxs-lookup"><span data-stu-id="8e69a-110">Requirements</span></span>  
 <span data-ttu-id="8e69a-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8e69a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e69a-112">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="8e69a-112">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="8e69a-113">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e69a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e69a-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="8e69a-114">See Also</span></span>  
 [<span data-ttu-id="8e69a-115">融合介面</span><span class="sxs-lookup"><span data-stu-id="8e69a-115">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="8e69a-116">IInstallReferenceItem 介面</span><span class="sxs-lookup"><span data-stu-id="8e69a-116">IInstallReferenceItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)
