---
title: IInstallReferenceEnum 介面
ms.date: 03/30/2017
api_name:
- IInstallReferenceEnum
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IInstallReferenceEnum
helpviewer_keywords:
- IInstallReferenceEnum interface [.NET Framework fusion]
ms.assetid: 2863b33b-a541-462c-bbe8-702a2832898e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5781254b508887f2e76f6ca0eca6a2830ada172b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774011"
---
# <a name="iinstallreferenceenum-interface"></a><span data-ttu-id="24cad-102">IInstallReferenceEnum 介面</span><span class="sxs-lookup"><span data-stu-id="24cad-102">IInstallReferenceEnum Interface</span></span>
<span data-ttu-id="24cad-103">表示參考的組件安裝在全域組件快取的列舉值。</span><span class="sxs-lookup"><span data-stu-id="24cad-103">Represents an enumerator for the referenced assemblies installed in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24cad-104">語法</span><span class="sxs-lookup"><span data-stu-id="24cad-104">Syntax</span></span>  
  
```cpp  
interface IInstallReferenceEnum : IUnknown {  
    HRESULT GetNextInstallReferenceItem (  
        [out] IInstallReferenceItem **ppRefItem,  
        [in]  DWORD dwFlags,  
        [in]  LPVOID pvReserved  
    );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="24cad-105">方法</span><span class="sxs-lookup"><span data-stu-id="24cad-105">Methods</span></span>  
  
|<span data-ttu-id="24cad-106">方法</span><span class="sxs-lookup"><span data-stu-id="24cad-106">Method</span></span>|<span data-ttu-id="24cad-107">說明</span><span class="sxs-lookup"><span data-stu-id="24cad-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="24cad-108">GetNextInstallReferenceItem 方法</span><span class="sxs-lookup"><span data-stu-id="24cad-108">GetNextInstallReferenceItem Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-getnextinstallreferenceitem-method.md)|<span data-ttu-id="24cad-109">取得下一個指標`IInstallReferenceItem`包含在此`IInstallReferenceEnum`。</span><span class="sxs-lookup"><span data-stu-id="24cad-109">Gets a pointer to the next `IInstallReferenceItem` contained in this `IInstallReferenceEnum`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="24cad-110">需求</span><span class="sxs-lookup"><span data-stu-id="24cad-110">Requirements</span></span>  
 <span data-ttu-id="24cad-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="24cad-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24cad-112">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="24cad-112">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="24cad-113">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24cad-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24cad-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="24cad-114">See also</span></span>

- [<span data-ttu-id="24cad-115">融合介面</span><span class="sxs-lookup"><span data-stu-id="24cad-115">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [<span data-ttu-id="24cad-116">IInstallReferenceItem 介面</span><span class="sxs-lookup"><span data-stu-id="24cad-116">IInstallReferenceItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)
