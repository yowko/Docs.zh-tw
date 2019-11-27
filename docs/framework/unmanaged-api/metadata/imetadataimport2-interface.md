---
title: IMetaDataImport2 介面
ms.date: 03/30/2017
api_name:
- IMetaDataImport2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2
helpviewer_keywords:
- IMetaDataImport2 interface [.NET Framework metadata]
ms.assetid: d39b2b87-ba53-4771-ae53-952a68452511
topic_type:
- apiref
ms.openlocfilehash: 0fd7915ef46899bdce8312bc6e8a466167e26382
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74429204"
---
# <a name="imetadataimport2-interface"></a><span data-ttu-id="92410-102">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="92410-102">IMetaDataImport2 Interface</span></span>
<span data-ttu-id="92410-103">擴充[IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)介面，以提供使用泛型型別的功能。</span><span class="sxs-lookup"><span data-stu-id="92410-103">Extends the [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface to provide the capability of working with generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="92410-104">方法</span><span class="sxs-lookup"><span data-stu-id="92410-104">Methods</span></span>  
  
|<span data-ttu-id="92410-105">方法</span><span class="sxs-lookup"><span data-stu-id="92410-105">Method</span></span>|<span data-ttu-id="92410-106">描述</span><span class="sxs-lookup"><span data-stu-id="92410-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="92410-107">EnumGenericParamConstraints 方法</span><span class="sxs-lookup"><span data-stu-id="92410-107">EnumGenericParamConstraints Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparamconstraints-method.md)|<span data-ttu-id="92410-108">取得與指定標記所代表的泛型參數相關聯之泛型參數條件約束陣列的列舉值。</span><span class="sxs-lookup"><span data-stu-id="92410-108">Gets an enumerator for an array of generic parameter constraints associated with the generic parameter represented by the specified token.</span></span>|  
|[<span data-ttu-id="92410-109">EnumGenericParams 方法</span><span class="sxs-lookup"><span data-stu-id="92410-109">EnumGenericParams Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparams-method.md)|<span data-ttu-id="92410-110">取得與指定的 TypeDef 或 MethodDef token 相關聯之泛型參數標記陣列的列舉值。</span><span class="sxs-lookup"><span data-stu-id="92410-110">Gets an enumerator for an array of generic parameter tokens associated with the specified TypeDef or MethodDef token.</span></span>|  
|[<span data-ttu-id="92410-111">EnumMethodSpecs 方法</span><span class="sxs-lookup"><span data-stu-id="92410-111">EnumMethodSpecs Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enummethodspecs-method.md)|<span data-ttu-id="92410-112">取得與指定的 MethodDef 或 MemberRef token 相關聯的 MethodSpec 標記陣列的列舉值。</span><span class="sxs-lookup"><span data-stu-id="92410-112">Gets an enumerator for an array of MethodSpec tokens associated with the specified MethodDef or MemberRef token.</span></span>|  
|[<span data-ttu-id="92410-113">GetGenericParamConstraintProps 方法</span><span class="sxs-lookup"><span data-stu-id="92410-113">GetGenericParamConstraintProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamconstraintprops-method.md)|<span data-ttu-id="92410-114">取得與指定之條件約束標記所表示的泛型參數條件約束相關聯的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="92410-114">Gets the metadata associated with the generic parameter constraint represented by the specified constraint token.</span></span>|  
|[<span data-ttu-id="92410-115">GetGenericParamProps 方法</span><span class="sxs-lookup"><span data-stu-id="92410-115">GetGenericParamProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamprops-method.md)|<span data-ttu-id="92410-116">取得與指定標記所表示的泛型參數相關聯的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="92410-116">Gets the metadata associated with the generic parameter represented by the specified token.</span></span>|  
|[<span data-ttu-id="92410-117">GetMethodSpecProps 方法</span><span class="sxs-lookup"><span data-stu-id="92410-117">GetMethodSpecProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getmethodspecprops-method.md)|<span data-ttu-id="92410-118">取得指定的 MethodSpec token 所參考之方法的中繼資料簽章。</span><span class="sxs-lookup"><span data-stu-id="92410-118">Gets the metadata signature of the method referenced by the specified MethodSpec token.</span></span>|  
|[<span data-ttu-id="92410-119">GetPEKind 方法</span><span class="sxs-lookup"><span data-stu-id="92410-119">GetPEKind Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md)|<span data-ttu-id="92410-120">取得值，識別可移植執行檔（PE）中的程式碼本質，通常是在目前中繼資料範圍中定義的 DLL 或 EXE 檔案</span><span class="sxs-lookup"><span data-stu-id="92410-120">Gets a value identifying the nature of the code in a portable executable (PE) file, typically a DLL or EXE file, defined in the current metadata scope</span></span>|  
|[<span data-ttu-id="92410-121">GetVersionString 方法</span><span class="sxs-lookup"><span data-stu-id="92410-121">GetVersionString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getversionstring-method.md)|<span data-ttu-id="92410-122">取得用來建立元件之執行時間的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="92410-122">Gets the version number of the runtime that was used to build the assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="92410-123">需求</span><span class="sxs-lookup"><span data-stu-id="92410-123">Requirements</span></span>  
 <span data-ttu-id="92410-124">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="92410-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92410-125">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="92410-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="92410-126">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="92410-126">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="92410-127">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92410-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92410-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="92410-128">See also</span></span>

- <xref:System.Reflection.PortableExecutableKinds>
- [<span data-ttu-id="92410-129">中繼資料介面</span><span class="sxs-lookup"><span data-stu-id="92410-129">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="92410-130">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="92410-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
