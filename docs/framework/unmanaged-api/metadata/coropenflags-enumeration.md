---
title: CorOpenFlags 列舉
ms.date: 03/30/2017
api_name:
- CorOpenFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorOpenFlags
helpviewer_keywords:
- CorOpenFlags enumeration [.NET Framework metadata]
ms.assetid: e27a83b5-2698-4996-9032-1e0fed8b91ca
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6f231c4f9782518e30cbaa89c6b085c72aafcc92
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445441"
---
# <a name="coropenflags-enumeration"></a><span data-ttu-id="cb9d1-102">CorOpenFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="cb9d1-102">CorOpenFlags Enumeration</span></span>
<span data-ttu-id="cb9d1-103">包含在開啟資訊清單檔案時控制中繼資料行為的旗標值。</span><span class="sxs-lookup"><span data-stu-id="cb9d1-103">Contains flag values that control metadata behavior upon opening manifest files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb9d1-104">語法</span><span class="sxs-lookup"><span data-stu-id="cb9d1-104">Syntax</span></span>  
  
```  
typedef enum CorOpenFlags  
{  
    ofRead              =   0x00000000,  
    ofWrite             =   0x00000001,  
    ofReadWriteMask     =   0x00000001,  
    ofCopyMemory        =   0x00000002,  
    ofCacheImage        =   0x00000004,  
    ofManifestMetadata  =   0x00000008,  
    ofReadOnly          =   0x00000010,  
    ofTakeOwnership     =   0x00000020,  
    ofCacheImage        =   0x00000004,  
    ofNoTypeLib         =   0x00000080,  
    ofNoTransform       =   0x00001000,  
    ofReserved1         =   0x00000100,  
    ofReserved2         =   0x00000200,  
    ofReserved          =   0xffffff40  
} CorOpenFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="cb9d1-105">成員</span><span class="sxs-lookup"><span data-stu-id="cb9d1-105">Members</span></span>  
  
|<span data-ttu-id="cb9d1-106">成員</span><span class="sxs-lookup"><span data-stu-id="cb9d1-106">Member</span></span>|<span data-ttu-id="cb9d1-107">描述</span><span class="sxs-lookup"><span data-stu-id="cb9d1-107">Description</span></span>|  
|------------|-----------------|  
|`ofRead`|<span data-ttu-id="cb9d1-108">指出應將檔案開啟為僅供讀取。</span><span class="sxs-lookup"><span data-stu-id="cb9d1-108">Indicates that the file should be opened for reading only.</span></span>|  
|`ofWrite`|<span data-ttu-id="cb9d1-109">指出應將檔案開啟為可供寫入。</span><span class="sxs-lookup"><span data-stu-id="cb9d1-109">Indicates that the file should be opened for writing.</span></span><br /><br /> <span data-ttu-id="cb9d1-110">若您在開啟 .winmd 檔案時使用 `ofWrite` 旗標，也應該傳遞 `ofNoTransform` 旗標。</span><span class="sxs-lookup"><span data-stu-id="cb9d1-110">If you are using the `ofWrite` flag when opening a .winmd file, you should also pass the `ofNoTransform` flag.</span></span>|  
|`ofReadWriteMask`|<span data-ttu-id="cb9d1-111">讀取及寫入的遮罩。</span><span class="sxs-lookup"><span data-stu-id="cb9d1-111">A mask for reading and writing.</span></span>|  
|`ofCopyMemory`|<span data-ttu-id="cb9d1-112">指出應將檔案讀取至記憶體。</span><span class="sxs-lookup"><span data-stu-id="cb9d1-112">Indicates that the file should be read into memory.</span></span> <span data-ttu-id="cb9d1-113">中繼資料應保留其自己的複本。</span><span class="sxs-lookup"><span data-stu-id="cb9d1-113">Metadata should maintain its own copy.</span></span>|  
|`ofCacheImage`|<span data-ttu-id="cb9d1-114">已過時。</span><span class="sxs-lookup"><span data-stu-id="cb9d1-114">Obsolete.</span></span> <span data-ttu-id="cb9d1-115">會忽略此旗標。</span><span class="sxs-lookup"><span data-stu-id="cb9d1-115">This flag is ignored.</span></span>|  
|`ofManifestMetadata`|<span data-ttu-id="cb9d1-116">已過時。</span><span class="sxs-lookup"><span data-stu-id="cb9d1-116">Obsolete.</span></span> <span data-ttu-id="cb9d1-117">會忽略此旗標。</span><span class="sxs-lookup"><span data-stu-id="cb9d1-117">This flag is ignored.</span></span>|  
|`ofReadOnly`|<span data-ttu-id="cb9d1-118">指出應該開啟檔案進行讀取，且呼叫`QueryInterface`如[IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)無法進行。</span><span class="sxs-lookup"><span data-stu-id="cb9d1-118">Indicates that the file should be opened for reading, and that a call to `QueryInterface` for an [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) cannot be made.</span></span>|  
|`ofTakeOwnership`|<span data-ttu-id="cb9d1-119">指出使用的呼叫配置的記憶體[CoTaskMemAlloc](http://msdn.microsoft.com/library/c4cb588d-9482-4f90-a92e-75b604540d5c)和中繼資料，將會釋放。</span><span class="sxs-lookup"><span data-stu-id="cb9d1-119">Indicates that the memory was allocated using a call to [CoTaskMemAlloc](http://msdn.microsoft.com/library/c4cb588d-9482-4f90-a92e-75b604540d5c) and will be freed by the metadata.</span></span>|  
|`ofNoTypeLib`|<span data-ttu-id="cb9d1-120">已過時。</span><span class="sxs-lookup"><span data-stu-id="cb9d1-120">Obsolete.</span></span> <span data-ttu-id="cb9d1-121">會忽略此旗標。</span><span class="sxs-lookup"><span data-stu-id="cb9d1-121">This flag is ignored.</span></span>|  
|`ofNoTransform`|<span data-ttu-id="cb9d1-122">指出應停用 .winmd 檔案的自動轉換。</span><span class="sxs-lookup"><span data-stu-id="cb9d1-122">Indicates that automatic transforms of .winmd files should be disabled.</span></span> <span data-ttu-id="cb9d1-123">換言之，應停用 Windows 執行階段類型對 .NET Framework 類型的投影。</span><span class="sxs-lookup"><span data-stu-id="cb9d1-123">In other words, the projection of a Windows Runtime type to a .NET Framework type should be disabled.</span></span> <span data-ttu-id="cb9d1-124">如需詳細資訊，請參閱[.NET 和 Windows 執行階段與下面其實](http://msdn.microsoft.com/magazine/jj651569.aspx)。</span><span class="sxs-lookup"><span data-stu-id="cb9d1-124">For more information, see [Underneath the Hood with .NET and the Windows Runtime](http://msdn.microsoft.com/magazine/jj651569.aspx).</span></span>|  
|`ofReserved1`|<span data-ttu-id="cb9d1-125">保留供內部使用。</span><span class="sxs-lookup"><span data-stu-id="cb9d1-125">Reserved for internal use.</span></span>|  
|`ofReserved2`|<span data-ttu-id="cb9d1-126">保留供內部使用。</span><span class="sxs-lookup"><span data-stu-id="cb9d1-126">Reserved for internal use.</span></span>|  
|`ofReserved`|<span data-ttu-id="cb9d1-127">保留供內部使用。</span><span class="sxs-lookup"><span data-stu-id="cb9d1-127">Reserved for internal use.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cb9d1-128">需求</span><span class="sxs-lookup"><span data-stu-id="cb9d1-128">Requirements</span></span>  
 <span data-ttu-id="cb9d1-129">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cb9d1-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb9d1-130">**標頭：** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="cb9d1-130">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="cb9d1-131">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb9d1-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb9d1-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb9d1-132">See Also</span></span>  
 [<span data-ttu-id="cb9d1-133">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="cb9d1-133">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
