---
title: IMetaDataImport::CountEnum 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.CountEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::CountEnum
helpviewer_keywords:
- CountEnum method [.NET Framework metadata]
- IMetaDataImport::CountEnum method [.NET Framework metadata]
ms.assetid: d1de53ad-9435-4b5f-9df7-07f21210e5b5
topic_type:
- apiref
ms.openlocfilehash: f2470cd7112adff35ef49c21a155072fcd4008be
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727279"
---
# <a name="imetadataimportcountenum-method"></a><span data-ttu-id="2c8d5-102">IMetaDataImport::CountEnum 方法</span><span class="sxs-lookup"><span data-stu-id="2c8d5-102">IMetaDataImport::CountEnum Method</span></span>

<span data-ttu-id="2c8d5-103">取得列舉中由指定列舉值抓取的元素數目。</span><span class="sxs-lookup"><span data-stu-id="2c8d5-103">Gets the number of elements in the enumeration that was retrieved by the specified enumerator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c8d5-104">語法</span><span class="sxs-lookup"><span data-stu-id="2c8d5-104">Syntax</span></span>  
  
```cpp  
HRESULT CountEnum (  
   [in]  HCORENUM    hEnum,
   [out] ULONG       *pulCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2c8d5-105">參數</span><span class="sxs-lookup"><span data-stu-id="2c8d5-105">Parameters</span></span>  

 `hEnum`  
 <span data-ttu-id="2c8d5-106">在列舉值的控制碼。</span><span class="sxs-lookup"><span data-stu-id="2c8d5-106">[in] The handle for the enumerator.</span></span>  
  
 `pulCount`  
 <span data-ttu-id="2c8d5-107">擴展列舉的元素數目。</span><span class="sxs-lookup"><span data-stu-id="2c8d5-107">[out] The number of elements enumerated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2c8d5-108">備註</span><span class="sxs-lookup"><span data-stu-id="2c8d5-108">Remarks</span></span>  

 <span data-ttu-id="2c8d5-109">指定的控制碼 `hEnum` 是從先前的 `Enum` *名稱* 呼叫取得 (例如， [IMetaDataImport：： EnumTypeDefs](imetadataimport-enumtypedefs-method.md)) 。</span><span class="sxs-lookup"><span data-stu-id="2c8d5-109">The handle specified by `hEnum` is obtained from a previous `Enum`*Name* call (for example, [IMetaDataImport::EnumTypeDefs](imetadataimport-enumtypedefs-method.md)).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c8d5-110">需求</span><span class="sxs-lookup"><span data-stu-id="2c8d5-110">Requirements</span></span>  

 <span data-ttu-id="2c8d5-111">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2c8d5-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c8d5-112">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="2c8d5-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2c8d5-113">連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="2c8d5-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2c8d5-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c8d5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c8d5-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2c8d5-115">See also</span></span>

- [<span data-ttu-id="2c8d5-116">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="2c8d5-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="2c8d5-117">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="2c8d5-117">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
