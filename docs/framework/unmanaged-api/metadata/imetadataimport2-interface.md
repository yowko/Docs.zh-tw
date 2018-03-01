---
title: "IMetaDataImport2 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7cd9d2cd2837ff43fbb266717546db3aa98190e3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimport2-interface"></a>IMetaDataImport2 介面
擴充[IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)介面，以提供使用泛型類型的功能。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[EnumGenericParamConstraints 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparamconstraints-method.md)|取得與指定語彙基元所代表的泛型參數相關聯的泛型參數條件約束的陣列的列舉值。|  
|[EnumGenericParams 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparams-method.md)|陣列的泛型參數指定的 TypeDef 或 MethodDef 相關聯的語彙基元的列舉值取得語彙基元。|  
|[EnumMethodSpecs 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enummethodspecs-method.md)|取得列舉值陣列的 MethodSpec 語彙基元相關聯的指定 MethodDef 或 MemberRef 語彙基元。|  
|[GetGenericParamConstraintProps 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamconstraintprops-method.md)|取得與指定的條件約束語彙基元所代表的泛型參數條件約束相關聯的中繼資料。|  
|[GetGenericParamProps 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamprops-method.md)|取得與指定語彙基元所代表的泛型參數相關聯的中繼資料。|  
|[GetMethodSpecProps 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getmethodspecprops-method.md)|取得所指定的 MethodSpec 參考方法的中繼資料簽章語彙基元。|  
|[GetPEKind 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md)|取得值，識別可攜式執行檔 (PE) 中的程式碼的本質檔，通常是 DLL 或 EXE 檔，在目前中繼資料範圍中定義|  
|[GetVersionString 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getversionstring-method.md)|取得執行階段用來建置組件的版本號碼。|  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：**做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Reflection.PortableExecutableKinds>  
 [中繼資料介面](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
