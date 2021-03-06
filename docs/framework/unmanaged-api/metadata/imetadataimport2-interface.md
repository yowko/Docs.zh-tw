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
ms.openlocfilehash: a845ecfde6583d625d2a8f165443344ff9e40d05
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95702543"
---
# <a name="imetadataimport2-interface"></a>IMetaDataImport2 介面

擴充 [IMetaDataImport](imetadataimport-interface.md) 介面，以提供使用泛型型別的功能。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[EnumGenericParamConstraints 方法](imetadataimport2-enumgenericparamconstraints-method.md)|取得泛型參數條件約束陣列的列舉值，這些條件約束與指定標記所表示的泛型參數相關聯。|  
|[EnumGenericParams 方法](imetadataimport2-enumgenericparams-method.md)|取得與指定的 TypeDef 或 MethodDef token 相關聯之泛型參數標記陣列的列舉值。|  
|[EnumMethodSpecs 方法](imetadataimport2-enummethodspecs-method.md)|取得與指定的 MethodDef 或 MemberRef token 相關聯的 MethodSpec 標記陣列的列舉值。|  
|[GetGenericParamConstraintProps 方法](imetadataimport2-getgenericparamconstraintprops-method.md)|取得與指定之條件約束 token 所表示之泛型參數條件約束相關聯的中繼資料。|  
|[GetGenericParamProps 方法](imetadataimport2-getgenericparamprops-method.md)|取得與指定標記所表示之泛型參數相關聯的中繼資料。|  
|[GetMethodSpecProps 方法](imetadataimport2-getmethodspecprops-method.md)|取得指定的 MethodSpec token 所參考之方法的中繼資料簽章。|  
|[GetPEKind 方法](imetadataimport2-getpekind-method.md)|取得值，這個值會識別可攜式可執行檔中的程式碼本質， (PE) 檔，通常是 DLL 或 EXE 檔案，定義于目前的中繼資料範圍中。|  
|[GetVersionString 方法](imetadataimport2-getversionstring-method.md)|取得用來建立元件之執行時間的版本號碼。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 當做 MsCorEE.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Reflection.PortableExecutableKinds>
- [中繼資料介面](metadata-interfaces.md)
- [IMetaDataImport 介面](imetadataimport-interface.md)
