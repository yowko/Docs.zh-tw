---
title: 合約
ms.date: 03/30/2017
ms.assetid: aa00f6b3-7e1f-4213-841a-206463fca20b
ms.openlocfilehash: e4a21e95a6f1f1860ed36c968d17bb8ac8465dce
ms.sourcegitcommit: 9ee6cd851b6e176a5811ea28ed0d5935c71950f9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68868437"
---
# <a name="contract"></a>合約
合約  
  
## <a name="syntax"></a>語法  
  
```csharp
class Contract  
{  
  sint32 AppDomainId;  
  Behavior Behaviors[];  
  string Name;  
  string Namespace;  
  Operation Operations[];  
  sint32 ProcessId;  
  Contract ref;  
  string SessionMode;  
  string Type;  
};  
```  
  
## <a name="methods"></a>方法  
 Contract 類別不會定義任何方法。  
  
## <a name="properties"></a>屬性  
 Contract 類別有下列屬性：  
  
### <a name="appdomainid"></a>AppDomainId  
 資料型別：sint32  
  
 存取類型:唯讀  
  
 裝載合約之的 appdomain 的識別碼。  
  
### <a name="behaviors"></a>「行為」  
 資料類型:行為陣列  
  
 存取類型:唯讀  
  
 與此合約有關聯的行為。  
  
### <a name="name"></a>名稱  
 資料型別：字串  
  
 存取類型:唯讀  
  
 WSDL 中合約的名稱。  
  
### <a name="namespace"></a>命名空間  
 資料型別：字串  
  
 存取類型:唯讀  
  
 WSDL 中 `portType` 項目的命名空間。  
  
### <a name="operations"></a>作業  
 資料類型:Operation 陣列  
  
 存取類型:唯讀  
  
 此合約的作業。  
  
### <a name="processid"></a>ProcessId  
 資料型別：sint32  
  
 存取類型:唯讀  
  
 裝載合約之處理序的處理序識別碼。  
  
### <a name="ref"></a>ref  
 資料類型:合約  
  
 存取類型:唯讀  
  
 當合約是雙工合約時的回呼類型。  
  
### <a name="sessionmode"></a>SessionMode  
 資料型別：字串  
  
 存取類型:唯讀  
  
 代表合約是否需要與此合約關聯的繫結才能使用通道工作階段。  
  
### <a name="type"></a>類型  
 資料型別：字串  
  
 存取類型:唯讀  
  
 合約的類型。  
  
## <a name="requirements"></a>需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------------|  
|命名空間|於 root\ServiceModel 中定義|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Description.ContractDescription>
