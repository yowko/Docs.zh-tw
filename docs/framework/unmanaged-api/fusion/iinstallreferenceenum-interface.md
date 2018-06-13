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
ms.openlocfilehash: cac9f9db0b7527a80671c825a4435e8ea2d135b8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429656"
---
# <a name="iinstallreferenceenum-interface"></a><span data-ttu-id="e316c-102">IInstallReferenceEnum 介面</span><span class="sxs-lookup"><span data-stu-id="e316c-102">IInstallReferenceEnum Interface</span></span>
<span data-ttu-id="e316c-103">代表安裝在全域組件快取的參考組件的列舉值。</span><span class="sxs-lookup"><span data-stu-id="e316c-103">Represents an enumerator for the referenced assemblies installed in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e316c-104">語法</span><span class="sxs-lookup"><span data-stu-id="e316c-104">Syntax</span></span>  
  
```  
interface IInstallReferenceEnum : IUnknown {  
    HRESULT GetNextInstallReferenceItem (  
        [out] IInstallReferenceItem **ppRefItem,  
        [in]  DWORD dwFlags,  
        [in]  LPVOID pvReserved  
    );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="e316c-105">方法</span><span class="sxs-lookup"><span data-stu-id="e316c-105">Methods</span></span>  
  
|<span data-ttu-id="e316c-106">方法</span><span class="sxs-lookup"><span data-stu-id="e316c-106">Method</span></span>|<span data-ttu-id="e316c-107">描述</span><span class="sxs-lookup"><span data-stu-id="e316c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e316c-108">GetNextInstallReferenceItem 方法</span><span class="sxs-lookup"><span data-stu-id="e316c-108">GetNextInstallReferenceItem Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-getnextinstallreferenceitem-method.md)|<span data-ttu-id="e316c-109">取得下一個指標`IInstallReferenceItem`包含在這個`IInstallReferenceEnum`。</span><span class="sxs-lookup"><span data-stu-id="e316c-109">Gets a pointer to the next `IInstallReferenceItem` contained in this `IInstallReferenceEnum`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e316c-110">需求</span><span class="sxs-lookup"><span data-stu-id="e316c-110">Requirements</span></span>  
 <span data-ttu-id="e316c-111">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e316c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e316c-112">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="e316c-112">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="e316c-113">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e316c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e316c-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e316c-114">See Also</span></span>  
 [<span data-ttu-id="e316c-115">融合介面</span><span class="sxs-lookup"><span data-stu-id="e316c-115">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="e316c-116">IInstallReferenceItem 介面</span><span class="sxs-lookup"><span data-stu-id="e316c-116">IInstallReferenceItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)
