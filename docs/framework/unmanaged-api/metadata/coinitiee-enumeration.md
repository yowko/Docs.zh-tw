---
title: "COINITIEE 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COINITIEE
api_location: mscoree.dll
api_type: COM
f1_keywords: COINITIEE
helpviewer_keywords: COINITIEE enumeration [.NET Framework metadata]
ms.assetid: 64264238-3b68-4bac-a887-36b552426a6c
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 03711186954aa24beff65e5d4d5b5e484c6dc276
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="coinitiee-enumeration"></a><span data-ttu-id="863d8-102">COINITIEE 列舉</span><span class="sxs-lookup"><span data-stu-id="863d8-102">COINITIEE Enumeration</span></span>
<span data-ttu-id="863d8-103">指定所使用的常數[CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md)初始化 common language runtime 時。</span><span class="sxs-lookup"><span data-stu-id="863d8-103">Specifies constants used by [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) when initializing the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="863d8-104">語法</span><span class="sxs-lookup"><span data-stu-id="863d8-104">Syntax</span></span>  
  
```  
typedef enum tagCOINITEE {  
   COINITEE_DEFAULT = 0x0,  
   COINITEE_DLL     = 0x1,  
   COINITEE_MAIN    = 0x2  
} COINITIEE;  
```  
  
## <a name="members"></a><span data-ttu-id="863d8-105">成員</span><span class="sxs-lookup"><span data-stu-id="863d8-105">Members</span></span>  
  
|<span data-ttu-id="863d8-106">成員</span><span class="sxs-lookup"><span data-stu-id="863d8-106">Member</span></span>|<span data-ttu-id="863d8-107">說明</span><span class="sxs-lookup"><span data-stu-id="863d8-107">Description</span></span>|  
|------------|-----------------|  
|`COINITEE_DEFAULT`|<span data-ttu-id="863d8-108">預設的初始化模式。</span><span class="sxs-lookup"><span data-stu-id="863d8-108">Default initialization mode.</span></span> <span data-ttu-id="863d8-109">這會初始化執行階段並建立預設<xref:System.AppDomain>。</span><span class="sxs-lookup"><span data-stu-id="863d8-109">This initializes the runtime and creates the default <xref:System.AppDomain>.</span></span>|  
|`COINITEE_DLL`|<span data-ttu-id="863d8-110">若要執行的 managed 的 DLL 的初始化。</span><span class="sxs-lookup"><span data-stu-id="863d8-110">Initializes to run a managed DLL.</span></span>|  
|`COINITEE_MAIN`|<span data-ttu-id="863d8-111">初始化執行受管理的 EXE。</span><span class="sxs-lookup"><span data-stu-id="863d8-111">Initializes to run a managed EXE.</span></span> <span data-ttu-id="863d8-112">此初始化執行階段，但不會建立預設<xref:System.AppDomain>，這輸入主常式中的可執行檔之後所建立。</span><span class="sxs-lookup"><span data-stu-id="863d8-112">This initializes the runtime but does not create the default <xref:System.AppDomain>, which is created after entering the main routine of the EXE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="863d8-113">需求</span><span class="sxs-lookup"><span data-stu-id="863d8-113">Requirements</span></span>  
 <span data-ttu-id="863d8-114">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="863d8-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="863d8-115">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="863d8-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="863d8-116">**程式庫：**包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="863d8-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="863d8-117">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="863d8-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="863d8-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="863d8-118">See Also</span></span>  
 [<span data-ttu-id="863d8-119">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="863d8-119">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
