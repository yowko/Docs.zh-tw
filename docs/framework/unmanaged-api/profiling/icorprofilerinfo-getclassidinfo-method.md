---
title: ICorProfilerInfo::GetClassIDInfo 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetClassIDInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetClassIDInfo
helpviewer_keywords:
- GetClassIDInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetClassIDInfo method [.NET Framework profiling]
ms.assetid: 9e93b99e-5aca-415c-8e37-7f33753b612d
topic_type:
- apiref
ms.openlocfilehash: 7d19a43048da742e702636faaa46ecf1458556f5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722581"
---
# <a name="icorprofilerinfogetclassidinfo-method"></a><span data-ttu-id="6f168-102">ICorProfilerInfo::GetClassIDInfo 方法</span><span class="sxs-lookup"><span data-stu-id="6f168-102">ICorProfilerInfo::GetClassIDInfo Method</span></span>

<span data-ttu-id="6f168-103">取得指定類別的父模組和元資料標記。</span><span class="sxs-lookup"><span data-stu-id="6f168-103">Gets the parent module and the metadata token for the specified class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f168-104">語法</span><span class="sxs-lookup"><span data-stu-id="6f168-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClassIDInfo(  
    [in]  ClassID   classId,  
    [out] ModuleID  *pModuleId,  
    [out] mdTypeDef *pTypeDefToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6f168-105">參數</span><span class="sxs-lookup"><span data-stu-id="6f168-105">Parameters</span></span>  

 `classId`  
 <span data-ttu-id="6f168-106">在要取得其資訊之類別的識別碼。</span><span class="sxs-lookup"><span data-stu-id="6f168-106">[in] The ID of the class for which to get the information.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="6f168-107">擴展類別之父模組的識別碼指標。</span><span class="sxs-lookup"><span data-stu-id="6f168-107">[out] A pointer to the ID of the parent module of the class.</span></span>  
  
 `pTypeDefToken`  
 <span data-ttu-id="6f168-108">擴展類別的元資料標記指標。</span><span class="sxs-lookup"><span data-stu-id="6f168-108">[out] A pointer to the metadata token for the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6f168-109">備註</span><span class="sxs-lookup"><span data-stu-id="6f168-109">Remarks</span></span>  

 <span data-ttu-id="6f168-110">分析工具程式碼可以呼叫 [ICorProfilerInfo：： GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md) 來取得指定模組的中繼資料介面。</span><span class="sxs-lookup"><span data-stu-id="6f168-110">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md) to obtain a metadata interface for a given module.</span></span> <span data-ttu-id="6f168-111">然後，傳回至 `pTypeDefToken` 所參考位置的中繼資料語彙基元可以用來存取此類別的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="6f168-111">The metadata token that is returned to the location referenced by `pTypeDefToken` can then be used to access the metadata for the class.</span></span>  
  
 <span data-ttu-id="6f168-112">若要取得泛型型別的詳細資訊，請使用 [ICorProfilerInfo2：： GetClassIDInfo2](icorprofilerinfo2-getclassidinfo2-method.md)。</span><span class="sxs-lookup"><span data-stu-id="6f168-112">To get more information for generic types, use [ICorProfilerInfo2::GetClassIDInfo2](icorprofilerinfo2-getclassidinfo2-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f168-113">需求</span><span class="sxs-lookup"><span data-stu-id="6f168-113">Requirements</span></span>  

 <span data-ttu-id="6f168-114">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6f168-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f168-115">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6f168-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6f168-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6f168-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6f168-117">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f168-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f168-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6f168-118">See also</span></span>

- [<span data-ttu-id="6f168-119">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="6f168-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
