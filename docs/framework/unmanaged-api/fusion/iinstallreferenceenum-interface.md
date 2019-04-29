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
ms.openlocfilehash: 35faeb69e864a428dc40394ad89a7d50b95bbcab
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61757660"
---
# <a name="iinstallreferenceenum-interface"></a><span data-ttu-id="4ece7-102">IInstallReferenceEnum 介面</span><span class="sxs-lookup"><span data-stu-id="4ece7-102">IInstallReferenceEnum Interface</span></span>
<span data-ttu-id="4ece7-103">表示參考的組件安裝在全域組件快取的列舉值。</span><span class="sxs-lookup"><span data-stu-id="4ece7-103">Represents an enumerator for the referenced assemblies installed in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ece7-104">語法</span><span class="sxs-lookup"><span data-stu-id="4ece7-104">Syntax</span></span>  
  
```  
interface IInstallReferenceEnum : IUnknown {  
    HRESULT GetNextInstallReferenceItem (  
        [out] IInstallReferenceItem **ppRefItem,  
        [in]  DWORD dwFlags,  
        [in]  LPVOID pvReserved  
    );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="4ece7-105">方法</span><span class="sxs-lookup"><span data-stu-id="4ece7-105">Methods</span></span>  
  
|<span data-ttu-id="4ece7-106">方法</span><span class="sxs-lookup"><span data-stu-id="4ece7-106">Method</span></span>|<span data-ttu-id="4ece7-107">描述</span><span class="sxs-lookup"><span data-stu-id="4ece7-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4ece7-108">GetNextInstallReferenceItem 方法</span><span class="sxs-lookup"><span data-stu-id="4ece7-108">GetNextInstallReferenceItem Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-getnextinstallreferenceitem-method.md)|<span data-ttu-id="4ece7-109">取得下一個指標`IInstallReferenceItem`包含在此`IInstallReferenceEnum`。</span><span class="sxs-lookup"><span data-stu-id="4ece7-109">Gets a pointer to the next `IInstallReferenceItem` contained in this `IInstallReferenceEnum`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4ece7-110">需求</span><span class="sxs-lookup"><span data-stu-id="4ece7-110">Requirements</span></span>  
 <span data-ttu-id="4ece7-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4ece7-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ece7-112">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="4ece7-112">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="4ece7-113">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ece7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ece7-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4ece7-114">See also</span></span>

- [<span data-ttu-id="4ece7-115">融合介面</span><span class="sxs-lookup"><span data-stu-id="4ece7-115">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [<span data-ttu-id="4ece7-116">IInstallReferenceItem 介面</span><span class="sxs-lookup"><span data-stu-id="4ece7-116">IInstallReferenceItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)
