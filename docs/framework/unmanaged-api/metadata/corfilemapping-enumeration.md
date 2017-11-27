---
title: "CorFileMapping 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorFileMapping
api_location: mscoree.dll
api_type: COM
f1_keywords: CorFileMapping
helpviewer_keywords: CorFileMapping enumeration [.NET Framework metadata]
ms.assetid: 3ca41592-b8da-475a-8032-a15627730003
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6736f154ef6b03c0bfe34d16a419955324316273
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="corfilemapping-enumeration"></a><span data-ttu-id="09cb0-102">CorFileMapping 列舉</span><span class="sxs-lookup"><span data-stu-id="09cb0-102">CorFileMapping Enumeration</span></span>
<span data-ttu-id="09cb0-103">包含描述的檔案會從呼叫傳回的對應型別值[imetadatainfo:: Getfilemapping](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="09cb0-103">Contains values that describe the type of file mapping that is returned from a call to the [IMetaDataInfo::GetFileMapping](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09cb0-104">語法</span><span class="sxs-lookup"><span data-stu-id="09cb0-104">Syntax</span></span>  
  
```  
typedef enum CorFileMapping {  
  
    fmFlat                  =   0x0000,  
    fmExecutableImage       =   0x0001  
  
} CorFileMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="09cb0-105">成員</span><span class="sxs-lookup"><span data-stu-id="09cb0-105">Members</span></span>  
  
|<span data-ttu-id="09cb0-106">成員</span><span class="sxs-lookup"><span data-stu-id="09cb0-106">Member</span></span>|<span data-ttu-id="09cb0-107">說明</span><span class="sxs-lookup"><span data-stu-id="09cb0-107">Description</span></span>|  
|------------|-----------------|  
|`fmFlat`|<span data-ttu-id="09cb0-108">做為資料檔對應檔。</span><span class="sxs-lookup"><span data-stu-id="09cb0-108">The file is mapped as a data file.</span></span> <span data-ttu-id="09cb0-109">也就是說，`SEC_IMAGE`旗標不傳遞至 Microsoft Win32`CreateFileMapping`函式。</span><span class="sxs-lookup"><span data-stu-id="09cb0-109">That is, the `SEC_IMAGE` flag was not passed to the Microsoft Win32 `CreateFileMapping` function.</span></span>|  
|`fmExecutableImage`|<span data-ttu-id="09cb0-110">對於執行，使用對應檔`LoadLibrary`函式或`CreateFileMapping`函式與`SEC_IMAGE`旗標。</span><span class="sxs-lookup"><span data-stu-id="09cb0-110">The file is mapped for execution, by using either the `LoadLibrary` function or the `CreateFileMapping` function with the `SEC_IMAGE` flag.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="09cb0-111">需求</span><span class="sxs-lookup"><span data-stu-id="09cb0-111">Requirements</span></span>  
 <span data-ttu-id="09cb0-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="09cb0-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09cb0-113">**標頭：** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="09cb0-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="09cb0-114">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09cb0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09cb0-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="09cb0-115">See Also</span></span>  
 [<span data-ttu-id="09cb0-116">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="09cb0-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)  
 [<span data-ttu-id="09cb0-117">GetFileMapping 方法</span><span class="sxs-lookup"><span data-stu-id="09cb0-117">GetFileMapping Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md)
