---
title: "IMetaDataImport2 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport2
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport2
helpviewer_keywords: IMetaDataImport2 interface [.NET Framework metadata]
ms.assetid: d39b2b87-ba53-4771-ae53-952a68452511
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1b00879f1d22d49e5f0dc3bdb072e0545feda68d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimport2-interface"></a><span data-ttu-id="d41ad-102">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="d41ad-102">IMetaDataImport2 Interface</span></span>
<span data-ttu-id="d41ad-103">擴充[IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)介面，以提供使用泛型類型的功能。</span><span class="sxs-lookup"><span data-stu-id="d41ad-103">Extends the [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface to provide the capability of working with generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d41ad-104">方法</span><span class="sxs-lookup"><span data-stu-id="d41ad-104">Methods</span></span>  
  
|<span data-ttu-id="d41ad-105">方法</span><span class="sxs-lookup"><span data-stu-id="d41ad-105">Method</span></span>|<span data-ttu-id="d41ad-106">說明</span><span class="sxs-lookup"><span data-stu-id="d41ad-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d41ad-107">EnumGenericParamConstraints 方法</span><span class="sxs-lookup"><span data-stu-id="d41ad-107">EnumGenericParamConstraints Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparamconstraints-method.md)|<span data-ttu-id="d41ad-108">取得與指定語彙基元所代表的泛型參數相關聯的泛型參數條件約束的陣列的列舉值。</span><span class="sxs-lookup"><span data-stu-id="d41ad-108">Gets an enumerator for an array of generic parameter constraints associated with the generic parameter represented by the specified token.</span></span>|  
|[<span data-ttu-id="d41ad-109">EnumGenericParams 方法</span><span class="sxs-lookup"><span data-stu-id="d41ad-109">EnumGenericParams Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparams-method.md)|<span data-ttu-id="d41ad-110">陣列的泛型參數指定的 TypeDef 或 MethodDef 相關聯的語彙基元的列舉值取得語彙基元。</span><span class="sxs-lookup"><span data-stu-id="d41ad-110">Gets an enumerator for an array of generic parameter tokens associated with the specified TypeDef or MethodDef token.</span></span>|  
|[<span data-ttu-id="d41ad-111">EnumMethodSpecs 方法</span><span class="sxs-lookup"><span data-stu-id="d41ad-111">EnumMethodSpecs Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enummethodspecs-method.md)|<span data-ttu-id="d41ad-112">取得列舉值陣列的 MethodSpec 語彙基元相關聯的指定 MethodDef 或 MemberRef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="d41ad-112">Gets an enumerator for an array of MethodSpec tokens associated with the specified MethodDef or MemberRef token.</span></span>|  
|[<span data-ttu-id="d41ad-113">GetGenericParamConstraintProps 方法</span><span class="sxs-lookup"><span data-stu-id="d41ad-113">GetGenericParamConstraintProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamconstraintprops-method.md)|<span data-ttu-id="d41ad-114">取得與指定的條件約束語彙基元所代表的泛型參數條件約束相關聯的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="d41ad-114">Gets the metadata associated with the generic parameter constraint represented by the specified constraint token.</span></span>|  
|[<span data-ttu-id="d41ad-115">GetGenericParamProps 方法</span><span class="sxs-lookup"><span data-stu-id="d41ad-115">GetGenericParamProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamprops-method.md)|<span data-ttu-id="d41ad-116">取得與指定語彙基元所代表的泛型參數相關聯的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="d41ad-116">Gets the metadata associated with the generic parameter represented by the specified token.</span></span>|  
|[<span data-ttu-id="d41ad-117">GetMethodSpecProps 方法</span><span class="sxs-lookup"><span data-stu-id="d41ad-117">GetMethodSpecProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getmethodspecprops-method.md)|<span data-ttu-id="d41ad-118">取得所指定的 MethodSpec 參考方法的中繼資料簽章語彙基元。</span><span class="sxs-lookup"><span data-stu-id="d41ad-118">Gets the metadata signature of the method referenced by the specified MethodSpec token.</span></span>|  
|[<span data-ttu-id="d41ad-119">GetPEKind 方法</span><span class="sxs-lookup"><span data-stu-id="d41ad-119">GetPEKind Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md)|<span data-ttu-id="d41ad-120">取得值，識別可攜式執行檔 (PE) 中的程式碼的本質檔，通常是 DLL 或 EXE 檔，在目前中繼資料範圍中定義</span><span class="sxs-lookup"><span data-stu-id="d41ad-120">Gets a value identifying the nature of the code in a portable executable (PE) file, typically a DLL or EXE file, defined in the current metadata scope</span></span>|  
|[<span data-ttu-id="d41ad-121">GetVersionString 方法</span><span class="sxs-lookup"><span data-stu-id="d41ad-121">GetVersionString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getversionstring-method.md)|<span data-ttu-id="d41ad-122">取得執行階段用來建置組件的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="d41ad-122">Gets the version number of the runtime that was used to build the assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d41ad-123">需求</span><span class="sxs-lookup"><span data-stu-id="d41ad-123">Requirements</span></span>  
 <span data-ttu-id="d41ad-124">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d41ad-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d41ad-125">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d41ad-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d41ad-126">**程式庫：**做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d41ad-126">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d41ad-127">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d41ad-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d41ad-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d41ad-128">See Also</span></span>  
 <xref:System.Reflection.PortableExecutableKinds>  
 [<span data-ttu-id="d41ad-129">中繼資料介面</span><span class="sxs-lookup"><span data-stu-id="d41ad-129">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="d41ad-130">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="d41ad-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
