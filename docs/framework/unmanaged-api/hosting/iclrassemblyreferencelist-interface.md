---
title: ICLRAssemblyReferenceList 介面
ms.date: 03/30/2017
api_name:
- ICLRAssemblyReferenceList
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyReferenceList
helpviewer_keywords:
- ICLRAssemblyReferenceList interface [.NET Framework hosting]
ms.assetid: 5f890fdf-d22a-429e-a35f-135273d1a636
topic_type:
- apiref
ms.openlocfilehash: f1aa40ef868bf6ff7730e01ab66a6fec58af1196
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615874"
---
# <a name="iclrassemblyreferencelist-interface"></a><span data-ttu-id="c7517-102">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="c7517-102">ICLRAssemblyReferenceList Interface</span></span>
<span data-ttu-id="c7517-103">管理通用語言執行時間（CLR）載入的元件清單，而不是由主機所載入。</span><span class="sxs-lookup"><span data-stu-id="c7517-103">Manages a list of assemblies that are loaded by the common language runtime (CLR) and not by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c7517-104">方法</span><span class="sxs-lookup"><span data-stu-id="c7517-104">Methods</span></span>  
  
|<span data-ttu-id="c7517-105">方法</span><span class="sxs-lookup"><span data-stu-id="c7517-105">Method</span></span>|<span data-ttu-id="c7517-106">描述</span><span class="sxs-lookup"><span data-stu-id="c7517-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c7517-107">IsAssemblyReferenceInList 方法</span><span class="sxs-lookup"><span data-stu-id="c7517-107">IsAssemblyReferenceInList Method</span></span>](iclrassemblyreferencelist-isassemblyreferenceinlist-method.md)|<span data-ttu-id="c7517-108">取得值，指出提供的指標是否參考清單中的元件。</span><span class="sxs-lookup"><span data-stu-id="c7517-108">Gets a value that indicates whether the supplied pointer references an assembly in the list.</span></span>|  
|[<span data-ttu-id="c7517-109">IsStringAssemblyReferenceInList 方法</span><span class="sxs-lookup"><span data-stu-id="c7517-109">IsStringAssemblyReferenceInList Method</span></span>](iclrassemblyreferencelist-isstringassemblyreferenceinlist-method.md)|<span data-ttu-id="c7517-110">取得值，指出提供的名稱是否符合清單中元件的名稱。</span><span class="sxs-lookup"><span data-stu-id="c7517-110">Gets a value that indicates whether the supplied name matches the name of an assembly in the list.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c7517-111">備註</span><span class="sxs-lookup"><span data-stu-id="c7517-111">Remarks</span></span>  
 <span data-ttu-id="c7517-112">呼叫[ICLRAssemblyIdentityManager：： GetCLRAssemblyReferenceList](iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md)方法，以取得實例的指標 `ICLRAssemblyReferenceList` 。</span><span class="sxs-lookup"><span data-stu-id="c7517-112">Call the [ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList](iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md) method to get a pointer to an instance of `ICLRAssemblyReferenceList`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7517-113">需求</span><span class="sxs-lookup"><span data-stu-id="c7517-113">Requirements</span></span>  
 <span data-ttu-id="c7517-114">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c7517-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7517-115">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="c7517-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c7517-116">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="c7517-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c7517-117">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7517-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7517-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c7517-118">See also</span></span>

- [<span data-ttu-id="c7517-119">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="c7517-119">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="c7517-120">IHostAssemblyStore 介面</span><span class="sxs-lookup"><span data-stu-id="c7517-120">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
- [<span data-ttu-id="c7517-121">裝載介面</span><span class="sxs-lookup"><span data-stu-id="c7517-121">Hosting Interfaces</span></span>](hosting-interfaces.md)
